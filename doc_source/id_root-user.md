# AWS account root user<a name="id_root-user"></a>

When you first create an Amazon Web Services \(AWS\) account, you begin with a single sign\-in identity that has complete access to all AWS services and resources in the account\. This identity is called the AWS account *root user*\. You can sign in as the root user using the email address and password that you used to create the account\.

**Important**  
We strongly recommend that you do not use the root user for your everyday tasks, even the administrative ones\. Instead, adhere to the [best practice of using the root user only to create your first IAM user](best-practices.md#create-iam-users)\. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks\. To view the tasks that require you to sign in as the root user, see [AWS Tasks That Require Root User](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\. For a tutorial on how to set up an administrator for daily use, see [Creating your first IAM admin user and group](getting-started_create-admin-group.md)\.

You can create, rotate, disable, or delete access keys \(access key IDs and secret access keys\) for your AWS account root user\. You can also change your root user password\. Anyone who has root user credentials for your AWS account has unrestricted access to all the resources in your account, including billing information\.

When you create access keys, you create the access key ID and secret access key as a set\. During access key creation, AWS gives you one opportunity to view and download the secret access key part of the access key\. If you don't download it or if you lose it, you can delete the access key and then create a new one\. You can create root user access keys with the [IAM console](https://console.aws.amazon.com/iam/home?#), AWS CLI, or AWS API\.

A newly created access key has the status of *active*, which means that you can use the access key for CLI and API calls\. You are [limited to two access keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html) for each IAM user, which is useful when you want to [rotate the access keys](https://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html#iam-user-access-keys)\. You can also assign up to two access keys to the root user\. When you disable an access key, you can't use it for API calls, and inactive keys do count toward your limit\. You can create or delete an access key any time\. However, when you delete an access key, it's gone forever and can't be retrieved\.

You can change the email address and password on the [Security Credentials](https://console.aws.amazon.com/iam/home?#security_credential) page\. You can also choose **Forgot password?** on the AWS sign\-in page to reset your password\.

**Topics**
+ [Create or delete an AWS account](#id_root-user_manage_account)
+ [Enable MFA on the AWS account root user](#id_root-user_manage_mfa)
+ [Creating access keys for the root user](#id_root-user_manage_add-key)
+ [Deleting access keys for the root user](#id_root-user_manage_delete-key)
+ [Changing the password for the root user](#id_root-user_manage_password)
+ [Securing the credentials for the root user](#id_root-user_secure_credentials)

## Create or delete an AWS account<a name="id_root-user_manage_account"></a>

For more information, see the following articles in the AWS Knowledge Center:
+ [How do I create and activate an AWS account?](http://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/)
+ [How do I close my AWS account?](http://aws.amazon.com/premiumsupport/knowledge-center/close-aws-account/)

## Enable MFA on the AWS account root user<a name="id_root-user_manage_mfa"></a>

If you continue to use the root user credentials, we recommend that you follow the security best practice to enable multi\-factor authentication \(MFA\) for your account\. Because your root user can perform sensitive operations in your account, adding an additional layer of authentication helps you to better secure your account\. Multiple types of MFA are available\. For more information about enabling MFA, see the following:
+ [Enable a virtual MFA device for your AWS account root user \(console\)](id_credentials_mfa_enable_virtual.md#enable-virt-mfa-for-root)
+ [Enable a hardware MFA device for the AWS account root user \(console\)](id_credentials_mfa_enable_physical.md#enable-hw-mfa-for-root)

## Creating access keys for the root user<a name="id_root-user_manage_add-key"></a>

You can use the AWS Management Console or AWS programming tools to create access keys for the root user\.

**To create an access key for the AWS account root user \(console\)**

1. Sign in to the [IAM console](https://console.aws.amazon.com/iam/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.
**Note**  
If you see three text boxes, then you previously signed in to the console with *[IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* credentials\. Your browser might remember this preference and open this account\-specific sign\-in page every time that you try to sign in\. You cannot use the IAM user sign\-in page to sign in as the account owner\. If you see the [IAM user sign\-in page](https://docs.aws.amazon.com/IAM/latest/UserGuide/console.html#user-sign-in-page), choose **Sign in using root user email** near the bottom of the page\. This returns you to the main sign\-in page\. From there, you can sign in as the root user using your AWS account email address and password\.

1. Choose your account name in the navigation bar, and then choose **My Security Credentials**\. 

1. If you see a warning about accessing the security credentials for your AWS account, choose **Continue to Security Credentials**\.

1. Expand the **Access keys \(access key ID and secret access key\)** section\.

1. Choose **Create New Access Key**\. If this feature is disabled, then you must delete one of the existing access keys before you can create a new key\. For more information, see [IAM Entity Object Limits](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html#reference_iam-quotas-entities) in the *IAM User Guide*\. 

   A warning explains that you have only this one opportunity to view or download the secret access key\. It cannot be retrieved later\. 
   + If you choose **Show Access Key**, you can copy the access key ID and secret key from your browser window and paste it somewhere else\.
   + If you choose **Download Key File**, you receive a file named `rootkey.csv` that contains the access key ID and the secret key\. Save the file somewhere safe\. 

1. When you no longer use the access key [we recommend that you delete it](best-practices.md#remove-credentials), or at least mark it inactive by choosing **Make Inactive** so that it cannot be misused\.

**To create an access key for the root user \(AWS CLI or AWS API\)**

Use one of the following:
+ AWS CLI: [aws iam create\-access\-key](https://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html)
+ AWS API: [CreateAccessKey](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html) 

## Deleting access keys for the root user<a name="id_root-user_manage_delete-key"></a>

You can use the AWS Management Console or various programming tools to delete access keys for the root user\.

**To delete an access key from the AWS account root user \(console\)**

1. Use your AWS account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the AWS account root user\.
**Note**  
If you see three text boxes, then you previously signed in to the console with *[IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* credentials\. Your browser might remember this preference and open this account\-specific sign\-in page every time that you try to sign in\. You cannot use the IAM user sign\-in page to sign in as the account owner\. If you see the [IAM user sign\-in page](https://docs.aws.amazon.com/IAM/latest/UserGuide/ console.html#user-sign-in-page), choose **Sign in using root user email** near the bottom of the page\. This returns you to the main sign\-in page\. From there, you can sign in as the root user using your AWS account email address and password\.

1. Choose your account name in the navigation bar, and then choose **My Security Credentials**\. 

1. If you see a warning about accessing the security credentials for your AWS account, choose **Continue to Security Credentials**\.

1. Expand the **Access keys \(access key ID and secret access key\)** section\.

1. Find the access key that you want to delete, and then, under the **Actions** column, choose **Delete**\.
**Note**  
You can mark an access key as inactive instead of deleting it\. This enables you to resume use of it in the future without having to change either the key ID or secret key\. While it is inactive, any attempts to use it in requests to the AWS API fail with the status of access denied\.

**To delete an access key for the root user \(AWS CLI or AWS API\)**

Use one of the following:
+ AWS CLI: [aws iam delete\-access\-key](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html)
+ AWS API: [DeleteAccessKey](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html) 

## Changing the password for the root user<a name="id_root-user_manage_password"></a>

For information about changing the root user's password, see [Changing the AWS account root user password](id_credentials_passwords_change-root.md)\. To change the root user, you must log in using the root user credentials\. To view the tasks that require you to sign in as the root user, see [AWS Tasks that Require Root User](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)

## Securing the credentials for the root user<a name="id_root-user_secure_credentials"></a>

For more information about securing the credentials for the AWS account root user, see [Lock away your AWS Account Root User access keys](best-practices.md#lock-away-credentials)\.