# Permitting IAM users to change their own passwords<a name="id_credentials_passwords_enable-user-change"></a>

You can grant IAM users the permission to change their own passwords for signing in to the AWS Management Console\. You can do this in one of two ways:
+ [Allow all IAM users in the account to change their own passwords](#proc_letalluserschangepassword)\. 
+ [Allow only selected IAM users to change their own passwords](#proc_letselectuserschangepassword)\. In this scenario, you disable the option for all users to change their own passwords and you use an IAM policy to grant permissions to only some users to change their own passwords and optionally other credentials like their own access keys\. 

**Important**  
We recommend that you [set a password policy](id_credentials_passwords_account-policy.md) so that users create strong passwords\.<a name="proc_letalluserschangepassword"></a>

**To allow all IAM users change their own passwords**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Account Settings**\.

1. In the **Password Policy** section, select **Allow users to change their own password**, and then click **Apply Password Policy**\. 

1. Point users to the following instructions that show how they can change their passwords: [How an IAM user changes their own password](id_credentials_passwords_user-change-own.md)\. 

For information about the AWS CLI, Tools for Windows PowerShell, and API commands that you can use to change the account's password policy \(which includes letting all users change their own passwords\), see [Setting a password policy \(AWS CLI\)](id_credentials_passwords_account-policy.md#PasswordPolicy_CLI)\.<a name="proc_letselectuserschangepassword"></a>

**To allow selected IAM users change their own passwords**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Account Settings**\. 

1. In the **Account Settings** section, make sure that **Allow users to change their own password** is not selected\. If this check box is selected, all users can change their own passwords\. \(See the previous procedure\.\) 

1. Create the users who should be able to change their own password, if they do not already exist\. For details, see [Creating an IAM user in your AWS account](id_users_create.md)\. 

1. Create an IAM group for the users who should be allowed to change their passwords, and then add the users from the previous step to the group\. For details, see [Creating your first IAM admin user and group](getting-started_create-admin-group.md) and [Managing IAM groups](id_groups_manage.md)\. 

   This step is optional, but it's a best practice to use groups to manage permissions so that you can add and remove users and change the permissions for the group as a whole\. 

1. Assign the following policy to the group\. For details, see [Managing IAM policies](access_policies_manage.md)\.

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Action": "iam:GetAccountPasswordPolicy",
         "Resource": "*"
       },
       {
         "Effect": "Allow",
         "Action": "iam:ChangePassword",
         "Resource": "arn:aws:iam::account-id-without-hyphens:user/${aws:username}"
       }
     ]
   }
   ```

   This policy grants access to the [ChangePassword](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ChangePassword.html) action, which lets users change only their own passwords from the console, the AWS CLI, Tools for Windows PowerShell, or the API\. It also grants access to the [GetAccountPasswordPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountPasswordPolicy.html) action, which lets the user view the current password policy; this permission is required so that the user can display the **Change Password** page in the console\. The user must be able to read the current password policy to ensure the changed password meets the requirements of the policy\.

1. Point users to the following instructions that show how they can change their passwords: [How an IAM user changes their own password](id_credentials_passwords_user-change-own.md)\. 

## For more information<a name="HowToPwdIAMUser-moreinfo"></a>

For more information on managing credentials, see the following topics:
+ [Permitting IAM users to change their own passwords](#id_credentials_passwords_enable-user-change) 
+ [Managing user passwords in AWS](id_credentials_passwords.md)
+ [Setting an account password policy for IAM users](id_credentials_passwords_account-policy.md)
+ [Managing IAM policies](access_policies_manage.md)
+ [How an IAM user changes their own password](id_credentials_passwords_user-change-own.md)