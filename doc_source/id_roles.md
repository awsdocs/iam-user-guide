# IAM roles<a name="id_roles"></a>

An IAM *role* is an IAM identity that you can create in your account that has specific permissions\. An IAM role is similar to an IAM user, in that it is an AWS identity with permission policies that determine what the identity can and cannot do in AWS\. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it\. Also, a role does not have standard long\-term credentials such as a password or access keys associated with it\. Instead, when you assume a role, it provides you with temporary security credentials for your role session\.

You can use roles to delegate access to users, applications, or services that don't normally have access to your AWS resources\. For example, you might want to grant users in your AWS account access to resources they don't usually have, or grant users in one AWS account access to resources in another account\. Or you might want to allow a mobile app to use AWS resources, but not want to embed AWS keys within the app \(where they can be difficult to rotate and where users can potentially extract them\)\. Sometimes you want to give AWS access to users who already have identities defined outside of AWS, such as in your corporate directory\. Or, you might want to grant access to your account to third parties so that they can perform an audit on your resources\.

For these scenarios, you can delegate access to AWS resources using an *IAM role*\. This section introduces roles and the different ways you can use them, when and how to choose among approaches, and how to create, manage, switch to \(or assume\), and delete roles\.

**Note**  
When you first create your AWS account, no roles are created by default\. As you add services to your account, they may add service\-linked roles to support their use cases\.  
  A service\-linked role is a type of service role that is linked to an AWS service\. The service can assume the role to perform an action on your behalf\. Service\-linked roles appear in your IAM account and are owned by the service\. An IAM administrator can view, but not edit the permissions for service\-linked roles\.   
Before you can delete service\-linked roles you must first delete their related resources\. This protects your resources because you can't inadvertently remove permission to access the resources\.  
For information about which services support using service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

**Topics**
+ [Roles terms and concepts](id_roles_terms-and-concepts.md)
+ [Common scenarios for roles: Users, applications, and services](id_roles_common-scenarios.md)
+ [Identity providers and federation](id_roles_providers.md)
+ [Using service\-linked roles](using-service-linked-roles.md)
+ [Creating IAM roles](id_roles_create.md)
+ [Using IAM roles](id_roles_use.md)
+ [Managing IAM roles](id_roles_manage.md)
+ [How IAM roles differ from resource\-based policies](id_roles_compare-resource-policies.md)