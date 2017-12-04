# Using IAM Roles<a name="id_roles_use"></a>

Before an IAM user, application, or service can use a role that you created, you must grant permissions to switch to the role\. You can use any policy attached to one of an IAM user's groups or to the user itself to grant the necessary permissions\. This section describes how to grant users permission to use a role, and then how the user can switch to a role using the AWS Management Console, the Tools for Windows PowerShell, the AWS Command Line Interface \(AWS CLI\) and the [http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API\.

**Important**  
If you create a role programmatically instead of in the IAM console, then you have an option to add a `Path` of up to 512 characters in addition to the `RoleName`, which can be up to 64 characters long\. However, if you intend to use a role with the Switch Role feature in the AWS console, then the combined `Path` and `RoleName` cannot exceed 64 characters\.

**Note**  
When using the AWS Management Console, you can switch roles only when signed in as an IAM user\. You cannot switch roles when signed in as the AWS account root user\.


+ [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)
+ [Granting a User Permissions to Pass a Role to an AWS Service](id_roles_use_passrole.md)
+ [Switching to a Role \(AWS Management Console\)](id_roles_use_switch-role-console.md)
+ [Switching to an IAM Role \(AWS Command Line Interface\)](id_roles_use_switch-role-cli.md)
+ [Switching to an IAM Role \(Tools for Windows PowerShell\)](id_roles_use_switch-role-twp.md)
+ [Switching to an IAM Role \(API\)](id_roles_use_switch-role-api.md)
+ [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)
+ [Revoking IAM Role Temporary Security Credentials](id_roles_use_revoke-sessions.md)