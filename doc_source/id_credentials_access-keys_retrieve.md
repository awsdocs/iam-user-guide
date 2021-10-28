# Resetting lost or forgotten passwords or access keys for AWS<a name="id_credentials_access-keys_retrieve"></a>

**Having trouble signing in to AWS?** Make sure that you're on the correct [AWS sign\-in page](console.md) for your type of user\. If you are the AWS account root user \(account owner\), you can sign in to AWS using the credentials that you set up when you created the AWS account\. If you are an IAM user, your account administrator can give you the credentials that you can use to sign in to AWS\. If you need to request support, do not use the feedback link on this page, as the form is received by the AWS Documentation team, not AWS Support\. Instead, on the [Contact Us](http://aws.amazon.com/contact-us/) page, expand **I cannot login to my AWS Account** and choose **Request Support for AWS Account Credentials**\.

On the main sign\-in page, you must enter your email address to sign in as the root user, or enter your account ID to sign in as an IAM user\. You can provide your password only on the sign\-in page that matches your user type\. For more information, see [Signing in to the AWS Management Console as an IAM user or root user](console.md)\.

If you are on the correct sign\-in page and lose or forget your passwords or access keys, you *cannot* retrieve them from IAM\. Instead, you can reset them using the following methods:
+ **AWS account root user password** – If you forget your root user password, you can reset the password from the AWS Management Console\. For details, see [Resetting a lost or forgotten root user password](#reset-root-password) later in this topic\.
+ **AWS account access keys** – If you forget your account access keys, you can create new access keys without disabling the existing access keys\. If you are not using the existing keys, you can delete those\. For details, see [Creating access keys for the root user](id_root-user.md#id_root-user_manage_add-key) and [Deleting access keys for the root user](id_root-user.md#id_root-user_manage_delete-key)\.
+ **IAM user password** – If you are an IAM user and you forget your password, you must ask your administrator to reset your password\. To learn how an administrator can manage your password, see [Managing passwords for IAM users](id_credentials_passwords_admin-change-user.md)\.
+ **IAM user access keys** – If you are an IAM user and you forget your access keys, you will need new access keys\. If you have permission to create your own access keys, you can find instructions for creating a new one at [Managing access keys \(console\)](id_credentials_access-keys.md#Using_CreateAccessKey)\. If you do not have the required permissions, you must ask your administrator to create new access keys\. If you are still using your old keys, ask your administrator not to delete the old keys\. To learn how an administrator can manage your access keys, see [Managing access keys for IAM users](id_credentials_access-keys.md)\.

You should follow the AWS [best practice](best-practices.md#rotate-credentials) of periodically changing your password and AWS access keys\. In AWS, you change access keys by *rotating* them\. This means that you create a new one, configure your applications to use the new key, and then delete the old one\. You are allowed to have two access key pairs active at the same time for just this reason\. For more information, see [Rotating access keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

## Resetting a lost or forgotten root user password<a name="reset-root-password"></a>

When you first created your AWS account, you provided an email address and password\. These are your AWS account root user credentials\. If you forget your root user password, you can reset the password from the AWS Management Console\.

**To reset your root user password:**

1. Use your AWS account email address to begin signing in to the [AWS Management Console](https://console.aws.amazon.com/) as the root user and then choose **Next**\.
**Note**  
 If you are signed in to the [AWS Management Console](https://console.aws.amazon.com/) with *IAM user* credentials, then you must sign out before you can reset the root user password\. If you see the account\-specific IAM user sign\-in page, choose **Sign\-in using root account credentials** near the bottom of the page\. If necessary, provide your account email address and choose **Next** to access the **Root user sign in** page\. 

1. Choose **Forgot your password?**\.

1. Provide the email address that is associated with the account\. Then provide the CAPTCHA text and choose **Continue**\.

1. Check the email that is associated with your AWS account for a message from Amazon Web Services\. The email will come from an address ending in `@amazon.com` or `@aws.amazon.com`\. Follow the directions in the email\. If you don't see the email in your account, check your spam folder\. If you no longer have access to the email, see [I don't have access to the email for my AWS account](troubleshoot-aws-sign-in.md#troubleshoot_general_lost-root-creds)\.