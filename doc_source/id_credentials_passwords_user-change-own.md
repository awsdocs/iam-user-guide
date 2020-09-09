# How an IAM user changes their own password<a name="id_credentials_passwords_user-change-own"></a>

If you have been granted permission to change your own IAM user password, you can use a special page in the AWS Management Console to do this\. You can also use the AWS CLI or AWS API\.

**Topics**
+ [Permissions required](#change-own-passwords-permissions-required)
+ [How IAM users change their own password \(console\)](#ManagingUserPwdSelf-Console)
+ [How IAM users change their own password \(AWS CLI or AWS API\)](#ManagingUserPwdSelf-CLIAPI)

## Permissions required<a name="change-own-passwords-permissions-required"></a>

To change the password for your own IAM user, you must have the permissions from the following policy: [AWS: Allows IAM users to change their own console password on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage-password-only.md)\.

## How IAM users change their own password \(console\)<a name="ManagingUserPwdSelf-Console"></a>

The following procedure describes how IAM users can use the AWS Management Console to change their own password\.

**To change your own IAM user password \(console\)**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

   To get your AWS account ID, contact your administrator\.

1. In the navigation bar on the upper right, choose your user name, and then choose **My Security Credentials**\.   
![\[AWS Management Console My Security Credentials link\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-user.shared.console.png)

1. On the **AWS IAM Credentials** tab, choose **Change password**\.

1. For **Current password**, enter your current password\. Enter a new password for **New password** and **Confirm new password**\. Then choose **Change password**\.
**Note**  
If the account has a password policy, the new password must meet the requirements of that policy\. For more information, see [Setting an account password policy for IAM users](id_credentials_passwords_account-policy.md)\. 

## How IAM users change their own password \(AWS CLI or AWS API\)<a name="ManagingUserPwdSelf-CLIAPI"></a>

The following procedure describes how IAM users can use the AWS CLI or AWS API to change their own password\.

**To change your own IAM password, use the following:**
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/change-password.html](https://docs.aws.amazon.com/cli/latest/reference/iam/change-password.html)
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ChangePassword.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ChangePassword.html)