# Choosing between managed policies and inline policies<a name="access_policies-choosing-managed-or-inline"></a>

Consider your use cases when deciding between managed and inline policies\. In most cases, we recommend that you use managed policies instead of inline policies\.

**Note**  
You can use both managed and inline policies together to define common and unique permissions for a principal entity\.

Managed policies provide the following features:

**Reusability**  
A single managed policy can be attached to multiple principal entities \(users, groups, and roles\)\. You can create a library of policies that define useful permissions for your AWS account, and then attach these policies to principal entities as needed\.

**Central change management**  
When you change a managed policy, the change is applied to all principal entities that the policy is attached to\. For example, if you want to add permission for a new AWS API, you can update the managed policy to add the permission\. If you're using an AWS managed policy, AWS updates the policy\. When the policy is updated, the changes are applied to all principal entities that the policy is attached to\. In contrast, to change an inline policy, you must individually edit each identity that contains the policy\. For example, if a group and a role both contain the same inline policy, you must individually edit both principal entities to change that policy\. 

**Versioning and rolling back**  
When you change a customer managed policy, the changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new version of the managed policy\. IAM stores up to five versions of your customer managed policies\. You can use policy versions to revert a policy to an earlier version as needed\.   
A policy version is different from a `Version` policy element\. The `Version` policy element is used within a policy and defines the version of the policy language\. To learn more about policy versions, see [Versioning IAM policies](access_policies_managed-versioning.md)\. To learn more about the `Version` policy element see [IAM JSON policy elements: Version](reference_policies_elements_version.md)\.

**Delegating permissions management**  
You can allow users in your AWS account to attach and detach policies while maintaining control over the permissions defined in those policies\. To do this, designate some users as full administrators—that is, administrators that can create, update, and delete policies\. You can then designate other users as limited administrators\. Those limited administrators can attach policies to other principal entities, but only the policies that you have allowed them to attach\.   
For more information about delegating permissions management, see [Controlling access to policies](access_controlling.md#access_controlling-policies)\. 

**Automatic updates for AWS managed policies**  
AWS maintains AWS managed policies and updates them when necessary, for example, to add permissions for new AWS services, without you having to make changes\. The updates are automatically applied to the principal entities that you have attached the AWS managed policy to\. 

## Using inline policies<a name="policies-using-inline-policies"></a>

Inline policies are useful if you want to maintain a strict one\-to\-one relationship between a policy and the identity to which it is applied\. For example, if you want to be sure that the permissions in a policy are not inadvertently assigned to an identity other than the one they're intended for\. When you use an inline policy, the permissions in the policy cannot be inadvertently attached to the wrong identity\. In addition, when you use the AWS Management Console to delete that identity, the policies embedded in the identity are deleted as well because they are part of the principal entity\.