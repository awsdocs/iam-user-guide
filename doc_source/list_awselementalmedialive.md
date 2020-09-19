# Actions, resources, and condition keys for AWS Elemental MediaLive<a name="list_awselementalmedialive"></a>

AWS Elemental MediaLive \(service prefix: `medialive`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/medialive/latest/ug/what-is.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/medialive/latest/ug/welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/medialive/latest/ug/IAM_policies.html) permission policies\.

**Topics**
+ [Actions defined by AWS Elemental MediaLive](#awselementalmedialive-actions-as-permissions)
+ [Resource types defined by AWS Elemental MediaLive](#awselementalmedialive-resources-for-iam-policies)
+ [Condition keys for AWS Elemental MediaLive](#awselementalmedialive-policy-keys)

## Actions defined by AWS Elemental MediaLive<a name="awselementalmedialive-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awselementalmedialive.html)

## Resource types defined by AWS Elemental MediaLive<a name="awselementalmedialive-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awselementalmedialive-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ channel ](https://docs.aws.amazon.com/medialive/latest/ug/channels.html)  |  arn:$\{Partition\}:medialive:$\{Region\}:$\{Account\}:channel:\*  |   [ aws:ResourceTag/$\{TagKey\} ](#awselementalmedialive-aws_ResourceTag___TagKey_)   | 
|   [ input ](https://docs.aws.amazon.com/medialive/latest/ug/inputs.html)  |  arn:$\{Partition\}:medialive:$\{Region\}:$\{Account\}:input:\*  |   [ aws:ResourceTag/$\{TagKey\} ](#awselementalmedialive-aws_ResourceTag___TagKey_)   | 
|   [ input\-device ](https://docs.aws.amazon.com/medialive/latest/ug/inputdevices.html)  |  arn:$\{Partition\}:medialive:$\{Region\}:$\{Account\}:inputDevice:\*  |  | 
|   [ input\-security\-group ](https://docs.aws.amazon.com/medialive/latest/ug/inputsecuritygroups.html)  |  arn:$\{Partition\}:medialive:$\{Region\}:$\{Account\}:inputSecurityGroup:\*  |   [ aws:ResourceTag/$\{TagKey\} ](#awselementalmedialive-aws_ResourceTag___TagKey_)   | 
|   [ multiplex ](https://docs.aws.amazon.com/medialive/latest/ug/multiplexes.html)  |  arn:$\{Partition\}:medialive:$\{Region\}:$\{Account\}:multiplex:\*  |   [ aws:ResourceTag/$\{TagKey\} ](#awselementalmedialive-aws_ResourceTag___TagKey_)   | 
|   [ reservation ](https://docs.aws.amazon.com/medialive/latest/ug/reservations.html)  |  arn:$\{Partition\}:medialive:$\{Region\}:$\{Account\}:reservation:\*  |   [ aws:ResourceTag/$\{TagKey\} ](#awselementalmedialive-aws_ResourceTag___TagKey_)   | 
|   [ offering ](https://docs.aws.amazon.com/medialive/latest/ug/input-output-reservations.html)  |  arn:$\{Partition\}:medialive:$\{Region\}:$\{Account\}:offering:\*  |  | 

## Condition keys for AWS Elemental MediaLive<a name="awselementalmedialive-policy-keys"></a>

AWS Elemental MediaLive defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/medialive/latest/ug/tagging.html)  | The tag for a MediaLive request\. | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/medialive/latest/ug/tagging.html)  | The tag for a MediaLive resource\. | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/medialive/latest/ug/tagging.html)  | The tag keys for a MediaLive resource or request\. | String | 