# Understanding Permissions Granted by a Policy<a name="access_policies_understand"></a>

The IAM console includes *policy summary* tables that describe the access level, resources, and conditions that are allowed or denied for each service in a policy\. Policies are summarized in three tables: the [policy summary](access_policies_understand-policy-summary.md), the [service summary](access_policies_understand-service-summary.md), and the [action summary](access_policies_understand-action-summary.md)\. The *policy summary* table includes a list of services\. Choose a service there to see the *service summary*\. This summary table includes a list of the actions and associated permissions for the chosen service\. You can choose an action from that table to view the *action summary*\. This table includes a list of resources and conditions for the chosen action\. 

![\[Policy summaries diagram image that illustrates the 3 tables and their relationship\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_summaries-diagram.png)

You can view policy summaries on the **Users** page or **Roles** page for all policies \(managed and inline\) that are attached to that user\. View summaries on the **Policies** page for all managed policies\. Managed policies include AWS managed policies, AWS managed job function policies, and customer managed policies\. You can view summaries for these policies on the **Policies** page regardless of whether they are attached to a user or other IAM identity\.

You can use the information in the policy summaries to understand the permissions that are allowed or denied by your policy\. Policy summaries can help you [troubleshoot](troubleshoot_policies.md) and fix policies that are not providing the permissions that you expect\.

**Topics**
+ [Policy Summary \(List of Services\)](access_policies_understand-policy-summary.md)
+ [Service Summary \(List of Actions\)](access_policies_understand-service-summary.md)
+ [Action Summary \(List of Resources\)](access_policies_understand-action-summary.md)
+ [Examples of Policy Summaries](access_policies_policy-summary-examples.md)