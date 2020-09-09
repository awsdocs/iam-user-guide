# Signing in to the AWS Management Console as an IAM user or root user<a name="console"></a>

The AWS Management Console provides a web\-based user interface that you can use to create and manage your AWS resources\. For example, you can start and stop Amazon EC2 instances, create Amazon DynamoDB tables, create Amazon S3 buckets, and so on\.

Before you can use the AWS Management Console, you must sign in to your AWS account\. The process that you will use to sign in to your AWS account depends on what type of AWS user you are\. There are two different types of users in AWS\. You are either the account owner \(root user\) or you are an IAM user\. The root user is created when the AWS account is created using the email address and password that were used to create the account\. IAM users are created by the root user or an IAM administrator within the AWS account\.

If you do not remember your credentials or have trouble signing in using your credentials, see [AWS sign\-in issues](troubleshoot-aws-sign-in.md)\.

**Topics**
+ [Sign in as the root user](#root-user-sign-in-page)
+ [Sign in as an IAM user](#user-sign-in-page)
+ [Your AWS account ID and its alias](console_account-alias.md)
+ [Troubleshooting AWS sign\-in or account issues](troubleshoot-aws-sign-in.md)

## Sign in as the root user<a name="root-user-sign-in-page"></a>

Before you sign in to an AWS account as the root user, be sure that you have the following required information\.

**Requirements**
+ The email address used to create the AWS account\.
+ The password for the root user\.

**To sign in to an AWS account as the root user**

1. Open [https://console\.aws\.amazon\.com/](https://console.aws.amazon.com/)\.

1. If you have not signed in previously using this browser, the main sign\-in page appears as follows\. Choose **Root user**, enter the email address associated with your account, and choose **Next**\.  
![\[Main sign-in page with Root user selected\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-main-capture.png)

   If you have signed in as a root user previously using this browser, your browser might remember the email address for the AWS account\. If so, you'll see the screen shown in the next step instead\.

   If you have signed in previously as an IAM user using this browser, your browser might display the IAM user sign in page instead\. To return to the main sign\-page, choose **Sign in using root user email**\.

1. Enter your password and choose **Sign in**\.  
![\[Root user sign-in page\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-root-user-capture.png)

## Sign in as an IAM user<a name="user-sign-in-page"></a>

Before you sign into an AWS account as an IAM user, be sure that you have the following required information\. If you do not have this information, contact the administrator for the AWS account\.

**Requirements**
+ One of the following:
  + The account alias\.
  + The 12\-digit AWS account ID\.
+ The user name for your IAM user\.
+ The password for your IAM user\.

If you are a root user or IAM administrator and need to provide the AWS account ID or AWS account alias to an IAM user, see [Your AWS account ID and its alias](console_account-alias.md)\.

If you are an IAM user, you can log in using either a sign\-in URL or the main sign\-in page\.

**To sign in to an AWS account as an IAM user using an IAM users sign\-in URL**

1. Open a browser and enter the following sign\-in URL, replacing *account\_alias\_or\_id* with the account alias or account ID provided by your administrator\.

   ```
   https://account_alias_or_id.signin.aws.amazon.com/console/
   ```

1. Enter your IAM user name and password and choose **Sign in**\.  
![\[IAM User Sign-in Page\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-iam-user-capture.png)

**To sign in to an AWS account as an IAM user using the main sign\-in page**

1. Open [https://console\.aws\.amazon\.com/](https://console.aws.amazon.com/)\.

1. If you have not signed in previously using this browser, the main sign\-in page appears\. Choose **IAM user**, enter the account alias or account ID, and choose **Next**\.  
![\[Main sign-in page with IAM user selected\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-main-capture-iam.png)

   If you have signed in as an IAM user previously using this browser, your browser might remember the account alias or account ID for the AWS account\. If so, you'll see the screen shown in the next step instead\.

1. Enter your IAM user name and password and choose **Sign in**\.  
![\[IAM User Sign-in Page\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/sign-in-iam-user-capture.png)

   If you have signed in as an IAM user for a different AWS account previously using this browser, or you need to sign in as a root user instead, choose **Sign in using root user email** to return to the main sign\-in page\.