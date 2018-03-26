# Resetting Your Lost or Forgotten Passwords or Access Keys<a name="id_credentials_access-keys_retrieve"></a>

If you lose or forget your passwords or access keys, you *cannot* retrieve them from IAM\. Instead, you can reset them using the following methods:
+ **AWS account root user password** – If you forget your root user password, you can reset the password from the AWS Management Console\. For details, see [Resetting a Lost or Forgotten Root User Password](#reset-root-password) later in this topic\.
+ **AWS account access keys** – If you forget your account access keys, you can create new access keys without disabling the existing access keys\. If you are not using the existing keys, you can delete those\. For details, see [Creating Access Keys for the Root User](id_root-user.md#id_root-user_manage_add-key) and [Deleting Access Keys from the Root User](id_root-user.md#id_root-user_manage_delete-key)\.
+ **IAM user password** – If you are an IAM user and you forget your password, you must ask your administrator to reset your password\. To learn how an administrator can manage your password, see [Managing Passwords for IAM Users](id_credentials_passwords_admin-change-user.md)\.
+ **IAM user access keys** – If you are an IAM user and you forget your access keys, you will need new access keys\. If you have permission to create your own access keys, you can find instructions for creating a new one at [Creating, Modifying, and Viewing Access Keys \(Console\)](id_credentials_access-keys.md#Using_CreateAccessKey)\. If you do not have the required permissions, you must ask your administrator to create new access keys\. If you are still using your old keys, ask your administrator not to delete the old keys\. To learn how an administrator can manage your access keys, see [Managing Access Keys for IAM Users](id_credentials_access-keys.md)\.

You should follow the AWS [best practice](best-practices.md#rotate-credentials) of periodically changing your password and AWS access keys\. In AWS, you change access keys by *rotating* them\. This means that you create a new one, configure your applications to use the new key, and then delete the old one\. You are allowed to have two access key pairs active at the same time for just this reason\. For more information, see [Rotating Access Keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

## Resetting a Lost or Forgotten Root User Password<a name="reset-root-password"></a>

When you first created your AWS account, you provided an email address and password\. These are your AWS account root user credentials\. If you forget your root user password, you can reset the password from the AWS Management Console\.

**To reset your root user password:**

1. Use your AWS account email address to begin signing in to the [AWS Management Console](https://console.aws.amazon.com/) as the root user\.
**Note**  
 If you are signed in to the [AWS Management Console](https://console.aws.amazon.com/console/home) with *IAM user* credentials, then you must sign out before you can reset the root user password\. If you see the account\-specific IAM user sign\-in page, choose **Sign\-in using root account credentials** near the bottom of the page\. If necessary, provide your account email address to access the **Root user sign in** page\. 

1. Choose **Forgot your password?**\.

1. Provide the email address that you used to create the account\. Then provide the CAPTCHA text and choose **Continue**\.

1. Check the email that is associated with your AWS account for a message from Amazon Web Services\. The email will come from an address ending in `@amazon.com` or `@aws.amazon.com`\. Follow the directions in the email\. If you don't see the email in your account, check your spam folder\. If you no longer have access to the email, see [I need to access an old account](troubleshoot_general.md#troubleshoot_general_lost-root-creds)\.