# Providing Access to an IAM User in Another AWS Account That You Own<a name="id_roles_common-scenarios_aws-accounts"></a>

You can grant your IAM users permission to switch to roles within your AWS account or to roles defined in other AWS accounts that you own\. 

**Note**  
If you want to grant access to an account that you do not own or control, see [Providing Access to AWS Accounts Owned by Third Parties](id_roles_common-scenarios_third-party.md) later in this topic\. 

Imagine that you have Amazon Elastic Compute Cloud \(Amazon EC2\) instances that are critical to your organization\. Instead of directly granting your users permission to terminate the instances, you can create a role with those privileges and allow administrators to switch to the role when they need to terminate an instance\. This adds the following layers of protection to the instances:
+ You must explicitly grant your users permission to assume the role\.
+ Your users must actively switch to the role using the AWS Management Console\.
+ You can add multi\-factor authentication \(MFA\) protection to the role so that only users who sign in with an MFA device can assume the role\.

We recommend using this approach to enforce the *principle of least access*, that is, restricting the use of elevated permissions to only those times when they are needed for specific tasks\. With roles you can help prevent accidental changes to sensitive environments, especially if you combine them with [auditing](cloudtrail-integration.md) to help ensure that roles are only used when needed\.

When you create a role for this purpose, you specify the accounts by ID whose users need access in the `Principal` element of the role's trust policy\. You can then grant specific users in those other accounts permissions to switch to the role\.

A user in one account can switch to a role in the same or a different account\. While using the role, the user can perform only the actions and access only the resources permitted by the role; their original user permissions are suspended\. When the user exits the role, the original user permissions are restored\.