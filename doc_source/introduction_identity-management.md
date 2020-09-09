# Overview of AWS identity management: Users<a name="introduction_identity-management"></a>

For greater security and organization, you can give access to your AWS account to specific users—identities that you create with custom permissions\. You can further simplify access for those users by federating existing identities into AWS\. 

**Topics**
+ [First\-time access only: Your root user credentials](#intro-identity-first-time-access)
+ [IAM users](#intro-identity-users)
+ [Federating existing users](#intro-identity-federation)

## First\-time access only: Your root user credentials<a name="intro-identity-first-time-access"></a>

When you create an AWS account, you create an AWS account root user identity, which you use to sign in to AWS\. You can sign in to the AWS Management Console using this root user identity—that is, the email address and password that you provided when creating the account\. This combination of your email address and password is also called your *root user credentials*\.

When you use your root user credentials, you have complete, unrestricted access to all resources in your AWS account, including access to your billing information and the ability to change your password\. This level of access is necessary when you first set up your account\. However, we recommend that you **don't** use root user credentials for everyday access\. We especially recommend that you do not share your root user credentials with anyone, because doing so gives them unrestricted access to your account\. It is not possible to restrict the permissions that are granted to the root user\. 

The following sections explain how you can use IAM to create and manage user identity and permissions to provide secure, limited access to your AWS resources, both for yourself and for others who need to work with your AWS resources\.

## IAM users<a name="intro-identity-users"></a>

The "identity" aspect of AWS Identity and Access Management \(IAM\) helps you with the question "Who is that user?", often referred to as *authentication*\. Instead of sharing your root user credentials with others, you can create individual IAM users within your account that correspond to users in your organization\. IAM users are not separate accounts; they are users within your account\. Each user can have its own password for access to the AWS Management Console\. You can also create an individual access key for each user so that the user can make programmatic requests to work with resources in your account\. In the following figure, the users Li, Mateo, DevApp1, DevApp2, TestApp1, and TestApp2 have been added to a single AWS account\. Each user has its own credentials\. 

![\[An AWS account with individual IAM users, each of whom has credentials.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/iam-intro-account-with-users.diagram.png)

Notice that some of the users are actually applications \(for example, DevApp1\)\. An IAM user doesn't have to represent an actual person; you can create an IAM user in order to generate an access key for an application that runs in your corporate network and needs AWS access\.

We recommend that you create an IAM user for yourself and then assign yourself administrative permissions for your account\. You can then sign in as that user to add more users as needed\. 

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