# Creating a Role to Delegate Permissions to an IAM User<a name="id_roles_create_for-user"></a>

You can use IAM roles to delegate access to your AWS resources\. With IAM roles, you can establish trust relationships between your *trusting* account and other AWS *trusted* accounts\. The trusting account owns the resource to be accessed and the trusted account contains the users who need access to the resource\.

After you create the trust relationship, an IAM user or an application from the trusted account can use the AWS Security Token Service \(AWS STS\) [http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API action\. This action provides temporary security credentials that enable access to AWS resources in your account\.

The accounts can both be controlled by you, or the account with the users can be controlled by a third party\. If the other account with the users is in an AWS account that you do not control, then you can use the `externalID` attribute and a unique identifier supplied by the third\-party account\. This helps ensure that access occurs only in the correct contexts\. For more information, see [How to Use an External ID When Granting Access to Your AWS Resources to a Third Party](id_roles_create_for-user_externalid.md)\.

For information about how to use roles to delegate permissions, see [Roles Terms and Concepts](id_roles_terms-and-concepts.md)\. For information about using a service role to allow services to access resources in your account, see [Creating a Role to Delegate Permissions to an AWS Service](id_roles_create_for-service.md)\.

## Creating an IAM Role \(Console\)<a name="roles-creatingrole-user-console"></a>

You can use the AWS Management Console to create a role that an IAM user can assume\. For example, imagine that your organization has multiple AWS accounts to isolate a development environment from a production environment\. To view a high\-level description of the steps necessary to set up and use a role that allows users in the development account to access resources in the production account, see [Example Scenario Using Separate Development and Production Accounts](id_roles_common-scenarios_aws-accounts.md#id_roles_common-scenarios_aws-accounts-example)\.

**To create a role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the console, choose **Roles** and then choose **Create role**\.

1. Choose the **Another AWS account** role type\.

1. For **Account ID**, type the AWS account ID to which you want to grant access to your resources\.

   The administrator of the specified account can grant permission to assume this role to any IAM user in that account\. To do this, the administrator attaches a policy to the user or a group that grants permission for the `sts:AssumeRole` action\. That policy must specify the role's ARN as the `Resource`\. 

1. If you are granting permissions to users from an account that you do not control, select **Require external ID**\. The external ID can be any word or number that is agreed upon between you and the administrator of the third party account\. This option automatically adds a condition to the trust policy that allows the user to assume the role only if the request includes the correct `sts:ExternalID`\. For more information, see [How to Use an External ID When Granting Access to Your AWS Resources to a Third Party](id_roles_create_for-user_externalid.md)\.
**Important**  
Choosing this option restricts access to the role only through the AWS CLI, Tools for Windows PowerShell, or the AWS API\. This is because you cannot use the AWS console to switch to a role that has an `externalID` condition in its trust policy\. However, you can create this kind of access programmatically by writing a script or an application using the relevant SDK\. For more information and a sample script, see [How to Enable Cross\-Account Access to the AWS Management Console](http://aws.amazon.com/blogs/security/how-to-enable-cross-account-access-to-the-aws-management-console) in the *AWS Security Blog*\.

1. If you want to restrict the role to users who sign in with multi\-factor authentication \(MFA\), select **Require MFA**\. This adds a condition to the role's trust policy that checks for an MFA sign\-in\. A user who wants to assume the role must sign in with a temporary one\-time password from a configured MFA device\. Users without MFA authentication cannot assume the role\. For more information about MFA, see [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)

1. Choose **Next: Permissions**\.

1. Choose one or more permissions policies to attach to the role\. Choose policies that specify what actions can be done on specific resources \(similar to setting permissions for IAM groups\)\. For information about using policies to manage permissions, see [IAM Policies](access_policies.md)\. 

   The permissions that you specify are available to any entity that uses the role\. By default, a role has no permissions\.

   Select the box next to the policy that assigns the permissions that you want the users to have\. Then choose **Next: Review**\. If you prefer, you can select no policies at this time, create the policies later, and then attach them to the role\.

1. For **Role name**, type a name for your role\. This name helps you identify the purpose of this role\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because various entities might reference the role, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Role description**, type a description for the new role\.

1. Review the role and then choose **Create role**\.
**Important**  
Remember that this is only the first half of the configuration required\. You must also give individual users in the trusted account permissions to switch to the role\. For more information about this step, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

After you create the role and grant it permissions to perform AWS tasks or access AWS resources, the user can assume the role\. For more information, see [Switching to a Role \(AWS Management Console\)](id_roles_use_switch-role-console.md)\.

## Creating an IAM Role \(AWS CLI\)<a name="roles-creatingrole-user-cli"></a>

Creating a role from the AWS CLI involves multiple steps\. When you use the console to create a role, many of the steps are done for you, but with the AWS CLI you must explicitly perform each step yourself\. You must create the policy and assign a permissions policy to the role\.

**To create a role for cross\-account access \(AWS CLI\)**
+ Create a role: [aws iam create\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/create-role.html)
+ Attach a managed permission policy to the role: [aws iam attach\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-role-policy.html)

   \-or\-

  Create an inline permission policy for the role: [aws iam put\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)

The following example shows both steps in a simple environment\. The example assumes that you are using a client computer running Windows, and have already configured your command line interface with your account credentials and region\. For more information, see [Configuring the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)\.

The sample trust policy referenced in the first command contains the following JSON code\. It enables users in the account 123456789012 to assume the role, but only if the user provides MFA authentication\. For more information about MFA, see [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": { "AWS": "arn:aws:iam::123456789012:root" },
    "Action": "sts:AssumeRole",
    "Condition": { "Bool": { "aws:MultiFactorAuthPresent": "true" } }
  }
}
```

**Important**  
If your `Principal` element contains an ARN that points to a specific IAM role or user, then that ARN is transformed to a unique principal ID when the policy is saved\. This helps mitigate the risk of someone escalating their privileges by removing and recreating the role or user\. You don't normally see this ID in the console, because there is also a reverse transformation back to the ARN when the trust policy is displayed\. However, if you delete the role or user, then the relationship is broken\. The policy no longer applies, even if you recreate the user or role because it does not match the principal ID stored in the trust policy\. When this happens, the principal ID shows up in the console because AWS can no longer map it back to an ARN\. The result is that if you delete and recreate a user or role referenced in a trust policy's `Principal` element, you must edit the role to replace the ARN\. The user or role is transformed into the new principal ID when you save the policy\.

The managed policy referenced in the second command is assumed to already exists in IAM\. This policy allows the user who assumes the role to perform only the `ListBucket` action on an S3 bucket named `example_bucket`\. The policy looks like this:

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "s3:ListBucket",
    "Resource": "arn:aws:s3:::example_bucket"
  }
}
```

The commands to run are the following:

```
# Create the role and attach the trust policy that allows users in an account to switch to the role.
$ aws iam create-role --role-name Test-UserAccess-Role --assume-role-policy-document file://C:\policies\trustpolicyforacct123456789012.json

# Attach the permissions policy (in this example a managed policy) to the role to specify what it is allowed to do.
$ aws iam attach-role-policy --role-name Test-UserAccess-Role --policy-arn arn:aws:iam::123456789012:role/PolicyForRole
```

**Important**  
Remember that this is only the first half of the configuration required\. You must also give individual users in the trusted account permissions to switch to the role\. For more information about this step, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

After you create the role and grant it permissions to perform AWS tasks or access AWS resources, the user can switch to the role\. For more information, see [Switching to an IAM Role \(AWS Command Line Interface\)](id_roles_use_switch-role-cli.md)\.

## Creating an IAM Role \(AWS API\)<a name="roles-creatingrole-user-api"></a>

You can use API calls to create a role that an IAM user can switch to\.

**To create a role in code \(API\)**
+ Create a role: [CreateRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateRole.html)

  For the role's trust policy, you can specify a file location\.
+ Attach a managed permission policy to the role: [AttachRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html)

   \-or\-

  Create an inline permission policy for the role: [PutRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)

**Important**  
Remember that this is only the first half of the configuration required\. You must also give individual users in the trusted account permissions to switch to the role\. For more information about this step, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

After you create the role and grant it permissions to perform AWS tasks or access AWS resources, the user can switch to the role\. For more information, see [Switching to an IAM Role \(API\)](id_roles_use_switch-role-api.md)\.

 For more information about MFA, see [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\.