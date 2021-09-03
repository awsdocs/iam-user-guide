# Configuring MFA\-protected API access<a name="id_credentials_mfa_configure-api-require"></a>

With IAM policies, you can specify which API operations a user is allowed to call\. In some cases, you might want the additional security of requiring users to be authenticated with AWS multi\-factor authentication \(MFA\) before you allow them to perform particularly sensitive actions\.

For example, you might have a policy that allows a user to perform the Amazon EC2 `RunInstances`, `DescribeInstances`, and `StopInstances` actions\. But you might want to restrict a destructive action like `TerminateInstances` and ensure that users can perform that action only if they authenticate with an AWS MFA device\.

**Topics**
+ [Overview](#MFAProtectedAPI-overview)
+ [Scenario: MFA protection for cross\-account delegation](#MFAProtectedAPI-cross-account-delegation)
+ [Scenario: MFA protection for access to API operations in the current account](#MFAProtectedAPI-user-mfa)
+ [Scenario: MFA protection for resources that have resource\-based policies](#MFAProtectedAPI-resource-policies)

## Overview<a name="MFAProtectedAPI-overview"></a>

Adding MFA protection to API operations involves these tasks:

1. The administrator configures an AWS MFA device for each user who needs to make API requests that require MFA authentication\. This process is described at [Enabling MFA devices for users in AWS](id_credentials_mfa_enable.md)\. 

1. The administrator creates policies for the users that include a `Condition` element that checks whether the user authenticated with an AWS MFA device\.

1. The user calls one of the AWS STS API operations that support the MFA parameters [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) or [GetSessionToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html), depending on the scenario for MFA protection, as explained later\. As part of the call, the user includes the device identifier for the device that's associated with the user\. The user also includes the time\-based one\-time password \(TOTP\) that the device generates\. In either case, the user gets back temporary security credentials that the user can then use to make additional requests to AWS\.
**Note**  
MFA protection for a service's API operations is available only if the service supports temporary security credentials\. For a list of these services, see [ Using Temporary Security Credentials to Access AWS](https://docs.aws.amazon.com/STS/latest/UsingSTS/UsingTokens.html)\.

If authorization fails, AWS returns an access denied error message \(as it does for any unauthorized access\)\. With MFA\-protected API policies in place, AWS denies access to the API operations specified in the policies if the user attempts to call an API operation without valid MFA authentication\. The operation is also denied if the time stamp of the request for the API operation is outside of the allowed range specified in the policy\. The user must be reauthenticated with MFA by requesting new temporary security credentials with an MFA code and device serial number\.

### IAM policies with MFA conditions<a name="MFAProtectedAPI-policies"></a>

Policies with MFA conditions can be attached to the following:
+ An IAM user or group
+ A resource such as an Amazon S3 bucket, Amazon SQS queue, or Amazon SNS topic
+ The trust policy of an IAM role that can be assumed by a user

You can use an MFA condition in a policy to check the following properties:
+ Existence—To simply verify that the user did authenticate with MFA, check that the `aws:MultiFactorAuthPresent` key is `True` in a `Bool` condition\. The key is only present when the user authenticates with short\-term credentials\. Long\-term credentials, such as access keys, do not include this key\.
+ Duration—If you want to grant access only within a specified time after MFA authentication, use a numeric condition type to compare the `aws:MultiFactorAuthAge` key's age to a value \(such as 3600 seconds\)\. Note that the `aws:MultiFactorAuthAge` key is not present if MFA was not used\.

The following example shows the trust policy of an IAM role that includes an MFA condition to test for the existence of MFA authentication\. With this policy, users from the AWS account specified in the `Principal` element \(replace `ACCOUNT-B-ID` with a valid AWS account ID\) can assume the role that this policy is attached to\. However such users can only assume the role if the user is authenticated using MFA\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {"AWS": "ACCOUNT-B-ID"},
    "Action": "sts:AssumeRole",
    "Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
  }
}
```

For more information on the condition types for MFA, see [AWS global condition context keys](reference_policies_condition-keys.md), [Numeric condition operators](reference_policies_elements_condition_operators.md#Conditions_Numeric), and [Condition operator to check existence of condition keys ](reference_policies_elements_condition_operators.md#Conditions_Null)\. 

### Choosing between GetSessionToken and AssumeRole<a name="scenarios"></a>

AWS STS provides two API operations that let users pass MFA information: `GetSessionToken` and `AssumeRole`\. The API operation that the user calls to get temporary security credentials depends on which of the following scenarios applies\. 

**Use `GetSessionToken` for the following scenarios:**
+ Call API operations that access resources in the same AWS account as the IAM user who makes the request\. Note that temporary credentials from a `GetSessionToken` request can access IAM and AWS STS API operations *only* if you include MFA information in the request for credentials\. Because temporary credentials returned by `GetSessionToken` include MFA information, you can check for MFA in individual API operations made by the credentials\. 
+ Access to resources that are protected with resource\-based policies that include an MFA condition\.

The purpose of the `GetSessionToken` operation is to authenticate the user using MFA\. You cannot use policies to control authentication operations\.

**Use `AssumeRole` for the following scenarios:**
+ Call API operations that access resources in the same or a different AWS account\. The API calls can include any IAM or AWS STS API\. Note that to protect access you enforce MFA at the time when the user assumes the role\. The temporary credentials returned by `AssumeRole` do not include MFA information in the context, so you cannot check individual API operations for MFA\. This is why you must use `GetSessionToken` to restrict access to resources protected by resource\-based policies\.

Details about how to implement these scenarios are provided later in this document\.

### Important points about MFA\-protected API access<a name="MFAProtectedAPI-important-points"></a>

It's important to understand the following aspects of MFA protection for API operations:
+ MFA protection is available only with temporary security credentials, which must be obtained with `AssumeRole` or `GetSessionToken`\. 
+ You cannot use MFA\-protected API access with AWS account root user credentials\.
+ You cannot use MFA\-protected API access with U2F security keys\.
+ Federated users cannot be assigned an MFA device for use with AWS services, so they cannot access AWS resources controlled by MFA\. \(See next point\.\) 
+ Other AWS STS API operations that return temporary credentials do not support MFA\. For `AssumeRoleWithWebIdentity` and `AssumeRoleWithSAML`, the user is authenticated by an external provider and AWS cannot determine whether that provider required MFA\. For `GetFederationToken`, MFA is not necessarily associated with a specific user\. 
+ Similarly, long\-term credentials \(IAM user access keys and root user access keys\) cannot be used with MFA\-protected API access because they don't expire\.
+ `AssumeRole` and `GetSessionToken` can also be called without MFA information\. In that case, the caller gets back temporary security credentials, but the session information for those temporary credentials does not indicate that the user authenticated with MFA\.
+ To establish MFA protection for API operations, you add MFA conditions to policies\. A policy must include the `aws:MultiFactorAuthPresent` condition key to enforce the use of MFA\. For cross\-account delegation, the role's trust policy must include the condition key\.
+ When you allow another AWS account to access resources in your account, the security of your resources depends on the configuration of the trusted account \(the other account, not yours\)\. This is true even when you require multi\-factor authentication\. Any identity in the trusted account that has permission to create virtual MFA devices can construct an MFA claim to satisfy that part of your role's trust policy\. Before you allow members of another account access to your AWS resources that require multi\-factor authentication, you should ensure that the trusted account's owner follows security best practices\. For example, the trusted account should restrict access to sensitive API operations, such as MFA device\-management API operations, to specific, trusted identities\.
+ If a policy includes an MFA condition, a request is denied if users have not been MFA authenticated, or if they provide an invalid MFA device identifier or invalid TOTP\.

## Scenario: MFA protection for cross\-account delegation<a name="MFAProtectedAPI-cross-account-delegation"></a>

In this scenario, you want to delegate access to IAM users in another account, but only if the users are authenticated with an AWS MFA device\. \(For more information about cross\-account delegation, see [Roles terms and concepts](id_roles_terms-and-concepts.md)\. 

Imagine that you have account A \(the trusting account that owns the resource to be accessed\), with the IAM user Anaya, who has administrator permission\. She wants to grant access to user Richard in account B \(the trusted account\), but wants to make sure that Richard is authenticated with MFA before he assumes the role\. 

1. In the trusting account A, Anaya creates an IAM role named `CrossAccountRole` and sets the principal in the role's trust policy to the account ID of account B\. The trust policy grants permission to the AWS STS `AssumeRole` action\. Anaya also adds an MFA condition to the trust policy, as in the following example\. 

   ```
   {
     "Version": "2012-10-17",
     "Statement": {
       "Effect": "Allow",
       "Principal": {"AWS": "ACCOUNT-B-ID"},
       "Action": "sts:AssumeRole",
       "Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
     }
   }
   ```

1. Anaya adds a permissions policy to the role that specifies what the role is allowed to do\. The permissions policy for a role with MFA protection is no different than any other role\-permission policy\. The following example shows the policy that Anaya adds to the role; it allows an assuming user to perform any Amazon DynamoDB action on the table `Books` in account A\. This policy also allows the `dynamodb:ListTables` action, which is required to perform actions in the console\. 
**Note**  
The permissions policy does not include an MFA condition\. It is important to understand that the MFA authentication is used only to determine whether a user can assume the role\. Once the user has assumed the role, no further MFA checks are made\. 

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Sid": "TableActions",
               "Effect": "Allow",
               "Action": "dynamodb:*",
               "Resource": "arn:aws:dynamodb:*:ACCOUNT-A-ID:table/Books"
           },
           {
               "Sid": "ListTable",
               "Effect": "Allow",
               "Action": "dynamodb:ListTable",
               "Resource": "*"
           }
       ]
   }
   ```

1. In trusted account B, the administrator makes sure that IAM user Richard is configured with an AWS MFA device and that he knows the ID of the device\. The device ID is the serial number if it's a hardware MFA device, or the device's ARN if it's a virtual MFA device\.

1. In account B, the administrator attaches the following policy to user Richard \(or a group that he's a member of\) that allows him to call the `AssumeRole` action\. The resource is set to the ARN of the role that Anaya created in step 1\. Notice that this policy does not contain an MFA condition\.

   ```
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Effect": "Allow",
       "Action": ["sts:AssumeRole"],
       "Resource": ["arn:aws:iam::ACCOUNT-A-ID:role/CrossAccountRole"]
     }]
   }
   ```

1. In account B, Richard \(or an application that Richard is running\) calls `AssumeRole`\. The API call includes the ARN of the role to assume \(`arn:aws:iam::ACCOUNT-A-ID:role/CrossAccountRole`\), the ID of the MFA device, and the current TOTP that Richard gets from his device\. 

   When Richard calls `AssumeRole`, AWS determines whether he has valid credentials, including the requirement for MFA\. If so, Richard successfully assumes the role and can perform any DynamoDB action on the table named `Books` in account A while using the role's temporary credentials\. 

   For an example of a program that calls `AssumeRole`, see [Calling AssumeRole with MFA authentication \(Python\)](id_credentials_mfa_sample-code.md#MFAProtectedAPI-example-assumerole)\.

## Scenario: MFA protection for access to API operations in the current account<a name="MFAProtectedAPI-user-mfa"></a>

In this scenario, you should ensure that a user in your AWS account can access sensitive API operations only when the user is authenticated using an AWS MFA device\.

Imagine that you have account A that contains a group of developers who need to work with EC2 instances\. Ordinary developers can work with the instances, but they are not granted permissions for the `ec2:StopInstances` or `ec2:TerminateInstances` actions\. You want to limit those "destructive" privileged actions to just a few trusted users, so you add MFA protection to the policy that allows these sensitive Amazon EC2 actions\. 

In this scenario, one of those trusted users is user Sofía\. User Anaya is an administrator in account A\. 

1. Anaya makes sure that Sofía is configured with an AWS MFA device and that Sofía knows the ID of the device\. The device ID is the serial number if it's a hardware MFA device, or the device's ARN if it's a virtual MFA device\. 

1. Anaya creates a group named `EC2-Admins` and adds user Sofía to the group\.

1. Anaya attaches the following policy to the `EC2-Admins` group\. This policy grants users permission to call the Amazon EC2 `StopInstances` and `TerminateInstances` actions only if the user has authenticated using MFA\. 

   ```
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Effect": "Allow",
       "Action": [
         "ec2:StopInstances",
         "ec2:TerminateInstances"
       ],
       "Resource": ["*"],
       "Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
     }]
   }
   ```

1. 
**Note**  
For this policy to take effect, users must first sign out and then sign in again\.

   If user Sofía needs to stop or terminate an Amazon EC2 instance, she \(or an application that she is running\) calls `GetSessionToken`\. This API operation passes the ID of the MFA device and the current TOTP that Sofía gets from her device\.

1. User Sofía \(or an application that Sofía is using\) uses the temporary credentials provided by `GetSessionToken` to call the Amazon EC2 `StopInstances` or `TerminateInstances` action\. 

   For an example of a program that calls `GetSessionToken`, see [Calling GetSessionToken with MFA authentication \(Python and C\#\)](id_credentials_mfa_sample-code.md#MFAProtectedAPI-example-getsessiontoken) later in this document\.

## Scenario: MFA protection for resources that have resource\-based policies<a name="MFAProtectedAPI-resource-policies"></a>

In this scenario, you are the owner of an S3 bucket, an SQS queue, or an SNS topic\. You want to make sure that any user from any AWS account who accesses the resource is authenticated by an AWS MFA device\. 

This scenario illustrates a way to provide cross\-account MFA protection without requiring users to assume a role first\. In this case, the user can access the resource if three conditions are met: The user must be authenticated by MFA, be able to get temporary security credentials from `GetSessionToken`, and be in an account that is trusted by the resource's policy\. 

Imagine that you are in account A and you create an S3 bucket\. You want to grant access to this bucket to users who are in several different AWS accounts, but only if those users are authenticated with MFA\.

In this scenario, user Anaya is an administrator in account A\. User Nikhil is an IAM user in account C\.

1. In account A, Anaya creates a bucket named `Account-A-bucket`\.

1. Anaya adds the bucket policy to the bucket\. The policy allows any user in account A, account B, or account C to perform the Amazon S3 `PutObject` and `DeleteObject` actions in the bucket\. The policy includes an MFA condition\. 

   ```
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Effect": "Allow",
       "Principal": {"AWS": [
         "ACCOUNT-A-ID",
         "ACCOUNT-B-ID",
         "ACCOUNT-C-ID"
       ]},
       "Action": [
         "s3:PutObject",
         "s3:DeleteObject"
       ],
       "Resource": ["arn:aws:s3:::ACCOUNT-A-BUCKET-NAME/*"],
       "Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
     }]
   }
   ```
**Note**  
Amazon S3 offers an MFA Delete feature for *root* account access \(only\)\. You can enable Amazon S3 MFA Delete when you set the versioning state of the bucket\. Amazon S3 MFA Delete cannot be applied to an IAM user, and is managed independently from MFA\-protected API access\. An IAM user with permissions to delete a bucket cannot delete a bucket with Amazon S3 MFA Delete enabled\. For more information on Amazon S3 MFA Delete, see [MFA Delete](https://docs.aws.amazon.com/AmazonS3/latest/dev/MultiFactorAuthenticationDelete.html)\.

1. In account C, an administrator makes sure that user Nikhil is configured with an AWS MFA device and that he knows the ID of the device\. The device ID is the serial number if it's a hardware MFA device, or the device's ARN if it's a virtual MFA device\. 

1. In account C, Nikhil \(or an application that he is running\) calls `GetSessionToken`\. The call includes the ID or ARN of the MFA device and the current TOTP that Nikhil gets from his device\. 

1. Nikhil \(or an application that he is using\) uses the temporary credentials returned by `GetSessionToken` to call the Amazon S3 `PutObject` action to upload a file to `Account-A-bucket`\. 

   For an example of a program that calls `GetSessionToken`, see [Calling GetSessionToken with MFA authentication \(Python and C\#\)](id_credentials_mfa_sample-code.md#MFAProtectedAPI-example-getsessiontoken) later in this document\.
**Note**  
The temporary credentials that `AssumeRole` returns won't work in this case\. Although the user can provide MFA information to assume a role, the temporary credentials returned by `AssumeRole` don't include the MFA information\. That information is required in order to meet the MFA condition in the policy\. 