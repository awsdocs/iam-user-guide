# Security best practices in IAM<a name="best-practices"></a>


|  | 
| --- |
| The AWS Identity and Access Management best practices were updated on July 14, 2022\. | 

To help secure your AWS resources, follow these best practices for AWS Identity and Access Management \(IAM\) \. 

**Topics**
+ [Require human users to use federation with an identity provider to access AWS using temporary credentials](#bp-users-federation-idp)
+ [Require workloads to use temporary credentials with IAM roles to access AWS](#bp-workloads-use-roles)
+ [Require multi\-factor authentication \(MFA\)](#enable-mfa-for-privileged-users)
+ [Rotate access keys regularly for use cases that require long\-term credentials](#rotate-credentials)
+ [Safeguard your root user credentials and don't use them for everyday tasks](#lock-away-credentials)
+ [Apply least\-privilege permissions](#grant-least-privilege)
+ [Get started with AWS managed policies and move toward least\-privilege permissions](#bp-use-aws-defined-policies)
+ [Use IAM Access Analyzer to generate least\-privilege policies based on access activity](#bp-gen-least-privilege-policies)
+ [Regularly review and remove unused users, roles, permissions, policies, and credentials](#remove-credentials)
+ [Use conditions in IAM policies to further restrict access](#use-policy-conditions)
+ [Verify public and cross\-account access to resources with IAM Access Analyzer](#bp-preview-access)
+ [Use IAM Access Analyzer to validate your IAM policies to ensure secure and functional permissions](#best-practice-policy-validation)
+ [Establish permissions guardrails across multiple accounts](#bp-permissions-guardrails)
+ [Use permissions boundaries to delegate permissions management within an account](#bp-permissions-boundaries)

## Require human users to use federation with an identity provider to access AWS using temporary credentials<a name="bp-users-federation-idp"></a>

Human users, also known as *human identities,* are the people, administrators, developers, operators, and consumers of your applications\. They must have an identity to access your AWS environments and applications\. Human users that are members of your organization are also known as *workforce identities\.* Human users can also be external users with whom you collaborate, and who interact with your AWS resources\. They can do this via a web browser, client application, mobile app, or interactive command\-line tools\.

Require your human users to use temporary credentials when accessing AWS\. You can use an identity provider for your human users to provide federated access to AWS accounts by assuming roles, which provide temporary credentials\. For centralized access management, we recommend that you use [AWS Single Sign\-On \(AWS SSO\)](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) to manage access to your accounts and permissions within those accounts\. You can manage your user identities with AWS SSO, or manage access permissions for user identities in AWS SSO from an external identity provider\. For more information, see [What is AWS Single Sign\-On](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html) in the *AWS Single Sign\-On User Guide*\.

For more information about roles, see [Roles terms and concepts](id_roles_terms-and-concepts.md)\.

## Require workloads to use temporary credentials with IAM roles to access AWS<a name="bp-workloads-use-roles"></a>

A *workload* is a collection of resources and code that delivers business value, such as an application or backend process\. Your workload can have applications, operational tools, and components that require an identity to make requests to AWS services, such as requests to read data\. These identities include machines running in your AWS environments, such as Amazon EC2 instances or AWS Lambda functions\.

You can also manage *machine identities* for external parties who need access\. To give access to machine identities, you can use IAM roles\. IAM roles have specific permissions and provide a way to access AWS by relying on temporary security credentials with a role session\. Additionally, you might have machines outside of AWS that need access to your AWS environments\. For machines that run outside of AWS you can use [AWS Identity and Access Management Roles Anywhere](https://docs.aws.amazon.com/rolesanywhere/latest/userguide/introduction.html)\. For more information about roles, see [IAM roles](id_roles.md)\. For details about how to use roles to delegate access across AWS accounts, see [IAM tutorial: Delegate access across AWS accounts using IAM roles](tutorial_cross-account-with-roles.md)\.

## Require multi\-factor authentication \(MFA\)<a name="enable-mfa-for-privileged-users"></a>

We recommend using IAM roles for human users and workloads that access your AWS resources so that they use temporary credentials\. However, for scenarios in which you need IAM or root users in your account, require MFA for additional security\. With MFA, users have a device that generates a response to an authentication challenge\. Each user's credentials and device\-generated response are required to complete the sign\-in process\. For more information, see [Using multi\-factor authentication \(MFA\) in AWS](id_credentials_mfa.md)\.

If you use AWS SSO for centralized access management for human users, you can use the AWS SSO MFA capabilities when your identity source is configured with the AWS SSO identity store, AWS Managed Microsoft AD, or AD Connector\. For more information about MFA in AWS SSO see [ Multi\-factor authentication](https://docs.aws.amazon.com/singlesignon/latest/userguide/enable-mfa.html) in the *AWS Single Sign\-On User Guide*\.

## Rotate access keys regularly for use cases that require long\-term credentials<a name="rotate-credentials"></a>

Where possible, we recommend relying on temporary credentials instead of creating long\-term credentials such as access keys\. However, for scenarios in which you need IAM users with programmatic access and long\-term credentials, we recommend that you rotate access keys\. Regularly rotating long\-term credentials helps you familiarize yourself with the process\. This is useful in case you are ever in a situation where you must rotate credentials, such as when an employee leaves your company\. We recommend that you use *IAM access last used information* to rotate and remove access keys safely\. For more information, see [Rotating access keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

There are specific use cases that require long\-term credentials with IAM users in AWS\. Some of the use cases include the following:
+ **Programmatic use cases that cannot use IAM roles** – You might run code from a location that needs to access AWS\. In some situations, you can't use IAM roles to provide temporary credentials, such as for WordPress plugins\. In these situations, use IAM user long\-term access keys for that code to authenticate to AWS\.
+ **Third\-party AWS clients** – If you are using tools that don’t support access with AWS SSO, such as third\-party AWS clients or vendors that are not hosted on AWS, use IAM user long\-term access keys\.
+ **AWS CodeCommit access** – If you are using CodeCommit to store your code, you can use an IAM user with either SSH keys or service\-specific credentials for CodeCommit to authenticate to your repositories\. We recommend that you do this in addition to using an AWS SSO user for normal authentication\. To give users access to your CodeCommit repositories without configuring IAM users, you can configure the git\-remote\-codecommit utility\. For more information about IAM and CodeCommit, see [Using IAM with CodeCommit: Git credentials, SSH keys, and AWS access keys](id_credentials_ssh-keys.md)\. For more information about configuring the git\-remote\-codecommit utility, see [Connecting to AWS CodeCommit repositories with rotating credentials](https://docs.aws.amazon.com/codecommit/latest/userguide/temporary-access.html#temporary-access-configure-credentials) in the *AWS CodeCommit User Guide*\.
+ **Amazon Keyspaces \(for Apache Cassandra\) access** – In a situation where you are unable to use AWS SSO users, such as for testing purposes for Cassandra compatibility, you can use an IAM user with service\-specific credentials to authenticate with Amazon Keyspaces\. You can also connect to Amazon Keyspaces using temporary credentials\. For more information, see [Using temporary credentials to connect to Amazon Keyspaces using an IAM role and the SigV4 plugin](https://docs.aws.amazon.com/keyspaces/latest/devguide/access.credentials.html#temporary.credentials.IAM) in the *Amazon Keyspaces \(for Apache Cassandra\) Developer Guide*\.

## Safeguard your root user credentials and don't use them for everyday tasks<a name="lock-away-credentials"></a>

When you create an AWS account you establish a root user name and password to sign in to the AWS Management Console\. Safeguard your root user credentials the same way you would protect other sensitive personal information\. You can do this by configuring MFA for your root user credentials\. We don't recommend generating access keys for your root user, because they allow full access to all your resources for all AWS services, including your billing information\. Don’t use your root user for everyday tasks\. Use the root user to complete the tasks that only the root user can perform\. For the complete list of these tasks, see [Tasks that require root user credentials](https://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html#aws_tasks-that-require-root) in the *AWS General Reference*\. For more information, see [Best practices to protect your account's root user](https://docs.aws.amazon.com/accounts/latest/reference/best-practices-root-user.html) in the *AWS Account Management User Guide*\.

## Apply least\-privilege permissions<a name="grant-least-privilege"></a>

When you set permissions with IAM policies, grant only the permissions required to perform a task\. You do this by defining the actions that can be taken on specific resources under specific conditions, also known as *least\-privilege permissions*\. You might start with broad permissions while you explore the permissions that are required for your workload or use case\. As your use case matures, you can work to reduce the permissions that you grant to work toward least privilege\. For more information about using IAM to apply permissions, see [Policies and permissions in IAM](access_policies.md)\.

## Get started with AWS managed policies and move toward least\-privilege permissions<a name="bp-use-aws-defined-policies"></a>

To get started granting permissions to your users and workloads, use the *AWS managed policies* that grant permissions for many common use cases\. They are available in your AWS account\. Keep in mind that AWS managed policies might not grant least\-privilege permissions for your specific use cases because they are available for use by all AWS customers\. As a result, we recommend that you reduce permissions further by defining [customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#customer-managed-policies) that are specific to your use cases\. For more information, see [AWS managed policies](access_policies_managed-vs-inline.md#aws-managed-policies)\. For more information about AWS managed policies that are designed for specific job functions, see [AWS managed policies for job functions](access_policies_job-functions.md)\.

## Use IAM Access Analyzer to generate least\-privilege policies based on access activity<a name="bp-gen-least-privilege-policies"></a>

To grant only the permissions required to perform a task, you can generate policies based on your access activity that is logged in AWS CloudTrail\. [IAM Access Analyzer](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html) analyzes the services and actions that your IAM roles use, and then generates a fine\-grained policy that you can use\. After you test each generated policy, you can deploy the policy to your production environment\. This ensures that you grant only the required permissions to your workloads\. For more information about policy generation, see [IAM Access Analyzer policy generation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-generation.html)\.

## Regularly review and remove unused users, roles, permissions, policies, and credentials<a name="remove-credentials"></a>

You might have IAM users, roles, permissions, policies, or credentials that you no longer need in your AWS account\. IAM provides *last accessed information* to help you identify the users, roles, permissions, policies, and credentials that you no longer need so that you can remove them\. This helps you reduce the number of users, roles, permissions, policies, and credentials that you have to monitor\. You can also use this information to refine your IAM policies to better adhere to least\-privilege permissions\. For more information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\. 

## Use conditions in IAM policies to further restrict access<a name="use-policy-conditions"></a>

You can specify conditions under which a policy statement is in effect\. That way, you can grant access to actions and resources, but only if the access request meets specific conditions\. For example, you can write a policy condition to specify that all requests must be sent using SSL\. You can also use conditions to grant access to service actions, but only if they are used through a specific AWS service, such as AWS CloudFormation\. For more information, see [IAM JSON policy elements: Condition](reference_policies_elements_condition.md)\.

## Verify public and cross\-account access to resources with IAM Access Analyzer<a name="bp-preview-access"></a>

Before you grant permissions for public or cross\-account access in AWS, we recommend that you verify if such access is required\. You can use IAM Access Analyzer to help you preview and analyze public and cross\-account access for supported resource types\. You do this by reviewing the [findings](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-findings.html) that IAM Access Analyzer generates\. These findings help you verify that your resource access controls grant the access that you expect\. Additionally, as you update public and cross\-account permissions, you can verify the effect of your changes before deploying new access controls to your resources\. IAM Access Analyzer also monitors supported resource types continuously and generates a finding for resources that allow public or cross\-account access\. For more information, see [Previewing access with IAM Access Analyzer APIs](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-preview-access-apis.html)\.

## Use IAM Access Analyzer to validate your IAM policies to ensure secure and functional permissions<a name="best-practice-policy-validation"></a>

Validate the policies you create to ensure that they adhere to the [IAM policy language](access_policies.md#access_policies-json) \(JSON\) and IAM best practices\. You can validate your policies by using IAM Access Analyzer policy validation\. IAM Access Analyzer provides more than 100 policy checks and actionable recommendations to help you author secure and functional policies\. As you author new policies or edit existing policies in the console, IAM Access Analyzer provides recommendations to help you refine and validate your policies before you save them\. Additionally, we recommend that you review and validate all of your existing policies\. For more information, see [IAM Access Analyzer policy validation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-validation.html)\. For more information about policy checks provided by IAM Access Analyzer, see [IAM Access Analyzer policy check reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-reference-policy-checks.html)\.

## Establish permissions guardrails across multiple accounts<a name="bp-permissions-guardrails"></a>

As you scale your workloads, separate them by using multiple accounts that are managed with AWS Organizations\. We recommend that you use Organizations [service control policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html) \(SCPs\) to establish permissions guardrails to control access for all IAM users and roles across your accounts\. SCPs are a type of organization policy that you can use to manage permissions in your organization at the AWS organization, OU, or account level\. The permissions guardrails that you establish apply to all users and roles within the covered accounts\. However, SCPs alone are insufficient to grant permissions to the accounts in your organization\. To do this, your administrator must attach [identity\-based or resource\-based policies](access_policies_identity-vs-resource.md) to IAM users, IAM roles, or the resources in your accounts\. For more information, see [AWS Organizations, accounts, and IAM guardrails](https://docs.aws.amazon.com/prescriptive-guidance/latest/security-reference-architecture/organizations.html)\.

## Use permissions boundaries to delegate permissions management within an account<a name="bp-permissions-boundaries"></a>

In some scenarios, you might want to delegate permissions management within an account to others\. For example, you could allow developers to create and manage roles for their workloads\. When you delegate permissions to others, use *permissions boundaries* to set the maximum permissions that you delegate\. A permissions boundary is an advanced feature for using a managed policy to set the maximum permissions that an identity\-based policy can grant to an IAM role\. A permissions boundary does not grant permissions on its own\. For more information, see [Permissions boundaries for IAM entities](access_policies_boundaries.md)\.