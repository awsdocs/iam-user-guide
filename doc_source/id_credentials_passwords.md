# Managing Passwords<a name="id_credentials_passwords"></a>

You can manage passwords for your AWS account root user and for IAM users in your account\. IAM users need passwords in order to access the AWS Management Console\. Users do not need passwords to access AWS resources programmatically by using the AWS CLI, Tools for Windows PowerShell, the AWS SDKs or APIs\. For those environments, users need [access keys](id_credentials_access-keys.md) instead\.

**Topics**
+ [Changing the AWS Account Root User Password](id_credentials_passwords_change-root.md)
+ [Setting an Account Password Policy for IAM Users](id_credentials_passwords_account-policy.md)
+ [Managing Passwords for IAM Users](id_credentials_passwords_admin-change-user.md)
+ [Permitting IAM Users to Change Their Own Passwords](id_credentials_passwords_enable-user-change.md)
+ [How IAM Users Change Their Own Password](#id_credentials_passwords_user-change-own)

## How IAM Users Change Their Own Password<a name="id_credentials_passwords_user-change-own"></a>

If IAM users have been granted permission to change their own passwords, they can use a special page in the AWS Management Console to do this\. They can also use the command line interface or the IAM API\. 

For information about the permissions that users need in order to change their own passwords, see [Permitting IAM Users to Change Their Own Passwords](id_credentials_passwords_enable-user-change.md)\.

**Topics**
+ [How IAM Users Change Their Own Password \(AWS Management Console\)](#ManagingUserPwdSelf-Console)
+ [How IAM Users Change Their Own Password \(AWS CLI, Tools for Windows PowerShell, or AWS API\)](#ManagingUserPwdSelf-CLIAPI)

### How IAM Users Change Their Own Password \(AWS Management Console\)<a name="ManagingUserPwdSelf-Console"></a>

The following procedure describes how IAM users can use the AWS Management Console to change their own password\.

**To use the console to change your own password as an IAM user**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

   To get your AWS account ID, contact your administrator\.

1. In the navigation bar on the upper right, choose your user name, and then choose **Security Credentials**\.   
![\[AWS Management Console Security Credentials link\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. For **Current password**, type your current password\. Type a new password in the **New password** and **Confirm new password** boxes\. Then click **Submit**\.
**Note**  
If the account has a password policy, the new password must meet the requirements of that policy\. For more information, see [Setting an Account Password Policy for IAM Users](id_credentials_passwords_account-policy.md)\. 

### How IAM Users Change Their Own Password \(AWS CLI, Tools for Windows PowerShell, or AWS API\)<a name="ManagingUserPwdSelf-CLIAPI"></a>

The following procedure describes how IAM users can use the AWS CLI, Tools for Windows PowerShell, or AWS API to change their own password\.

**To change your own IAM password, use the following commands**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/change-password.html](http://docs.aws.amazon.com/cli/latest/reference/iam/change-password.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Edit-IAMPassword.html&tocid=Edit-IAMPassword](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Edit-IAMPassword.html&tocid=Edit-IAMPassword)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ChangePassword.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ChangePassword.html)