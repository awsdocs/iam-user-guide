# Overview of AWS identity management: Users<a name="introduction_identity-management"></a>

You can give access to your AWS account to specific users and provide them specific permissions to access resources in your AWS account\. You can use both IAM and AWS IAM Identity Center \(successor to AWS Single Sign\-On\) to create new users or federate existing users into AWS\. The main difference between the two is that IAM users are granted long\-term credentials to your AWS resources while users in IAM Identity Center have temporary credentials that are established each time the user signs\-in to AWS\. As a [best practice](best-practices.md), require human users to use federation with an identity provider to access AWS using temporary credentials instead of as an IAM user\. A primary use for IAM users is to give workloads that cannot use IAM roles the ability to make programmatic requests to AWS services using the API or CLI\. 

**Topics**
+ [First\-time access only: Your root user credentials](#intro-identity-first-time-access)
+ [IAM users and users in IAM Identity Center](#intro-identity-users)
+ [Federating existing users](#intro-identity-federation)
+ [Access control methods](#AccessControlMethods)

## First\-time access only: Your root user credentials<a name="intro-identity-first-time-access"></a>

  When you create an AWS account, you begin with one sign\-in identity that has complete access to all AWS services and resources in the account\. This identity is called the AWS account *root user* and is accessed by signing in with the email address and password that you used to create the account\. We strongly recommend that you don't use the root user for your everyday tasks\. Safeguard your root user credentials and use them to perform the tasks that only the root user can perform\. For the complete list of tasks that require you to sign in as the root user, see [Tasks that require root user credentials](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html) in the *AWS Account Management Reference Guide*\. Only service control policies \(SCPs\) in organizations can restrict the permissions that are granted to the root user\. 

## IAM users and users in IAM Identity Center<a name="intro-identity-users"></a>

 IAM users are not separate accounts; they are users within your account\. Each user can have its own password for access to the AWS Management Console\. You can also create an individual access key for each user so that the user can make programmatic requests to work with resources in your account\.

IAM users are granted long\-term credentials to your AWS resources\. As a best practice, do not create IAM users with long\-term credentials for your human users\. Instead, require your human users to use temporary credentials when accessing AWS\. 

**Note**  
For scenarios in which you need IAM users with programmatic access and long\-term credentials, we recommend that you rotate access keys\. For more information, see [Rotating access keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

In contrast, users in AWS IAM Identity Center \(successor to AWS Single Sign\-On\) are granted short\-term credentials to your AWS resources\. For centralized access management, we recommend that you use [AWS IAM Identity Center \(successor to AWS Single Sign\-On\) \(IAM Identity Center\)](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) to manage access to your accounts and permissions within those accounts\. IAM Identity Center is automatically configured with an Identity Center directory as your default identity source where you can create users and groups, and assign their level of access to your AWS resources\. For more information, see [What is AWS IAM Identity Center \(successor to AWS Single Sign\-On\)](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\.

## Federating existing users<a name="intro-identity-federation"></a>

If the users in your organization already have a way to be authenticated, such as by signing in to your corporate network, you don't have to create separate IAM users or users in IAM Identity Center for them\. Instead, you can *federate* those user identities into AWS using either IAM or AWS IAM Identity Center \(successor to AWS Single Sign\-On\)\.

The following diagram shows how a user can get temporary AWS security credentials to access resources in your AWS account\. 

![\[Users who are already authenticated elsewhere can be federated into AWS and assume an IAM role that gives them permissions to access specific resources.For more information about roles, see .\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[Users who are already authenticated elsewhere can be federated into AWS and assume an IAM role that gives them permissions to access specific resources.For more information about roles, see .\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

Federation is particularly useful in these cases: 
+ **Your users already exist in a corporate directory\.** 

  If your corporate directory is compatible with Security Assertion Markup Language 2\.0 \(SAML 2\.0\), you can configure your corporate directory to provide single\-sign on \(SSO\) access to the AWS Management Console for your users\. For more information, see [Common scenarios for temporary credentials](id_credentials_temp.md#sts-introduction)\. 

  If your corporate directory is not compatible with SAML 2\.0, you can create an identity broker application to provide single\-sign on \(SSO\) access to the AWS Management Console for your users\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\. 

  If your corporate directory is Microsoft Active Directory, you can use AWS IAM Identity Center \(successor to AWS Single Sign\-On\) to connect a self\-managed directory in Active Directory or a directory in [AWS Directory Service](https://aws.amazon.com/directoryservice/) to establish trust between your corporate directory and your AWS account\. 

  If you are using an external identity provider \(IdP\) such as Okta or Azure Active Directory to manage users, you can use AWS IAM Identity Center \(successor to AWS Single Sign\-On\) to establish trust between your IdP and your AWS account\. For more information, see [Connect to an external identity provider](https://docs.aws.amazon.com/singlesignon/latest/userguide/manage-your-identity-source-idp.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\.
+ **Your users already have Internet identities\.**

  If you are creating a mobile app or web\-based app that can let users identify themselves through an Internet identity provider like Login with Amazon, Facebook, Google, or any OpenID Connect \(OIDC\) compatible identity provider, the app can use federation to access AWS\. For more information, see [About web identity federation](id_roles_providers_oidc.md)\. 
**Tip**  
To use identity federation with Internet identity providers, we recommend you use [Amazon Cognito](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html)\.

## Access control methods<a name="AccessControlMethods"></a>

Here are the ways you can control access to your AWS resources\.