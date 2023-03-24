# Getting set up with IAM<a name="getting-set-up"></a>

**Important**  
 IAM [best practices](best-practices.md) recommend that you require human users to use federation with an identity provider to access AWS using temporary credentials instead of using IAM users with long\-term credentials\.

AWS Identity and Access Management \(IAM\) helps you securely control access to Amazon Web Services \(AWS\) and your account resources\. IAM can also keep your sign\-in credentials private\. You don't need to specifically sign up to use IAM\. There is no charge to use IAM\. 

Use IAM to give identities, such as users and roles, access to resources in your account\. For example, you can use IAM with existing users in your corporate directory that you manage external to AWS or you can create users in AWS using AWS IAM Identity Center \(successor to AWS Single Sign\-On\)\. Federated identities assume defined IAM roles to access only the resources they need\. For more information about IAM Identity Center, see [What is IAM Identity Center?](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide\.*

**Note**  
IAM works only with AWS products that are integrated with IAM\. For a list of services that support IAM, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

**Topics**
+ [Sign up for an AWS account](#sign-up-for-aws)
+ [Create an administrative user](#create-an-admin)
+ [Prepare for least\-privilege permissions](#LeastPrivilege)

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

## Prepare for least\-privilege permissions<a name="LeastPrivilege"></a>

Using *least\-privilege permissions* is an IAM best practice recommendation\. The concept of least\-privilege permissions is to grant users only the permissions required to perform a task\. As you get set up, consider how you are going to support least\-privilege permissions\. Both the root user and the administrator user have powerful privileges that are not required for everyday tasks\. While you are learning about AWS and testing out different services we recommend that you create at least one additional user in IAM Identity Center with lesser privileges that you can use in different scenarios\. You can use IAM policies to define the actions that can be taken on specific resources under specific conditions and then connect to those resources with your lesser privileged account\.

If you are using IAM Identity Center, consider using IAM Identity Center permissions sets to get started\. To learn more, see [Create a permission set](https://docs.aws.amazon.com/singlesignon/latest/userguide/howtocreatepermissionset.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\. 

If you are not using IAM Identity Center, use IAM roles to define the privileges for different IAM entities\. To learn more, see [Creating IAM roles](id_roles_create.md)\.

Both IAM roles and IAM Identity Center permissions sets can use AWS managed policies based on job functions\. For details on the permissions granted by these policies, see [AWS managed policies for job functions](access_policies_job-functions.md)\. 

**Important**  
Keep in mind that AWS managed policies might not grant least\-privilege permissions for your specific use cases because they are available for use by all AWS customers\. After getting set up, we recommend that you use IAM Access Analyzer to generate least\-privilege policies based on your access activity that is logged in AWS CloudTrail\. For more information about policy generation, see [IAM Access Analyzer policy generation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-generation.html)\.