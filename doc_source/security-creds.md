# AWS security credentials<a name="security-creds"></a>

When you interact with AWS, you specify your AWS *security credentials* to verify who you are and whether you have permission to access the resources that you are requesting\. AWS uses the security credentials to authenticate and authorize your requests\.

For example, if you want to download a protected file from an Amazon Simple Storage Service \(Amazon S3\) bucket, your credentials must allow that access\. If your credentials don't show you are authorized to download the file, AWS denies your request\. However, your AWS security credentials aren't required for you to download a file in an Amazon S3 bucket that is publicly shared\.

There are different types of users in AWS\. All AWS users have security credentials\. There is the account owner \(root user\), users in AWS IAM Identity Center \(successor to AWS Single Sign\-On\), federated users, and IAM users\.

Users have either long\-term or temporary security credentials\. Root user, IAM user, and access keys have long\-term security credentials that do not expire\. To protect long\-term credentials you can [manage and rotate access keys](id_credentials_access-keys.md), [change passwords](id_credentials_passwords.md), and [enable MFA](id_credentials_mfa.md)\. 

IAM roles, users in AWS IAM Identity Center \(successor to AWS Single Sign\-On\), and federated users have temporary security credentials\. Temporary security credentials expire after a defined period of time or when the user ends their session\. Temporary credentials work almost identically to long\-term credentials, with the following differences:
+ Temporary security credentials are *short\-term*, as the name implies\. They can be configured to last for anywhere from a few minutes to several hours\. After the credentials expire, AWS no longer recognizes them or allows any kind of access from API requests made with them\.
+ Temporary security credentials are not stored with the user but are generated dynamically and provided to the user when requested\. When \(or even before\) the temporary security credentials expire, the user can request new credentials, as long as the user requesting them still has permissions to do so\.

As a result, temporary credentials have the following advantages over long\-term credentials:
+ You do not have to distribute or embed long\-term AWS security credentials with an application\.
+ You can provide access to your AWS resources to users without having to define an AWS identity for them\. Temporary credentials are the basis for [roles and identity federation](id_roles.md)\.
+ The temporary security credentials have a limited lifetime, so you do not have to rotate them or explicitly revoke them when they're no longer needed\. After temporary security credentials expire, they cannot be reused\. You can specify how long the credentials are valid, up to a maximum limit\. 

## Security considerations<a name="security-considerations-ref"></a>

We recommend that you consider the following information when determining the security provisions for your AWS account:
+  When you create an AWS account, we create the account root user\. The credentials of the root user \(account owner\) allow full access to all resources in the account\. The first task you perform with the root user is to grant another user administrative permissions to your AWS account so that you minimize the usage of the root user\. 
+ You can't use IAM policies to deny the root user access to resources explicitly\. You can only use an AWS Organizations [service control policy \(SCP\)](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_type-auth.html) to limit the permissions of the root user\. 
+ If you forget or lose your root user password, you must have access to the email address associated with your account in order to reset it\.
+ If you lose your root user access keys, you must be able to sign in to your account as the root user to create new ones\.
+ Do not use the root user for your everyday tasks\. Use it to perform the tasks that only the root user can perform\. For the complete list of tasks that require you to sign in as the root user, see [Tasks that require root user credentials](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html) in the *AWS Account Management Reference Guide*\.
+ Security credentials are account\-specific\. If you have access to multiple AWS accounts, you have separate credentials for each account\.
+ [Policies](access_policies.md) determine what actions a user, role, or member of a user group can perform, on which AWS resources, and under what conditions\. Using policies you can securely control access to AWS services and resources in your AWS account\. If you must modify or revoke permissions in response to a security event, you delete or modify the policies instead of making changes directly to the identity\.
+ Be sure to save the sign\-in credentials for your *Emergency Access* IAM user and any access keys you created for programmatic access in a secure location\. If you lose your access keys, you must sign in to your account to create new ones\.
+ We strongly recommend that you use temporary credentials provides by IAM roles and federated users instead of the long\-term credentials provided by IAM users and access keys\.

## Federated identity<a name="sec-federated-identity-overview"></a>

