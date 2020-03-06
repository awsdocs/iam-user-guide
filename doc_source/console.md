# The IAM Console and Sign\-In Page<a name="console"></a>

The AWS Management Console provides a web\-based way to administer AWS services\. You can sign in to the console and create, list, and perform other tasks with AWS services for your account\. These tasks might include starting and stopping Amazon EC2 instances and Amazon RDS databases, creating Amazon DynamoDB tables, creating IAM users, and so on\.

When you open the AWS Management Console you might see one of three separate sign\-in pages:
+ **[Main Sign\-In Page](#main-sign-in-page)** – From [https://console\.aws\.amazon\.com/](https://console.aws.amazon.com/), enter your root user email address or your IAM user account ID\.
+ **[AWS Account Root User Sign\-In Page](#root-user-sign-in-page)** – Enter your root user password\.
+ **[IAM User Sign\-In Page](#user-sign-in-page)** – Enter your IAM user name and password on this page\.

**Sign\-in Process**

![\[Sign-in Pages\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-logic.png)

If you previously signed in on a different page, your browser might remember this preference\. You can use links on the root user and IAM user sign\-in pages to return to the main page\. 

## Main Sign\-In Page<a name="main-sign-in-page"></a>

You can access the main sign\-in page by going to [https://console.aws.amazon.com/](https://console.aws.amazon.com/)\. 

On the main AWS sign\-in page, you can choose to sign in as the root user or an IAM user\. Enter your AWS account root user email address to sign in as the account owner\. When you enter the root user email address, you are directed to the root user sign\-in page\. 

To sign in as an IAM user, choose **IAM user** and enter your account ID or account alias\. When you enter account information, you are directed to the IAM user sign\-in page\.

**Main Sign\-in Page**

![\[Main Sign-in Page\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-main-capture.png)

## AWS Account Root User Sign\-In Page<a name="root-user-sign-in-page"></a>

When you first create an Amazon Web Services \(AWS\) account, you begin with a single sign\-in identity that has complete access to all AWS services and resources in the account\. This identity is called the AWS account *root user* and is accessed by signing in with the email address and password that you used to create the account\.

**Important**  
We strongly recommend that you do not use the root user for your everyday tasks, even the administrative ones\. Instead, adhere to the [best practice of using the root user only to create your first IAM user](best-practices.md#create-iam-users)\. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks\. To view the tasks that require you to sign in as the root user, see [AWS Tasks That Require Root User](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\. For a tutorial on how to set up an administrator for daily use, see [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)\.

To access the root user sign\-in page, you must choose **Root user** and enter the root user email address on the main sign\-in page\. Then you can enter your password on this page\.

**Root User Sign\-in Page**

![\[Root User Sign-in Page\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-root-user-capture.png)

To return to the main sign\-in page, choose **Sign in to a different account**\. 

If you forgot your root user password, choose **Forgot your password?** to reset it\. For more information about resetting passwords, see [Resetting Your Lost or Forgotten Passwords or Access Keys](id_credentials_access-keys_retrieve.md)\.

## IAM User Sign\-In Page<a name="user-sign-in-page"></a>

To access the IAM user sign\-in page, choose **IAM user** and enter your account ID or alias on the main sign\-in page\. Then choose **Next** and enter your IAM user name and password on this page\.

**IAM Sign\-in Page**

![\[IAM User Sign-in Page\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-iam-user-capture.png)

To return to the main sign\-in page, choose **Sign\-in using root user email**\. 

If you forgot your IAM password, you can't reset it\. Only your IAM administrator can reset your password\. For more information about resetting passwords, see [Resetting a Lost or Forgotten Root User Password](id_credentials_access-keys_retrieve.md#reset-root-password)\.

To use the AWS Management Console, IAM users must provide their account ID or account alias in addition to their user name and password\. When you, as an administrator, [create an IAM user in the console](id_users_create.md#id_users_create_console), you must send the sign\-in credentials to that user, including the user name and the URL to the account sign\-in page\. 

**Important**  
Depending on how you set up the IAM user, provide all users with a temporary password for their first sign\-in and, if appropriate, an MFA device\. For detailed information about passwords and MFA devices, see [Managing Passwords](id_credentials_passwords.md) and [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\. 

Your unique account sign\-in page URL is created automatically when you begin using IAM\. You do not have to do anything to use this sign\-in page\.

```
https://My_AWS_Account_ID.signin.aws.amazon.com/console/
```

You can also customize the account sign\-in URL for your account if you want the URL to contain your company name \(or other friendly identifier\) instead of your AWS account ID number\. For more information about creating an account alias, see [Your AWS Account ID and Its Alias](console_account-alias.md)\.

**Tip**  
To create a bookmark for your account sign\-in page in your web browser, you should manually type the sign\-in URL for your account in the bookmark entry\. Do not use your web browser bookmark feature because redirects can obscure the sign\-in URL\. 

You can find the URL for your account sign\-in page anytime by viewing the dashboard of the IAM console\.

![\[URL to your account-specific sign-in page in the IAM dashboard\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccountAlias.console.png)

IAM users can also sign in at the following general sign\-in endpoint and type an account ID or account alias manually:

```
[https://console\.aws\.amazon\.com/](https://console.aws.amazon.com/)
```

**Note**  
To find your AWS account ID number on the AWS Management Console, choose **Support** on the navigation bar on the upper right, and then choose **Support Center**\. Your currently signed\-in account number \(ID\) appears in the **Support Center** title bar\.  

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/account-id-support-center.console.png)

For convenience, the AWS sign\-in page uses a browser cookie to remember the IAM user name and account information\. The next time the user goes to any page in the AWS Management Console, the console uses the cookie to redirect the user to the account sign\-in page\.