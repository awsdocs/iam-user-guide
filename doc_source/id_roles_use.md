# Using IAM Roles<a name="id_roles_use"></a>

Before an IAM user, application, or service can use a role that you created, you must grant permissions to switch to the role\. You can use any policy attached to one of an IAM user's groups or to the user itself to grant the necessary permissions\. This section describes how to grant users permission to use a role, and then how the user can switch to a role using the AWS Management Console, the Tools for Windows PowerShell, the AWS Command Line Interface \(AWS CLI\) and the [http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API\.

**Important**  
If you create a role programmatically instead of in the IAM console, then you have an option to add a `Path` of up to 512 characters in addition to the `RoleName`, which can be up to 64 characters long\. However, if you intend to use a role with the **Switch Role** feature in the AWS console, then the combined `Path` and `RoleName` cannot exceed 64 characters\.

You can switch roles from the AWS Management Console\. You can assume a role by calling an AWS CLI or API operation or by using a custom URL\. The method that you use determines who can assume the role and how long the role session can last\.


**Comparing methods for using roles**  

|  Method |  **Who can assume the role**  | **Method to specify credential lifetime** |  **Credential lifetime \(min \| max \| default\)**  | 
| --- | --- | --- | --- | 
| AWS Management Console | IAM user \(by [switching roles](id_roles_use_switch-role-console.md)\) | None | 1h \| 1h \| 1h | 
| [http://docs.aws.amazon.com/cli/latest/reference/sts/assume-role.html](http://docs.aws.amazon.com/cli/latest/reference/sts/assume-role.html) CLI or [http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API operation | IAM user or role¹ | duration\-seconds CLI or DurationSeconds API parameter | 15m \| Maximum session duration setting² \| 1hr  | 
| [http://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-saml.html](http://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-saml.html) CLI or [http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html) API operation | Any user authenticated using SAML | duration\-seconds CLI or DurationSeconds API parameter | 15m \| Maximum session duration setting² \| 1hr  | 
| [http://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-web-identity.html](http://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-web-identity.html) CLI or [http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html) API operation | Any user authenticated using a web identity provider | duration\-seconds CLI or DurationSeconds API parameter | 15m \| Maximum session duration setting² \| 1hr  | 
| [Console URL](id_roles_providers_enable-console-custom-url.md) constructed with AssumeRole  | IAM user or role | SessionDuration HTML parameter in the URL | 15m \| 12hr \| 1hr  | 
| [Console URL](id_roles_providers_enable-console-custom-url.md) constructed with AssumeRoleWithSAML  | Any user authenticated using SAML | SessionDuration HTML parameter in the URL | 15m \| 12hr \| 1hr | 
| [Console URL](id_roles_providers_enable-console-custom-url.md) constructed with AssumeRoleWithWebIdentity  | Any user authenticated using a web identity provider | SessionDuration HTML parameter in the URL | 15m \| 12hr \| 1hr  | 

¹ Using the credentials for one role to assume a different role is called [*role chaining*](id_roles_terms-and-concepts.md#iam-term-role-chaining)\. When you use role chaining, your new credentials are limited to a maximum duration of one hour\.

² The maximum session duration is a setting that you can apply to a role from the console, the AWS CLI, or the API\. This setting specifies the maximum session duration for the role when it is assumed from the CLI or API\. This setting can have a value from 1 hour to 12 hours\. For details about the maximum session duration setting, see [Modifying a Role](id_roles_manage_modify.md)\. This setting determines the maximum session duration that you can request when you get the role credentials\. For example, when you use the [AssumeRole\*](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API operations to assume a role, you can specify a session length using the `DurationSeconds` parameter\. Use this parameter to specify the length of the role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the Maximum Session Duration Setting for a Role](#id_roles_use_view-role-max-session) later in this page\.

## View the Maximum Session Duration Setting for a Role<a name="id_roles_use_view-role-max-session"></a>

When you use an AWS CLI or API operation to assume a role, you can specify a value for the `DurationSeconds` parameter\. You can use this parameter to specify the duration of the role session, from 900 seconds \(15 minutes\) up to the **Maximum CLI/API session duration** setting for the role\. Before you specify the parameter, you should view this setting for your role\. If you specify a value for the `DurationSeconds` parameter that is higher than the maximum setting, the operation fails\.

**To view a role's maximum session duration \(console\)**

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role that you want to view\.

1. Next to **Maximum CLI/API session duration**, view the maximum session length that you can specify in your AWS CLI or API operation\. 

**To view a role's maximum session duration setting \(AWS CLI, AWS API\)**

1. If you don't know the name of the role that you want to assume, use one of the following commands to list the roles in your account:
   + AWS CLI: [aws iam list\-roles](http://docs.aws.amazon.com/cli/latest/reference/iam/list-roles.html)
   + IAM API: [ListRoles](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRoles.html)

1. To view the role's maximum session duration, use one of the following commands\. Then view the maximum session duration parameter:
   + AWS CLI: [aws iam get\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)
   + IAM API: [GetRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html)

**Topics**
+ [View the Maximum Session Duration Setting for a Role](#id_roles_use_view-role-max-session)
+ [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)
+ [Granting a User Permissions to Pass a Role to an AWS Service](id_roles_use_passrole.md)
+ [Switching to a Role \(AWS Management Console\)](id_roles_use_switch-role-console.md)
+ [Switching to an IAM Role \(AWS Command Line Interface\)](id_roles_use_switch-role-cli.md)
+ [Switching to an IAM Role \(Tools for Windows PowerShell\)](id_roles_use_switch-role-twp.md)
+ [Switching to an IAM Role \(API\)](id_roles_use_switch-role-api.md)
+ [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)
+ [Revoking IAM Role Temporary Security Credentials](id_roles_use_revoke-sessions.md)