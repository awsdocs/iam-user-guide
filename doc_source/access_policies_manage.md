# Managing IAM policies<a name="access_policies_manage"></a>

IAM gives you the tools to create and manage all types of IAM policies \(managed policies and inline policies\)\. To add permissions to an IAM identity \(IAM user, group, or role\), you create a policy and then attach the policy to the identity\. You can attach multiple policies to an identity, and each policy can contain multiple permissions\.

Consult these resources for details:
+ For more information about the different types of IAM policies, see [Policies and permissions in IAM](access_policies.md)\. 
+ For general information about using policies within IAM, see [Access management for AWS resources](access.md)\.
+ For information about how permissions are evaluated when multiple policies are in effect for a given IAM identity, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.
+ The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\.

**Topics**
+ [Creating IAM policies](access_policies_create.md)
+ [Validating IAM policy grammar](access_policies_policy-validator.md)
+ [Testing IAM policies with the IAM policy simulator](access_policies_testing-policies.md)
+ [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md)
+ [Versioning IAM policies](access_policies_managed-versioning.md)
+ [Editing IAM policies](access_policies_manage-edit.md)
+ [Deleting IAM policies](access_policies_manage-delete.md)
+ [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)