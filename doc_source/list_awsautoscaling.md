# Actions, resources, and condition keys for AWS Auto Scaling<a name="list_awsautoscaling"></a>

AWS Auto Scaling \(service prefix: `autoscaling-plans`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/autoscaling/plans/userguide/what-is-aws-auto-scaling.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/autoscaling/plans/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/autoscaling/plans/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by AWS Auto Scaling](#awsautoscaling-actions-as-permissions)
+ [Resource types defined by AWS Auto Scaling](#awsautoscaling-resources-for-iam-policies)
+ [Condition keys for AWS Auto Scaling](#awsautoscaling-policy-keys)

## Actions defined by AWS Auto Scaling<a name="awsautoscaling-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateScalingPlan ](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_CreateScalingPlan.html)  | Creates a scaling plan\. | Write |  |  |  | 
|   [ DeleteScalingPlan ](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DeleteScalingPlan.html)  | Deletes the specified scaling plan\. | Write |  |  |  | 
|   [ DescribeScalingPlanResources ](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DescribeScalingPlanResources.html)  | Describes the scalable resources in the specified scaling plan\. | Read |  |  |  | 
|   [ DescribeScalingPlans ](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_DescribeScalingPlans.html)  | Describes the specified scaling plans or all of your scaling plans\. | Read |  |  |  | 
|   [ GetScalingPlanResourceForecastData ](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_GetScalingPlanResourceForecastData.html)  | Retrieves the forecast data for a scalable resource\. | Read |  |  |  | 
|   [ UpdateScalingPlan ](https://docs.aws.amazon.com/autoscaling/plans/APIReference/API_UpdateScalingPlan.html)  | Updates a scaling plan\. | Write |  |  |  | 

## Resource types defined by AWS Auto Scaling<a name="awsautoscaling-resources-for-iam-policies"></a>

AWS Auto Scaling does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Auto Scaling, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS Auto Scaling<a name="awsautoscaling-policy-keys"></a>

Auto Scaling has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.