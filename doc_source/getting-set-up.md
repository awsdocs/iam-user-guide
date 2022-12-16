# Getting set up with IAM<a name="getting-set-up"></a>

**Important**  
The IAM best practices have been updated\. As a [best practice](best-practices.md), require human users to use federation with an identity provider to access AWS using temporary credentials\. An additional best practice recommendation is to require workloads to use temporary credentials with IAM roles to access AWS\. IAM users are to be used only in very limited scenarios where an IAM role cannot be assumed\. To learn about using AWS IAM Identity Center \(successor to AWS Single Sign\-On\) to create users with temporary credentials, see [Getting started](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\. 

AWS Identity and Access Management \(IAM\) helps you securely control access to Amazon Web Services \(AWS\) and your account resources\. IAM can also keep your account credentials private\. You don't need to specifically sign up to use IAM\. There is no charge to use IAM\. 

**Note**  
IAM works only with AWS products that are integrated with IAM\. For a list of services that support IAM, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

Use IAM to give identities, such as users and roles, access to resources in your account\. As a [best practice](best-practices.md), we recommend that you require human users to use federation with an identity provider to access AWS using temporary credentials\. For example, you can use IAM with existing users in your corporate directory that you manage external to AWS or you can create users in AWS using AWS IAM Identity Center \(successor to AWS Single Sign\-On\)\. Federated identities assume defined IAM roles to access only the resources they need\. For more information about IAM Identity Center, see [What is IAM Identity Center?](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide\.*

As a security best practice, do not create IAM users to grant access to humans user because they have long term credentials\.

**Topics**
+ [Access control methods](#AccessControlMethods)
+ [Sign up for an AWS account](#sign-up-for-aws)
+ [Create an administrative user](#create-an-admin)

## Access control methods<a name="AccessControlMethods"></a>

Here are the ways you can use IAM to control access to your AWS resources\.

## Sign up for an AWS account<a name="sign-up-for-aws"></a>

If you do not have an AWS account, complete the following steps to create one\.

**To sign up for an AWS account**

1. Open [https://portal\.aws\.amazon\.com/billing/signup](https://portal.aws.amazon.com/billing/signup)\.

1. Follow the online instructions\.

   Part of the sign\-up procedure involves receiving a phone call and entering a verification code on the phone keypad\.

   When you sign up for an AWS account, an *AWS account root user* is created\. The root user has access to all AWS services and resources in the account\. As a security best practice, [assign administrative access to an administrative user](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html), and use only the root user to perform [tasks that require root user access](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html)\.

AWS sends you a confirmation email after the sign\-up process is complete\. At any time, you can view your current account activity and manage your account by going to [https://aws\.amazon\.com/](https://aws.amazon.com/) and choosing **My Account**\.

## Create an administrative user<a name="create-an-admin"></a>

After you sign up for an AWS account, create an administrative user so that you don't use the root user for everyday tasks\.

**Secure your AWS account root user**

1.  Sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.

   For help signing in by using root user, see [Signing in as the root user](https://docs.aws.amazon.com/signin/latest/userguide/console-sign-in-tutorials.html#introduction-to-root-user-sign-in-tutorial) in the *AWS Sign\-In User Guide*\.

1. Turn on multi\-factor authentication \(MFA\) for your root user\.

   For instructions, see [Enable a virtual MFA device for your AWS account root user \(console\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html#enable-virt-mfa-for-root) in the *IAM User Guide*\.

**Create an administrative user**
+ For your daily administrative tasks, grant administrative access to an administrative user in AWS IAM Identity Center \(successor to AWS Single Sign\-On\)\.

  For instructions, see [Getting started](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\.

**Sign in as the administrative user**
+ To sign in with your IAM Identity Center user, use the sign\-in URL that was sent to your email address when you created the IAM Identity Center user\.

  For help signing in using an IAM Identity Center user, see [Signing in to the AWS access portal](https://docs.aws.amazon.com/signin/latest/userguide/iam-id-center-sign-in-tutorial.html) in the *AWS Sign\-In User Guide*\.