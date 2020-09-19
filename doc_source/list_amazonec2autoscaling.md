# Actions, resources, and condition keys for Amazon EC2 Auto Scaling<a name="list_amazonec2autoscaling"></a>

Amazon EC2 Auto Scaling \(service prefix: `autoscaling`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/autoscaling/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AutoScaling/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/autoscaling/latest/userguide/IAM.html) permission policies\.

**Topics**
+ [Actions defined by Amazon EC2 Auto Scaling](#amazonec2autoscaling-actions-as-permissions)
+ [Resource types defined by Amazon EC2 Auto Scaling](#amazonec2autoscaling-resources-for-iam-policies)
+ [Condition keys for Amazon EC2 Auto Scaling](#amazonec2autoscaling-policy-keys)

## Actions defined by Amazon EC2 Auto Scaling<a name="amazonec2autoscaling-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2autoscaling.html)

## Resource types defined by Amazon EC2 Auto Scaling<a name="amazonec2autoscaling-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonec2autoscaling-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ autoScalingGroup ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-resources)  |  arn:$\{Partition\}:autoscaling:$\{Region\}:$\{Account\}:autoScalingGroup:$\{GroupId\}:autoScalingGroupName/$\{GroupFriendlyName\}  |   [ autoscaling:ResourceTag/$\{TagKey\} ](#amazonec2autoscaling-autoscaling_ResourceTag___TagKey_)   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2autoscaling-aws_ResourceTag___TagKey_)   | 
|   [ launchConfiguration ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-resources)  |  arn:$\{Partition\}:autoscaling:$\{Region\}:$\{Account\}:launchConfiguration:$\{Id\}:launchConfigurationName/$\{LaunchConfigurationName\}  |  | 

## Condition keys for Amazon EC2 Auto Scaling<a name="amazonec2autoscaling-policy-keys"></a>

Amazon EC2 Auto Scaling defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ autoscaling:ImageId ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The AMI used to create the instance\. | String | 
|   [ autoscaling:InstanceType ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The type of instance, in terms of the hardware resources available\. | String | 
|   [ autoscaling:InstanceTypes ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The types of instances, in terms of the hardware resources available\. | String | 
|   [ autoscaling:LaunchConfigurationName ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The name of a launch configuration\. | String | 
|   [ autoscaling:LaunchTemplateVersionSpecified ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | Filters access by whether users can specify any version of a launch template or only the Latest or Default version | Bool | 
|   [ autoscaling:LoadBalancerNames ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The name of the load balancer\. | String | 
|   [ autoscaling:MaxSize ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The maximum scaling size\. | Numeric | 
|   [ autoscaling:MetadataHttpEndpoint ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | Filters access by whether the HTTP endpoint is enabled for the instance metadata service\. | String | 
|   [ autoscaling:MetadataHttpPutResponseHopLimit ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | Filters access by the allowed number of hops when calling the instance metadata service\. | Numeric | 
|   [ autoscaling:MetadataHttpTokens ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | Filters access by whether tokens are required when calling the instance metadata service \(optional or required\) | String | 
|   [ autoscaling:MinSize ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The minimum scaling size\. | Numeric | 
|   [ autoscaling:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The value of a tag attached to a resource\. | String | 
|   [ autoscaling:SpotPrice ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The spot price associated with an instance\. | Numeric | 
|   [ autoscaling:TargetGroupARNs ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The ARN of a target group\. | ARN | 
|   [ autoscaling:VPCZoneIdentifiers ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The identifier of a VPC zone\. | String | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/autoscaling/latest/userguide/control-access-using-iam.html#policy-auto-scaling-condition-keys)  | The value of a tag associated with the request\. | String | 
|   aws:ResourceTag/$\{TagKey\}  | Filters actions based on tag\-value associated with the resource\. | String | 
|   aws:TagKeys  | Filters create requests based on the presence of mandatory tags in the request\. | String | 