Federated identities are users with external identities that are granted temporary AWS credentials that they can use to access secure AWS account resources\. External identities can come from a corporate identity store \(such as LDAP or Windows Active Directory\) or from a third party \(such as Login in with Amazon, Facebook, or Google\)\. Federated identities do not sign in with the AWS Management Console or AWS access portal\.

To enable federated identities to sign in to AWS, you must create a custom URL that includes `https://signin.aws.amazon.com/federation`\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.

For more information about federated identities, see [Identity providers and federation](id_roles_providers.md)\.

## Multi\-factor authentication \(MFA\)<a name="sec-multi-factor-authentication"></a>

Multi\-factor authentication \(MFA\) provides an extra level of security for users who can access your AWS account\. For additional security, we recommend that you require MFA on the AWS account root user credentials and all IAM users\. For more information, see [Using Multi\-Factor Authentication \(MFA\) in AWS](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html) in the *IAM User Guide*\.

When you activate MFA and you sign in to your AWS account, you are prompted for your sign\-in credentials, plus a response generated by an MFA device, such as a code, a touch or tap, or a biometric scan\. When you add MFA, your AWS account settings and resources are more secure\.

By default, MFA isn't activated\. You can activate and manage MFA devices for the AWS account root user by going to the [Security credentials](https://console.aws.amazon.com/iam/home?#security_credential) page or the [IAM](https://console.aws.amazon.com/iam/home?#) dashboard in the AWS Management Console\. For more information about activating MFA for IAM users, see [Enabling MFA devices for users in AWS](id_credentials_mfa_enable.md)\.

For more information about signing in with multi\-factor authentication \(MFA\) devices, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\.

## Programmatic access<a name="sec-access-keys-and-secret-access-keys"></a>

You provide your AWS access keys to make programmatic calls to AWS or to use the AWS Command Line Interface or AWS Tools for PowerShell\. We recommend using short\-term access keys when possible\.

When you create a long\-term access key, you create the access key ID \(for example, `AKIAIOSFODNN7EXAMPLE`\) and secret access key \(for example, `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY`\) as a set\. The secret access key is available for download only when you create it\. If you don't download your secret access key or if you lose it, you must create a new one\.

In many scenarios, you don't need long\-term access keys that never expire \(as you have when you create access keys for an IAM user\)\. Instead, you can create IAM roles and generate temporary security credentials\. Temporary security credentials include an access key ID and a secret access key, but they also include a security token that indicates when the credentials expire\. After they expire, they're no longer valid\.

Access key IDs beginning with `AKIA` are long\-term access keys for an IAM user or an AWS account root user\. Access key IDs beginning with `ASIA` are temporary credentials access keys that you create using AWS STS operations\.

Users need programmatic access if they want to interact with AWS outside of the AWS Management Console\. The way to grant programmatic access depends on the type of user that's accessing AWS:
+ If you manage identities in IAM Identity Center, the AWS APIs require a profile, and the AWS Command Line Interface requires a profile or an environment variable\.
+ If you have IAM users, the AWS APIs and the AWS Command Line Interface require access keys\. Whenever possible, create temporary credentials that consist of an access key ID, a secret access key, and a security token that indicates when the credentials expire\.

To grant users programmatic access, choose one of the following options\.


****  

| Which user needs programmatic access? | To | By | 
| --- | --- | --- | 
|  Workforce identity \(Users managed in IAM Identity Center\)  | Use short\-term credentials to sign programmatic requests to the AWS CLI or AWS APIs \(directly or by using the AWS SDKs\)\. |  Following the instructions for the interface that you want to use: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/security-creds.html)  | 
| IAM | Use short\-term credentials to sign programmatic requests to the AWS CLI or AWS APIs \(directly or by using the AWS SDKs\)\. | Following the instructions in [Using temporary credentials with AWS resources](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html) in the IAM User Guide\. | 
| IAM | Use long\-term credentials to sign programmatic requests to the AWS CLI or AWS APIs \(directly or by using the AWS SDKs\)\.\(Not recommended\) | Following the instructions in [Managing access keys for IAM users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) in the IAM User Guide\. | 

