# Actions, resources, and condition keys for Application Auto Scaling<a name="list_applicationautoscaling"></a>

Application Auto Scaling \(service prefix: `application-autoscaling`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/autoscaling/application/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/autoscaling/application/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/autoscaling/application/userguide/IAM.html) permission policies\.

**Topics**
+ [Actions defined by Application Auto Scaling](#applicationautoscaling-actions-as-permissions)
+ [Resource types defined by Application Auto Scaling](#applicationautoscaling-resources-for-iam-policies)
+ [Condition keys for Application Auto Scaling](#applicationautoscaling-policy-keys)

## Actions defined by Application Auto Scaling<a name="applicationautoscaling-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DeleteScalingPolicy ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_DeleteScalingPolicy.html)  | Deletes an Application Auto Scaling scaling policy that was previously created\. | Write |  |  |  | 
|   [ DeleteScheduledAction ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_DeleteScheduledAction.html)  | Deletes an Application Auto Scaling scheduled action that was previously created\. | Write |  |  |  | 
|   [ DeregisterScalableTarget ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_DeregisterScalableTarget.html)  | Deregisters a scalable target that was previously registered\. | Write |  |  |  | 
|   [ DescribeScalableTargets ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_DescribeScalableTargets.html)  | Provides descriptive information for scalable targets with a specified service namespace\. | Read |  |  |  | 
|   [ DescribeScalingActivities ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_DescribeScalingActivities.html)  | Provides descriptive information for scaling activities with a specified service namespace for the previous six weeks\. | Read |  |  |  | 
|   [ DescribeScalingPolicies ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_DescribeScalingPolicies.html)  | Provides descriptive information for scaling policies with a specified service namespace\. | Read |  |  |  | 
|   [ DescribeScheduledActions ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_DescribeScheduledActions.html)  | Provides descriptive information for scheduled actions with a specified service namespace\. | Read |  |  |  | 
|   [ PutScalingPolicy ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_PutScalingPolicy.html)  | Creates or updates a policy for an existing Application Auto Scaling scalable target\. | Write |  |  |  | 
|   [ PutScheduledAction ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_PutScheduledAction.html)  | Creates or updates a scheduled action for an existing Application Auto Scaling scalable target\. | Write |  |  |  | 
|   [ RegisterScalableTarget ](https://docs.aws.amazon.com/autoscaling/application/APIReference/API_RegisterScalableTarget.html)  | Registers or updates a scalable target\. A scalable target is a resource that can be scaled out or in with Application Auto Scaling\. | Write |  |  |  | 

## Resource types defined by Application Auto Scaling<a name="applicationautoscaling-resources-for-iam-policies"></a>

Application Auto Scaling does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Application Auto Scaling, specify `“Resource”: “*”` in your policy\.

## Condition keys for Application Auto Scaling<a name="applicationautoscaling-policy-keys"></a>

Application Auto Scaling has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.