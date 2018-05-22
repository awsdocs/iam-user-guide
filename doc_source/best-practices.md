# IAM Best Practices<a name="best-practices"></a>

To help secure your AWS resources, follow these recommendations for the AWS Identity and Access Management \(IAM\) service\. 

**Topics**
+ [Lock Away Your AWS Account Root User Access Keys](#lock-away-credentials)
+ [Create Individual IAM Users](#create-iam-users)
+ [Use Groups to Assign Permissions to IAM Users](#use-groups-for-permissions)
+ [Use AWS Defined Policies to Assign Permissions Whenever Possible](#bp-use-aws-defined-policies)
+ [Grant Least Privilege](#grant-least-privilege)
+ [Use Access Levels to Review IAM Permissions](#use-access-levels-to-review-permissions)
+ [Configure a Strong Password Policy for Your Users](#configure-strong-password-policy)
+ [Enable MFA for Privileged Users](#enable-mfa-for-privileged-users)
+ [Use Roles for Applications That Run on Amazon EC2 Instances](#use-roles-with-ec2)
+ [Delegate by Using Roles Instead of by Sharing Credentials](#delegate-using-roles)
+ [Rotate Credentials Regularly](#rotate-credentials)
+ [Remove Unnecessary Credentials](#remove-credentials)
+ [Use Policy Conditions for Extra Security](#use-policy-conditions)
+ [Monitor Activity in Your AWS Account](#keep-a-log)
+ [Video Presentation About IAM Best Practices](#top-practices-video)

## Lock Away Your AWS Account Root User Access Keys<a name="lock-away-credentials"></a>

You use an access key \(an access key ID and secret access key\) to make programmatic requests to AWS\. However, do not use your AWS account root user access key\. The access key for your AWS account gives full access to all your resources for all AWS services, including your billing information\. You cannot restrict the permissions associated with your AWS account access key\. 

Therefore, protect your AWS account access key like you would your credit card numbers or any other sensitive secret\. Here are some ways to do that: 
+ If you don't already have an access key for your AWS account, don't create one unless you absolutely need to\. Instead, use your account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) and create an IAM user for yourself that has administrative privileges, as explained in the next section\.
+ If you do have an access key for your AWS account, delete it\. If you must keep it, rotate \(change\) the access key regularly\. To delete or rotate your AWS account access keys, go to the [Security Credentials page](https://console.aws.amazon.com/iam/home?#security_credential) in the AWS Management Console and sign in with your account's email address and password\. You can manage your access keys in the **Access keys** section\.
+ Never share your AWS account password or access keys with anyone\. The remaining sections of this document discuss various ways to avoid having to share your AWS account root user credentials with other users and to avoid having to embed them in an application\. 
+ Use a strong password to help protect account\-level access to the AWS Management Console\. For information about managing your AWS account root user password, see [Changing the AWS Account Root User Password](id_credentials_passwords_change-root.md)\.
+ Enable AWS multi\-factor authentication \(MFA\) on your AWS account\. For more information, see [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\. 

## Create Individual IAM Users<a name="create-iam-users"></a>

Don't use your AWS account root user credentials to access AWS, and don't give your credentials to anyone else\. Instead, create individual users for anyone who needs access to your AWS account\. Create an IAM user for yourself as well, give that user administrative privileges, and use that IAM user for all your work\. For information about how to do this, see [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)\. 

By creating individual IAM users for people accessing your account, you can give each IAM user a unique set of security credentials\. You can also grant different permissions to each IAM user\. If necessary, you can change or revoke an IAM user's permissions any time\. \(If you give out your root user credentials, it can be difficult to revoke them, and it is impossible to restrict their permissions\.\)

**Note**  
Before you set permissions for individual IAM users, though, see the next point about groups\.

## Use Groups to Assign Permissions to IAM Users<a name="use-groups-for-permissions"></a>

Instead of defining permissions for individual IAM users, it's usually more convenient to create groups that relate to job functions \(administrators, developers, accounting, etc\.\)\. Next, define the relevant permissions for each group\. Finally, assign IAM users to those groups\. All the users in an IAM group inherit the permissions assigned to the group\. That way, you can make changes for everyone in a group in just one place\. As people move around in your company, you can simply change what IAM group their IAM user belongs to\. 

For more information, see the following:
+ [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)
+ [Managing IAM Groups](id_groups_manage.md)

## Use AWS Defined Policies to Assign Permissions Whenever Possible<a name="bp-use-aws-defined-policies"></a>

We recommend that you use the managed policies that are created and maintained by AWS to grant permissions whenever possible\. A key advantage of using these policies is that they are maintained and updated by AWS as new services or new API operations are introduced\. 

AWS\-managed policies are designed to support common tasks\. They typically provide access to a single service or a limited set of actions\. For more information about AWS managed policies, see [AWS Managed Policies](access_policies_managed-vs-inline.md#aws-managed-policies)\.

AWS managed policies for job functions can span multiple services and align with common job functions in the IT industry\. For a list and descriptions of job function policies, see [AWS Managed Policies for Job Functions](access_policies_job-functions.md)\.

## Grant Least Privilege<a name="grant-least-privilege"></a>

When you create IAM policies, follow the standard security advice of granting *least privilege*—that is, granting only the permissions required to perform a task\. Determine what users need to do and then craft policies for them that let the users perform *only* those tasks\. 

Start with a minimum set of permissions and grant additional permissions as necessary\. Doing so is more secure than starting with permissions that are too lenient and then trying to tighten them later\.

You can use access level groupings to understand the level of access that a policy grants\. [Policy actions](reference_policies_elements_action.md) are classified as `List`, `Read`, `Write`, `Permissions management`, or `Tagging`\. For example, you can choose actions from the `List` and `Read` access levels to grant read\-only access to your users\. To learn how to use policy summaries to understand access level permissions, see [Use Access Levels to Review IAM Permissions](#use-access-levels-to-review-permissions)\.

One feature that can help with this is the **Access Advisor** tab\. This tab is available on the IAM console details page whenever you inspect a user, group, role, or policy\. The tab includes information about which services are actually used by a user, group, role, or by anyone that uses a policy\. You can use this information to identify unnecessary permissions so that you can refine your IAM policies to better adhere to the principle of least privilege\. For more information, see [Reducing Policy Scope by Viewing User Activity](access_policies_access-advisor.md)\.

For more information, see the following:
+ [Access Management](access.md)
+ Policy topics for individual services, which provide examples of how to write policies for service\-specific resources\. Examples:
  + [Authentication and Access Control for Amazon DynamoDB](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html) in the *Amazon DynamoDB Developer Guide*
  + [Using Bucket Policies and User Policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/using-iam-policies.html) in the *Amazon Simple Storage Service Developer Guide*
  + [Access Control List \(ACL\) Overview](http://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html) in the *Amazon Simple Storage Service Developer Guide*

## Use Access Levels to Review IAM Permissions<a name="use-access-levels-to-review-permissions"></a>

To improve the security of your AWS account, you should regularly review and monitor each of your IAM policies\. Make sure that your policies grant the [least privilege](#grant-least-privilege) that is needed to perform only the necessary actions\.

When you review a policy, you can view the [policy summary](access_policies_understand.md) that includes a summary of the access level for each service within that policy\. AWS categorizes each service action into one of four *access levels* based on what each action does: `List`, `Read`, `Write`, or `Permissions management`\. You can use these access levels to determine which actions to include in your policies\.

For example, in the Amazon S3 service, you might want to allow a large group of users to access `List` and `Read` actions\. Such actions permit those users to list the buckets and get objects in Amazon S3\. However, you should allow only a small group of users to access the Amazon S3 `Write` actions to delete buckets or put objects into an S3 bucket\. Additionally, you should restrict permissions to allow only administrators to access the Amazon S3 `Permissions management` actions\. This ensures that only a limited number of people can manage bucket policies in Amazon S3\. This is especially important for `Permissions management` actions in IAM and AWS Organizations services\.

To view the access level classification that is assigned to each action in a service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\.

To see the access levels for a policy, you must first locate the policy's summary\. The policy summary is included on the **Policies** page for managed policies, and on the **Users** page for policies that are attached to a user\. For more information, see [Policy Summary \(List of Services\)](access_policies_understand-policy-summary.md)\.

Within a policy summary, the **Access level** column shows that the policy provides **Full** or **Limited** access to one or more of the four AWS access levels for the service\. Alternately, it might show that the policy provides **Full access** to all the actions within the service\. You can use the information within this **Access level** column to understand the level of access that the policy provides\. You can then take action to make your AWS account more secure\. For details and examples of the access level summary, see [Understanding Access Level Summaries Within Policy Summaries](access_policies_understand-policy-summary-access-level-summaries.md)\.

## Configure a Strong Password Policy for Your Users<a name="configure-strong-password-policy"></a>

If you allow users to change their own passwords, require that they create strong passwords and that they rotate their passwords periodically\. On the [Account Settings](https://console.aws.amazon.com/iam/home?#account_settings) page of the IAM console, you can create a password policy for your account\. You can use the password policy to define password requirements, such as minimum length, whether it requires non\-alphabetic characters, how frequently it must be rotated, and so on\.

For more information, see [Setting an Account Password Policy for IAM Users](id_credentials_passwords_account-policy.md)\.

## Enable MFA for Privileged Users<a name="enable-mfa-for-privileged-users"></a>

For extra security, enable multi\-factor authentication \(MFA\) for privileged IAM users \(users who are allowed access to sensitive resources or API operations\)\. With MFA, users have a device that generates a unique authentication code \(a one\-time password, or OTP\)\. Users must provide both their normal credentials \(like their user name and password\) and the OTP\. The MFA device can either be a special piece of hardware, or it can be a virtual device \(for example, it can run in an app on a smartphone\)\. 

For more information, see [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\. 

## Use Roles for Applications That Run on Amazon EC2 Instances<a name="use-roles-with-ec2"></a>

Applications that run on an Amazon EC2 instance need credentials in order to access other AWS services\. To provide credentials to the application in a secure way, use IAM *roles*\. A role is an entity that has its own set of permissions, but that isn't a user or group\. Roles also don't have their own permanent set of credentials the way IAM users do\. In the case of Amazon EC2, IAM dynamically provides temporary credentials to the EC2 instance, and these credentials are automatically rotated for you\.

When you launch an EC2 instance, you can specify a role for the instance as a launch parameter\. Applications that run on the EC2 instance can use the role's credentials when they access AWS resources\. The role's permissions determine what the application is allowed to do\.

For more information, see [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)\.

## Delegate by Using Roles Instead of by Sharing Credentials<a name="delegate-using-roles"></a>

You might need to allow users from another AWS account to access resources in your AWS account\. If so, don't share security credentials, such as access keys, between accounts\. Instead, use IAM roles\. You can define a role that specifies what permissions the IAM users in the other account are allowed\. You can also designate which AWS accounts have the IAM users that are allowed to assume the role\. 

For more information, see [Roles Terms and Concepts](id_roles_terms-and-concepts.md)\.

## Rotate Credentials Regularly<a name="rotate-credentials"></a>

Change your own passwords and access keys regularly, and make sure that all IAM users in your account do as well\. That way, if a password or access key is compromised without your knowledge, you limit how long the credentials can be used to access your resources\. You can apply a password policy to your account to require all your IAM users to rotate their passwords, and you can choose how often they must do so\. 

For more information about setting a password policy in your account, see [Setting an Account Password Policy for IAM Users](id_credentials_passwords_account-policy.md)\. 

For more information about rotating access keys for IAM users, see [Rotating Access Keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

## Remove Unnecessary Credentials<a name="remove-credentials"></a>

Remove IAM user credentials \(that is, passwords and access keys\) that are not needed\. For example, an IAM user that is used for an application does not need a password \(passwords are necessary only to sign in to AWS websites\)\. Similarly, if a user does not and will never use access keys, there's no reason for the user to have them\. Passwords and access keys that have not been used recently might be good candidates for removal\. You can find unused passwords or access keys using the console, using the API, or by downloading the credentials report\.

For more information about finding IAM user credentials that have not been used recently, see [Finding Unused Credentials](id_credentials_finding-unused.md)\.

For more information about deleting passwords for an IAM user, see [Managing Passwords for IAM Users](id_credentials_passwords_admin-change-user.md)\.

For more information about deactivating or deleting access keys for an IAM user, see [Managing Access Keys for IAM Users](id_credentials_access-keys.md)\.

For more information about IAM credential reports, see [Getting Credential Reports for Your AWS Account](id_credentials_getting-report.md)\. 

## Use Policy Conditions for Extra Security<a name="use-policy-conditions"></a>

To the extent that it's practical, define the conditions under which your IAM policies allow access to a resource\. For example, you can write conditions to specify a range of allowable IP addresses that a request must come from\. You can also specify that a request is allowed only within a specified date range or time range\. You can also set conditions that require the use of SSL or MFA \(multi\-factor authentication\)\. For example, you can require that a user has authenticated with an MFA device in order to be allowed to terminate an Amazon EC2 instance\.

For more information, see [IAM JSON Policy Elements: Condition](reference_policies_elements_condition.md) in the IAM Policy Elements Reference\.

## Monitor Activity in Your AWS Account<a name="keep-a-log"></a>

You can use logging features in AWS to determine the actions users have taken in your account and the resources that were used\. The log files show the time and date of actions, the source IP for an action, which actions failed due to inadequate permissions, and more\.

Logging features are available in the following AWS services:
+ [Amazon CloudFront](https://aws.amazon.com/cloudfront/) – Logs user requests that CloudFront receives\. For more information, see [Access Logs](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AccessLogs.html) in the *Amazon CloudFront Developer Guide*\.
+ [AWS CloudTrail](https://aws.amazon.com/cloudtrail/) – Logs AWS API calls and related events made by or on behalf of an AWS account\. For more information, see the [http://docs.aws.amazon.com/awscloudtrail/latest/userguide/](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.
+ [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) – Monitors your AWS Cloud resources and the applications you run on AWS\. You can set alarms in CloudWatch based on metrics that you define\. For more information, see the [http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/)\.
+ [AWS Config](https://aws.amazon.com/config/) – Provides detailed historical information about the configuration of your AWS resources, including your IAM users, groups, roles, and policies\. For example, you can use AWS Config to determine the permissions that belonged to a user or group at a specific time\. For more information, see the [http://docs.aws.amazon.com/config/latest/developerguide/](http://docs.aws.amazon.com/config/latest/developerguide/)\.
+ [Amazon Simple Storage Service \(Amazon S3\)](https://aws.amazon.com/s3/) – Logs access requests to your Amazon S3 buckets\. For more information, see [Server Access Logging](http://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) in the *Amazon Simple Storage Service Developer Guide*\.

## Video Presentation About IAM Best Practices<a name="top-practices-video"></a>

[![AWS Videos](http://img.youtube.com/vi/_wiGpBQGCjU/0.jpg)](http://www.youtube.com/watch?v=_wiGpBQGCjU)