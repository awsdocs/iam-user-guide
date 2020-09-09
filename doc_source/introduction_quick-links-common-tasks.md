# Quick links to common tasks<a name="introduction_quick-links-common-tasks"></a>

Use the following links to get help with common tasks associated with IAM\.

**Sign in as an IAM user**  
See [How IAM users sign in to AWS](id_users_sign-in.md)\. 

**Manage passwords for IAM users**  
You need a password in order to access the AWS Management Console, including access to billing information\.  
For your AWS account root user, see [Changing the AWS account root user password](id_credentials_passwords_change-root.md)\.   
For an IAM user, see [Managing passwords for IAM users](id_credentials_passwords_admin-change-user.md)\. 

**Manage permissions for IAM users**  
You use policies to grant permissions to the IAM users in your AWS account\. IAM users have no permissions when they are created, so you must add permissions to allow them to use AWS resources\.   
For more information, see [Managing IAM policies](access_policies_manage.md)\. 

**List the users in your AWS account and get information about their credentials**  
See [Getting credential reports for your AWS account](id_credentials_getting-report.md)\. 

**Add multi\-factor authentication \(MFA\)**  
To add a virtual MFA device, see one of the following:   
+ [Enable a virtual MFA device for your AWS account root user \(console\)](id_credentials_mfa_enable_virtual.md#enable-virt-mfa-for-root)
+ [Enable a virtual MFA device for an IAM user \(console\)](id_credentials_mfa_enable_virtual.md#enable-virt-mfa-for-iam-user)
To add a U2F security key, see one of the following:   
+ [Enable a U2F security key for the AWS account root user \(console\)](id_credentials_mfa_enable_u2f.md#enable-u2f-mfa-for-root)
+ [Enable a U2F security key for another IAM user \(console\)](id_credentials_mfa_enable_u2f.md#enable-u2f-mfa-for-iam-user)
To add a hardware MFA device, see one of the following:   
+ [Enable a hardware MFA device for the AWS account root user \(console\)](id_credentials_mfa_enable_physical.md#enable-hw-mfa-for-root)\.
+ [Enable a hardware MFA device for another IAM user \(console\)](id_credentials_mfa_enable_physical.md#enable-hw-mfa-for-iam-user)

**Get an access key**  
You need an access key if you want to make AWS requests using the [AWS SDKs](https://aws.amazon.com/tools/), the [AWS Command Line Tools](https://aws.amazon.com/tools/#Command_Line_Tools), or the API operations\.   
You can view and download your secret access key *only* when you create the access key\. You cannot view or recover a secret access key later\. However, if you lose your secret access key, you can create a new access key\. 
For your AWS account, see [Managing Access Keys for your AWS Account](https://docs.aws.amazon.com/general/latest/gr/managing-aws-access-keys.html)\.   
For an IAM user, see [Managing access keys for IAM users](id_credentials_access-keys.md)\. 

**Tag a user or role**  
You can tag an IAM user or role using the IAM console, the AWS CLI, or the API through one of the AWS SDKs\.   
To learn about tags in IAM, see [Tagging IAM users and roles](id_tags.md)\.  
For details about how to manage tags in IAM, see [Managing tags on IAM entities \(console\)](id_tags.md#id_tags_procs-console)\.  
To learn about using IAM tags to control access to AWS, see [Controlling access to and for IAM users and roles using IAM resource tags](access_iam-tags.md)\. 

**View the actions, resources, and condition keys for all services**  
This set of reference documentation can help you write detailed IAM policies\. Each AWS service defines the actions, resources, and condition context keys that you use in IAM policies\. To learn more, see [Actions, Resources, and Condition Keys for AWS Services](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_actions-resources-contextkeys.html)\.

**Get started with all of AWS**  
This set of documentation deals primarily with the IAM service\. To learn about getting started with AWS and using multiple services to solve a problem such as building and launching your first project, see the [Getting Started Resource Center](https://aws.amazon.com/getting-started/)\. 