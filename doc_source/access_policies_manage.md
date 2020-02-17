# Managing IAM Policies<a name="access_policies_manage"></a>

IAM gives you the tools to create and manage all types of IAM policies \(managed policies and inline policies\)\. To add permissions to an IAM identity \(IAM user, group, or role\), you create a policy and then attach the policy to the identity\. You can attach multiple policies to an identity, and each policy can contain multiple permissions\.

Consult these resources for details:
+ For more information about the different types of IAM policies, see [Policies and Permissions](access_policies.md)\. 
+ For general information about using policies within IAM, see [Access Management](access.md)\.
+ For information about how permissions are evaluated when multiple policies are in effect for a given IAM identity, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.
+ For information about policy size and naming limitations, see [IAM and STS Limits](reference_iam-limits.md)\.

**Topics**
+ [Creating IAM Policies](access_policies_create.md)
+ [Validating JSON Policies](access_policies_policy-validator.md)
+ [Testing IAM Policies with the IAM Policy Simulator](access_policies_testing-policies.md)
+ [Adding and Removing IAM Identity Permissions](access_policies_manage-attach-detach.md)
+ [Versioning IAM Policies](access_policies_managed-versioning.md)
+ [Editing IAM Policies](access_policies_manage-edit.md)
+ [Deleting IAM Policies](access_policies_manage-delete.md)
+ [Refining Permissions Using Service Last Accessed Data](access_policies_access-advisor.md)