# Changing the AWS account root user password<a name="id_credentials_passwords_change-root"></a>

You must be signed in as the AWS account root user and not an IAM user to change the root user password\. To learn how to reset a *forgotten* root user password, see [Resetting lost or forgotten passwords or access keys for AWS](id_credentials_access-keys_retrieve.md)\.

**To change the password for the root user**

1. Use your AWS account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the AWS account root user\.
**Note**  
If you see three text boxes, then you previously signed in to the console with *[IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* credentials\. Your browser might remember this preference and open this account\-specific sign\-in page every time that you try to sign in\. You cannot use the IAM user sign\-in page to sign in as the account owner\. If you see the [IAM user sign\-in page](https://docs.aws.amazon.com/IAM/latest/UserGuide/ console.html#user-sign-in-page), choose **Sign in using root user email** near the bottom of the page\. This returns you to the main sign\-in page\. From there, you can sign in as the root user using your AWS account email address and password\.

1. In the upper right corner of the console, choose your account name or number and then choose **My Account**\.

1. On the right side of the page, next to the **Account Settings** section, choose **Edit**\.

1. On the **Password** line choose **Edit** to change your password\.

1. Choose a strong password\. Although you can [set an account password policy for IAM users](id_credentials_passwords_account-policy.md), that policy does not apply to your AWS account root user\.

   AWS requires that your password meet these conditions:
   + have a minimum of 8 characters and a maximum of 128 characters
   + include a minimum of three of the following mix of character types: uppercase, lowercase, numbers, and \! @ \# $ % ^ & \* \(\) <> \[\] \{\} \| \_\+\-= symbols
   + not be identical to your AWS account name or email address
**Note**  
AWS is rolling out improvements to the sign\-in process\. One of those improvements is to enforce a more secure password policy for your account\. If your account has been upgraded, you are required to meet the password policy above\. If your account has not yet been upgraded, then AWS does not enforce this policy, but highly recommends that you follow its guidelines for a more secure password\.

   To protect your password, it's important to follow these best practices:
   + Change your password periodically and keep your password private, since anyone who knows your password may access your account\. 
   + Use a different password on AWS than you use on other sites\. 
   + Avoid passwords that are easy to guess\. These include passwords such as `secret`, `password`, `amazon`, or `123456`\. They also include things like a dictionary word, your name, email address, or other personal information that can easily be obtained\.