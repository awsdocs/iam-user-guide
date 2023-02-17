# Overview of AWS identity management: Users<a name="introduction_identity-management"></a>

For greater security and organization, you can give access to your AWS account to specific users—identities that you create with custom permissions\. You can further simplify access for those users by federating existing identities into AWS\. As a [best practice](best-practices.md), require human users to use federation with an identity provider to access AWS using temporary credentials instead of as an IAM user\. A primary use for IAM users is to give workloads that cannot use IAM roles the ability to make programmatic requests to AWS services using the API or CLI\. 

**Topics**
+ [First\-time access only: Your root user credentials](#intro-identity-first-time-access)
+ [IAM users](#intro-identity-users)
+ [Federating existing users](#intro-identity-federation)

## First\-time access only: Your root user credentials<a name="intro-identity-first-time-access"></a>

When you create an AWS account, you create an AWS account root user identity, which you use to sign in to AWS\. You can sign in to the AWS Management Console using this root user identity—that is, the email address and password that you provided when creating the account\. This combination of your email address and password is also called your *root user credentials*\.

When you use your root user credentials, you have complete, unrestricted access to all resources in your AWS account, including access to your billing information and the ability to change your password\. This level of access is necessary when you first set up your account\. However, we recommend that you **don't** use root user credentials for everyday access\. We especially recommend that you do not share your root user credentials with anyone, because doing so gives them unrestricted access to your account\. Only service control policies \(SCPs\) in organizations can restrict the permissions that are granted to the root user\. 

The following sections explain how you can use IAM to create and manage user identity and permissions to provide secure, limited access to your AWS resources, both for yourself and for others who need to work with your AWS resources\.

## IAM users<a name="intro-identity-users"></a>

The "identity" aspect of AWS Identity and Access Management \(IAM\) helps you with the question "Who is that user?", often referred to as *authentication*\. IAM users are not separate accounts; they are users within your account\. Each user can have its own password for access to the AWS Management Console\. You can also create an individual access key for each user so that the user can make programmatic requests to work with resources in your account\.

IAM users are granted long term credentials to your AWS resources\. As a best practice, you should require your human users to use temporary credentials when accessing AWS\. You can use an identity provider for your human users to provide federated access to AWS accounts by assuming roles, which provide temporary credentials\. For centralized access management, we recommend that you use [AWS IAM Identity Center \(successor to AWS Single Sign\-On\) \(IAM Identity Center\)](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) to manage access to your accounts and permissions within those accounts\. You can manage your user identities with IAM Identity Center, or manage access permissions for user identities in IAM Identity Center from an external identity provider\. For more information, see [What is AWS IAM Identity Center \(successor to AWS Single Sign\-On\)](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\.

For more information about roles, see [Roles terms and concepts](id_roles_terms-and-concepts.md)\.

In the following figure, the users Li, Mateo, DevApp1, DevApp2, TestApp1, and TestApp2 have been added to a single AWS account\. Each user has its own credentials\. Li and Mateo are human users that have been granted long\-term credentials for emergency use only, while the others are workloads that cannot assume AWS roles\.

![\[An AWS account with individual IAM users, each of whom has credentials.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/iam-intro-account-with-users.diagram.png)

**Note**  
For scenarios in which you need IAM users with programmatic access and long\-term credentials, we recommend that you rotate access keys\. For more information, see [Rotating access keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

## Federating existing users<a name="intro-identity-federation"></a>

If the users in your organization already have a way to be authenticated, such as by signing in to your corporate network, you don't have to create separate IAM users for them\. Instead, you can *federate* those user identities into AWS\.

The following diagram shows how a user can use IAM to get temporary AWS security credentials to access resources in your AWS account\. 

![\[Users who are already authenticated elsewhere can be federated into AWS without requiring an IAM user.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[Users who are already authenticated elsewhere can be federated into AWS without requiring an IAM user.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

Federation is particularly useful in these cases: 
+ **Your users already have identities in a corporate directory\.** 

  If your corporate directory is compatible with Security Assertion Markup Language 2\.0 \(SAML 2\.0\), you can configure your corporate directory to provide single\-sign on \(SSO\) access to the AWS Management Console for your users\. For more information, see [Common scenarios for temporary credentials](id_credentials_temp.md#sts-introduction)\. 

  If your corporate directory is not compatible with SAML 2\.0, you can create an identity broker application to provide single\-sign on \(SSO\) access to the AWS Management Console for your users\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\. 

  If your corporate directory is Microsoft Active Directory, you can use [AWS Directory Service](https://aws.amazon.com/directoryservice/) to establish trust between your corporate directory and your AWS account\. 
+ **Your users already have Internet identities\.**

  If you are creating a mobile app or web\-based app that can let users identify themselves through an Internet identity provider like Login with Amazon, Facebook, Google, or any OpenID Connect \(OIDC\) compatible identity provider, the app can use federation to access AWS\. For more information, see [About web identity federation](id_roles_providers_oidc.md)\. 
**Tip**  
To use identity federation with Internet identity providers, we recommend you use [Amazon Cognito](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html)\.