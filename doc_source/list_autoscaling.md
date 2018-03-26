# Actions and Condition Context Keys for Auto Scaling<a name="list_autoscaling"></a>

Auto Scaling \(service prefix: autoscaling\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Auto Scaling**

For information about using the following Auto Scaling API actions in an IAM policy, see [Auto Scaling Actions](http://docs.aws.amazon.com/autoscaling/latest/userguide/IAM.html#UsingWithAutoScaling_Actions) in the *Amazon EC2 Auto Scaling User Guide*\.
+ `[autoscaling:AttachInstances](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_AttachInstances.html)`
+ `[autoscaling:AttachLoadBalancerTargetGroups](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_AttachLoadBalancerTargetGroups.html)`
+ `[autoscaling:AttachLoadBalancers](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_AttachLoadBalancers.html)`
+ `[autoscaling:CompleteLifecycleAction](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_CompleteLifecycleAction.html)`
+ `[autoscaling:CreateAutoScalingGroup](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_CreateAutoScalingGroup.html)`
+ `[autoscaling:CreateLaunchConfiguration](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_CreateLaunchConfiguration.html)`
+ `[autoscaling:CreateOrUpdateTags](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_CreateOrUpdateTags.html)`
+ `[autoscaling:DeleteAutoScalingGroup](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DeleteAutoScalingGroup.html)`
+ `[autoscaling:DeleteLaunchConfiguration](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DeleteLaunchConfiguration.html)`
+ `[autoscaling:DeleteLifecycleHook](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DeleteLifecycleHook.html)`
+ `[autoscaling:DeleteNotificationConfiguration](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DeleteNotificationConfiguration.html)`
+ `[autoscaling:DeletePolicy](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DeletePolicy.html)`
+ `[autoscaling:DeleteScheduledAction](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DeleteScheduledAction.html)`
+ `[autoscaling:DeleteTags](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DeleteTags.html)`
+ `[autoscaling:DescribeAccountLimits](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeAccountLimits.html)`
+ `[autoscaling:DescribeAdjustmentTypes](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeAdjustmentTypes.html)`
+ `[autoscaling:DescribeAutoScalingGroups](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeAutoScalingGroups.html)`
+ `[autoscaling:DescribeAutoScalingInstances](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeAutoScalingInstances.html)`
+ `[autoscaling:DescribeAutoScalingNotificationTypes](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeAutoScalingNotificationTypes.html)`
+ `[autoscaling:DescribeLaunchConfigurations](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeLaunchConfigurations.html)`
+ `[autoscaling:DescribeLifecycleHookTypes](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeLifecycleHookTypes.html)`
+ `[autoscaling:DescribeLifecycleHooks](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeLifecycleHooks.html)`
+ `[autoscaling:DescribeLoadBalancerTargetGroups](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeLoadBalancerTargetGroups.html)`
+ `[autoscaling:DescribeLoadBalancers](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeLoadBalancers.html)`
+ `[autoscaling:DescribeMetricCollectionTypes](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeMetricCollectionTypes.html)`
+ `[autoscaling:DescribeNotificationConfigurations](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeNotificationConfigurations.html)`
+ `[autoscaling:DescribePolicies](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribePolicies.html)`
+ `[autoscaling:DescribeScalingActivities](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeScalingActivities.html)`
+ `[autoscaling:DescribeScalingProcessTypes](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeScalingProcessTypes.html)`
+ `[autoscaling:DescribeScheduledActions](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeScheduledActions.html)`
+ `[autoscaling:DescribeTags](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeTags.html)`
+ `[autoscaling:DescribeTerminationPolicyTypes](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DescribeTerminationPolicyTypes.html)`
+ `[autoscaling:DetachInstances](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DetachInstances.html)`
+ `[autoscaling:DetachLoadBalancerTargetGroups](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DetachLoadBalancerTargetGroups.html)`
+ `[autoscaling:DetachLoadBalancers](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DetachLoadBalancers.html)`
+ `[autoscaling:DisableMetricsCollection](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_DisableMetricsCollection.html)`
+ `[autoscaling:EnableMetricsCollection](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_EnableMetricsCollection.html)`
+ `[autoscaling:EnterStandby](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_EnterStandby.html)`
+ `[autoscaling:ExecutePolicy](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_ExecutePolicy.html)`
+ `[autoscaling:ExitStandby](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_ExitStandby.html)`
+ `[autoscaling:PutLifecycleHook](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_PutLifecycleHook.html)`
+ `[autoscaling:PutNotificationConfiguration](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_PutNotificationConfiguration.html)`
+ `[autoscaling:PutScalingPolicy](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_PutScalingPolicy.html)`
+ `[autoscaling:PutScheduledUpdateGroupAction](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_PutScheduledUpdateGroupAction.html)`
+ `[autoscaling:RecordLifecycleActionHeartbeat](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_RecordLifecycleActionHeartbeat.html)`
+ `[autoscaling:ResumeProcesses](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_ResumeProcesses.html)`
+ `[autoscaling:SetDesiredCapacity](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_SetDesiredCapacity.html)`
+ `[autoscaling:SetInstanceHealth](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_SetInstanceHealth.html)`
+ `[autoscaling:SetInstanceProtection](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_SetInstanceProtection.html)`
+ `[autoscaling:SuspendProcesses](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_SuspendProcesses.html)`
+ `[autoscaling:TerminateInstanceInAutoScalingGroup](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_TerminateInstanceInAutoScalingGroup.html)`
+ `[autoscaling:UpdateAutoScalingGroup](http://docs.aws.amazon.com/autoscaling/ec2/APIReference/API_UpdateAutoScalingGroup.html)`

**Condition context keys for Auto Scaling**

For more information about using condition keys in an IAM policy for Auto Scaling, see [Auto Scaling Keys](http://docs.aws.amazon.com/autoscaling/latest/userguide/IAM.html#UsingWithAutoScaling_Actions) in the *Amazon EC2 Auto Scaling User Guide*\.

Auto Scaling has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ `autoscaling:ImageId`
+ `autoscaling:InstanceType`
+ `autoscaling:LaunchConfigurationName`
+ `autoscaling:LoadBalancerNames`
+ `autoscaling:MaxSize`
+ `autoscaling:MinSize`
+ `autoscaling:ResourceTag/`
+ `autoscaling:SpotPrice`
+ `autoscaling:TargetGroupARNs`
+ `autoscaling:VPCZoneIdentifiers`
+ `aws:RequestTag/`