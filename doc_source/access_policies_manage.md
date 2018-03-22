# Managing IAM Policies<a name="access_policies_manage"></a>

IAM gives you the tools to create and manage all types of IAM policies \(managed policies and inline policies\)\. To add permissions to an IAM principal entity—that is, an IAM user, group, or role—you create a policy and then attach the policy to the principal entity\. You can attach multiple policies to a principal entity, and each policy can contain multiple permissions\.

Consult these resources for details:
+ For more information about the different types of IAM policies, see [IAM Policies](access_policies.md)\. 
+ For general information about using policies within IAM, see [Access Management](access.md)\.
+ For information about how permissions are evaluated when multiple policies are in effect for a given IAM principal entity, see [IAM JSON Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.
+ For information about policy size and naming limitations, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.

**Topics**
+ [Creating IAM Policies](access_policies_create.md)
+ [Validating JSON Policies](access_policies_policy-validator.md)
+ [Testing IAM Policies with the IAM Policy Simulator](access_policies_testing-policies.md)
+ [Attaching and Detaching IAM Policies](access_policies_manage-attach-detach.md)
+ [Versioning IAM Policies](access_policies_managed-versioning.md)
+ [Editing IAM Policies](access_policies_manage-edit.md)
+ [Deleting IAM Policies](access_policies_manage-delete.md)
+ [Reducing Policy Scope by Viewing User Activity](access_policies_access-advisor.md)