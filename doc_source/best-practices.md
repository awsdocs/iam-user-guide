# IAM Best Practices<a name="best-practices"></a>

To help secure your AWS resources, follow these recommendations for the AWS Identity and Access Management \(IAM\) service\. 

**Topics**
+ [Lock Away Your AWS Account Root User Access Keys](#lock-away-credentials)
+ [Create Individual IAM Users](#create-iam-users)
+ [Use Groups to Assign Permissions to IAM Users](#use-groups-for-permissions)
+ [Use Federation to Enable Single Sign-on (SSO)](#use-federation)
+ [Grant Least Privilege](#grant-least-privilege)
+ [Get Started Using Permissions With AWS Managed Policies](#bp-use-aws-defined-policies)
+ [Use Customer Managed Policies Instead of Inline Policies](#best-practice-managed-vs-inline)
+ [Use Access Levels to Review IAM Permissions](#use-access-levels-to-review-permissions)
+ [Configure a Strong Password Policy for Your Users](#configure-strong-password-policy)
+ [Enable MFA for Privileged Users](#enable-mfa-for-privileged-users)
+ [Use Roles for Applications That Run on Amazon EC2 Instances](#use-roles-with-ec2)
+ [Use Roles to Delegate Permissions](#delegate-using-roles)
+ [Do Not Share Access Keys](#sharing-credentials)
+ [Rotate Credentials Regularly](#rotate-credentials)
+ [Remove Unnecessary Credentials](#remove-credentials)
+ [Use Policy Conditions for Extra Security](#use-policy-conditions)
+ [Monitor Activity in Your AWS Account](#keep-a-log)
+ [Video Presentation About IAM Best Practices](#top-practices-video)

## Lock Away Your AWS Account Root User Access Keys<a name="lock-away-credentials"></a>

You use an access key \(an access key ID and secret access key\) to make programmatic requests to AWS\. However, do not use your AWS account root user access key\. The access key for your AWS account root user gives full access to all your resources for all AWS services, including your billing information\. You cannot reduce the permissions associated with your AWS account root user access key\. 

Therefore, protect your root user access key like you would your credit card numbers or any other sensitive secret\. Here are some ways to do that: 
+ If you don't already have an access key for your AWS account root user, don't create one unless you absolutely need to\. Instead, use your account email address and password to sign in to the AWS Management Console and [create an IAM user for yourself](getting-started_create-admin-group.md) that has administrative permissions\.
+ If you do have an access key for your AWS account root user, delete it\. If you must keep it, rotate \(change\) the access key regularly\. To delete or rotate your root user access keys, go to the [My Security Credentials page](https://console.aws.amazon.com/iam/home?#security_credential) in the AWS Management Console and sign in with your account's email address and password\. You can manage your access keys in the **Access keys** section\. For more information about rotating access keys, see [Rotating Access Keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.
+ Never share your AWS account root user password or access keys with anyone\. The remaining sections of this document discuss various ways to avoid having to share your AWS account root user credentials with other users and to avoid having to embed them in an application\. 
+ Use a strong password to help protect account\-level access to the AWS Management Console\. For information about managing your AWS account root user password, see [Changing the AWS Account Root User Password](id_credentials_passwords_change-root.md)\.
+ Enable AWS multi\-factor authentication \(MFA\) on your AWS account root user account\. For more information, see [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\. 

## Create Individual IAM Users<a name="create-iam-users"></a>

Don't use your AWS account root user credentials to access AWS, and don't give your credentials to anyone else\. Instead, create individual users for anyone who needs access to your AWS account\. Create an IAM user for yourself as well, give that user administrative permissions, and use that IAM user for all your work\. For information about how to do this, see [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)\. 

By creating individual IAM users for people accessing your account, you can give each IAM user a unique set of security credentials\. You can also grant different permissions to each IAM user\. If necessary, you can change or revoke an IAM user's permissions any time\. \(If you give out your root user credentials, it can be difficult to revoke them, and it is impossible to restrict their permissions\.\)

**Note**  
Before you set permissions for individual IAM users, though, see the next point about groups\.

**Tip**  
However, if you currently have an identity directory of your corporate users, it would be wise to federate that existing identity directory to AWS IAM\. See the [Use Federation to Enable Single Sign-on (SSO)](#use-federation) section for more information\.

## Use Groups to Assign Permissions to IAM Users<a name="use-groups-for-permissions"></a>

Instead of defining permissions for individual IAM users, it's usually more convenient to create groups that relate to job functions \(administrators, developers, accounting, etc\.\)\. Next, define the relevant permissions for each group\. Finally, assign IAM users to those groups\. All the users in an IAM group inherit the permissions assigned to the group\. That way, you can make changes for everyone in a group in just one place\. As people move around in your company, you can simply change what IAM group their IAM user belongs to\. 

For more information, see the following:
+ [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)
+ [Managing IAM Groups](id_groups_manage.md)

## Use Federation to Enable Single Sign-on (SSO)<a name="use-federation"></a>

If you already have an identity directory of your corporate users, you can enable single sign-on (SSO) to your AWS accounts by using federation and AWS Identity and Access Management (IAM)\. By federating your AWS accounts, users can sign in to the AWS Management Console and AWS Command Line Interface (CLI) using credentials from your corporate directory\. To help you manage federation for multiple AWS accounts centrally, you can use [AWS Single Sign-On](https://aws.amazon.com/single-sign-on/) to manage SSO access for all of your accounts in [AWS Organizations](https://aws.amazon.com/organizations/)\. Federation also enables you to manage access to your AWS accounts by adding and removing users from your corporate directory, such as [Microsoft Active Directory](https://aws.amazon.com/directoryservice/active-directory/)\.

To learn more, see [Enabling SAML 2.0 Federated Users to Access the AWS Management Console](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_enable-console-saml.html)\.

## Grant Least Privilege<a name="grant-least-privilege"></a>

When you create IAM policies, follow the standard security advice of granting *least privilege*, or granting only the permissions required to perform a task\. Determine what users need to do and then craft policies for them that let the users perform *only* those tasks\. 

Start with a minimum set of permissions and grant additional permissions as necessary\. Doing so is more secure than starting with permissions that are too lenient and then trying to tighten them later\.

You can use access level groupings to understand the level of access that a policy grants\. [Policy actions](reference_policies_elements_action.md) are classified as `List`, `Read`, `Write`, `Permissions management`, or `Tagging`\. For example, you can choose actions from the `List` and `Read` access levels to grant read\-only access to your users\. To learn how to use policy summaries to understand access level permissions, see [Use Access Levels to Review IAM Permissions](#use-access-levels-to-review-permissions)\.

One feature that can help with this is *service last accessed data*\. View this data on the **Access Advisor** tab on the IAM console details page for a user, group, role, or policy\. You can also use the AWS CLI or AWS API to retrieve service last accessed data\. This data includes information about which services a user, group, role, or anyone using a policy attempted to access and when\. You can use this information to identify unnecessary permissions so that you can refine your IAM policies to better adhere to the principle of least privilege\. For more information, see [Reducing Permissions Using Service Last Accessed Data](access_policies_access-advisor.md)\.

To further reduce permissions, you can view your account's events in CloudTrail **Event history**\. CloudTrail event logs include detailed event information that you can use to reduce the policy's permissions and include only the actions and resources that your IAM entities need\. For more information, see [Viewing CloudTrail Events in the CloudTrail Console](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events-console.html) in the *AWS CloudTrail User Guide*\.

For more information, see the following:
+ [Access Management](access.md)
+ Policy topics for individual services, which provide examples of how to write policies for service\-specific resources\. Examples:
  + [Authentication and Access Control for Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html) in the *Amazon DynamoDB Developer Guide*
  + [Using Bucket Policies and User Policies](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-iam-policies.html) in the *Amazon Simple Storage Service Developer Guide*
  + [Access Control List \(ACL\) Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html) in the *Amazon Simple Storage Service Developer Guide*

## Get Started Using Permissions With AWS Managed Policies<a name="bp-use-aws-defined-policies"></a>

Providing your employees with only the permissions they need requires time and detailed knowledge of IAM policies\. Employees need time to learn which AWS services they want or need to use\. Administrators need time to learn about and test IAM\. 

To get started quickly, you can use AWS managed policies to give your employees the permissions they need to get started\. These policies are already available in your account and are maintained and updated by AWS\. For more information about AWS managed policies, see [AWS Managed Policies](access_policies_managed-vs-inline.md#aws-managed-policies)\.

AWS managed policies are designed to provide permissions for many common use cases\. Full access AWS managed policies such as [AmazonDynamoDBFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AmazonDynamoDBFullAccess) and [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) define permissions for service administrators by granting full access to a service\. Power\-user AWS managed policies such as [AWSCodeCommitPowerUser](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AWSCodeCommitPowerUser) and [AWSKeyManagementServicePowerUser](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AWSKeyManagementServicePowerUser) provide multiple levels of access to AWS services without allowing permissions management permissions\. Partial\-access AWS managed policies such as [AmazonMobileAnalyticsWriteOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AmazonMobileAnalyticsWriteOnlyAccess) and [AmazonEC2ReadOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AmazonEC2ReadOnlyAccess) provide specific levels of access to AWS services\. AWS managed policies make it easier for you to assign appropriate permissions to users, groups, and roles than if you had to write the policies yourself\. 

AWS managed policies for job functions can span multiple services and align with common job functions in the IT industry\. For a list and descriptions of job function policies, see [AWS Managed Policies for Job Functions](access_policies_job-functions.md)\.

## Use Customer Managed Policies Instead of Inline Policies<a name="best-practice-managed-vs-inline"></a>

For custom policies, we recommend that you use managed policies instead of inline policies\. A key advantage of using these policies is that you can view all of your managed policies in one place in the console\. You can also view this information with a single AWS CLI or AWS API operation\. Inline policies are policies that exist only on an IAM identity \(user, group, or role\)\. Managed policies are separate IAM resources that you can attach to multiple identities\. For more information, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\.

If you have inline policies in your account, you can convert them to managed policies\. To do this, copy the policy to a new managed policy, attach the new policy to the identity that has the inline policy, and then delete the inline policy\. You can do this using the instructions below\.

**To convert an inline policy to a managed policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups**, **Users**, or **Roles**\.

1. In the list, choose the name of the group, user, or role that has the policy you want to remove\.

1. Choose the **Permissions** tab\. If you chose **Groups**, expand the **Inline Policies** section if necessary\.

1. For groups, choose **Show Policy** next to the inline policy that you want to remove\. For users and roles, choose **Show *n* more**, if necessary, and then choose the arrow next to the inline policy that you want to remove\.

1. Copy the JSON policy document for the policy\.

1. In the navigation pane, choose **Policies**\.

1. Choose **Create policy** and then choose the **JSON** tab\.

1. Replace the existing text with your JSON policy text, and then choose **Review policy**\.

1. Enter a name for your policy and choose **Create policy**\.

1. In the navigation pane, choose **Groups**, **Users**, or **Roles**, and again choose the name of the group, user, or role that has the policy you want to remove\.

1. For groups, choose **Attach Policy**\. For users and roles, choose **Add permissions**\.

1. For groups, select the check box next to the name of your new policy, and then choose **Attach Policy**\. For users or roles, choose **Add permissions**\. On the next page, choose **Attach existing policies directly**, select the check box next to the name of your new policy, choose **Next: Review**, and then choose **Add permissions**\.

   You are returned to the **Summary** page for your group, user, or role\.

1. For groups, choose **Remove Policy** next to the inline policy that you want to remove\. For users or roles, choose **X** next to the inline policy that you want to remove\.

In some circumstances, we do recommend choosing inline policies over managed policies\. For details, see [Choosing Between Managed Policies and Inline Policies](access_policies_managed-vs-inline.md#choosing-managed-or-inline)\.

## Use Access Levels to Review IAM Permissions<a name="use-access-levels-to-review-permissions"></a>

To improve the security of your AWS account, you should regularly review and monitor each of your IAM policies\. Make sure that your policies grant the [least privilege](#grant-least-privilege) that is needed to perform only the necessary actions\.

When you review a policy, you can view the [policy summary](access_policies_understand.md) that includes a summary of the access level for each service within that policy\. AWS categorizes each service action into one of four *access levels* based on what each action does: `List`, `Read`, `Write`, or `Permissions management`\. You can use these access levels to determine which actions to include in your policies\.

For example, in the Amazon S3 service, you might want to allow a large group of users to access `List` and `Read` actions\. Such actions permit those users to list the buckets and get objects in Amazon S3\. However, you should allow only a small group of users to access the Amazon S3 `Write` actions to delete buckets or put objects into an S3 bucket\. Additionally, you should reduce permissions to allow only administrators to access the Amazon S3 `Permissions management` actions\. This ensures that only a limited number of people can manage bucket policies in Amazon S3\. This is especially important for `Permissions management` actions in IAM and AWS Organizations services\.

To view the access level classification that is assigned to each action in a service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\.

To see the access levels for a policy, you must first locate the policy's summary\. The policy summary is included on the **Policies** page for managed policies, and on the **Users** page for policies that are attached to a user\. For more information, see [Policy Summary \(List of Services\)](access_policies_understand-policy-summary.md)\.

Within a policy summary, the **Access level** column shows that the policy provides **Full** or **Limited** access to one or more of the four AWS access levels for the service\. Alternately, it might show that the policy provides **Full access** to all the actions within the service\. You can use the information within this **Access level** column to understand the level of access that the policy provides\. You can then take action to make your AWS account more secure\. For details and examples of the access level summary, see [Understanding Access Level Summaries Within Policy Summaries](access_policies_understand-policy-summary-access-level-summaries.md)\.

## Configure a Strong Password Policy for Your Users<a name="configure-strong-password-policy"></a>

If you allow users to change their own passwords, require that they create strong passwords and that they rotate their passwords periodically\. On the [Account Settings](https://console.aws.amazon.com/iam/home?#account_settings) page of the IAM console, you can create a password policy for your account\. You can use the password policy to define password requirements, such as minimum length, whether it requires non\-alphabetic characters, how frequently it must be rotated, and so on\.

For more information, see [Setting an Account Password Policy for IAM Users](id_credentials_passwords_account-policy.md)\.

## Enable MFA for Privileged Users<a name="enable-mfa-for-privileged-users"></a>

For extra security, enable multi\-factor authentication \(MFA\) for privileged IAM users \(users who are allowed access to sensitive resources or API operations\)\. With MFA, users have a device that generates a response to an authentication challenge\. Both the user's credentials and the device\-generated response are required to complete the sign\-in process\. The response is generated in one of the following ways: 
+ Virtual and hardware MFA devices generate a code that you view on the app or device and then enter on the sign\-in screen\. 
+ U2F security keys generate a response when you tap the device\. The user does not manually enter a code on the sign\-in screen\.

For more information, see [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\. 

## Use Roles for Applications That Run on Amazon EC2 Instances<a name="use-roles-with-ec2"></a>

Applications that run on an Amazon EC2 instance need credentials in order to access other AWS services\. To provide credentials to the application in a secure way, use IAM *roles*\. A role is an entity that has its own set of permissions, but that isn't a user or group\. Roles also don't have their own permanent set of credentials the way IAM users do\. In the case of Amazon EC2, IAM dynamically provides temporary credentials to the EC2 instance, and these credentials are automatically rotated for you\.

When you launch an EC2 instance, you can specify a role for the instance as a launch parameter\. Applications that run on the EC2 instance can use the role's credentials when they access AWS resources\. The role's permissions determine what the application is allowed to do\.

For more information, see [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)\.

## Use Roles to Delegate Permissions<a name="delegate-using-roles"></a>

Don't share security credentials between accounts to allow users from another AWS account to access resources in your AWS account\. Instead, use IAM roles\. You can define a role that specifies what permissions the IAM users in the other account are allowed\. You can also designate which AWS accounts have the IAM users that are allowed to assume the role\. 

For more information, see [Roles Terms and Concepts](id_roles_terms-and-concepts.md)\.

## Do Not Share Access Keys<a name="sharing-credentials"></a>

Access keys provide programmatic access to AWS\. Do not embed access keys within unencrypted code or share these security credentials between users in your AWS account\. For applications that need access to AWS, configure the program to retrieve temporary security credentials using an IAM role\. To allow your users individual programmatic access, create an IAM user with personal access keys\.

For more information, see [Switching to an IAM Role \(AWS API\)](id_roles_use_switch-role-api.md) and [Managing Access Keys for IAM Users](id_credentials_access-keys.md)\.

## Rotate Credentials Regularly<a name="rotate-credentials"></a>

Change your own passwords and access keys regularly, and make sure that all IAM users in your account do as well\. That way, if a password or access key is compromised without your knowledge, you limit how long the credentials can be used to access your resources\. You can apply a password policy to your account to require all your IAM users to rotate their passwords, and you can choose how often they must do so\. 

For more information about setting a password policy in your account, see [Setting an Account Password Policy for IAM Users](id_credentials_passwords_account-policy.md)\. 

For more information about rotating access keys for IAM users, see [Rotating Access Keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

## Remove Unnecessary Credentials<a name="remove-credentials"></a>

Remove IAM user credentials \(passwords and access keys\) that are not needed\. For example, if you created an IAM user for an application that does not use the console, then the IAM user does not need a password\. Similarly, if a user only uses the console, remove their access keys\. Passwords and access keys that have not been used recently might be good candidates for removal\. You can find unused passwords or access keys using the console, using the CLI or API, or by downloading the credentials report\.

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
+ [Amazon CloudFront](https://aws.amazon.com/cloudfront/) – Logs user requests that CloudFront receives\. For more information, see [Access Logs](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AccessLogs.html) in the *Amazon CloudFront Developer Guide*\.
+ [AWS CloudTrail](https://aws.amazon.com/cloudtrail/) – Logs AWS API calls and related events made by or on behalf of an AWS account\. For more information, see the [https://docs.aws.amazon.com/awscloudtrail/latest/userguide/](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.
+ [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) – Monitors your AWS Cloud resources and the applications you run on AWS\. You can set alarms in CloudWatch based on metrics that you define\. For more information, see the [https://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/](https://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/)\.
+ [AWS Config](https://aws.amazon.com/config/) – Provides detailed historical information about the configuration of your AWS resources, including your IAM users, groups, roles, and policies\. For example, you can use AWS Config to determine the permissions that belonged to a user or group at a specific time\. For more information, see the [https://docs.aws.amazon.com/config/latest/developerguide/](https://docs.aws.amazon.com/config/latest/developerguide/)\.
+ [Amazon Simple Storage Service \(Amazon S3\)](https://aws.amazon.com/s3/) – Logs access requests to your Amazon S3 buckets\. For more information, see [Server Access Logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) in the *Amazon Simple Storage Service Developer Guide*\.

## Video Presentation About IAM Best Practices<a name="top-practices-video"></a>

[![AWS Videos](http://img.youtube.com/vi/_wiGpBQGCjU/0.jpg)](http://www.youtube.com/watch?v=_wiGpBQGCjU)
