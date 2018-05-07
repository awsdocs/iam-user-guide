# Actions, Resources, and Condition Keys for AWS Elemental MediaLive<a name="list_awselementalmedialive"></a>

AWS Elemental MediaLive \(service prefix: `medialive`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com//medialive/latest/ug/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com//medialive/latest/apireference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com//medialive/latest/ug/IAM_policies.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Elemental MediaLive](#awselementalmedialive-actions-as-permissions)
+ [Resources Defined by MediaLive](#awselementalmedialive-resources-for-iam-policies)
+ [Condition Keys for AWS Elemental MediaLive](#awselementalmedialive-policy-keys)

## Actions Defined by AWS Elemental MediaLive<a name="awselementalmedialive-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [CreateChannel](http://docs.aws.amazon.com//medialive/latest/apireference/channels.html) | Create a medialive channel | Write |  |  |  | 
| [CreateInput](http://docs.aws.amazon.com//medialive/latest/apireference/inputs.html) | Create a medialive input | Write |  |  |  | 
| [CreateInputSecurityGroup](http://docs.aws.amazon.com//medialive/latest/apireference/inputsecuritygroups.html) | Create a medialive input security group | Write |  |  |  | 
| [DeleteChannel](http://docs.aws.amazon.com//medialive/latest/apireference/channels-channelid.html) | Delete a medialive channel | Write |  |  |  | 
| [DeleteInput](http://docs.aws.amazon.com//medialive/latest/apireference/inputs-inputid.html) | Delete a medialive input | Write |  |  |  | 
| [DeleteInputSecurityGroup](http://docs.aws.amazon.com//medialive/latest/apireference/inputsecuritygroups-inputsecuritygroupid.html) | Delete a medialive input security group | Write |  |  |  | 
| [DescribeChannel](http://docs.aws.amazon.com//medialive/latest/apireference/channels-channelid.html) | Get details about a medialive channel | Read |  |  |  | 
| [DescribeInput](http://docs.aws.amazon.com//medialive/latest/apireference/inputs-inputid.html) | Describe a medialive input | Read |  |  |  | 
| [DescribeInputSecurityGroup](http://docs.aws.amazon.com//medialive/latest/apireference/inputsecuritygroups-inputsecuritygroupid.html) | Describe a medialive input security group | Read |  |  |  | 
| [ListChannels](http://docs.aws.amazon.com//medialive/latest/apireference/channels.html) | List medialive channels | List |  |  |  | 
| [ListInputSecurityGroups](http://docs.aws.amazon.com//medialive/latest/apireference/inputsecuritygroups.html) | List medialive input security groups | List |  |  |  | 
| [ListInputs](http://docs.aws.amazon.com//medialive/latest/apireference/inputs.html) | List medialive inputs | List |  |  |  | 
| [StartChannel](http://docs.aws.amazon.com//medialive/latest/apireference/channels-channelid-start.html) | Start a medialive channel | Write |  |  |  | 
| [StopChannel](http://docs.aws.amazon.com//medialive/latest/apireference/channels-channelid-stop.html) | Stop a medialive channel | Write |  |  |  | 

## Resources Defined by MediaLive<a name="awselementalmedialive-resources-for-iam-policies"></a>

MediaLive has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Elemental MediaLive<a name="awselementalmedialive-policy-keys"></a>

MediaLive has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.