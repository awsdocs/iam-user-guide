# Identities \(Users, Groups, and Roles\)<a name="id"></a>

This section describes *IAM identities*, which you create to provide authentication for people and processes in your AWS account\. This section also describes IAM *groups*, which are collections of IAM users that you can manage as a unit\. Identities represent the user, and can be authenticated and then authorized to perform actions in AWS\. Each of these can be associated with one or more [*policies*](access.md) to determine what actions a user, role, or member of a group can do with which AWS resources and under what conditions\.

## [The AWS Account Root User](id_root-user.md)<a name="id_root"></a>

When you first create an AWS account, you create an account \(or root user\) identity, which you use to sign in to AWS\. You can sign in to the AWS Management Console as the root user—that is, the email address and password that you provide when you create the account\. This combination of your email address and password is called your root user credentials\.

When you sign in as the root user, you have complete, unrestricted access to all resources in your AWS account, including access to your billing information and the ability to change your password\. This level of access is necessary when you initially set up the account\. However, we recommend that you ***don't*** use root user credentials for everyday access\. We especially recommend that you do not share your root user credentials with anyone, because doing so gives them unrestricted access to your account\. It is not possible to restrict the permissions that are granted to the AWS account\. Instead, we strongly recommend that you adhere to the [best practice of using the root user only to create your first IAM user](best-practices.md#create-iam-users) and then securely locking away the root user credentials\. 

## [IAM Users](id_users.md)<a name="id_iam-users"></a>

An IAM [*user*](id_users.md) is an entity that you create in AWS\. The IAM user represents the person or service who uses the IAM user to interact with AWS\. A primary use for IAM users is to give people the ability to sign in to the AWS Management Console for interactive tasks and to make programmatic requests to AWS services using the API or CLI\. A user in AWS consists of a name, a password to sign into the AWS Management Console, and up to two access keys that can be used with the API or CLI\. When you create an IAM user, you grant it permissions by making it a member of a group that has appropriate permission policies attached \(recommended\), or by directly attaching policies to the user\. You can also clone the permissions of an existing IAM user, which automatically makes the new user a member of the same groups and attaches all the same policies\.

## [IAM Groups](id_groups.md)<a name="id_iam-groups"></a>

An IAM [*group*](id_groups.md) is a collection of IAM users\. You can use groups to specify permissions for a collection of users, which can make those permissions easier to manage for those users\. For example, you could have a group called *Admins* and give that group the types of permissions that administrators typically need\. Any user in that group automatically has the permissions that are assigned to the group\. If a new user joins your organization and should have administrator privileges, you can assign the appropriate permissions by adding the user to that group\. Similarly, if a person changes jobs in your organization, instead of editing that user's permissions, you can remove him or her from the old groups and add him or her to the appropriate new groups\. Note that a group is not truly an identity because it cannot be identified as a `Principal` in a [resource\-based or trust policy](access_policies_identity-vs-resource.md)\. It is only a way to attach policies to multiple users at one time\.

## [IAM Roles](id_roles.md)<a name="id_iam-roles"></a>

An IAM [*role*](id_roles.md) is very similar to a user, in that it is an identity with permission policies that determine what the identity can and cannot do in AWS\. However, a role does not have any credentials \(password or access keys\) associated with it\. Instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it\. An IAM user can assume a role to temporarily take on different permissions for a specific task\. A role can be assigned to a [federated user](id_roles_providers.md) who signs in by using an external identity provider instead of IAM\. AWS uses details passed by the identity provider to determine which role is mapped to the federated user\.

## [Temporary Credentials](id_credentials_temp.md)<a name="id_temp-creds"></a>

Temporary credentials are primarily used with IAM roles, but there are also other uses\. You can request temporary credentials that have a more restricted set of permissions than your standard IAM user\. This prevents you from accidentally performing tasks that are not permitted by the more restricted credentials\. A benefit of temporary credentials is that they expire automatically after a set period of time\. You have control over the duration that the credentials are valid\.

## When to Create an IAM User \(Instead of a Role\)<a name="id_which-to-choose"></a>

Because an IAM user is just an identity with specific permissions in your account, you might not need to create an IAM user for every occasion on which you need credentials\. In many cases, you can take advantage of IAM *roles* and their temporary security credentials instead of using the long\-term credentials associated with an IAM user\. 
+ **You created an AWS account and you're the only person who works in your account\.**

  It's possible to work with AWS using the root user credentials for your AWS account, but we don't recommend it\. Instead, we strongly recommend that you create an IAM user for yourself and use the credentials for that user when you work with AWS\. For more information, see [IAM Best Practices](best-practices.md)\.
+ **Other people in your group need to work in your AWS account, and your group is using no other identity mechanism\.**

  Create IAM users for the individuals who need access to your AWS resources, assign appropriate permissions to each user, and give each user his or her own credentials\. We strongly recommend that you never share credentials among multiple users\. 
+ **You want to use the [command\-line interface](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html) \(CLI\) to work with AWS\.**

  The CLI needs credentials that it can use to make calls to AWS\. Create an IAM user and give that user permissions to run the CLI commands you need\. Then configure the CLI on your computer to use the access key credentials associated with that IAM user\. 

## When to Create an IAM Role \(Instead of a User\)<a name="id_which-to-choose_role"></a>

Create an IAM role in the following situations:

**You're creating an application that runs on an Amazon Elastic Compute Cloud \(Amazon EC2\) instance and that application makes requests to AWS\.**  
Don't create an IAM user and pass the user's credentials to the application or embed the credentials in the application\. Instead, create an IAM role that you attach to the EC2 instance to give applications running on the instance temporary security credentials\. The credentials have the permissions specified in the policies attached to the role\. For details, see [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)\.

**You're creating an app that runs on a mobile phone and that makes requests to AWS\.**  
Don't create an IAM user and distribute the user's access key with the app\. Instead, use an identity provider like Login with Amazon, Amazon Cognito, Facebook, or Google to authenticate users and map the users to an IAM role\. The app can use the role to get temporary security credentials that have the permissions specified by the policies attached to the role\. For more information, see the following:   
+ [Amazon Cognito Overview](http://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html#d0e840) in the *AWS Mobile SDK for Android Developer Guide*
+ [Amazon Cognito Overview](http://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html#d0e664) in the *AWS Mobile SDK for iOS Developer Guide*
+ [About Web Identity Federation](id_roles_providers_oidc.md)

**Users in your company are authenticated in your corporate network and want to be able to use AWS without having to sign in again—that is, you want to allow users to federate into AWS\.**  
Don't create IAM users\. Configure a federation relationship between your enterprise identity system and AWS\. You can do this in two ways:   
+ If your company's identity system is compatible with SAML 2\.0, you can establish trust between your company's identity system and AWS\. For more information, see [About SAML 2\.0\-based Federation](id_roles_providers_saml.md)\.
+ Create and use a custom proxy server that translates user identities from the enterprise into IAM roles that provide temporary AWS security credentials\. For more information, see [Creating a URL that Enables Federated Users to Access the AWS Management Console \(Custom Federation Broker\)](id_roles_providers_enable-console-custom-url.md)\.