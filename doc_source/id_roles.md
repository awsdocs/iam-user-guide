# IAM Roles<a name="id_roles"></a>

An IAM *role* is similar to a user, in that it is an AWS identity with permission policies that determine what the identity can and cannot do in AWS\. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it\. Also, a role does not have standard long\-term credentials \(password or access keys\) associated with it\. Instead, if a user assumes a role, [temporary security credentials](id_credentials_temp.md) are created dynamically and provided to the user\.

You can use roles to delegate access to users, applications, or services that don't normally have access to your AWS resources\. For example, you might want to grant users in your AWS account access to resources they don't usually have, or grant users in one AWS account access to resources in another account\. Or you might want to allow a mobile app to use AWS resources, but not want to embed AWS keys within the app \(where they can be difficult to rotate and where users can potentially extract them\)\. Sometimes you want to give AWS access to users who already have identities defined outside of AWS, such as in your corporate directory\. Or, you might want to grant access to your account to third parties so that they can perform an audit on your resources\.

For these scenarios, you can delegate access to AWS resources using an *IAM role*\. This section introduces roles and the different ways you can use them, when and how to choose among approaches, and how to create, manage, switch to \(or assume\), and delete roles\.

**Topics**
+ [Roles Terms and Concepts](id_roles_terms-and-concepts.md)
+ [Common Scenarios for Roles: Users, Applications, and Services](id_roles_common-scenarios.md)
+ [Identity Providers and Federation](id_roles_providers.md)
+ [Using Service\-Linked Roles](using-service-linked-roles.md)
+ [Creating IAM Roles](id_roles_create.md)
+ [Using IAM Roles](id_roles_use.md)
+ [Managing IAM Roles](id_roles_manage.md)
+ [How IAM Roles Differ from Resource\-based Policies](id_roles_compare-resource-policies.md)