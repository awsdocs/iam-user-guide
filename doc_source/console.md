# The IAM Console and Sign\-in Page<a name="console"></a>

The AWS Management Console provides a web\-based way to administer AWS services\. You can sign in to the console and create, list, and perform other tasks with AWS services for your account\. These tasks might include starting and stopping Amazon EC2 instances and Amazon RDS databases, creating Amazon DynamoDB tables, creating IAM users, and so on\.

When you first create an Amazon Web Services \(AWS\) account, you begin with a single sign\-in identity that has complete access to all AWS services and resources in the account\. This identity is called the AWS account *root user* and is accessed by signing in with the email address and password that you used to create the account\.

**Important**  
We strongly recommend that you do not use the root user for your everyday tasks, even the administrative ones\. Instead, adhere to the [best practice of using the root user only to create your first IAM user](best-practices.md#create-iam-users)\. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks\. To view the tasks that require you to sign in as the root user, see [AWS Tasks That Require Root User](http://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\. For a tutorial on how to set up an administrator for daily use, see [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)\.

This section provides information about the AWS Management Console sign\-in page\. It explains how to create a unique sign\-in URL for IAM users in your account, and how to sign in as the root user\. 

**Note**  
If your organization has an existing identity system, you might want to create a single sign\-on \(SSO\) option\. SSO gives users access to the AWS Management Console for your account without requiring them to have an IAM user identity\. SSO also eliminates the need for users to sign in to your organization's site and to AWS separately\. For more information, see [Creating a URL that Enables Federated Users to Access the AWS Management Console \(Custom Federation Broker\)](id_roles_providers_enable-console-custom-url.md)\. 

## The IAM User Sign\-in Page<a name="user-sign-in-page"></a>

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
To find your AWS account ID number on the AWS Management Console, choose **Support** on the navigation bar on the upper\-right, and then choose **Support Center**\. Your currently signed\-in account ID appears in the upper\-right corner below the **Support** menu\.  

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/account-id-support-center.console.png)

For convenience, the AWS sign\-in page uses a browser cookie to remember the IAM user name and account information\. The next time the user goes to any page in the AWS Management Console, the console uses the cookie to redirect the user to the account sign\-in page\.

## The AWS Account Root User Sign\-in Page<a name="BrowserDefault"></a>

Use your AWS account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the root user\.

**Note**  
If you previously signed in to the console with *[IAM user](id_users.md)* credentials, your browser might remember this preference and open your account\-specific sign\-in page\. You cannot use the IAM user sign\-in page to sign in with your AWS account root user credentials\. If you see the IAM user sign\-in page, choose **Sign\-in using root account credentials** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account email address and password\.