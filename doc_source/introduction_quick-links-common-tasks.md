# Quick links to common tasks<a name="introduction_quick-links-common-tasks"></a>

Use the following links to get help with common tasks associated with IAM\.

**Sign in for different user types**  
Sign in to the [IAM console](https://console.aws.amazon.com/iam) by choosing **IAM user** and entering your AWS account ID or account alias\. On the next page, enter your IAM user name and your password\.  
To sign in with your IAM Identity Center user, use the sign\-in URL that was sent to your email address when you created the IAM Identity Center user\.  
For help signing in using an IAM Identity Center user, see [Signing in to the AWS access portal](https://docs.aws.amazon.com/signin/latest/userguide/iam-id-center-sign-in-tutorial.html) in the *AWS Sign\-In User Guide*\.  
 Sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.  
 See [What is AWS Sign\-In](https://docs.aws.amazon.com/signin/latest/userguide/what-is-sign-in.html) in the *AWS Sign\-In User Guide* for help determining your user type and sign\-in page\. 

**Manage passwords for users**  
You need a password in order to access the AWS Management Console, including access to billing information\.  
For your AWS account root user, see [Changing the AWS account root user password](id_credentials_passwords_change-root.md)\.   
For an IAM user, see [Managing passwords for IAM users](id_credentials_passwords_admin-change-user.md)\. 

**Manage permissions for users**  
You use policies to grant permissions to the IAM users in your AWS account\. IAM users have no permissions when they are created, so you must add permissions to allow them to use AWS resources\.   
To provide access, add permissions to your users, groups, or roles:  
+ Users and groups in AWS IAM Identity Center \(successor to AWS Single Sign\-On\):

  Create a permission set\. Follow the instructions in [Create a permission set](https://docs.aws.amazon.com/singlesignon/latest/userguide/howtocreatepermissionset.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\.
+ Users managed in IAM through an identity provider:

  Create a role for identity federation\. Follow the instructions in [Creating a role for a third\-party identity provider \(federation\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-idp.html) in the *IAM User Guide*\.
+ IAM users:
  + Create a role that your user can assume\. Follow the instructions in [Creating a role for an IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user.html) in the *IAM User Guide*\.
  + \(Not recommended\) Attach a policy directly to a user or add a user to a user group\. Follow the instructions in [Adding permissions to a user \(console\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html#users_change_permissions-add-console) in the *IAM User Guide*\.
For more information, see [Managing IAM policies](access_policies_manage.md)\. 

**List the users in your AWS account and get information about their credentials**  
See [Getting credential reports for your AWS account](id_credentials_getting-report.md)\. 

**Add multi\-factor authentication \(MFA\)**  
To add a virtual MFA device, see one of the following:   
+ [Enable a virtual MFA device for your AWS account root user \(console\)](id_credentials_mfa_enable_virtual.md#enable-virt-mfa-for-root)
+ [Enable a virtual MFA device for an IAM user \(console\)](id_credentials_mfa_enable_virtual.md#enable-virt-mfa-for-iam-user)
To add a FIDO security key, see one of the following:   
+ [Enable a FIDO security key for the AWS account root user \(console\)](id_credentials_mfa_enable_fido.md#enable-fido-mfa-for-root)
+ [Enable a FIDO security key for another IAM user \(console\)](id_credentials_mfa_enable_fido.md#enable-fido-mfa-for-iam-user)
To add a hardware MFA device, see one of the following:   
+ [Enable a hardware TOTP token for the AWS account root user\(console\)](id_credentials_mfa_enable_physical.md#enable-hw-mfa-for-root)\.
+ [Enable a hardware TOTP token for another IAM user \(console\)](id_credentials_mfa_enable_physical.md#enable-hw-mfa-for-iam-user)

**Get an access key**  
You need an access key if you want to make AWS requests using the [AWS SDKs](https://aws.amazon.com/tools/), the [AWS Command Line Tools](https://aws.amazon.com/tools/#Command_Line_Tools), or the API operations\.  
Before you start creating access keys, we highly recommend that you read the security best practices for access keys\. For more information, see [Best practices for managing AWS access keys](https://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html) in the *AWS General Reference*\.  
For your AWS account, see [Programmatic access](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) in the *AWS General Reference*\.  
For an IAM user, see [Managing access keys for IAM users](id_credentials_access-keys.md)\. 

**Tag IAM resources**  
You can tag the following IAM resources:  
+ IAM users
+ IAM roles
+ Customer managed policies
+ Identity providers
+ Server certificates
+ Virtual MFA devices
To learn about tags in IAM, see [Tagging IAM resources](id_tags.md)\.  
To learn about using tags to control access to AWS resources, see [Controlling access to AWS resources using tags](access_tags.md)\.

**View the actions, resources, and condition keys for all services**  
This set of reference documentation can help you write detailed IAM policies\. Each AWS service defines the actions, resources, and condition context keys that you use in IAM policies\. To learn more, see [Actions, Resources, and Condition Keys for AWS Services](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_actions-resources-contextkeys.html)\.

**Get started with all of AWS**  
This set of documentation deals primarily with the IAM service\. To learn about getting started with AWS and using multiple services to solve a problem such as building and launching your first project, see the [Getting Started Resource Center](https://aws.amazon.com/getting-started/)\. 