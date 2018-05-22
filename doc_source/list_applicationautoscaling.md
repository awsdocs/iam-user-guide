# Actions, Resources, and Condition Keys for Application Auto Scaling<a name="list_applicationautoscaling"></a>

Application Auto Scaling \(service prefix: `application-autoscaling`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/userguide/IAM.html) permission policies\.

**Topics**
+ [Actions Defined by Application Auto Scaling](#applicationautoscaling-actions-as-permissions)
+ [Resources Defined by Application Auto Scaling](#applicationautoscaling-resources-for-iam-policies)
+ [Condition Keys for Application Auto Scaling](#applicationautoscaling-policy-keys)

## Actions Defined by Application Auto Scaling<a name="applicationautoscaling-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DeleteScalingPolicy.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DeleteScalingPolicy.html) | Deletes an Application Auto Scaling scaling policy that was previously created\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DeleteScheduledAction.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DeleteScheduledAction.html) | Deletes an Application Auto Scaling scheduled action that was previously created\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DeregisterScalableTarget.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DeregisterScalableTarget.html) | Deregisters a scalable target that was previously registered\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DescribeScalableTargets.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DescribeScalableTargets.html) | Provides descriptive information for scalable targets with a specified service namespace\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DescribeScalingActivities.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DescribeScalingActivities.html) | Provides descriptive information for scaling activities with a specified service namespace for the previous six weeks\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DescribeScalingPolicies.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DescribeScalingPolicies.html) | Provides descriptive information for scaling policies with a specified service namespace\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DescribeScheduledActions.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_DescribeScheduledActions.html) | Provides descriptive information for scheduled actions with a specified service namespace\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_PutScalingPolicy.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_PutScalingPolicy.html) | Creates or updates a policy for an existing Application Auto Scaling scalable target\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_PutScheduledAction.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_PutScheduledAction.html) | Creates or updates a scheduled action for an existing Application Auto Scaling scalable target\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_RegisterScalableTarget.html](http://docs.aws.amazon.com/ApplicationAutoScaling/latest/APIReference/API_RegisterScalableTarget.html) | Registers or updates a scalable target\. A scalable target is a resource that can be scaled out or in with Application Auto Scaling\. | Write |  |  |  | 

## Resources Defined by Application Auto Scaling<a name="applicationautoscaling-resources-for-iam-policies"></a>

Application Auto Scaling has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Application Auto Scaling<a name="applicationautoscaling-policy-keys"></a>

Application Auto Scaling has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.