# Troubleshoot AWS sign\-in or account issues<a name="troubleshoot_sign_in"></a>

Use the information here to help you troubleshoot sign\-in and other AWS account issues\. For step\-by\-step directions to sign in to an AWS account, see [Signing in to the AWS Management Console as an IAM user or root user](console.md)\.

If you are having trouble signing in to Amazon\.com, see [Amazon Customer Service](https://www.amazon.com/gp/help/customer/contact-us/) instead\.

**Topics**
+ [My credentials aren't working](#troubleshoot-my-credentials-are-not-working)
+ [I need my AWS account ID or AWS account alias](#troubleshoot-need-aws-account-id-or-alias)
+ [I forgot my IAM user name or password](#troubleshoot-forgot-iam-user-name-or-password)
+ [I forgot the root user password for my AWS account](#troubleshoot-forgot-root-password)
+ [I don't have access to the email for my AWS account](#troubleshoot_general_lost-root-creds)
+ [I need to change the credit card for my AWS account](#troubleshoot-change-credit-card)
+ [I need to report fraudulent AWS account activity](#troubleshoot-report-suspicious-account-activity)
+ [I need to close my AWS account](#troublehoot-close-aws-account)

## My credentials aren't working<a name="troubleshoot-my-credentials-are-not-working"></a>

When you can't sign in to the AWS Management Console, try to remember how you previously accessed AWS\.

**If you don't remember using a password at all**

You might have previously accessed AWS without using AWS credentials\. This is common for enterprise single sign\-on through IAM Identity Center\. Accessing AWS this way means that you use your corporate credentials to access AWS accounts or applications without entering your credentials\.
+ **AWS access portal** – If an administrator allows you to use credentials from outside AWS to access AWS, you need the URL for your portal\. Check your email, browser favorites, or browser history for a URL that includes `awsapps.com/start` or `signin.aws/platform/login`\.

  For example, your custom URL might include an ID or a domain such as `https://d-1234567890.awsapps.com/start`\. If you can't find your portal link, contact your administrator\. AWS Support can't help you recover this information\. 

**If you remember your user name and password**

You might be on the wrong page\. Try signing in on a different page:
+ **Root user sign\-in page** – If you created or own an AWS account and need to perform restricted actions, enter your account email address in the [AWS Management Console](https://console.aws.amazon.com/)\. To learn how to access the root user, see [Signing in as the root user](https://docs.aws.amazon.com/signin/latest/userguide/console-sign-in-tutorials.html#introduction-to-root-user-sign-in-tutorial) in the *AWS Sign\-In User Guide*\. If you forgot your root user password, you can reset it\. See [I forgot my root user password for my AWS account](https://docs.aws.amazon.com/signin/latest/userguide/troubleshooting-sign-in-issues.html#troubleshoot-forgot-root-password) in the *AWS Sign\-In User Guide* for more information\. If you forgot your AWS account email address, check your email inbox for an email from AWS\.
+ **IAM user sign\-in page** – If you or someone else created an IAM user within a single AWS account, you must know that account ID or alias\. Enter your account ID or alias, user name, and password in to the [AWS Management Console](https://console.aws.amazon.com/)\. To learn how to access the IAM user sign\-in page, see [Signing in as an IAM user](https://docs.aws.amazon.com/signin/latest/userguide/console-sign-in-tutorials.html#introduction-to-iam-user-sign-in-tutorial) in the *AWS Sign\-In User Guide*\. If you forgot your IAM user password, see [I forgot my IAM user password for my AWS account](https://docs.aws.amazon.com/signin/latest/userguide/troubleshooting-sign-in-issues.html#troubleshoot-forgot-iam-password) in the *AWS Sign\-In User Guide* for information on resetting your IAM user password\. If you forgot your account number, search your email, browser favorites, or browser history for a URL that includes `signin.aws.amazon.com/`\. Your account ID or alias will follow the `"account="` text in the URL\. If you can’t find your account ID or alias, contact your administrator\. AWS Support can’t help you recover this information\. You can’t see your account ID or alias until after you sign in\. 
+ **AWS access portal** – If an administrator set up an AWS IAM Identity Center \(successor to AWS Single Sign\-On\) identity source for AWS, you must sign in using your user name and password\. In this case, you need the URL for your portal\. Check your email, secure password storage, browser favorites, or browser history for a URL that includes `awsapps.com/start` or `signin.aws/platform/login`\. For example, your custom URL might include an ID or a domain such as `https://d-1234567890.awsapps.com/start.` If you can’t find your portal link, contact your administrator\. AWS Support can’t help you recover this information\.

For more assistance on troubleshooting your sign\-in issues, see [What do I do if I'm having trouble signing in to or accessing my AWS account?](http://aws.amazon.com/premiumsupport/knowledge-center/sign-in-account/)

The following video provides more information about how to sign in when your credentials aren't working:

## I need my AWS account ID or AWS account alias<a name="troubleshoot-need-aws-account-id-or-alias"></a>

If you are an IAM user and you are not signed in, you must ask your administrator for the AWS account ID or AWS account alias\. You need this information, plus your IAM user name and password, to sign in to an AWS account\.

## I forgot my IAM user name or password<a name="troubleshoot-forgot-iam-user-name-or-password"></a>

If you are an IAM user, your administrator provides your credentials\. If you forget your password, you must ask your administrator to reset it\.

For security purposes, AWS doesn't have access to view, provide, or change your credentials\.

## I forgot the root user password for my AWS account<a name="troubleshoot-forgot-root-password"></a>

If you are a root user and you have lost or forgot the password for your AWS account, you can reset your password\. You must know the email address used to create the AWS account and you must have access to the email account\. For more information, see [Resetting lost or forgotten passwords or access keys for AWS](id_credentials_access-keys_retrieve.md)\.

## I don't have access to the email for my AWS account<a name="troubleshoot_general_lost-root-creds"></a>

When you create an AWS account, you provide an email address and password\. These are the credentials for the AWS account root user\. If you are not sure of the email address associated with your AWS account, check for saved correspondence from no\-reply@amazon\.com to any email address for your organization that might have been used to open the AWS account\.

If you know the email address but no longer have access to the email, first try to recover access to the email using one of the following options:
+ If you own the domain for email address, you can restore a deleted email address\. Alternatively, you can set up a catch\-all for your email account, which "catches all" messages sent to email addresses that no longer exist in the mail server and redirects them to another email address\.
+ If the email address on the account is part of your corporate email system, we recommend that you contact your IT system administrators\. They might be able to help you regain access to the email\.

If you're still not able to sign in to your AWS account you can find alternate support options at [Contact us](https://aws.amazon.com/contact-us/)\. Choose **Still unable to log into your AWS account** and then choose one of the available support options\.

## I need to change the credit card for my AWS account<a name="troubleshoot-change-credit-card"></a>

To change the credit card for your AWS account, you must be able to sign in\. AWS has protections in place that require you to prove that you're the account owner\. For directions, see [Managing your credit card payment methods](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-cc.html) in the *AWS Billing User Guide*\.

## I need to report fraudulent AWS account activity<a name="troubleshoot-report-suspicious-account-activity"></a>

If you suspect fraudulent activity using your AWS account and would like to make a report, see [How do I report abuse of AWS resources](http://aws.amazon.com/premiumsupport/knowledge-center/report-aws-abuse/)\.

If you are having trouble with a purchase made on Amazon\.com, see [Amazon Customer Service](https://www.amazon.com/gp/help/customer/contact-us/)\.

## I need to close my AWS account<a name="troublehoot-close-aws-account"></a>

If you have an AWS account, you can use the following directions to close it: [Closing an Account](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/close-account.html) in the *Billing and Cost Management User Guide*\.