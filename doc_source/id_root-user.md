# The AWS Account Root User<a name="id_root-user"></a>

When you first create an Amazon Web Services \(AWS\) account, you begin with a single sign\-in identity that has complete access to all AWS services and resources in the account\. This identity is called the AWS account *root user* and is accessed by signing in with the email address and password that you used to create the account\.

**Important**  
We strongly recommend that you do not use the root user for your everyday tasks, even the administrative ones\. Instead, adhere to the [best practice of using the root user only to create your first IAM user](best-practices.md#create-iam-users)\. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks\. To view the tasks that require you to sign in as the root user, see [AWS Tasks That Require Root User](http://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\. For a tutorial on how to set up an administrator for daily use, see [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)\.

To manage your root user, follow the steps in the following procedures\.

**Topics**
+ [Enable MFA on the AWS Account Root User](#id_root-user_manage_mfa)
+ [Creating Access Keys for the Root User](#id_root-user_manage_add-key)
+ [Deleting Access Keys from the Root User](#id_root-user_manage_delete-key)
+ [Changing the Root User's Password](#id_root-user_manage_password)

## Enable MFA on the AWS Account Root User<a name="id_root-user_manage_mfa"></a>

If you continue to use the root user credentials, we recommend that you follow the security best practice to enable multi\-factor authentication \(MFA\) for your account\. Because your root user can perform sensitive operations in your account, adding an additional layer of authentication helps you to better secure your account\. Multiple types of MFA are available\. For more information about enabling MFA, see the following:
+ [Enable a Virtual MFA Device for Your AWS Account Root User \(Console\)](id_credentials_mfa_enable_virtual.md#enable-virt-mfa-for-root)
+ [Enable a Hardware MFA Device for the AWS Account Root User \(Console\)](id_credentials_mfa_enable_physical.md#enable-hw-mfa-for-root)

## Creating Access Keys for the Root User<a name="id_root-user_manage_add-key"></a>

You can use the AWS Management Console or AWS programming tools to create access keys for the root user\.

**To create an access key for the AWS account root user \(console\)**

1. Use your AWS account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the AWS account root user\.
**Note**  
If you previously signed in to the console with *[IAM user](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* credentials, your browser might remember this preference and open your account\-specific sign\-in page\. You cannot use the IAM user sign\-in page to sign in with your AWS account root user credentials\. If you see the IAM user sign\-in page, choose **Sign\-in using root user credentials** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account email address and password\.

1. Choose your account name in the navigation bar, and then choose **My Security Credentials**\. 

1. If you see a warning about accessing the security credentials for your AWS account, choose **Continue to Security Credentials**\.

1. Expand the **Access keys \(access key ID and secret access key\)** section\.

1. Choose **Create New Access Key**\. A warning explains that you have only this one opportunity to view or download the secret access key\. It cannot be retrieved later\. 
   + If you choose **Show Access Key**, you can copy the access key ID and secret key from your browser window and paste it somewhere else\.
   + If you choose **Download Key File**, you receive a file named `rootkey.csv` that contains the access key ID and the secret key\. Save the file somewhere safe\. 

1. When you no longer use the access key [we recommend that you delete it](best-practices.md#remove-credentials), or at least mark it inactive by choosing **Make Inactive** so that it cannot be misused if leaked\.

**To create an access key for the root user \(programmatically\)**

Use one of the following commands:
+ AWS CLI: [aws iam create\-access\-key](http://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html)
+ Tools for Windows PowerShell: [New\-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMAccessKey.html&tocid=New-IAMAccessKey)
+ AWS API: [CreateAccessKey](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html) 

## Deleting Access Keys from the Root User<a name="id_root-user_manage_delete-key"></a>

You can use the AWS Management Console or various programming tools to delete access keys for the root user\.

**To delete an access key from the AWS account root user \(console\)**

1. Use your AWS account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the root user\.
**Note**  
If you previously signed in to the console with *[IAM user](id_users.md)* credentials, your browser might remember this preference and open your account\-specific sign\-in page\. You cannot use the IAM user sign\-in page to sign in with your AWS account root user credentials\. If you see the IAM user sign\-in page, choose **Sign\-in using root account credentials** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account email address and password\.

1. Choose your account name in the navigation bar, and then choose **My Security Credentials**\. 

1. If you see a warning about accessing the security credentials for your AWS account, choose **Continue to Security Credentials**\.

1. Expand the **Access keys \(access key ID and secret access key\)** section\.

1. Find the access key that you want to delete, and then, under the **Actions** column, choose **Delete**\.
**Note**  
You can mark an access key as inactive instead of deleting it\. This enables you to resume use of it in the future without having to change either the key ID or secret key\. While it is inactive, any attempts to use it in requests to the AWS API fail with the status of access denied\.

**To delete an access key for the root user \(programmatically\)**

Use one of the following commands:
+ AWS CLI: [aws iam delete\-access\-key](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html)
+ Tools for Windows PowerShell: [Remove\-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccessKey.html&tocid=Remove-IAMAccessKey)
+ AWS API: [DeleteAccessKey](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html) 

## Changing the Root User's Password<a name="id_root-user_manage_password"></a>

For information about changing the root user's password, see [Changing the AWS Account Root User Password](id_credentials_passwords_change-root.md)\. To change the root user, you must log in using the root user credentials\. To view the tasks that require you to sign in as the root user, see [AWS Tasks that Require Root User](http://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)