# Actions, Resources, and Condition Keys for Auto Scaling<a name="list_autoscaling"></a>

Auto Scaling \(service prefix: `autoscaling`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/autoscaling/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/autoscaling/latest/userguide/IAM.html) permission policies\.

**Topics**
+ [Actions Defined by Auto Scaling](#autoscaling-actions-as-permissions)
+ [Resources Defined by Auto Scaling](#autoscaling-resources-for-iam-policies)
+ [Condition Keys for Auto Scaling](#autoscaling-policy-keys)

## Actions Defined by Auto Scaling<a name="autoscaling-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [AttachInstances](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_AttachInstances.html) | Attaches one or more EC2 instances to the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [AttachLoadBalancerTargetGroups](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_AttachLoadBalancerTargetGroups.html) | Attaches one or more target groups to the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [AttachLoadBalancers](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_AttachLoadBalancers.html) | Attaches one or more load balancers to the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [CompleteLifecycleAction](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_CompleteLifecycleAction.html) | Completes the lifecycle action for the specified token or instance with the specified result\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [CreateAutoScalingGroup](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_CreateAutoScalingGroup.html) | Creates an Auto Scaling group with the specified name and attributes\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [CreateLaunchConfiguration](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_CreateLaunchConfiguration.html) | Creates a launch configuration\. |   | [launchConfiguration\*](#autoscaling-launchConfiguration)  |  |  | 
| [CreateOrUpdateTags](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_CreateOrUpdateTags.html) | Creates or updates tags for the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DeleteAutoScalingGroup](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DeleteAutoScalingGroup.html) | Deletes the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DeleteLaunchConfiguration](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DeleteLaunchConfiguration.html) | Deletes the specified launch configuration\. |   | [launchConfiguration\*](#autoscaling-launchConfiguration)  |  |  | 
| [DeleteLifecycleHook](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DeleteLifecycleHook.html) | Deletes the specified lifecycle hook\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DeleteNotificationConfiguration](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DeleteNotificationConfiguration.html) | Deletes the specified notification\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DeletePolicy](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DeletePolicy.html) | Deletes the specified Auto Scaling policy\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DeleteScheduledAction](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DeleteScheduledAction.html) | Deletes the specified scheduled action\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DeleteTags](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DeleteTags.html) | Deletes the specified tags\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DescribeAccountLimits](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeAccountLimits.html) | Describes the current Auto Scaling resource limits for your AWS account\. |   |  |  |  | 
| [DescribeAdjustmentTypes](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeAdjustmentTypes.html) | Describes the policy adjustment types for use with PutScalingPolicy\. |   |  |  |  | 
| [DescribeAutoScalingGroups](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeAutoScalingGroups.html) | Describes one or more Auto Scaling groups\. If a list of names is not provided, the call describes all Auto Scaling groups\. |   |  |  |  | 
| [DescribeAutoScalingInstances](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeAutoScalingInstances.html) | Describes one or more Auto Scaling instances\. If a list is not provided, the call describes all instances\. |   |  |  |  | 
| [DescribeAutoScalingNotificationTypes](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeAutoScalingNotificationTypes.html) | Describes the notification types that are supported by Auto Scaling\. |   |  |  |  | 
| [DescribeLaunchConfigurations](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeLaunchConfigurations.html) | Describes one or more launch configurations\. If you omit the list of names, then the call describes all launch configurations\. |   |  |  |  | 
| [DescribeLifecycleHookTypes](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeLifecycleHookTypes.html) | Describes the available types of lifecycle hooks\. |   |  |  |  | 
| [DescribeLifecycleHooks](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeLifecycleHooks.html) | Describes the lifecycle hooks for the specified Auto Scaling group\. |   |  |  |  | 
| [DescribeLoadBalancerTargetGroups](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeLoadBalancerTargetGroups.html) | Describes the target groups for the specified Auto Scaling group\. |   |  |  |  | 
| [DescribeLoadBalancers](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeLoadBalancers.html) | Describes the load balancers for the specified Auto Scaling group\. |   |  |  |  | 
| [DescribeMetricCollectionTypes](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeMetricCollectionTypes.html) | Describes the available CloudWatch metrics for Auto Scaling\. |   |  |  |  | 
| [DescribeNotificationConfigurations](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeNotificationConfigurations.html) | Describes the notification actions associated with the specified Auto Scaling group\. |   |  |  |  | 
| [DescribePolicies](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribePolicies.html) | Describes the policies for the specified Auto Scaling group\. |   |  |  |  | 
| [DescribeScalingActivities](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeScalingActivities.html) | Describes one or more scaling activities for the specified Auto Scaling group\.  |   |  |  |  | 
| [DescribeScalingProcessTypes](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeScalingProcessTypes.html) | Describes the scaling process types for use with ResumeProcesses and SuspendProcesses\. |   |  |  |  | 
| [DescribeScheduledActions](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeScheduledActions.html) | Describes the actions scheduled for your Auto Scaling group that haven't run\. |   |  |  |  | 
| [DescribeTags](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeTags.html) | Describes the specified tags\. |   |  |  |  | 
| [DescribeTerminationPolicyTypes](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DescribeTerminationPolicyTypes.html) | Describes the termination policies supported by Auto Scaling\. |   |  |  |  | 
| [DetachInstances](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DetachInstances.html) | Removes one or more instances from the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DetachLoadBalancerTargetGroups](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DetachLoadBalancerTargetGroups.html) | Detaches one or more target groups from the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DetachLoadBalancers](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DetachLoadBalancers.html) | Removes one or more load balancers from the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [DisableMetricsCollection](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_DisableMetricsCollection.html) | Disables monitoring of the specified metrics for the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [EnableMetricsCollection](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_EnableMetricsCollection.html) | Enables monitoring of the specified metrics for the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [EnterStandby](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_EnterStandby.html) | Moves the specified instances into Standby mode\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [ExecutePolicy](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_ExecutePolicy.html) | Executes the specified policy\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [ExitStandby](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_ExitStandby.html) | Moves the specified instances out of Standby mode\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [PutLifecycleHook](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_PutLifecycleHook.html) | Creates or updates a lifecycle hook for the specified Auto Scaling Group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [PutNotificationConfiguration](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_PutNotificationConfiguration.html) | Configures an Auto Scaling group to send notifications when specified events take place\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [PutScalingPolicy](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_PutScalingPolicy.html) | Creates or updates a policy for an Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [PutScheduledUpdateGroupAction](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_PutScheduledUpdateGroupAction.html) | Creates or updates a scheduled scaling action for an Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [RecordLifecycleActionHeartbeat](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_RecordLifecycleActionHeartbeat.html) | Records a heartbeat for the lifecycle action associated with the specified token or instance\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [ResumeProcesses](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_ResumeProcesses.html) | Resumes the specified suspended Auto Scaling processes, or all suspended process, for the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [SetDesiredCapacity](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_SetDesiredCapacity.html) | Sets the size of the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [SetInstanceHealth](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_SetInstanceHealth.html) | Sets the health status of the specified instance\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [SetInstanceProtection](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_SetInstanceProtection.html) | Updates the instance protection settings of the specified instances\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [SuspendProcesses](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_SuspendProcesses.html) | Suspends the specified Auto Scaling processes, or all processes, for the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [TerminateInstanceInAutoScalingGroup](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_TerminateInstanceInAutoScalingGroup.html) | Terminates the specified instance and optionally adjusts the desired group size\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 
| [UpdateAutoScalingGroup](http://docs.aws.amazon.com/AutoScaling/latest/APIReference/API_UpdateAutoScalingGroup.html) | Updates the configuration for the specified Auto Scaling group\. |   | [autoScalingGroup\*](#autoscaling-autoScalingGroup)  | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  |  | 

## Resources Defined by Auto Scaling<a name="autoscaling-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#autoscaling-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [autoScalingGroup](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-resources) | arn:$\{Partition\}:autoscaling:$\{Region\}:$\{Account\}:autoScalingGroup:$\{GroupId\}:autoScalingGroupName/$\{GroupFriendlyName\} | [autoscaling:ResourceTag/](#autoscaling-autoscaling_ResourceTag_)  | 
| [launchConfiguration](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-resources) | arn:$\{Partition\}:autoscaling:$\{Region\}:$\{Account\}:launchConfiguration:$\{Id\}:launchConfigurationName/$\{LaunchConfigurationName\} |  | 

## Condition Keys for Auto Scaling<a name="autoscaling-policy-keys"></a>

Auto Scaling defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [autoscaling:ImageId](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The AMI used to create the instance\. | String | 
| [autoscaling:InstanceType](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The type of instance, in terms of the hardware resources available\. | String | 
| [autoscaling:LaunchConfigurationName](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The name of a launch configuration\. | String | 
| [autoscaling:LoadBalancerNames](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The name of the load balancer\. | String | 
| [autoscaling:MaxSize](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The maximum scaling size\. | Numeric | 
| [autoscaling:MinSize](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The minimum scaling size\. | Numeric | 
| [autoscaling:ResourceTag/](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The value of a tag attached to a resource\. | String | 
| [autoscaling:SpotPrice](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The spot price associated with an instance\. | Numeric | 
| [autoscaling:TargetGroupARNs](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The ARN of a target group\. | ARN | 
| [autoscaling:VPCZoneIdentifiers](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The identifier of a VPC zone\. | String | 
| [aws:RequestTag/](http://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys) | The value of a tag associated with the request\. | String | 