# Configuring MFA\-Protected API Access<a name="id_credentials_mfa_configure-api-require"></a>

With IAM policies, you can specify which APIs a user is allowed to call\. In some cases, you might want the additional security of requiring a user to be authenticated with AWS multi\-factor authentication \(MFA\) before the user is allowed to perform particularly sensitive actions\.

For example, you might have a policy that allows a user to perform the Amazon EC2 `RunInstances`, `DescribeInstances`, and `StopInstances` actions\. But you might want to restrict a destructive action like `TerminateInstances` and ensure that users can perform that action only if they authenticate with an AWS MFA device\.

**Topics**
+ [Overview](#MFAProtectedAPI-overview)
+ [Scenario: MFA Protection for Cross\-Account Delegation](#MFAProtectedAPI-cross-account-delegation)
+ [Scenario: MFA Protection for Access to APIs in the Current Account](#MFAProtectedAPI-user-mfa)
+ [Scenario: MFA Protection for Resources That Have Resource\-based Policies](#MFAProtectedAPI-resource-policies)

## Overview<a name="MFAProtectedAPI-overview"></a>

Adding MFA protection to APIs involves these tasks:

1. The administrator configures an AWS MFA device for each user who needs to make API requests that require MFA authentication\. This process is described at [Enabling MFA Devices](id_credentials_mfa_enable.md)\. 

1. The administrator creates policies for the users that include a `Condition` element that checks whether the user authenticated with an AWS MFA device\.

1. The user calls one of the STS APIs that support the MFA parameters [AssumeRole](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) or [GetSessionToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html), depending on the scenario for MFA protection, as explained later\. As part of the call, the user includes the device identifier for the device that's associated with the user, as well as the time\-based one\-time password \(TOTP\) that the device generates\. In either case, the user gets back temporary security credentials that the user can then use to make additional requests to AWS\.
**Note**  
MFA protection for a service's APIs is available only if the service supports temporary security credentials\. For a list of these services, see [ Using Temporary Security Credentials to Access AWS](http://docs.aws.amazon.com/STS/latest/UsingSTS/UsingTokens.html)\.

If authorization fails, AWS returns an "Access Denied" error message \(as it does for any unauthorized access\)\. With MFA\-protected API policies in place, AWS denies access to the APIs specified in the policies if the user attempts to use an API without valid MFA authentication or if the timestamp of the request for the API is outside of the allowed range specified in the policy\. The user must be reauthenticated with MFA by requesting new temporary security credentials with an MFA code and device serial number\.

### IAM Policies with MFA Conditions<a name="MFAProtectedAPI-policies"></a>

Policies with MFA conditions can be attached to the following:
+ An IAM user or group
+ A resource such as an Amazon S3 bucket, Amazon SQS queue, or Amazon SNS topic
+ The trust policy of an IAM role that can be assumed by a user

You can use an MFA condition in a policy to check the following properties:
+ Existence—To simply verify that the user did authenticate with MFA, check that the `aws:MultiFactorAuthPresent` key is `True` in a `Bool` condition\. The key is only present when the user authenticates with short term credentials\. Long term credentials, such as access keys, do not include this key\.
+ Duration—If you want to grant access only within a specified time after MFA authentication, use a numeric condition type to compare the `aws:MultiFactorAuthAge` key's age to a value \(such as 3600 seconds\)\. Note that the `aws:MultiFactorAuthAge` key is not present if MFA was not used\.

The following example shows the trust policy of an IAM role that includes an MFA condition to test for the existence of MFA authentication\. With this policy, users from the AWS account specified in the `Principal` element \(replace `ACCOUNT-B-ID` with a valid AWS account ID\) can assume the role that this policy is attached to, but only if the user is MFA authenticated\.

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

For more information on the condition types for MFA, see [AWS Global Condition Context Keys](reference_policies_condition-keys.md), [Numeric Condition Operators](reference_policies_elements_condition_operators.md#Conditions_Numeric), and [Condition Operator to Check Existence of Condition Keys ](reference_policies_elements_condition_operators.md#Conditions_Null) 

### Choosing Between GetSessionToken and AssumeRole<a name="scenarios"></a>

AWS STS provides two APIs that let users pass MFA information: `GetSessionToken` and `AssumeRole`\. The API that the user calls to get temporary security credentials depends on which of the following scenarios applies\. 

Use `GetSessionToken` for these scenarios:
+ Call APIs that access resources in the same AWS account as the IAM user who makes the request\. Note that temporary credentials from a `GetSessionToken` request can access IAM and STS APIs *only* if you include MFA information in the request for credentials\. Because temporary credentials returned by `GetSessionToken` include MFA information, you can check for MFA in individual API calls made by the credentials\.
+ Access to resources that are protected with resource\-based policies that include an MFA condition\.

Use `AssumeRole` for these scenarios:
+ Call APIs that access resources in the same or a different AWS account\. The API calls can include any IAM or STS API\. Note that to protect access you enforce MFA at the time when the user assumes the role\. The temporary credentials returned by `AssumeRole` do not include MFA information in the context, so you cannot check individual API calls for MFA\. This is why you must use `GetSessionToken` to restrict access to resources protected by resource\-based policies\.

Details about how to implement these scenarios are provided later in this document\.

### Important Points About MFA\-Protected API Access<a name="MFAProtectedAPI-important-points"></a>

It's important to understand the following aspects of MFA protection for APIs:
+ MFA protection is available only with temporary security credentials, which must be obtained with `AssumeRole` or `GetSessionToken`\. 
+ You cannot use MFA\-protected API access with AWS account root user credentials\.
+ Federated users cannot be assigned an MFA device for use with AWS services, so they cannot access AWS resources controlled by MFA\. \(See next point\.\) 
+ Other AWS STS APIs that return temporary credentials do not support MFA\. For `AssumeRoleWithWebIdentity` and `AssumeRoleWithSAML`, the user is authenticated by an external provider and AWS cannot determine whether that provider required MFA\. For `GetFederationToken`, MFA is not necessarily associated with a specific user\. 
+ Similarly, long\-term credentials \(IAM user access keys and root user access keys\) cannot be used with MFA\-protected API access because they don't expire\.
+ `AssumeRole` and `GetSessionToken` can also be called without MFA information\. In that case, the caller gets back temporary security credentials, but the session information for those temporary credentials does not indicate that the user authenticated with MFA\.
+ To establish MFA protection for APIs, you add MFA conditions to policies\. If a policy doesn't include the condition for MFAs, the policy does not enforce the use of MFA\. For cross\-account delegation, if the role's trust policy doesn’t include an MFA condition then there is no MFA protection for the API calls that are made with the role's temporary security credentials\.
+ When you allow another AWS account to access resources in your account, *even when you require multi\-factor authentication*, the security of your resources depends on the configuration of the trusted account—that is, the other account \(not yours\)\. Any identity in the trusted account that has permission to create virtual MFA devices can construct an MFA claim to satisfy that part of your role's trust policy\. Before you allow another account's access to your AWS resources that require multi\-factor authentication, you should ensure that the trusted account's owner follows security best practices and restricts access to sensitive APIs—such as MFA device\-management APIs—to specific, trusted identities\.
+ If a policy includes an MFA condition, a request is denied if users have not been MFA authenticated, or if they provide an invalid MFA device identifier or invalid TOTP\.

## Scenario: MFA Protection for Cross\-Account Delegation<a name="MFAProtectedAPI-cross-account-delegation"></a>

In this scenario, you want to delegate access to IAM users in another account, but only if the users are authenticated with an AWS MFA device\. \(For more information about cross\-account delegation, see [Roles Terms and Concepts](id_roles_terms-and-concepts.md)\. 

Imagine that you have account A \(the trusting account that owns the resource to be accessed\), with the IAM user Alice, who has administrator permission\. She wants to grant access to user Bob in account B \(the trusted account\), but wants to make sure that Bob is authenticated with MFA before he assumes the role\. 

1. In the trusting account A, Alice creates an IAM role named `CrossAccountRole` and sets the principal in the role's trust policy to the account ID of account B\. The trust policy grants permission to the AWS STS `AssumeRole` action\. Alice also adds an MFA condition to the trust policy, as in the following example\. 

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

1. Alice adds a permission policy to the role that specifies what the role is allowed to do\. The permission policy for a role with MFA protection is no different than any other role\-permission policy\. The following example shows the policy that Alice adds to the role; it allows an assuming user to perform any DynamoDB action on the table `Books` in account A\. 
**Note**  
The permission policy does not include an MFA condition\. It is important to understand that the MFA authentication is used only to determine whether a user can assume the role\. Once the user has assumed the role, no further MFA checks are made\. 

   ```
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Effect": "Allow",
       "Action": ["dynamodb:*"],
       "Resource": ["arn:aws:dynamodb:region:ACCOUNT-A-ID:table/Books"]
     }]
   }
   ```

1. In trusted account B, the administrator makes sure that IAM user Bob is configured with an AWS MFA device and that he knows the ID of the device—that is, the serial number if it's a hardware MFA device, or the device's ARN if it's a virtual MFA device\.

1. In account B, the administrator attaches the following policy to user Bob \(or a group that he's a member of\) that allows him to call the `AssumeRole` action\. The resource is set to the ARN of the role that Alice created in step 1\. Notice that this policy does not contain an MFA condition\.

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

1. In account B, Bob \(or an application that Bob is running\) calls `AssumeRole`\. The API call includes the ARN of the role to assume \(`arn:aws:iam::ACCOUNT-A-ID:role/CrossAccountRole`\), the ID of the MFA device, and the current TOTP that Bob gets from his device\. 

   When Bob calls `AssumeRole`, AWS determines whether he has valid credentials, including the requirement for MFA\. If so, Bob successfully assumes the role and can perform any DynamoDB action on the table named `Books` in account A while using the role's temporary credentials\. 

   For an example of a program that calls `AssumeRole`, see [Calling AssumeRole with MFA Authentication \(Python\)](id_credentials_mfa_sample-code.md#MFAProtectedAPI-example-assumerole)\.

## Scenario: MFA Protection for Access to APIs in the Current Account<a name="MFAProtectedAPI-user-mfa"></a>

In this scenario, you want to make sure that a user in your AWS account can access sensitive API actions only when the user is authenticated using an AWS MFA device\.

Imagine that you have account A that contains a group of developers who need to work with EC2 instances\. Ordinary developers can work with the instances, but they are not granted permissions for the `ec2:StopInstances` or `ec2:TerminateInstances` actions\. You want to limit those "destructive" privileged actions to just a few trusted users, so you add MFA protection to the policy that allows these sensitive Amazon EC2 actions\. 

In this scenario, one of those trusted users is user Carol\. User Alice is an administrator in account A\. 

1. Alice makes sure that Carol is configured with an AWS MFA device and that Carol knows the ID of the device—the serial number if it's a hardware MFA device, or the device's ARN if it's a virtual MFA device\. 

1. Alice creates a group named `EC2-Admins` and adds user Carol to the group\.

1. Alice attaches the following policy to the `EC2-Admins` group\. This policy grants users permission to call the Amazon EC2 `StopInstances` and `TerminateInstances` actions only if the user has authenticated using MFA\. 

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

1. If user Carol needs to stop or terminate an Amazon EC2 instance, she \(or an application that she is running\) calls `GetSessionToken` passing the ID of the MFA device and the current TOTP that Carol gets from her device\.

1. User Carol \(or an application that Carol is using\) uses the temporary credentials provided by `GetSessionToken` to call the Amazon EC2 `StopInstances` or `StopInstances` action\. 

   For an example of a program that calls `GetSessionToken`, see [Calling GetSessionToken with MFA Authentication \(Python and C\#\)](id_credentials_mfa_sample-code.md#MFAProtectedAPI-example-getsessiontoken) later in this document\.

## Scenario: MFA Protection for Resources That Have Resource\-based Policies<a name="MFAProtectedAPI-resource-policies"></a>

In this scenario, you are the owner of an S3 bucket, an SQS queue, or an SNS topic and you want to make sure that any user from any AWS account who accesses the resource is authenticated by an AWS MFA device\. 

This scenario illustrates a way to provide cross\-account MFA protection without requiring users to assume a role first\. If the user is authenticated by MFA and is able to get temporary security credentials from `GetSessionToken`, and if the user's account is trusted by the resource's policy, the user can access the resource\. 

Imagine that you are in account A and you create an S3 bucket\. You want to grant access to this bucket to users who are in several different AWS accounts, but only if those users are authenticated with MFA\.

In this scenario, user Alice is an administrator in account A\. User Charlie is an IAM user in account C\.

1. In account A, Alice creates a bucket named `Account-A-bucket`\.

1. Alice adds the bucket policy to the bucket\. The policy allows any user in account A, account B, or account C to perform the S3 `PutObject` and `DeleteObject` actions in the bucket\. The policy includes an MFA condition\. 

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
Amazon S3 offers an MFA Delete feature for *root* account access \(only\)\. You can enable Amazon S3 MFA Delete when you set the versioning state of the bucket\. Amazon S3 MFA Delete cannot be applied to an IAM user, and is managed independently from MFA\-protected API access\. An IAM user with permission to delete a bucket cannot delete a bucket with Amazon S3 MFA Delete enabled\. For more information on Amazon S3 MFA Delete, see [MFA Delete](http://docs.aws.amazon.com/AmazonS3/latest/dev/MultiFactorAuthenticationDelete.html)\.

1. In account C, an administrator makes sure that user Charlie is configured with an AWS MFA device and that he knows the ID of the device—the serial number if it's a hardware MFA device, or the device's ARN if it's a virtual MFA device\. 

1. In account C, Charlie \(or an application that he is running\) calls `GetSessionToken`\. The call includes the ID or ARN of the MFA device and the current TOTP that Charlie gets from his device\. 

1. Charlie \(or an application that he is using\) uses the temporary credentials returned by `GetSessionToken` to call the Amazon S3 `PutObject` action to upload a file to `Account-A-bucket`\. 

   For an example of a program that calls `GetSessionToken`, see [Calling GetSessionToken with MFA Authentication \(Python and C\#\)](id_credentials_mfa_sample-code.md#MFAProtectedAPI-example-getsessiontoken) later in this document\.
**Note**  
The temporary credentials that `AssumeRole` returns won't work in this case because although the user can provide MFA information to assume a role, the temporary credentials returned by `AssumeRole` don't include the MFA information that is required in order to meet the MFA condition in the policy\. 