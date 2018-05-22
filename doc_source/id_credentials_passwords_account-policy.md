# Setting an Account Password Policy for IAM Users<a name="id_credentials_passwords_account-policy"></a>

You can set a password policy on your AWS account to specify complexity requirements and mandatory rotation periods for your IAM users' passwords\.

You can use a password policy to do these things:
+ Set a minimum password length\.
+ Require specific character types, including uppercase letters, lowercase letters, numbers, and non\-alphanumeric characters\. Be sure to remind your users that passwords are case sensitive\.
+ Allow all IAM users to change their own passwords\.
**Note**  
When you allow your IAM users to change their own passwords, IAM automatically allows them to view the password policy\. IAM users need permission to view the account's password policy in order to create a password that complies with the policy\.
+ Require IAM users to change their password after a specified period of time \(enable password expiration\)\.
+ Prevent IAM users from reusing previous passwords\.
+ Force IAM users to contact an account administrator when the user has allowed his or her password to expire\.

**Important**  
The password settings described here apply only to **passwords** assigned to IAM users and do not affect any access keys they might have\. If a password expires, the user cannot sign\-in to the AWS Management Console\. However, if the user has valid access keys, then the user can still run any AWS CLI or Tools for Windows PowerShell commands or call any API operations through an application that the user's permissions allow\. 

When you create or change a password policy, most of the password policy settings are enforced the next time your users change their passwords, but some of the settings are enforced immediately\. For example: 
+ When you set minimum length and character type requirements, the settings are enforced the next time your users change their passwords\. Users are not forced to change their existing passwords, even if the existing passwords do not adhere to the updated password policy\.
+ When you set a password expiration period, the expiration period is enforced immediately\. For example, when you set a password expiration period of 90 days, all IAM users that currently have an existing password that is more than 90 days old are forced to change their password at next sign\-in\.

For information about the permissions that you need in order to set a password policy, see [Permitting IAM Users to Change Their Own Passwords](id_credentials_passwords_enable-user-change.md)\. 

The IAM password policy does not apply to the AWS root account password\.

