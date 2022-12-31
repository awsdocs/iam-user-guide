# IAM Identities \(users, user groups, and roles\)<a name="id"></a>

**Important**  
The IAM best practices have been updated\. As a [best practice](best-practices.md), require human users to use federation with an identity provider to access AWS using temporary credentials\. An additional best practice recommendation is to require workloads to use temporary credentials with IAM roles to access AWS\. IAM users are to be used only in very limited scenarios where an IAM role cannot be assumed\. To learn about using AWS IAM Identity Center \(successor to AWS Single Sign\-On\) to create users with temporary credentials, see [Getting started](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\. 

**Tip**  
**Having trouble signing in to AWS?** Make sure that you're on the correct [AWS sign\-in page](console.md) for your type of user:  
To sign in as the AWS account root user \(account owner\), use the credentials that you set up when you created the AWS account\.
To sign in as an IAM user, use the credentials your account administrator gave you to sign in to AWS\.
To sign in with your IAM Identity Center user, use the sign\-in URL that was sent to your email address when you created the IAM Identity Center user\.  
For help signing in using an IAM Identity Center user, see [Signing in to the AWS access portal](https://docs.aws.amazon.com/signin/latest/userguide/iam-id-center-sign-in-tutorial.html) in the *AWS Sign\-In User Guide*\.

**Note**  
If you need to request support, do not use the **Feedback** link on this page\. Feedback you enter is received by the AWS Documentation team, not AWS Support\. Instead, choose the **Contact Us** link at the top of this page\. There, you'll find links to resources to help you get the support that you need\.

The AWS account root user or an IAM administrator for the account can create *IAM identities*\. An IAM identity provides access to an AWS account\. An *IAM user group* is a collection of IAM users managed as a unit\. An IAM identity represents a human user or programmatic workload, and can be authenticated and then authorized to perform actions in AWS\. Each IAM identity can be associated with one or more *policies*\. Policies determine what actions a user, role, or member of a user group can perform, on which AWS resources, and under what conditions\.

## [AWS account root user](id_root-user.md)<a name="id_root"></a>

When you first create an AWS account, you begin with one sign\-in identity that has complete access to all AWS services and resources in the account\. This identity is called the AWS account *root user* and is accessed by signing in with the email address and password that you used to create the account\.

**Important**  
We strongly recommend that you don't use the root user for your everyday tasks\. Safeguard your root user credentials and use them to perform the tasks that only the root user can perform\. For the complete list of tasks that require you to sign in as the root user, see [Tasks that require root user credentials](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html) in the *AWS Account Management Reference Guide*\.

## [IAM users](id_users.md)<a name="id_iam-users"></a>

An *[IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* is an identity within your AWS account that has specific permissions for a single person or application\. Where possible, we recommend relying on temporary credentials instead of creating IAM users who have long\-term credentials such as passwords and access keys\. However, if you have specific use cases that require long\-term credentials with IAM users, we recommend that you rotate access keys\. For more information, see [Rotate access keys regularly for use cases that require long\-term credentials](best-practices.md#rotate-credentials)\.To add IAM users to your AWS account, see [Creating an IAM user in your AWS account](id_users_create.md)\.

## [IAM user groups](id_groups.md)<a name="id_iam-groups"></a>

An [https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html) is an identity that specifies a collection of IAM users\. You can't use a group to sign\-in\. You can use groups to specify permissions for multiple users at a time\. Groups make permissions easier to manage for large sets of users\. For example, you could have a group named *IAMPublishers* and give that group the types of permissions that publishing workloads typically need\.

## [IAM roles](id_roles.md)<a name="id_iam-roles"></a>

An *[IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)* is an identity within your AWS account that has specific permissions\. It is similar to an IAM user, but is not associated with a specific person\. You can temporarily assume an IAM role in the AWS Management Console by [switching roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-console.html)\. You can assume a role by calling an AWS CLI or AWS API operation or by using a custom URL\. For more information about methods for using roles, see [Using IAM roles](id_roles_use.md)\.

IAM roles with temporary credentials are used in the following situations:
+ **Federated user access** –  To assign permissions to a federated identity, you create a role and define permissions for the role\. When a federated identity authenticates, the identity is associated with the role and is granted the permissions that are defined by the role\. For information about roles for federation, see [ Creating a role for a third\-party Identity Provider](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-idp.html) in the *IAM User Guide*\. If you use IAM Identity Center, you configure a permission set\. To control what your identities can access after they authenticate, IAM Identity Center correlates the permission set to a role in IAM\. For information about permissions sets, see [ Permission sets](https://docs.aws.amazon.com/singlesignon/latest/userguide/permissionsetsconcept.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\. 
+ **Temporary IAM user permissions** – An IAM user or role can assume an IAM role to temporarily take on different permissions for a specific task\.
+ **Cross\-account access** – You can use an IAM role to allow someone \(a trusted principal\) in a different account to access resources in your account\. Roles are the primary way to grant cross\-account access\. However, with some AWS services, you can attach a policy directly to a resource \(instead of using a role as a proxy\)\. To learn the difference between roles and resource\-based policies for cross\-account access, see [How IAM roles differ from resource\-based policies](id_roles_compare-resource-policies.md)\.
+ **Cross\-service access** –  Some AWS services use features in other AWS services\. For example, when you make a call in a service, it's common for that service to run applications in Amazon EC2 or store objects in Amazon S3\. A service might do this using the calling principal's permissions, using a service role, or using a service\-linked role\. 
  + **Principal permissions** –  When you use an IAM user or role to perform actions in AWS, you are considered a principal\. Policies grant permissions to a principal\. When you use some services, you might perform an action that then triggers another action in a different service\. In this case, you must have permissions to perform both actions\. To see whether an action requires additional dependent actions in a policy, see [Actions, resources, and condition keys for Identity And Access Management;](https://docs.aws.amazon.com/service-authorization/latest/reference/list_identityandaccessmanagement.html) in the *Service Authorization Reference*\. 
  + **Service role** –  A service role is an [IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) that a service assumes to perform actions on your behalf\. An IAM administrator can create, modify, and delete a service role from within IAM\. For more information, see [Creating a role to delegate permissions to an AWS service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the *IAM User Guide*\. 
  + **Service\-linked role** –  A service\-linked role is a type of service role that is linked to an AWS service\. The service can assume the role to perform an action on your behalf\. Service\-linked roles appear in your IAM account and are owned by the service\. An IAM administrator can view, but not edit the permissions for service\-linked roles\. 
+ **Applications running on Amazon EC2** –  You can use an IAM role to manage temporary credentials for applications that are running on an EC2 instance and making AWS CLI or AWS API requests\. This is preferable to storing access keys within the EC2 instance\. To assign an AWS role to an EC2 instance and make it available to all of its applications, you create an instance profile that is attached to the instance\. An instance profile contains the role and enables programs that are running on the EC2 instance to get temporary credentials\. For more information, see [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html) in the *IAM User Guide*\. 

## [Temporary credentials in IAM](id_credentials_temp.md)<a name="id_temp-creds"></a>

As a [best practice](best-practices.md), use temporary credentials with both human users and workloads\. Temporary credentials are primarily used with IAM roles, but there are also other uses\. You can request temporary credentials that have a more restricted set of permissions than your standard IAM user\. This prevents you from accidentally performing tasks that are not permitted by the more restricted credentials\. A benefit of temporary credentials is that they expire automatically after a set period of time\. You have control over the duration that the credentials are valid\.

## When to use IAM Identity Center users?<a name="id_sso_users"></a>

 We recommend that all human users use IAM Identity Center to access AWS resources\. IAM Identity Center enables significant improvements over accessing AWS resources as an IAM user\. IAM Identity Center provides:
+ A central set of identities and assignments
+ Access to accounts across an entire AWS Organization 
+ Connection to your existing identity provider
+ Temporary credentials
+ Multi\-factor authentication \(MFA\) 
+ Self\-service MFA configuration for end\-users
+ Administrative enforcement of MFA usage
+ Single sign\-on to all AWS account entitlements

For more information, see [What is IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/singlesignon/latest/userguide/what-is.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\.

## When to create an IAM user \(instead of a role\)<a name="id_which-to-choose"></a>

We recommend you only use IAM users for use cases not supported by federated users\. Some of the use cases include the following:
+ **Workloads that cannot use IAM roles** – You might run a workload from a location that needs to access AWS\. In some situations, you can't use IAM roles to provide temporary credentials, such as for WordPress plugins\. In these situations, use IAM user long\-term access keys for that workload to authenticate to AWS\.
+ **Third\-party AWS clients** – If you are using tools that don’t support access with IAM Identity Center, such as third\-party AWS clients or vendors that are not hosted on AWS, use IAM user long\-term access keys\.
+ **AWS CodeCommit access** – If you are using CodeCommit to store your code, you can use an IAM user with either SSH keys or service\-specific credentials for CodeCommit to authenticate to your repositories\. We recommend that you do this in addition to using a user in IAM Identity Center for normal authentication\. Users in IAM Identity Center are the people in your workforce who need access to your AWS accounts or to your cloud applications\. To give users access to your CodeCommit repositories without configuring IAM users, you can configure the git\-remote\-codecommit utility\. For more information about IAM and CodeCommit, see [Using IAM with CodeCommit: Git credentials, SSH keys, and AWS access keys](id_credentials_ssh-keys.md)\. For more information about configuring the git\-remote\-codecommit utility, see [Connecting to AWS CodeCommit repositories with rotating credentials](https://docs.aws.amazon.com/codecommit/latest/userguide/temporary-access.html#temporary-access-configure-credentials) in the *AWS CodeCommit User Guide*\.
+ **Amazon Keyspaces \(for Apache Cassandra\) access** – In a situation where you are unable to use users in IAM Identity Center, such as for testing purposes for Cassandra compatibility, you can use an IAM user with service\-specific credentials to authenticate with Amazon Keyspaces\. Users in IAM Identity Center are the people in your workforce who need access to your AWS accounts or to your cloud applications\. You can also connect to Amazon Keyspaces using temporary credentials\. For more information, see [Using temporary credentials to connect to Amazon Keyspaces using an IAM role and the SigV4 plugin](https://docs.aws.amazon.com/keyspaces/latest/devguide/access.credentials.html#temporary.credentials.IAM) in the *Amazon Keyspaces \(for Apache Cassandra\) Developer Guide*\.

## When to create an IAM role \(instead of a user\)<a name="id_which-to-choose_role"></a>

Create an IAM role in the following situations:

**You're creating an application that runs on an Amazon Elastic Compute Cloud \(Amazon EC2\) instance and that application makes requests to AWS\.**  
Don't create an IAM user and pass the user's credentials to the application or embed the credentials in the application\. Instead, create an IAM role that you attach to the EC2 instance to give temporary security credentials to applications running on the instance\. When an application uses these credentials in AWS, it can perform all of the operations that are allowed by the policies attached to the role\. For details, see [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](id_roles_use_switch-role-ec2.md)\.

**You're creating an app that runs on a mobile phone and that makes requests to AWS\.**  
Don't create an IAM user and distribute the user's access key with the app\. Instead, use an identity provider like Login with Amazon, Amazon Cognito, Facebook, or Google to authenticate users and map the users to an IAM role\. The app can use the role to get temporary security credentials that have the permissions specified by the policies attached to the role\. For more information, see the following:   
+ [Amazon Cognito Overview](https://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html#d0e840) in the *AWS Mobile SDK for Android Developer Guide*
+ [Amazon Cognito Overview](https://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html#d0e664) in the *AWS Mobile SDK for iOS Developer Guide*
+ [About web identity federation](id_roles_providers_oidc.md)

**Users in your company are authenticated in your corporate network and want to be able to use AWS without having to sign in again—that is, you want to allow users to federate into AWS\.**  
Don't create IAM users\. Configure a federation relationship between your enterprise identity system and AWS\. You can do this in two ways:   
+ If your company's identity system is compatible with SAML 2\.0, you can establish trust between your company's identity system and AWS\. For more information, see [About SAML 2\.0\-based federation](id_roles_providers_saml.md)\.
+ Create and use a custom proxy server that translates user identities from the enterprise into IAM roles that provide temporary AWS security credentials\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.