# Deprecated AWS managed policies<a name="access_policies_managed-deprecated"></a>

To simplify the assignment of permissions, AWS provides [managed policies](access_policies_managed-vs-inline.md)—predefined policies that are ready to be attached to your IAM users, groups, and roles\.

Sometimes AWS needs to add a new permission to an existing policy, such as when a new service is introduced\. Adding a new permission to an existing policy does not disrupt or remove any feature or ability\.

However, AWS might choose to create a *new* policy when the needed changes could impact customers if they were applied to an existing policy\. For example, removing permissions from an existing policy could break the permissions of any IAM entity or application that depended upon it, potentially disrupting a critical operation\.

Therefore, when such a change is required, AWS creates a completely new policy with the required changes and makes it available to customers\. The old policy is then marked *deprecated*\. A deprecated managed policy appears with a warning icon next to it in the **Policies** list in the IAM console\.

A deprecated policy has the following characteristics:
+ It continues to work for all *currently* attached users, groups, and roles\. Nothing breaks\.
+ It *cannot* be attached to any new users, groups, or roles\. If you detach it from a current entity, you cannot reattach it\.
+ After you detach it from all current entities, it is no longer visible and can no longer be used in any way\.

If any user, group, or role requires the policy, you must instead attach the new policy\. When you receive notice that a policy is deprecated, we recommend that you immediately plan to attach all users, groups, and roles to the replacement policy and detach them from the deprecated policy\. Continuing to use the deprecated policy can carry risks that are mitigated only by switching to the replacement policy\.