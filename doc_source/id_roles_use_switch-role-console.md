# Switching to a Role \(AWS Management Console\)<a name="id_roles_use_switch-role-console"></a>

A *role* specifies a set of permissions that you can use to access AWS resources that you need\. In that sense, it is similar to a [user in AWS Identity and Access Management](http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) \(IAM\)\. When you sign in as a user, you get a specific set of permissions\. However, you don't sign in to a role, but once signed in you can switch to a role\. This temporarily sets aside your original user permissions and instead gives you the permissions assigned to the role\. The role can be in your own account or any other AWS account\. For more information about roles, their benefits, and how to create them, see [IAM Roles](id_roles.md), and [Creating IAM Roles](id_roles_create.md)\.

**Important**  
When you switch roles in the AWS Management Console, the console always uses your original credentials to authorize the switch\. This applies whether you sign in as an IAM user, as a SAML\-federated role, or as a web\-identity federated role\. For example, if you switch to RoleA, it uses your original user or federated role credentials to determine if you are allowed to assume RoleA\. If you then try to switch to RoleB *while you are using RoleA*, it still uses your **original** user or federated role credentials to authorize your attempt to switch to RoleB, not the credentials for RoleA\.

This section describes how to use the IAM console to switch to a role:

+ You can only switch roles when you sign in as an IAM user\. You cannot switch roles if you sign in as the AWS account root user\.

+ If your administrator provides you with a link, click the link and then skip to step [[ERROR] BAD/MISSING LINK TEXT](#StepJumpToHere) in the following procedure\. The link takes you to the appropriate web page and fills in the account ID \(or alias\) and the role name for you\.
**Tip**  
You can manually construct the link yourself by using the following format:  
`https://signin.aws.amazon.com/switchrole?account=account_id_number&roleName=role_name&displayName=text_to_display`  
Where your administrator provides the *account\_id\_number* and *role\_name* to you\. For *text\_to\_display*, see the explanation in step 5 in the following procedure\.
**Important**  
If you create the role programmatically instead of in the IAM console, then you have an option to add a `Path` of up to 512 characters in addition to the `RoleName`, which can be up to 64 characters long\. However, to use a role with the Switch Role feature in the AWS console, the combined `Path` and `RoleName` cannot exceed 64 characters\.

+ You can manually switch roles using the information your administrator provides by using the procedures below\. 

To troubleshoot common issues that you might encounter when you assume a role, see [I Can't Assume a Role](troubleshoot_roles.md#troubleshoot_roles_cant-assume-role)\.

**To switch to a role**

1. Sign in to the AWS Management Console as an IAM user and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the IAM console, choose your user name on the navigation bar in the upper right\. It typically looks like this: ***username*@*account\_ID\_number\_or\_alias***\.

1. For **Identity**, select **Switch Role**\. If this is the first time selecting this option, a page appears with more information\. After reading it, click **Switch Role**\. If you clear your browser cookies, this page can appear again\.

1. On the **Switch Role** page, type the account ID number or the account alias and the name of the role that was provided by your administrator\.
**Note**  
If your administrator created the role with a path, such as `division_abc/subdivision_efg/roleToDoXYZ`, then you must type that complete path and name in the **Role** box\. If you type only the role name, the attempt to switch role fails\.
**Important**  
If you create the role programmatically instead of in the IAM console, then you have an option to add a `Path` of up to 512 characters in addition to the `RoleName`, which can be up to 64 characters long\. However, to use a role with the Switch Role feature in the IAM console, the combined `Path` and `RoleName` cannot exceed 64 characters\. This is a limit of the browser cookies that store the role name\.

1. \(Optional\) Type text that you want to appear on the navigation bar in place of your user name when this role is active\. A name is suggested, based on the account and role information, but you can change it to whatever has meaning for you\. You can also select a color to highlight the display name\. The name and color can help remind you when this role is active, which changes your permissions\. For example, for a role that gives you access to the test environment, you might specify a **Display Name** of **Test** and select the green **Display Color**\. For the role that gives you access to production, you might specify a **Display Name** of **Production** and select red as the **Display Color**\.

1. Click **Switch Role**\. The display name and color replace your user name on the navigation bar, and you can start using the permissions that the role grants you\.

**Tip**  
The last several roles that you used appear on the **Identity** menu\. The next time you need to switch to one of those roles, you can simply click the desired role\. You only need to enter the account and role information manually if the role is not displayed on the Identity menu\.

**To stop using a role**

1. In the IAM console, select your role's **Display Name** on the right side of the navigation bar\.

1. Select **Back to *UserName***\. The role and its permissions are deactivated, and the permissions associated with your IAM user and groups are automatically restored\.