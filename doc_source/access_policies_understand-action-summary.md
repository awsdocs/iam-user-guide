# Action summary \(list of resources\)<a name="access_policies_understand-action-summary"></a>

Policies are summarized in three tables: the [policy summary](access_policies_understand-policy-summary.md), the [service summary](access_policies_understand-service-summary.md), and the action summary\. The *action summary* table includes a list of resources and the associated conditions that apply to the chosen action\. 

![\[Policy summaries diagram image that illustrates the 3 tables and their relationship\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_summaries-action-sum.png)

To view an action summary for each action that grants permissions, choose the link in the service summary\. The action summary table includes details about the resource, including its **Region** and **Account**\. You can also view the conditions that apply to each resource\. This shows you conditions that apply to some resources but not others\.

## Viewing action summaries<a name="viewing-action-summaries"></a>

You can view the action summary for any policy that is attached to a user on the **Users** page\. You can view the action summary for any policy that is attached to a role on the **Roles** page\. You can view the action summary for managed policies on the **Policies** page\. However, if you try to view the action summary for a managed policy from the **Users** page or the **Roles** page, you are redirected to the **Policies** page\.

**To view the action summary for a managed policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. In the list of policies, choose the name of the policy that you want to view\.

1. On the **Summary** page for the policy, view the **Permissions** tab to see the policy summary\.

1. In the policy summary list of services, choose the name of the service that you want to view\.

1. In the service summary list of actions, choose the name of the action that you want to view\.

**To view the action summary for a policy attached to a user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Users** from the navigation pane\.

1. In the list of users, choose the name of the user whose policy you want to view\.

1. On the **Summary** page for the user, view the **Permissions** tab to see the list of policies that are attached to the user directly or from a group\.

1. In the table of policies for the user, expand the row of the policy that you want to view\.

1. In the policy summary list of services, choose the name of the service that you want to view\.
**Note**  
If the policy that you select is an inline policy that is attached directly to the user, then the service summary table appears\. If the policy is an inline policy attached from a group, then you are taken to the JSON policy document for that group\. If the policy is a managed policy, then you are taken to the service summary for that policy on the **Policies** page\.

1. In the service summary list of actions, choose the name of the action that you want to view\.

**To view the action summary for a policy attached to a role**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles**\.

1. In the list of roles, choose the name of the role whose policy you want to view\.

1. On the **Summary** page for the role, view the **Permissions** tab to see the list of policies that are attached to the role\.

1. In the table of policies for the role, expand the row of the policy that you want to view\.

1. In the policy summary list of services, choose the name of the service that you want to view\.

1. In the service summary list of actions, choose the name of the action that you want to view\.

## Understanding the elements of an action summary<a name="understanding-elements-action-summary"></a>

The example below is the action summary for the `PutObject` \(Write\) action from the Amazon S3 service summary \(see [Service summary \(list of actions\)](access_policies_understand-service-summary.md)\)\. For this action, the policy defines multiple conditions on a single resource\.

![\[Action summary dialog image\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-summary-resource-dialog.png)

The action summary page includes the following information:

1. Next to the **Back** link appears the name of the service and action in the format `service: action` \(in this case **S3: PutObject**\)\. The action summary for this service includes the list of resources that are defined in the policy\.

1. Choose **\{ \} JSON** to see additional details about the policy, such as viewing the multiple conditions that are applied to the actions\. \(If you are viewing the action summary for an inline policy that is attached directly to a user, the steps differ\. To access the JSON policy document in that case, you must close the action summary dialog box and return to the policy summary\.\)

1. To view the summary for a specific resource, type keywords into the search box to reduce the list of available resources\.

1. **Resource** – This column lists the resources that the policy defines for the chosen service\. In this example, the **PutObject** action is allowed on all object paths, but on only the `developer_bucket` Amazon S3 bucket resource\. Depending on the information that the service provides to IAM, you might see an ARN such as `arn:aws:s3:::developer_bucket/*`, or you might see the defined resource type, such as `BucketName = developer_bucket, ObjectPath = All`\.

1. **Region** – This column shows the Region in which the resource is defined\. Resources can be defined for all Regions, or a single Region\. They cannot exist in more than one specific Region\.
   + **All Regions** – The actions that are associated with the resource apply to all Regions\. In this example, the action belongs to a global service, Amazon S3\. Actions that belong to global services apply to all Regions\.
   + Region text – The actions associated with the resource apply to one Region\. For example, a policy can specify the `us-east-2` Region for a resource\.

1. **Account** – This column indicates whether the services or actions associated with the resource apply to a specific account\. Resources can exist in all accounts or a single account\. They cannot exist in more than one specific account\.
   + **All accounts** – The actions that are associated with the resource apply to all accounts\. In this example, the action belongs to a global service, Amazon S3\. Actions that belong to global services apply to all accounts\.
   + **This account** – The actions that are associated with the resource apply only to the account that you are currently logged in to\.
   + Account number – The actions that are associated with the resource apply to one account \(one that you are not currently logged in to\)\. For example, if a policy specifies the `123456789012` account for a resource, then the account number appears in the policy summary\.

1. **Request condition** – This column shows whether the actions that are associated with the resource are subject to conditions\. This example includes the `s3:x-amz-acl = public-read` condition\. To learn more about those conditions, choose **\{ \} JSON** to review the JSON policy document\.