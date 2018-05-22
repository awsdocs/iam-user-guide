# Actions, Resources, and Condition Keys for Auto Scaling Plans<a name="list_autoscalingplans"></a>

Auto Scaling Plans \(service prefix: `autoscaling-plans`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/autoscaling/plans/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/autoscaling/plans/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/autoscaling/plans/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Auto Scaling Plans](#autoscalingplans-actions-as-permissions)
+ [Resources Defined by Auto Scaling Plans](#autoscalingplans-resources-for-iam-policies)
+ [Condition Keys for Auto Scaling Plans](#autoscalingplans-policy-keys)

## Actions Defined by Auto Scaling Plans<a name="autoscalingplans-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_CreateScalingPlan.html](http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_CreateScalingPlan.html) | Creates a scaling plan\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DeleteScalingPlan.html](http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DeleteScalingPlan.html) | Deletes the specified scaling plan\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DescribeScalingPlanResources.html](http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DescribeScalingPlanResources.html) | Describes the scalable resources in the specified scaling plan\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DescribeScalingPlans.html](http://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DescribeScalingPlans.html) | Describes the specified scaling plans or all of your scaling plans\. | Read |  |  |  | 

## Resources Defined by Auto Scaling Plans<a name="autoscalingplans-resources-for-iam-policies"></a>

Auto Scaling Plans has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Auto Scaling Plans<a name="autoscalingplans-policy-keys"></a>

Auto Scaling Plans has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.