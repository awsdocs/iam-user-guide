# About web identity federation<a name="id_roles_providers_oidc"></a>

Imagine that you are creating a mobile app that accesses AWS resources, such as a game that runs on a mobile device and stores player and score information using Amazon S3 and DynamoDB\. 

When you write such an app, you'll make requests to AWS services that must be signed with an AWS access key\. However, we **strongly** recommend that you do **not** embed or distribute long\-term AWS credentials with apps that a user downloads to a device, even in an encrypted store\. Instead, build your app so that it requests temporary AWS security credentials dynamically when needed using *web identity federation*\. The supplied temporary credentials map to an AWS role that has only the permissions needed to perform the tasks required by the mobile app\.

With web identity federation, you don't need to create custom sign\-in code or manage your own user identities\. Instead, users of your app can sign in using a well\-known external identity provider \(IdP\), such as Login with Amazon, Facebook, Google, or any other [OpenID Connect \(OIDC\)](http://openid.net/connect/)\-compatible IdP\. They can receive an authentication token, and then exchange that token for temporary security credentials in AWS that map to an IAM role with permissions to use the resources in your AWS account\. Using an IdP helps you keep your AWS account secure, because you don't have to embed and distribute long\-term security credentials with your application\.

For most scenarios, we recommend that you use [Amazon Cognito](https://aws.amazon.com/cognito/) because it acts as an identity broker and does much of the federation work for you\. For details, see the following section, [Using Amazon Cognito for mobile apps](id_roles_providers_oidc_cognito.md)\.

If you don't use Amazon Cognito, then you must write code that interacts with a web IdP, such as Facebook, and then calls the `AssumeRoleWithWebIdentity` API to trade the authentication token you get from those IdPs for AWS temporary security credentials\. If you have already used this approach for existing apps, you can continue to use it\.

**Topics**
+ [Using Amazon Cognito for mobile apps](id_roles_providers_oidc_cognito.md)
+ [Using web identity federation API operations for mobile apps](id_roles_providers_oidc_manual.md)
+ [Identifying users with web identity federation](id_roles_providers_oidc_user-id.md)
+ [Additional resources for web identity federation](id_roles_providers_oidc_resources.md)