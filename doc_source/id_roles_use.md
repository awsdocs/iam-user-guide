# Using IAM roles<a name="id_roles_use"></a>

Before an IAM user, application, or service can use a role that you created, you must grant permissions to switch to the role\. You can use any policy attached to one of an IAM user's groups or to the user itself to grant the necessary permissions\. This section describes how to grant users permission to use a role\. It also explains how the user can switch to a role from the AWS Management Console, the Tools for Windows PowerShell, the AWS Command Line Interface \(AWS CLI\) and the [https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API\.

**Important**  
When you create a role programmatically instead of in the IAM console, you have an option to add a `Path` of up to 512 characters in addition to the `RoleName`, which can be up to 64 characters long\. However, if you intend to use a role with the **Switch Role** feature in the AWS Management Console, then the combined `Path` and `RoleName` cannot exceed 64 characters\.

You can switch roles from the AWS Management Console\. You can assume a role by calling an AWS CLI or API operation or by using a custom URL\. The method that you use determines who can assume the role and how long the role session can last\.


**Comparing methods for using roles**  

|  Method of assuming the role |  **Who can assume the role**  | **Method to specify credential lifetime** |  **Credential lifetime \(min \| max \| default\)**  | 
| --- | --- | --- | --- | 
| AWS Management Console | IAM user \(by [switching roles](id_roles_use_switch-role-console.md)\) | Maximum session duration on the Role Summary page | 1h \| Maximum session duration setting² \| 1hr | 
| [https://docs.aws.amazon.com/cli/latest/reference/sts/assume-role.html](https://docs.aws.amazon.com/cli/latest/reference/sts/assume-role.html) CLI or [https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API operation | IAM user or role¹ | duration\-seconds CLI or DurationSeconds API parameter | 15m \| Maximum session duration setting² \| 1hr  | 
| [https://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-saml.html](https://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-saml.html) CLI or [https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html) API operation | Any user authenticated using SAML | duration\-seconds CLI or DurationSeconds API parameter | 15m \| Maximum session duration setting² \| 1hr  | 
| [https://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-web-identity.html](https://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-web-identity.html) CLI or [https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html) API operation | Any user authenticated using a web identity provider | duration\-seconds CLI or DurationSeconds API parameter | 15m \| Maximum session duration setting² \| 1hr  | 
| [Console URL](id_roles_providers_enable-console-custom-url.md) constructed with AssumeRole  | IAM user or role | SessionDuration HTML parameter in the URL | 15m \| 12hr \| 1hr  | 
| [Console URL](id_roles_providers_enable-console-custom-url.md) constructed with AssumeRoleWithSAML  | Any user authenticated using SAML | SessionDuration HTML parameter in the URL | 15m \| 12hr \| 1hr | 
| [Console URL](id_roles_providers_enable-console-custom-url.md) constructed with AssumeRoleWithWebIdentity  | Any user authenticated using a web identity provider | SessionDuration HTML parameter in the URL | 15m \| 12hr \| 1hr  | 

¹ Using the credentials for one role to assume a different role is called [*role chaining*](id_roles_terms-and-concepts.md#iam-term-role-chaining)\. When you use role chaining, your new credentials are limited to a maximum duration of one hour\. When you use roles to [grant permissions to applications that run on EC2 instances](id_roles_use_switch-role-ec2.md), those applications are not subject to this limitation\.

² This setting can have a value from 1 hour to 12 hours\. For details about modifying the maximum session duration setting, see [Modifying a role](id_roles_manage_modify.md)\. This setting determines the maximum session duration that you can request when you get the role credentials\. For example, when you use the [AssumeRole\*](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API operations to assume a role, you can specify a session length using the `DurationSeconds` parameter\. Use this parameter to specify the length of the role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. IAM users who switch roles in the console are granted the maximum session duration, or the remaining time in the IAM user's session, whichever is less\. Assume that you set a maximum duration of 5 hours on a role\. An IAM user that has been signed into the console for 10 hours \(out of the default maximum of 12\) switches to the role\. The available role session duration is 2 hours\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](#id_roles_use_view-role-max-session) later in this page\.

**Note**  
The maximum session duration setting does not limit sessions that are assumed by AWS services\.

**Topics**
+ [View the maximum session duration setting for a role](#id_roles_use_view-role-max-session)
+ [Granting a user permissions to switch roles](id_roles_use_permissions-to-switch.md)
+ [Granting a user permissions to pass a role to an AWS service](id_roles_use_passrole.md)
+ [Switching to a role \(console\)](id_roles_use_switch-role-console.md)
+ [Switching to an IAM role \(AWS CLI\)](id_roles_use_switch-role-cli.md)
+ [Switching to an IAM role \(Tools for Windows PowerShell\)](id_roles_use_switch-role-twp.md)
+ [Switching to an IAM role \(AWS API\)](id_roles_use_switch-role-api.md)
+ [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](id_roles_use_switch-role-ec2.md)
+ [Revoking IAM role temporary security credentials](id_roles_use_revoke-sessions.md)

## View the maximum session duration setting for a role<a name="id_roles_use_view-role-max-session"></a>

You can specify the maximum session duration for a role using the AWS Management Console or by using the AWS CLI or AWS API\. When you use an AWS CLI or API operation to assume a role, you can specify a value for the `DurationSeconds` parameter\. You can use this parameter to specify the duration of the role session, from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. Before you specify the parameter, you should view this setting for your role\. If you specify a value for the `DurationSeconds` parameter that is higher than the maximum setting, the operation fails\.

**To view a role's maximum session duration \(console\)**

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role that you want to view\.

1. Next to **Maximum session duration**, view the maximum session length that is granted for the role\. This is the maximum session duration that you can specify in your AWS CLI, or API operation\. 

**To view a role's maximum session duration setting \(AWS CLI\)**

1. If you don't know the name of the role that you want to assume, run the following command to list the roles in your account:
   + [aws iam list\-roles](https://docs.aws.amazon.com/cli/latest/reference/iam/list-roles.html)

1. To view the role's maximum session duration, run the following command\. Then view the maximum session duration parameter\.
   + [aws iam get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

**To view a role's maximum session duration setting \(AWS API\)**

1. If you don't know the name of the role that you want to assume, call the following operation to list the roles in your account:
   + [ListRoles](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRoles.html)

1. To view the role's maximum session duration, run the following operation\. Then view the maximum session duration parameter\.
   + [GetRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html)