# Switching to a Role \(AWS Management Console\)<a name="id_roles_use_switch-role-console"></a>

A *role* specifies a set of permissions that you can use to access AWS resources that you need\. In that sense, it is similar to a [user in AWS Identity and Access Management](http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) \(IAM\)\. When you sign in as a user, you get a specific set of permissions\. However, you don't sign in to a role, but once signed in you can switch to a role\. This temporarily sets aside your original user permissions and instead gives you the permissions assigned to the role\. The role can be in your own account or any other AWS account\. For more information about roles, their benefits, and how to create them, see [IAM Roles](id_roles.md), and [Creating IAM Roles](id_roles_create.md)\.

**Important**  
The permissions of your IAM user and any roles that you switch to are not cumulative\. Only one set of permissions is active at a time\. When you switch to a role, you temporarily give up your user permissions and work with the permissions that are assigned to the role\. When you exit the role, your user permissions are automatically restored\.

By default, your AWS Management Console session lasts for one hour\. 

When you switch roles in the AWS Management Console, the console always uses your original credentials to authorize the switch\. This applies whether you sign in as an IAM user, as a SAML\-federated role, or as a web\-identity federated role\. For example, if you switch to RoleA, IAM uses your original user or federated role credentials to determine if you are allowed to assume RoleA\. If you then switch to RoleB *while you are using RoleA*, IAM still uses your **original** user or federated role credentials to authorize the switch, not the credentials for RoleA\.

This section describes how to use the IAM console to switch to a role:
+ You can only switch roles when you sign in as an IAM user\. You cannot switch roles if you sign in as the AWS account root user\.
+ If your administrator provides you with a link, choose the link and then skip to step [Step 5](#StepJumpToHere) in the following procedure\. The link takes you to the appropriate webpage and fills in the account ID \(or alias\) and the role name for you\.
+ You can manually construct the link and then skip to step [Step 5](#StepJumpToHere) in the following procedure\. To construct your link, use the following format:

  `https://signin.aws.amazon.com/switchrole?account=account_id_number&roleName=role_name&displayName=text_to_display`

  Where you replace the following text:
  + *account\_id\_number*–The 12\-digit account identifier provided to you by your administrator\. Alternatively, your administrator might create an account alias so that the URL includes your account name instead of an account ID\. For more information, see [Your AWS Account ID and Its Alias](console_account-alias.md)\.
  + *role\_name*–The name of the role that you want to assume\. You can get this from the end of the role's ARN\. For example, provide the `TestRole` role name from the followin grole ARN: `namearn:aws:iam::403299380220:role/TestRole`\.
  + \(Optional\) *text\_to\_display*–The text that you want to appear on the navigation bar in place of your user name when this role is active\.
+ You can manually switch roles using the information your administrator provides by using the procedures below\. 

To troubleshoot common issues that you might encounter when you assume a role, see [I Can't Assume a Role](troubleshoot_roles.md#troubleshoot_roles_cant-assume-role)\.

**To switch to a role**

1. Sign in to the AWS Management Console as an IAM user and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the IAM console, choose your user name on the navigation bar in the upper right\. It typically looks like this: ***username*@*account\_ID\_number\_or\_alias***\.

1. Choose **Switch Role**\. If this is the first time choosing this option, a page appears with more information\. After reading it, choose **Switch Role**\. If you clear your browser cookies, this page can appear again\.

1. On the **Switch Role** page, type the account ID number or the account alias and the name of the role that was provided by your administrator\.
**Note**  
If your administrator created the role with a path, such as `division_abc/subdivision_efg/roleToDoX`, then you must type that complete path and name in the **Role** box\. If you type only the role name, or if the combined `Path` and `RoleName` exceed 64 characters, the role switch fails\. This is a limit of the browser cookies that store the role name\. If this happens, contact your administrator and ask them to reduce the size of the path and role name\.

1. <a name="StepJumpToHere"></a>\(Optional\) Type text that you want to appear on the navigation bar in place of your user name when this role is active\. A name is suggested, based on the account and role information, but you can change it to whatever has meaning for you\. You can also select a color to highlight the display name\. The name and color can help remind you when this role is active, which changes your permissions\. For example, for a role that gives you access to the test environment, you might specify a **Display Name** of **Test** and select the green **Color**\. For the role that gives you access to production, you might specify a **Display Name** of **Production** and select red as the **Color**\.

1. Choose **Switch Role**\. The display name and color replace your user name on the navigation bar, and you can start using the permissions that the role grants you\.

**Tip**  
The last several roles that you used appear on the menu\. The next time you need to switch to one of those roles, you can simply choose the role you want\. You only need to type the account and role information manually if the role is not displayed on the Identity menu\.

**To stop using a role**

1. In the IAM console, choose your role's **Display Name** on the right side of the navigation bar\.

1. Choose **Back to *UserName***\. The role and its permissions are deactivated, and the permissions associated with your IAM user and groups are automatically restored\.