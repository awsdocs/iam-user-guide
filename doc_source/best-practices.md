# Security best practices in IAM<a name="best-practices"></a>

To help secure your AWS resources, follow these recommendations for the AWS Identity and Access Management \(IAM\) service\. 

**Topics**
+ [Lock away your AWS account root user access keys](#lock-away-credentials)
+ [Use roles to delegate permissions](#delegate-using-roles)
+ [Grant least privilege](#grant-least-privilege)
+ [Get started using permissions with AWS managed policies](#bp-use-aws-defined-policies)
+ [Validate your policies](#best-practice-policy-validation)
+ [Use customer managed policies instead of inline policies](#best-practice-managed-vs-inline)
+ [Use access levels to review IAM permissions](#use-access-levels-to-review-permissions)
+ [Configure a strong password policy for your users](#configure-strong-password-policy)
+ [Enable MFA](#enable-mfa-for-privileged-users)
+ [Use roles for applications that run on Amazon EC2 instances](#use-roles-with-ec2)
+ [Do not share access keys](#sharing-credentials)
+ [Rotate credentials regularly](#rotate-credentials)
+ [Remove unnecessary credentials](#remove-credentials)
+ [Use policy conditions for extra security](#use-policy-conditions)
+ [Monitor activity in your AWS account](#keep-a-log)

## Lock away your AWS account root user access keys<a name="lock-away-credentials"></a>

You use an access key \(an access key ID and secret access key\) to make programmatic requests to AWS\. However, do not use your AWS account root user access key\. The access key for your AWS account root user gives full access to all your resources for all AWS services, including your billing information\. You cannot reduce the permissions associated with your AWS account root user access key\.

Therefore, protect your root user access key like you would your credit card numbers or any other sensitive secret\. Here are some ways to do that: 
+  We strongly recommend that you do not use the root user for your everyday tasks, even the administrative ones\. Instead, use your root user credentials only to [create your IAM admin user](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html)\. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks\. For everyday tasks, do not use your IAM admin user\. Instead, [use roles to delegate permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#delegate-using-roles)\.
+ If you do have an access key for your AWS account root user, delete it\. If you must keep it, rotate \(change\) the access key regularly\. To delete or rotate your root user access keys, go to the [My Security Credentials page](https://console.aws.amazon.com/iam/home?#security_credential) in the AWS Management Console and sign in with your account's email address and password\. You can manage your access keys in the **Access keys** section\. For more information about rotating access keys, see [Rotating access keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.
+ Never share your AWS account root user password or access keys with anyone\. The remaining sections of this document discuss various ways to avoid having to share your AWS account root user credentials with other users\. They also explain how to avoid having to embed them in an application\. 
+ Use a strong password to help protect account\-level access to the AWS Management Console\. For information about managing your AWS account root user password, see [Changing the AWS account root user password](id_credentials_passwords_change-root.md)\.
+ Enable AWS multi\-factor authentication \(MFA\) on your AWS account root user account\. For more information, see [Using multi\-factor authentication \(MFA\) in AWS](id_credentials_mfa.md)\. 

## Use roles to delegate permissions<a name="delegate-using-roles"></a>

You [assume an IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_request.html) by using AWS Security Token Service operations or [switch to a role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-console.html) in the AWS Management Console to receive a temporary credentials role session\. This is more secure than using your long\-term password or access key credentials\. A session has a limited duration, which reduces your risk if your credentials are compromised\.

As a best practice, use IAM role temporary credentials to access only the resources you need to do your job \([granting least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege)\)\. [Configure AWS Single Sign\-On](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) to allow users from your external identity source to access AWS resources in your accounts\. Within a single account, you can configure an IAM role to allow identities from a [SAML](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-idp_saml.html) or [web identity](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-idp_oidc.html) source to assume the role\.

For IAM users, [create separate roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user.html) for specific job tasks and [assume those roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-console.html) for those tasks\. Don't use your IAM admin user for your everyday work\.

To learn more about role terminology, see [Roles terms and concepts](id_roles_terms-and-concepts.md)\.

## Grant least privilege<a name="grant-least-privilege"></a>

When you create IAM policies, follow the standard security advice of granting *least privilege*, or granting only the permissions required to perform a task\. Determine what users \(and roles\) need to do and then craft policies that allow them to perform *only* those tasks\. 

Start with a minimum set of permissions and grant additional permissions as necessary\. Doing so is more secure than starting with permissions that are too lenient and then trying to tighten them later\.

As an alternative to least privilege, you can use [AWS managed policies](access_policies_managed-vs-inline.md#aws-managed-policies) or policies with wildcard `*` permissions to get started with policies\. Consider the security risk of granting your principals more permissions than they need to do their job\. Monitor those principals to learn which permissions they are using\. Then write least privilege policies\.

IAM provides several options to help you refine the permissions that you grant\.
+ **Understand access level groupings** – You can use access level groupings to understand the level of access that a policy grants\. [Policy actions](reference_policies_elements_action.md) are classified as `List`, `Read`, `Write`, `Permissions management`, or `Tagging`\. For example, you can choose actions from the `List` and `Read` access levels to grant read\-only access to your users\. To learn how to use policy summaries to understand access level permissions, see [Use access levels to review IAM permissions](#use-access-levels-to-review-permissions)\.
+ **Validate your policies** – You can perform policy validation using IAM Access Analyzer when you create and edit JSON policies\. We recommend that you review and validate all of your existing policies\. IAM Access Analyzer provides over 100 policy checks to validate your policies\. It generates security warnings when a statement in your policy allows access we consider overly permissive\. You can use the actionable recommendations that are provided through the security warnings as you work toward granting least privilege\. To learn more about policy checks provided by IAM Access Analyzer, see [IAM Access Analyzer policy validation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-validation.html)\.
+ **Generate a policy based on access activity** – To help you refine the permissions that you grant, you can generate an IAM policy that is based on the access activity for an IAM entity \(user or role\)\. IAM Access Analyzer reviews your AWS CloudTrail logs and generates a policy template that contains the permissions that have been used by the entity in your specified time frame\. You can use the template to create a managed policy with fine\-grained permissions and then attach it to the IAM entity\. That way, you grant only the permissions that the user or role needs to interact with AWS resources for your specific use case\. To learn more, see [Generate policies based on access activity](access_policies_generate-policy.md)\.
+ **Use last accessed information** – Another feature that can help with least privilege is *last accessed information*\. View this information on the **Access Advisor** tab on the IAM console details page for an IAM user, group, role, or policy\. Last accessed information also includes information about the actions that were last accessed for some services, such as Amazon EC2, IAM, Lambda, and Amazon S3\. If you sign in using AWS Organizations management account credentials, you can view service last accessed information in the **AWS Organizations** section of the IAM console\. You can also use the AWS CLI or AWS API to retrieve a report for last accessed information for entities or policies in IAM or Organizations\. You can use this information to identify unnecessary permissions so that you can refine your IAM or Organizations policies to better adhere to the principle of least privilege\. For more information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.
+ **Review account events in AWS CloudTrail** – To further reduce permissions, you can view your account's events in AWS CloudTrail **Event history**\. CloudTrail event logs include detailed event information that you can use to reduce the policy's permissions\. The logs include only the actions and resources that your IAM entities need\. For more information, see [Viewing CloudTrail Events in the CloudTrail Console](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events-console.html) in the *AWS CloudTrail User Guide*\.



For more information, see the following:
+ [Access management for AWS resources](access.md)
+ Policy topics for individual services, which provide examples of how to write policies for service\-specific resources\. Examples:
  + [Authentication and Access Control for Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html) in the *Amazon DynamoDB Developer Guide*
  + [Using Bucket Policies and User Policies](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-iam-policies.html) in the *Amazon Simple Storage Service User Guide*
  + [Access Control List \(ACL\) Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html) in the *Amazon Simple Storage Service User Guide*

## Get started using permissions with AWS managed policies<a name="bp-use-aws-defined-policies"></a>

We recommend using policies that [grant least privilege](#grant-least-privilege), or granting only the permissions required to perform a task\. The most secure way to grant least privilege is to write a custom policy with only the permissions needed by your team\. You must create a process to allow your team to request more permissions when necessary\. It takes time and expertise to [create IAM customer managed policies](access_policies_create-console.md) that provide your team with only the permissions they need\.

To get started adding permissions to your IAM identities \(users, groups of users, and roles\), you can use [AWS managed policies](access_policies_managed-vs-inline.md#aws-managed-policies)\. AWS managed policies cover common use cases and are available in your AWS account\. AWS managed policies don't grant least privilege permissions\. You must consider the security risk of granting your principals more permissions than they need to do their job\.

You can attach AWS managed policies, including job functions, to any IAM identity\. To switch to least privilege permissions, you can run AWS Identity and Access Management Access Analyzer to monitor the principals with AWS managed policies\. After learning which permissions they are using, then you can write a custom policy or generate a policy with only the required permissions for your team\. This is less secure, but provides more flexibility as you learn how your team is using AWS\.

AWS managed policies are designed to provide permissions for many common use cases\. For more information about AWS managed policies that are designed for specific job functions, see [AWS managed policies for job functions](access_policies_job-functions.md)\.

## Validate your policies<a name="best-practice-policy-validation"></a>

It is a best practice to validate the policies that you create\. You can perform policy validation when you create and edit JSON policies\. IAM identifies any JSON syntax errors, while IAM Access Analyzer provides over 100 policy checks and actionable recommendations to help you author secure and functional policies\. We recommend that you review and validate all of your existing policies\. To learn more about policy validation, see [Validating IAM policies](access_policies_policy-validator.md)\. To learn more about policy checks provided by IAM Access Analyzer, see [IAM Access Analyzer policy validation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-validation.html)\.

## Use customer managed policies instead of inline policies<a name="best-practice-managed-vs-inline"></a>

For custom policies, we recommend that you use managed policies instead of inline policies\. A key advantage of using these policies is that you can view all of your managed policies in one place in the console\. You can also view this information with a single AWS CLI or AWS API operation\. Inline policies are policies that exist only on an IAM identity \(user, user group, or role\)\. Managed policies are separate IAM resources that you can attach to multiple identities\. For more information, see [Managed policies and inline policies](access_policies_managed-vs-inline.md)\.

In some circumstances, we do recommend choosing inline policies over managed policies\. For details, see [Choosing between managed policies and inline policies](access_policies_managed-vs-inline.md#choosing-managed-or-inline)\.

You can convert inline policies into managed policies\. For more information, see [Converting an inline policy to a managed policy](access_policies_managed-vs-inline.md#convert-inline-to-managed-policy)\.

## Use access levels to review IAM permissions<a name="use-access-levels-to-review-permissions"></a>

To improve the security of your AWS account, you should regularly review and monitor each of your IAM policies\. Make sure that your policies grant the [least privilege](#grant-least-privilege) that is needed to perform only the necessary actions\.

When you review a policy, you can view the [policy summary](access_policies_understand.md) that includes a summary of the access level for each service within that policy\. AWS categorizes each service action into one of five *access levels* based on what each action does: `List`, `Read`, `Write`, `Permissions management`, or `Tagging`\. You can use these access levels to determine which actions to include in your policies\.

For example, in the Amazon S3 service, you might want to allow a large group of users to access `List` and `Read` actions\. Such actions permit those users to list the buckets and get objects in Amazon S3\. However, you should allow only a small group of users to access the Amazon S3 `Write` actions to delete buckets or put objects into an S3 bucket\. Additionally, you should reduce permissions to allow only administrators to access the Amazon S3 `Permissions management` actions\. This ensures that only a limited number of people can manage bucket policies in Amazon S3\. This is especially important for `Permissions management` actions in IAM and AWS Organizations services\. Allowing `Tagging` actions grants a user permission to perform actions that only modify tags for a resource\. However, some `Write` actions, such as `CreateRole`, allow tagging a resource when you create the resource or modify other attributes for that resource\. Therefore, denying access to `Tagging` actions does not prevent a user from tagging resources\. For details and examples of the access level classification, see [Understanding access level summaries within policy summaries](access_policies_understand-policy-summary-access-level-summaries.md)\.

To view the access level classification that is assigned to each action in a service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

To see the access levels for a policy, you must first locate the policy's summary\. The policy summary is included on the **Policies** page for managed policies, and on the **Users** page for policies that are attached to a user\. For more information, see [Policy summary \(list of services\)](access_policies_understand-policy-summary.md)\.

Within a policy summary, the **Access level** column shows that the policy provides **Full** or **Limited** access to one or more of the four AWS access levels for the service\. Alternately, it might show that the policy provides **Full access** to all the actions within the service\. You can use the information within this **Access level** column to understand the level of access that the policy provides\. You can then take action to make your AWS account more secure\. For details and examples of the access level classification, see [Understanding access level summaries within policy summaries](access_policies_understand-policy-summary-access-level-summaries.md)\.

## Configure a strong password policy for your users<a name="configure-strong-password-policy"></a>

If you allow users to change their own passwords, create a custom password policy that requires them to create strong passwords and rotate their passwords periodically\. On the [Account Settings](https://console.aws.amazon.com/iam/home?#account_settings) page of the IAM console, you can create a custom password policy for your account\. You upgrade from the AWS default password policy to define password requirements, such as minimum length, whether it requires nonalphabetic characters, and how frequently it must be rotated\. For more information, see [Setting an account password policy for IAM users](id_credentials_passwords_account-policy.md)\.

## Enable MFA<a name="enable-mfa-for-privileged-users"></a>

For extra security, we recommend that you require multi\-factor authentication \(MFA\) for all users in your account\. With MFA, users have a device that generates a response to an authentication challenge\. Both the user's credentials and the device\-generated response are required to complete the sign\-in process\. If a user's password or access keys are compromised, your account resources are still secure because of the additional authentication requirement\. 

The response is generated in one of the following ways: 
+ Virtual and hardware MFA devices generate a code that you view on the app or device and then enter on the sign\-in screen\. 
+ U2F security keys generate a response when you tap the device\. The user does not manually enter a code on the sign\-in screen\.

For privileged IAM users who are allowed to access sensitive resources or API operations, we recommend using U2F or hardware MFA devices\.

For more information about MFA, see [Using multi\-factor authentication \(MFA\) in AWS](id_credentials_mfa.md)\. 

To learn how to configure MFA\-protected API access for access keys, see [Configuring MFA\-protected API access](id_credentials_mfa_configure-api-require.md)\.

## Use roles for applications that run on Amazon EC2 instances<a name="use-roles-with-ec2"></a>

Applications that run on an Amazon EC2 instance need credentials in order to access other AWS services\. To provide credentials to the application in a secure way, use IAM *roles*\. A role is an entity that has its own set of permissions, but that isn't a user or user group\. Roles also don't have their own permanent set of credentials the way IAM users do\. In the case of Amazon EC2, IAM dynamically provides temporary credentials to the EC2 instance, and these credentials are automatically rotated for you\.

When you launch an EC2 instance, you can specify a role for the instance as a launch parameter\. Applications that run on the EC2 instance can use the role's credentials when they access AWS resources\. The role's permissions determine what the application is allowed to do\.

For more information, see [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](id_roles_use_switch-role-ec2.md)\.

## Do not share access keys<a name="sharing-credentials"></a>

Access keys provide programmatic access to AWS\. Do not embed access keys within unencrypted code or share these security credentials between users in your AWS account\. For applications that need access to AWS, configure the program to retrieve temporary security credentials using an IAM role\. To allow your users individual programmatic access, create an IAM user with personal access keys\.

For more information, see [Switching to an IAM role \(AWS API\)](id_roles_use_switch-role-api.md) and [Managing access keys for IAM users](id_credentials_access-keys.md)\.

## Rotate credentials regularly<a name="rotate-credentials"></a>

Change your own passwords and access keys regularly, and make sure that all IAM users in your account do as well\. That way, if a password or access key is compromised without your knowledge, you limit how long the credentials can be used to access your resources\. You can apply a custom password policy to your account to require all your IAM users to rotate their AWS Management Console passwords\. You can also choose how often they must do so\. 

For more information about setting a custom password policy in your account, see [Setting an account password policy for IAM users](id_credentials_passwords_account-policy.md)\. 

For more information about rotating access keys for IAM users, see [Rotating access keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

## Remove unnecessary credentials<a name="remove-credentials"></a>

Remove IAM user credentials \(passwords and access keys\) that are not needed\. For example, if you created an IAM user for an application that does not use the console, then the IAM user does not need a password\. Similarly, if a user only uses the console, remove their access keys\. Passwords and access keys that have not been used recently might be good candidates for removal\. You can find unused passwords or access keys using the console, using the CLI or API, or by downloading the credentials report\.

For more information about finding IAM user credentials that have not been used recently, see [Finding unused credentials](id_credentials_finding-unused.md)\.

For more information about deleting passwords for an IAM user, see [Managing passwords for IAM users](id_credentials_passwords_admin-change-user.md)\.

For more information about deactivating or deleting access keys for an IAM user, see [Managing access keys for IAM users](id_credentials_access-keys.md)\.

For more information about IAM credential reports, see [Getting credential reports for your AWS account](id_credentials_getting-report.md)\. 

## Use policy conditions for extra security<a name="use-policy-conditions"></a>

To the extent that it's practical, define the conditions under which your IAM policies allow access to a resource\. For example, you can write conditions to specify a range of allowable IP addresses that a request must come from\. You can also specify that a request is allowed only within a specified date range or time range\. You can also set conditions that require the use of SSL or MFA \(multi\-factor authentication\)\. For example, you can require that a user has authenticated with an MFA device in order to be allowed to terminate an Amazon EC2 instance\.

For more information, see [IAM JSON policy elements: Condition](reference_policies_elements_condition.md) in the IAM Policy Elements Reference\.

## Monitor activity in your AWS account<a name="keep-a-log"></a>

You can use logging features in AWS to determine the actions users have taken in your account and the resources that were used\. The log files show the time and date of actions, the source IP for an action, which actions failed due to inadequate permissions, and more\.

Logging features are available in the following AWS services:
+ [Amazon CloudFront](https://aws.amazon.com/cloudfront/) – Logs user requests that CloudFront receives\. For more information, see [Access Logs](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AccessLogs.html) in the *Amazon CloudFront Developer Guide*\.
+ [AWS CloudTrail](https://aws.amazon.com/cloudtrail/) – Logs AWS API calls and related events made by or on behalf of an AWS account\. For more information, see the [https://docs.aws.amazon.com/awscloudtrail/latest/userguide/](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.
+ [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) – Monitors your AWS Cloud resources and the applications you run on AWS\. You can set alarms in CloudWatch based on metrics that you define\. For more information, see the [https://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/](https://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/)\.
+ [AWS Config](https://aws.amazon.com/config/) – Provides detailed historical information about the configuration of your AWS resources, including your IAM users, user groups, roles, and policies\. For example, you can use AWS Config to determine the permissions that belonged to a user or user group at a specific time\. For more information, see the [https://docs.aws.amazon.com/config/latest/developerguide/](https://docs.aws.amazon.com/config/latest/developerguide/)\.
+ [Amazon Simple Storage Service \(Amazon S3\)](https://aws.amazon.com/s3/) – Logs access requests to your Amazon S3 buckets\. For more information, see [Server Access Logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) in the *Amazon Simple Storage Service User Guide*\.