The options currently available do not allow you to create what is commonly called a "lockout policy" that locks a user out of the account after a specified number of failed sign\-in attempts\. To get that kind of enhanced security, we recommend that you combine password policies together with multi\-factor authentication \(MFA\)\. For more information about MFA, see [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\.

**Topics**
+ [Password Policy Options](#password-policy-details)
+ [Setting a Password Policy \(AWS Management Console\)](#IAMPasswordPolicy)
+ [Setting a Password Policy \(AWS CLI, Tools for Windows PowerShell, or AWS API\)](#PasswordPolicy_CLI)

## Password Policy Options<a name="password-policy-details"></a>

The following list describes the options that are available when you configure a password policy for your account\.

**Minimum password length**  
You can specify the minimum number of characters allowed in an IAM user password\. You can enter any number from 6 to 128\.

**Require at least one uppercase letter**  
You can require that IAM user passwords contain at least one uppercase character from the ISO basic Latin alphabet \(A to Z\)\.

**Require at least one lowercase letter**  
You can require that IAM user passwords contain at least one lowercase character from the ISO basic Latin alphabet \(a to z\)\.

**Require at least one number**  
You can require that IAM user passwords contain at least one numeric character \(0 to 9\)\. 

**Require at least one nonalphanumeric character**  
You can require that IAM user passwords contain at least one of the following nonalphanumeric characters:  
`! @ # $ % ^ & * ( ) _ + - = [ ] { } | '`

**Allow users to change their own password**  
You can permit all IAM users in your account to use the IAM console to change their own passwords, as described in [Permitting IAM Users to Change Their Own Passwords](id_credentials_passwords_enable-user-change.md)\.   
Alternatively, you can let only some users manage passwords, either for themselves or for others\. To do so, you clear the **Allow users to change their own password** check box\. For more information about using policies to limit who can manage passwords, see [Permitting IAM Users to Change Their Own Passwords](id_credentials_passwords_enable-user-change.md)\.   
When you allow your IAM users to change their own passwords, IAM automatically allows them to view the password policy\. IAM users need permission to view the account's password policy in order to create a password that complies with the policy\.

**Enable password expiration**  
You can set IAM user passwords to be valid for only the specified number of days\. You specify the number of days that passwords remain valid after they are set\. For example, when you enable password expiration and set the password expiration period to 90 days, an IAM user can use a password for up to 90 days\. After 90 days, the password expires and the IAM user must set a new password before accessing the AWS Management Console\. You can choose a password expiration period between 1 and 1095 days, inclusive\.   
The AWS Management Console warns IAM users when they are within 15 days of password expiration\. IAM users can change their password at any time \(as long as they have been given permission to do so\)\. When they set a new password, the rotation period for that password starts over\. An IAM user can have only one valid password at a time\.

**Prevent password reuse**  
You can prevent IAM users from reusing a specified number of previous passwords\. You can set the number of previous passwords from 1 to 24, inclusive\. 

**Password expiration requires administrator reset**  
You can prevent IAM users from choosing a new password after their current password has expired\. For example, if the password policy specifies a password expiration period, but an IAM user fails to choose a new password before the expiration period ends, the IAM user cannot set a new password\. In that case, the IAM user must request a password reset from an account administrator in order to regain access to the AWS Management Console\. If you leave this check box cleared and an IAM user allows his or her password to expire, the user will be required to set a new password before accessing the AWS Management Console\.   
Before you enable this option, be sure that your AWS account has more than one user with administrative permissions \(that is, permission to reset IAM user passwords\) or that your administrators also have access keys that enable them to use the AWS CLI or Tools for Windows PowerShell separately from the AWS Management Console\. When this option is enabled and one administrator's password expires, a second administrator is required to sign\-in to the console to reset the expired password of the first administrator\. However, if the administrator with the expired password has valid access keys then he or she can run an AWS CLI or Tools for Windows PowerShell command to reset his or her own password\. The requirement for a second administrator applies only if a password expires and the first administrator has no access keys\.

## Setting a Password Policy \(AWS Management Console\)<a name="IAMPasswordPolicy"></a>

You can use the AWS Management Console to create, change, or delete a password policy\. As part of managing the password policy, you can let all users manage their own passwords\.

**To create or change a password policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Account Settings**\.

1. In the **Password Policy** section, select the options you want to apply to your password policy\. 

1. Click **Apply Password Policy**\. 

**To delete a password policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Account Settings**, and then in the **Password Policy** section, click **Delete Password Policy**\. 

## Setting a Password Policy \(AWS CLI, Tools for Windows PowerShell, or AWS API\)<a name="PasswordPolicy_CLI"></a>

To manage an account password policy from the AWS CLI, Tools for Windows PowerShell, or AWS API, use the following commands:

**To create or change a password policy**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/update-account-password-policy.html](http://docs.aws.amazon.com/cli/latest/reference/iam/update-account-password-policy.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMAccountPasswordPolicy.html&tocid=Update-IAMAccountPasswordPolicy](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMAccountPasswordPolicy.html&tocid=Update-IAMAccountPasswordPolicy)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccountPasswordPolicy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccountPasswordPolicy.html)

**To retrieve the password policy**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/get-account-password-policy.html](http://docs.aws.amazon.com/cli/latest/reference/iam/get-account-password-policy.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccountPasswordPolicy.html&tocid=Get-IAMAccountPasswordPolicy](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccountPasswordPolicy.html&tocid=Get-IAMAccountPasswordPolicy)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountPasswordPolicy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountPasswordPolicy.html) 

**To delete a password policy**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/delete-account-password-policy.html](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-account-password-policy.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccountPasswordPolicy.html&tocid=Remove-IAMAccountPasswordPolicy](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccountPasswordPolicy.html&tocid=Remove-IAMAccountPasswordPolicy)
+ AWS APII: [`DeleteAccountPasswordPolicy` ](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccountPasswordPolicy.html) 