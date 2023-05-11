# Service summary \(list of actions\)<a name="access_policies_understand-service-summary"></a>

Policies are summarized in three tables: the [policy summary](access_policies_understand-policy-summary.md), the service summary, and the [action summary](access_policies_understand-action-summary.md)\. The *service summary* table includes a list of the actions and summaries of the permissions that are defined by the policy for the chosen service\.

![\[Policy summaries diagram image that illustrates the 3 tables and their relationship\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_summaries-svc-sum.png)

You can view a service summary for each service listed in the policy summary that grants permissions\. The table is grouped into **Uncategorized actions**, **Uncategorized resource types**, and access level sections\. If the policy includes an action that IAM does not recognize, then the action is included in the **Uncategorized actions** section of the table\. If IAM recognizes the action, then it is included under one of the access level \(**List**, **Read**, **Write** and **Permissions management**\) sections of the table\. To view the access level classification that is assigned to each action in a service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

## Viewing service summaries<a name="viewing-service-summaries"></a>

You can view the service summary for managed policies on the **Policies** page\.

**To view the service summary for a managed policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. In the list of policies, choose the name of the policy that you want to view\.

1. On the **Policy details** page for the policy, view the **Permissions** tab to see the policy summary\.

1. In the policy summary list of services, choose the name of the service that you want to view\.

**To view the service summary for a policy attached to a user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. In the list of users, choose the name of the user whose policy you want to view\.

1. On the **Summary** page for the user, view the **Permissions** tab to see the list of policies that are attached to the user directly or from a group\.

1. In the table of policies for the user, choose the name of the policy that you want to view\.

   If you are on the **Users** page and choose to view the service summary for a policy that is attached to that user, you are redirected to the **Policies** page\. You can view service summaries only on the **Policies** page\.

1. Choose **Summary**\. In the policy summary list of services, choose the name of the service that you want to view\.
**Note**  
If the policy that you select is an inline policy that is attached directly to the user, then the service summary table appears\. If the policy is an inline policy attached from a group, then you are taken to the JSON policy document for that group\. If the policy is a managed policy, then you are taken to the service summary for that policy on the **Policies** page\.

**To view the service summary for a policy attached to a role**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Roles** from the navigation pane\.

1. In the list of roles, choose the name of the role whose policy you want to view\.

1. On the **Summary** page for the role, view the **Permissions** tab to see the list of policies that are attached to the role\.

1. In the table of policies for the role, choose the name of the policy that you want to view\.

   If you are on the **Roles** page and choose to view the service summary for a policy that is attached to that user, you are redirected to the **Policies** page\. You can view service summaries only on the **Policies** page\.

1. In the policy summary list of services, choose the name of the service that you want to view\.

## Understanding the elements of a service summary<a name="understanding-elements-service-summary"></a>

The example below is the service summary for Amazon S3 actions that are allowed from a policy summary\. The actions for this service are grouped by access level\. For example, 35 **Read** actions are defined out of the total 52 **Read** actions available for the service\.

![\[Service summary dialog image\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-summary-action-dialog.png)

The service summary page for a managed policy includes the following information:

1. If the policy does not grant permissions to all the actions, resources, and conditions defined for the service in the policy, then a warning banner appears at the top of the page\. The service summary then includes details about the problem\. To learn how policy summaries help you to understand and troubleshoot the permissions that your policy grants, see [My policy does not grant the expected permissions](troubleshoot_policies.md#policy-summary-not-grant-permissions)\.

1. Choose **JSON** to see additional details about the policy\. You can do this to view all conditions that are applied to the actions\. \(If you are viewing the service summary for an inline policy that is attached directly to a user, you must close the service summary dialog box and return to the policy summary to access the JSON policy document\.\)

1. To view the summary for a specific action, type keywords into the **Search** box to reduce the list of available actions\.

1. Next to the **Services** back arrow appears the name of the service \(in this case **S3**\)\. The service summary for this service includes the list of allowed or denied actions that are defined in the policy\. If the service appears under **\(Explicit deny\)** on the **Permissions** tab, then the actions listed in the service summary table are explicitly denied\. If the service appears under **Allow** on the **Permissions** tab, then the actions listed in the service summary table are allowed\. 

1. **Action** – This column lists the actions that are defined within the policy and provides the resources and conditions for each action\. If the policy grants or denies permissions to the action, then the action name links to the *[action summary](access_policies_understand-action-summary.md)* table\. The table groups these actions into at least one or up to five sections, depending on the level of access that the policy allows or denies\. The sections are **List**, **Read**, **Write**, **Permission Management**, and **Tagging**\. The count indicates the number of recognized actions that provide permissions within each access level\. The total is the number of known actions for the service\. In this example, 35 actions provide permissions out of 52 total known Amazon S3 **Read** actions\. To view the access level classification that is assigned to each action in a service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

1. **Show remaining actions** – Toggle this button to expand or hide the table to include actions that are known but do not provide permissions for this service\. Toggling the button also displays warnings for any elements that do not provide permissions\.

1. **Resource** – This column shows the resources that the policy defines for the service\. IAM does not check whether the resource applies to each action\. In this example, actions in the Amazon S3 service are allowed on only the `developer_bucket` Amazon S3 bucket resource\. Depending on the information that the service provides to IAM, you might see an ARN such as `arn:aws:s3:::developer_bucket/*`, or you might see the defined resource type, such as `BucketName = developer_bucket`\.
**Note**  
This column can include a resource from a different service\. If the policy statement that includes the resource does not include both actions and resources from the same service, then your policy includes mismatched resources\. IAM does not warn you about mismatched resources when you create a policy, or when you view a policy in the service summary\. IAM also does not indicate whether the action applies to the resources, only whether the service matches\. If this column includes a mismatched resource, then you should review your policy for errors\. To better understand your policies, always test them with the [policy simulator](access_policies_testing-policies.md)\.

1. **Request condition** – This column tells whether the actions associated with the resource are subject to conditions\. To learn more about those conditions, choose **JSON** to review the JSON policy document\.

1. **\(No access\) **– This policy includes an action that does not provide permissions\. 

1. **Resource warning** – For actions with resources that do not provide full permissions, you see one of the following warnings:
   + **This action does not support resource\-level permissions\. This requires a wildcard \(\*\) for the resource\.** – This means that the policy includes resource\-level permissions but must include `"Resource": ["*"]` to provide permissions for this action\.
   + **This action does not have an applicable resource\.** – This means that the action is included in the policy without a supported resource\.
   + **This action does not have an applicable resource and condition\.** – This means that the action is included in the policy without a supported resource and without a supported condition\. In this case, there is also condition included in the policy for this service, but there are no conditions that apply to this action\.

1. Actions that provide permissions include a link to the action summary\.