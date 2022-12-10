# Setting an account password policy for IAM users<a name="id_credentials_passwords_account-policy"></a>

You can set a custom password policy on your AWS account to specify complexity requirements and mandatory rotation periods for your IAM users' passwords\. If you don't set a custom password policy, IAM user passwords must meet the default AWS password policy\. For more information, see [Custom password policy options](#password-policy-details)\.

**Topics**
+ [Rules for setting a password policy](#password-policy-rules)
+ [Permissions required to set a password policy](#default-policy-permissions-required)
+ [Default password policy](#default-policy-details)
+ [Custom password policy options](#password-policy-details)
+ [Setting a password policy \(console\)](#IAMPasswordPolicy)
+ [Setting a password policy \(AWS CLI\)](#PasswordPolicy_CLI)
+ [Setting a password policy \(AWS API\)](#PasswordPolicy_API)

## Rules for setting a password policy<a name="password-policy-rules"></a>

The IAM password policy does not apply to the AWS account root user password or IAM user access keys\. If a password expires, the IAM user can't sign in to the AWS Management Console but can continue to use their access keys\.

When you create or change a password policy, most of the password policy settings are enforced the next time your users change their passwords\. However, some of the settings are enforced immediately\. For example: 
+ When the minimum length and character type requirements change, these settings are enforced the next time that your users change their passwords\. Users are not forced to change their existing passwords, even if the existing passwords do not adhere to the updated password policy\.
+ When you set a password expiration period, the expiration period is enforced immediately\. For example, assume that you set a password expiration period of 90 days\. In that case, the password expires for all IAM users whose existing password is older than 90 days\. Those users are required to change their password the next time that they sign in\.

You can't create a "lockout policy" to lock a user out of the account after a specified number of failed sign\-in attempts\. For enhanced security, we recommend that you combine a strong password policy with multi\-factor authentication \(MFA\)\. For more information about MFA, see [Using multi\-factor authentication \(MFA\) in AWS](id_credentials_mfa.md)\.

## Permissions required to set a password policy<a name="default-policy-permissions-required"></a>

You must configure permissions to allow an IAM entity \(user or role\) to view or edit their account password policy\. You can include the following password policy actions in an IAM policy: 
+ `iam:GetAccountPasswordPolicy` – Allows the entity to view the password policy for their account
+ `iam:DeleteAccountPasswordPolicy` – Allows the entity to delete the custom password policy for their account and revert to the default password policy
+ `iam:UpdateAccountPasswordPolicy` – Allows the entity to create or change the custom password policy for their account

The following policy allows full access to view and edit the account password policy\. To learn how to create an IAM policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "FullAccessPasswordPolicy",
            "Effect": "Allow",
            "Action": [
                "iam:GetAccountPasswordPolicy",
                "iam:DeleteAccountPasswordPolicy",
                "iam:UpdateAccountPasswordPolicy"
            ],
            "Resource": "*"
        }
    ]
}
```

For information about the permissions required for an IAM user to change their own password, see [Permitting IAM users to change their own passwords](id_credentials_passwords_enable-user-change.md)\.

## Default password policy<a name="default-policy-details"></a>

If an administrator does not set a custom password policy, IAM user passwords must meet the default AWS password policy\. The default password policy enforces the following conditions:
+ Minimum password length of 8 characters and a maximum length of 128 characters
+ Minimum of three of the following mix of character types: uppercase, lowercase, numbers, and non\-alphanumeric character \(`! @ # $ % ^ & * ( ) _ + - = [ ] { } | '`\)
+ Not be identical to your AWS account name or email address
+ Never expire password

## Custom password policy options<a name="password-policy-details"></a>

When you configure a custom password policy for your account, you can specify the following conditions:
+ **Password minimum length** – You can specify a minimum of 6 characters and a maximum of 128 characters\.
+ **Password strength** – You can select any of the following check boxes to define the strength of your IAM user passwords:
  + Require at least one uppercase letter from the Latin alphabet \(A–Z\)
  + Require at least one lowercase letter from the Latin alphabet \(a–z\)
  + Require at least one number
  + Require at least one nonalphanumeric character `! @ # $ % ^ & * ( ) _ + - = [ ] { } | '` 
+ **Turn on password expiration** – You can select and specify a minimum of 1 and a maximum of 1,095 days that IAM user passwords are valid after they are set\. For example, if you specify an expiration of 90 days, it immediately impacts all of your users\. For users with passwords older than 90 days, when they log into the console after the change, they must set a new password\. Users with passwords 75\-89 days old receive an AWS Management Console warning about their password expiration\. IAM users can change their password at any time if they have permission\. When they set a new password, the expiration period for that password starts over\. An IAM user can have only one valid password at a time\.
+ **Password expiration requires administrator reset** – Select this option to prevent IAM users from using the AWS Management Console to update their own passwords after the password expires\. Before you select this option, confirm that your AWS account has more than one user with administrative permissions to reset IAM user passwords\. Administrators with `iam:UpdateLoginProfile` permission can reset IAM user passwords\. IAM users with `iam:ChangePassword` permission and active access keys can reset their own IAM user console password programmatically\. If you clear this check box, IAM users with expired passwords must still set a new password before they can access the AWS Management Console\.
+ **Allow users to change their own password** – You can permit all IAM users in your account to change their own password\. This gives users access to the `iam:ChangePassword` action for only their user and to the `iam:GetAccountPasswordPolicy` action\. This option does not attach a permissions policy to each user\. Rather, IAM applies the permissions at the account\-level for all users\. Alternatively, you can allow only some users to manage their own passwords\. To do so, you clear this check box\. For more information about using policies to limit who can manage passwords, see [Permitting IAM users to change their own passwords](id_credentials_passwords_enable-user-change.md)\.
+ **Prevent password reuse** – You can prevent IAM users from reusing a specified number of previous passwords\. You can specify a minimum number of 1 and a maximum number of 24 previous passwords that can't be repeated\. 

## Setting a password policy \(console\)<a name="IAMPasswordPolicy"></a>

You can use the AWS Management Console to create, change, or delete a custom password policy\.

**To create a custom password policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Account settings**\.

1. In the **Password policy** section, choose **Edit**\. 

1. Choose **Custom** to use a custom password policy\.

1. Select the options that you want to apply to your password policy and choose **Save changes**\. 

1. Confirm that you want to set a custom password policy by choosing **Set custom**\.

**To change a custom password policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Account settings**\.

1. In the **Password policy** section, choose **Edit**\. 

1. Select the options that you want to apply to your password policy and choose **Save changes**\. 

1. Confirm that you want to set a custom password policy by choosing **Set custom**\.

**To delete a custom password policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Account settings**\.

1. In the **Password policy** section, choose **Edit**\. 

1. Choose **IAM default** to delete the custom password policy and choose **Save changes**\.

1. Confirm that you want to set the IAM default password policy by choosing **Set default**\.

## Setting a password policy \(AWS CLI\)<a name="PasswordPolicy_CLI"></a>

You can use the AWS Command Line Interface to set a password policy\.

**To manage the custom account password policy from the AWS CLI**  
Run the following commands:
+ To create or change the custom password policy: [https://docs.aws.amazon.com/cli/latest/reference/iam/update-account-password-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/update-account-password-policy.html)
+ To view the password policy: [https://docs.aws.amazon.com/cli/latest/reference/iam/get-account-password-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-account-password-policy.html) 
+ To delete the custom password policy: [https://docs.aws.amazon.com/cli/latest/reference/iam/delete-account-password-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-account-password-policy.html) 

## Setting a password policy \(AWS API\)<a name="PasswordPolicy_API"></a>

You can use AWS API operations to set a password policy\.

**To manage the custom account password policy from the AWS API**  
Call the following operations:
+ To create or change the custom password policy: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccountPasswordPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccountPasswordPolicy.html)
+ To view the password policy: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountPasswordPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountPasswordPolicy.html) 
+ To delete the custom password policy: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccountPasswordPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccountPasswordPolicy.html) 