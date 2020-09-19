# Actions, resources, and condition keys for AWS IoT<a name="list_awsiot"></a>

AWS IoT \(service prefix: `iot`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/iot/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/iot/latest/apireference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/iot/latest/developerguide/authorization.html) permission policies\.

**Topics**
+ [Actions defined by AWS IoT](#awsiot-actions-as-permissions)
+ [Resource types defined by AWS IoT](#awsiot-resources-for-iam-policies)
+ [Condition keys for AWS IoT](#awsiot-policy-keys)

## Actions defined by AWS IoT<a name="awsiot-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsiot.html)

## Resource types defined by AWS IoT<a name="awsiot-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiot-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ client ](https://docs.aws.amazon.com/iot/latest/developerguide/iot-message-broker.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:client/$\{ClientId\}  |  | 
|   [ index ](https://docs.aws.amazon.com/iot/latest/developerguide/iot-indexing.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:index/$\{IndexName\}  |  | 
|   [ job ](https://docs.aws.amazon.com/iot/latest/developerguide/iot-jobs.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:job/$\{JobId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ tunnel ](https://docs.aws.amazon.com/iot/latest/developerguide/iot-tunnels.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:tunnel/$\{TunnelId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ thing ](https://docs.aws.amazon.com/iot/latest/developerguide/thing-registry.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:thing/$\{ThingName\}  |  | 
|   [ thinggroup ](https://docs.aws.amazon.com/iot/latest/developerguide/thing-groups.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:thinggroup/$\{ThingGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ billinggroup ](https://docs.aws.amazon.com/iot/latest/developerguide/billing-groups.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:billinggroup/$\{BillingGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ dynamicthinggroup ](https://docs.aws.amazon.com/iot/latest/developerguide/dynamic-thing-groups.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:thinggroup/$\{ThingGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ thingtype ](https://docs.aws.amazon.com/iot/latest/developerguide/thing-types.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:thingtype/$\{ThingTypeName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ topic ](https://docs.aws.amazon.com/iot/latest/developerguide/iot-message-broker.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:topic/$\{TopicName\}  |  | 
|   [ topicfilter ](https://docs.aws.amazon.com/iot/latest/developerguide/topics.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:topicfilter/$\{TopicFilter\}  |  | 
|   [ rolealias ](https://docs.aws.amazon.com/iot/latest/developerguide/authorizing-direct-aws.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:rolealias/$\{RoleAlias\}  |  | 
|   [ authorizer ](https://docs.aws.amazon.com/iot/latest/developerguide/custom-authorizer.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:authorizer/$\{AuthorizerName\}  |  | 
|   [ policy ](https://docs.aws.amazon.com/iot/latest/developerguide/iot-policies.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:policy/$\{PolicyName\}  |  | 
|   [ cert ](https://docs.aws.amazon.com/iot/latest/developerguide/x509-certs.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:cert/$\{Certificate\}  |  | 
|   [ cacert ](https://docs.aws.amazon.com/iot/latest/developerguide/x509-certs.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:cacert/$\{CACertificate\}  |  | 
|   [ stream ](https://docs.aws.amazon.com/freertos/latest/userguide/freertos-ota-dev.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:stream/$\{streamId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ otaupdate ](https://docs.aws.amazon.com/freertos/latest/userguide/freertos-ota-dev.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:otaupdate/$\{otaUpdateId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ scheduledaudit ](https://docs.aws.amazon.com/iot/latest/developerguide/device-defender-audit.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:scheduledaudit/$\{ScheduleName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ mitigationaction ](https://docs.aws.amazon.com/iot/latest/developerguide/device-defender-mitigation-actions.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:mitigationaction/$\{MitigationActionName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ securityprofile ](https://docs.aws.amazon.com/iot/latest/developerguide/device-defender-detect.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:securityprofile/$\{SecurityProfileName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ dimension ](https://docs.aws.amazon.com/iot/latest/developerguide/device-defender-detect.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:dimension/$\{DimensionName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ rule ](https://docs.aws.amazon.com/iot/latest/developerguide/iot-rules.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:rule/$\{ruleName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiot-aws_ResourceTag___TagKey_)   | 
|   [ provisioningtemplate ](https://docs.aws.amazon.com/iot/latest/developerguide/provision-template.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:provisioningtemplate/$\{provisioningTemplate\}  |  | 

## Condition keys for AWS IoT<a name="awsiot-policy-keys"></a>

AWS IoT defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   aws:RequestTag/$\{TagKey\}  | A tag key that is present in the request that the user makes to IoT\. | String | 
|   aws:ResourceTag/$\{TagKey\}  | The tag key component of a tag attached to an IoT resource\. | String | 
|   aws:TagKeys  | The list of all the tag key names associated with the resource in the request\. | String | 
|   iot:Delete  | The flag indicating whether or not to also delete an IoT Tunnel immediately | Bool | 
|   iot:ThingGroupArn  | The list of all IoT Thing Group ARNs that the destination IoT Thing belongs to for an IoT Tunnel | String | 
|   iot:TunnelDestinationService  | The list of all destination services for an IoT Tunnel | String | 