## Alternatives for long\-term access keys<a name="sec-alternatives-to-long-term-access-keys"></a>

For many common use cases, there are alternatives to long\-term access keys\. To improve your account security, consider the following\.
+ **Don't embed long\-term access keys and secret access keys in your application code or in a code repository –** Instead, use AWS Secrets Manager, or other secrets management solution, so you don't have to hardcode keys in plaintext\. The application or client can then retrieve secrets when needed\. For more information, see [What is AWS Secrets Manager?](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html) in the *AWS Secrets Manager User Guide*\.
+ ** Use IAM roles to generate temporary security credentials whenever possible –** Always use mechanisms to issue temporary security credentials when possible, rather than long\-term access keys\. Temporary security credentials are more secure because they are not stored with the user but are generated dynamically and provided to the user when requested\. Temporary security credentials have a limited lifetime so you don't have to manage or rotate them\. Mechanisms that provide temporary access keys include IAM roles or the authentication of an IAM Identity Center user\. For machines that run outside of AWS you can use [AWS Identity and Access Management Roles Anywhere](https://docs.aws.amazon.com/rolesanywhere/latest/userguide/introduction.html)\. 
+ ** Use alternatives to long\-term access keys for the AWS Command Line Interface \(AWS CLI\) or the `aws-shell` –** Alternatives include the following\.
  + **AWS CloudShell** is a browser\-based, pre\-authenticated shell that you can launch directly from the AWS Management Console\. You can run AWS CLI commands against AWS services through your preferred shell \(Bash, Powershell, or Z shell\)\. When you do this, you don't need to download or install command line tools\. For more information, see [What is AWS CloudShell?](https://docs.aws.amazon.com/cloudshell/latest/userguide/welcome.html) in the *AWS CloudShell User Guide*\.
  + **AWS CLI Version 2 integration with AWS IAM Identity Center \(successor to AWS Single Sign\-On\) \(IAM Identity Center\)**\. You can authenticate users and provide short\-term credentials to run AWS CLI commands\. To learn more, see [Integrating AWS CLI with IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/integrating-asw-cli.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide* and [Configuring the AWS CLI to use IAM Identity Center](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html) in the *AWS Command Line Interface User Guide*\. 
+ **Don't create long\-term access keys for human users who need access to applications or AWS services –** IAM Identity Center can generate temporary access credentials for your external IdP users to access AWS services\. This eliminates the need to create and manage long\-term credentials in IAM\. In IAM Identity Center, create an IAM Identity Center permission set that grants the external IdP users access\. Then assign a group from IAM Identity Center to the permission set in the selected AWS accounts\. For more information, see [What is AWS IAM Identity Center \(successor to AWS Single Sign\-On\)](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html), [Connect to your external identity provider](https://docs.aws.amazon.com/singlesignon/latest/userguide/manage-your-identity-source-idp.html), and [Permission sets](https://docs.aws.amazon.com/singlesignon/latest/userguide/permissionsetsconcept.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\. 
+ **Don't store long\-term access keys within an AWS compute service –** Instead, assign an IAM role to compute resources\. This automatically supplies temporary credentials to grant access\. For example, when you create an instance profile that is attached to an Amazon EC2 instance, you can assign an AWS role to the instance and make it available to all of its applications\. An instance profile contains the role and enables programs that are running on the Amazon EC2 instance to get temporary credentials\. To learn more, see [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html)\.

## Accessing AWS using your AWS credentials<a name="aws-sec-cred-access-ref"></a>

AWS requires different types of security credentials, depending on how you access AWS and what type of AWS user you are\. For example, you use sign\-in credentials for the AWS Management Console while you use access keys to make programmatic calls to AWS\. Also, each identity you use, whether it be the account root user, an AWS Identity and Access Management \(IAM\) user, an AWS IAM Identity Center \(successor to AWS Single Sign\-On\) user, or a federated identity, has unique credentials within AWS\.

For step\-by\-step instructions on how to sign in to AWS according to your user type, see [How to sign in to AWS](https://docs.aws.amazon.com/signin/latest/userguide/how-to-sign-in.html) in the *AWS Sign\-In User Guide*\.