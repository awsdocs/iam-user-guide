# Actions, Resources, and Condition Keys for Amazon EC2 Auto Scaling<a name="list_amazonec2autoscaling"></a>

Amazon EC2 Auto Scaling \(service prefix: `autoscaling`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/autoscaling/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/AutoScaling/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/autoscaling/latest/userguide/IAM.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon EC2 Auto Scaling](#amazonec2autoscaling-actions-as-permissions)
+ [Resources Defined by EC2 Auto Scaling](#amazonec2autoscaling-resources-for-iam-policies)
+ [Condition Keys for Amazon EC2 Auto Scaling](#amazonec2autoscaling-policy-keys)

## Actions Defined by Amazon EC2 Auto Scaling<a name="amazonec2autoscaling-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2autoscaling.html)

## Resources Defined by EC2 Auto Scaling<a name="amazonec2autoscaling-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonec2autoscaling-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ autoScalingGroup ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-resources)  |  arn:$\{Partition\}:autoscaling:$\{Region\}:$\{Account\}:autoScalingGroup:$\{GroupId\}:autoScalingGroupName/$\{GroupFriendlyName\}  |   [ autoscaling:ResourceTag/tag\-key ](#amazonec2autoscaling-autoscaling_ResourceTag_tag-key)   | 
|   [ launchConfiguration ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-resources)  |  arn:$\{Partition\}:autoscaling:$\{Region\}:$\{Account\}:launchConfiguration:$\{Id\}:launchConfigurationName/$\{LaunchConfigurationName\}  |  | 

## Condition Keys for Amazon EC2 Auto Scaling<a name="amazonec2autoscaling-policy-keys"></a>

Amazon EC2 Auto Scaling defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ autoscaling:ImageId ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The AMI used to create the instance\. | String | 
|   [ autoscaling:InstanceType ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The type of instance, in terms of the hardware resources available\. | String | 
|   [ autoscaling:InstanceTypes ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The types of instances, in terms of the hardware resources available\. | String | 
|   [ autoscaling:LaunchConfigurationName ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The name of a launch configuration\. | String | 
|   [ autoscaling:LoadBalancerNames ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The name of the load balancer\. | String | 
|   [ autoscaling:MaxSize ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The maximum scaling size\. | Numeric | 
|   [ autoscaling:MinSize ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The minimum scaling size\. | Numeric | 
|   [ autoscaling:ResourceTag/tag\-key ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The value of a tag attached to a resource\. | String | 
|   [ autoscaling:SpotPrice ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The spot price associated with an instance\. | Numeric | 
|   [ autoscaling:TargetGroupARNs ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The ARN of a target group\. | ARN | 
|   [ autoscaling:VPCZoneIdentifiers ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The identifier of a VPC zone\. | String | 
|   [ aws:RequestTag/ ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The value of a tag associated with the request\. | String | 