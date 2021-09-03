# Service summary \(list of actions\)<a name="access_policies_understand-service-summary"></a>

Policies are summarized in three tables: the [policy summary](access_policies_understand-policy-summary.md), the service summary, and the [action summary](access_policies_understand-action-summary.md)\. The *service summary* table includes a list of the actions and summaries of the permissions that are defined by the policy for the chosen service\.

![\[Policy summaries diagram image that illustrates the 3 tables and their relationship\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_summaries-svc-sum.png)

You can view a service summary for each service listed in the policy summary that grants permissions\. The table is grouped into **Uncategorized actions**, **Uncategorized resource types**, and access level sections\. If the policy includes an action that IAM does not recognize, then the action is included in the **Uncategorized actions** section of the table\. If IAM recognizes the action, then it is included under one of the access level \(**List**, **Read**, **Write** and **Permissions management**\) sections of the table\. To view the access level classification that is assigned to each action in a service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

## Viewing service summaries<a name="viewing-service-summaries"></a>

You can view the service summary for managed policies on the **Policies** page, or view service summaries for inline and managed policies attached to a user or role through the **Users** page and **Roles** page\. However, if you choose a service name on the **Users** page or **Roles** page from a managed policy, you are redirected to the **Policies** page\. Service summaries for managed policies must be viewed on the **Policies** page\.

**To view the service summary for a managed policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. In the list of policies, choose the name of the policy that you want to view\.

1. On the **Summary** page for the policy, view the **Permissions** tab to see the policy summary\.

1. In the policy summary list of services, choose the name of the service that you want to view\.

**To view the service summary for a policy attached to a user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. In the list of users, choose the name of the user whose policy you want to view\.

1. On the **Summary** page for the user, view the **Permissions** tab to see the list of policies that are attached to the user directly or from a group\.

1. In the table of policies for the user, expand the row of the policy that you want to view\.

1. In the policy summary list of services, choose the name of the service that you want to view\.
**Note**  
If the policy that you select is an inline policy that is attached directly to the user, then the service summary table appears\. If the policy is an inline policy attached from a group, then you are taken to the JSON policy document for that group\. If the policy is a managed policy, then you are taken to the service summary for that policy on the **Policies** page\.

**To view the service summary for a policy attached to a role**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Roles** from the navigation pane\.

1. In the list of roles, choose the name of the role whose policy you want to view\.

1. On the **Summary** page for the role, view the **Permissions** tab to see the list of policies that are attached to the role\.

1. In the table of policies for the role, expand the row of the policy that you want to view\.

1. In the policy summary list of services, choose the name of the service that you want to view\.

## Understanding the elements of a service summary<a name="understanding-elements-service-summary"></a>

The example below is the service summary for Amazon S3 actions that are allowed from the **SummaryAllElements** policy summary \(see [**SummaryAllElements** JSON policy document](access_policies_understand-policy-summary.md#policy-summary-example-json)\)\. The actions for this service are grouped by **Uncategorized actions**, **Uncategorized resource types**, and access level\. For example, two **Write** actions are defined out of the total 29 **Write** actions available for the service\.

![\[Service summary dialog image\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-summary-action-dialog.png)

The service summary page for a managed policy includes the following information:

1. If the policy does not grant permissions to all the actions, resources, and conditions defined for the service in the policy, then a warning banner appears at the top of the page\. The service summary then includes details about the problem\. To learn how policy summaries help you to understand and troubleshoot the permissions that your policy grants, see [My policy does not grant the expected permissions](troubleshoot_policies.md#policy-summary-not-grant-permissions)\.

1. Next to the **Back** link appears the name of the service \(in this case S3\)\. The service summary for this service includes the list of allowed actions that are defined in the policy\. If instead, the text **\(Explicitly denied\)** appears next to the name of a service, then the actions listed in the service summary table are explicitly denied\.

1. Choose **\{ \} JSON** to see additional details about the policy\. You can do this to view all conditions that are applied to the actions\. \(If you are viewing the service summary for an inline policy that is attached directly to a user, you must close the service summary dialog box and return to the policy summary to access the JSON policy document\.\)

1. To view the summary for a specific action, type keywords into the search box to reduce the list of available actions\.

1. **Action \(2 of 69 actions\)** – This column lists the actions that are defined within the policy and provides the resources and conditions for each action\. If the policy grants permissions to the action, then the action name links to the *[action summary](access_policies_understand-action-summary.md)* table\. The count indicates the number of recognized actions that provide permissions\. The total is the number of known actions for the service\. In this example, 2 actions provide permissions out of 69 total known S3 actions\.

1. **Show/Hide remaining 67** – Choose this link to expand or hide the table to include actions that are known but do not provide permissions for this service\. Expanding the link also displays warnings for any elements that do not provide permissions\.

1. **Unrecognized resource types** – This policy includes at least one unrecognized resource type within the policy for this service\. You can use this warning to check whether a resource type might include a typo\. If the resource type is correct, then the service might not fully support policy summaries, might be in preview, or might be a custom service\. To request policy summary support for a specific resource type in a generally available \(GA\) service, see [Service does not support IAM policy summaries](troubleshoot_policies.md#unsupported-services-actions)\. In this example, the `autoscling` service name is missing an `a`\.

1. **Unrecognized actions** – This policy includes at least one unrecognized action within the policy for this service\. You can use this warning to check whether an action might include a typo\. If the action name is correct, then the service might not fully support policy summaries, might be in preview, or might be a custom service\. To request policy summary support for a specific action in a generally available \(GA\) service, see [Service does not support IAM policy summaries](troubleshoot_policies.md#unsupported-services-actions)\. In this example, the `DeletObject` ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) action is missing an `e`\. 
**Note**  
IAM reviews service names, actions, and resource types for services that support policy summaries\. However, your policy summary might include a resource value or condition that does not exist\. Always test your policies with the [policy simulator](access_policies_testing-policies.md)\.

1. For those actions that IAM recognizes, the table groups these actions into at least one or up to four sections, depending on the level of access that the policy allows or denies\. The sections are **List**, **Read**, **Write**, and **Permissions management**\. You can also see the number of actions that are defined out of the total number of actions available within each access level\. To view the access level classification that is assigned to each action in a service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

1. The ellipses \(…\) indicate that all the actions are included in the page, but we are showing only the rows with information relevant to this policy\. When you view this page in the AWS Management Console, you see all the actions for your service\.

1. **\(No access\) **– This policy includes an action that does not provide permissions\. 

1. Actions that provide permissions include a link to the action summary\.

1. **Resource** – This column shows the resources that the policy defines for the service\. IAM does not check whether the resource applies to each action\. In this example, actions in the S3 service are allowed on only the `developer_bucket` Amazon S3 bucket resource\. Depending on the information that the service provides to IAM, you might see an ARN such as `arn:aws:s3:::developer_bucket/*`, or you might see the defined resource type, such as `BucketName = developer_bucket`\.
**Note**  
This column can include a resource from a different service\. If the policy statement that includes the resource does not include both actions and resources from the same service, then your policy includes mismatched resources\. IAM does not warn you about mismatched resources when you create a policy, or when you view a policy in the service summary\. IAM also does not indicate whether the action applies to the resources, only whether the service matches\. If this column includes a mismatched resource, then you should review your policy for errors\. To better understand your policies, always test them with the [policy simulator](access_policies_testing-policies.md)\.

1. **Resource warning** – For actions with resources that do not provide full permissions, you see one of the following warnings:
   + **This action does not support resource\-level permissions\. This requires a wildcard \(\*\) for the resource\.** – This means that the policy includes resource\-level permissions but must include `"Resource": ["*"]` to provide permissions for this action\.
   + **This action does not have an applicable resource\.** – This means that the action is included in the policy without a supported resource\.
   + **This action does not have an applicable resource and condition\.** – This means that the action is included in the policy without a supported resource and without a supported condition\. In this case, there is also condition included in the policy for this service, but there are no conditions that apply to this action\.

   For the `ListAllMyBuckets` action, this policy includes the last warning because the action does not support resource\-level permissions and does not support the `s3:x-amz-acl` condition key\. If you fix either the resource problem or the condition problem, the remaining issue appears in a detailed warning\.

1. **Request condition** – This column tells whether the actions associated with the resource are subject to conditions\. To learn more about those conditions, choose **\{ \} JSON** to review the JSON policy document\.

1. **Condition warning** – For actions with conditions that do not provide full permissions, you see one of the following warnings:
   + **<CONDITION\_KEY> is not a supported condition key for this action\.** – This means that the policy includes a condition key for the service that is not supported for this action\.
   + **Multiple condition keys are not supported for this action\.** – This means that the policy includes more than one condition keys for the service that are not supported for this action\.

   For `GetObject`, this policy includes the `s3:x-amz-acl` condition key, which will not work with this action\. Although the action supports the resource, the policy does not grant any permissions for this action because the condition will never be true for this action\.