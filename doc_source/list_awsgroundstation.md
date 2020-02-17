# Actions, Resources, and Condition Keys for AWS Ground Station<a name="list_awsgroundstation"></a>

AWS Ground Station \(service prefix: `groundstation`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/ground-station/latest/ug/introduction.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/ground-station/latest/APIReference/welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/ground-station/latest/ug/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Ground Station](#awsgroundstation-actions-as-permissions)
+ [Resource Types Defined by AWS Ground Station](#awsgroundstation-resources-for-iam-policies)
+ [Condition Keys for AWS Ground Station](#awsgroundstation-policy-keys)

## Actions Defined by AWS Ground Station<a name="awsgroundstation-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsgroundstation.html)

## Resource Types Defined by AWS Ground Station<a name="awsgroundstation-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsgroundstation-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ Config ](https://docs.aws.amazon.com/ground-station/latest/APIReference/API_ConfigListItem.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:config/$\{configType\}/$\{configId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsgroundstation-aws_ResourceTag___TagKey_)   [ groundstation:configId ](#awsgroundstation-groundstation_configId)   [ groundstation:configType ](#awsgroundstation-groundstation_configType)   | 
|   [ Contact ](https://docs.aws.amazon.com/ground-station/latest/APIReference/API_ContactData.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:contact/$\{contactId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsgroundstation-aws_ResourceTag___TagKey_)   [ groundstation:contactId ](#awsgroundstation-groundstation_contactId)   | 
|   [ DataflowEndpointGroup ](https://docs.aws.amazon.com/ground-station/latest/APIReference/API_DataflowEndpoint.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:dataflow\-endpoint\-group/$\{dataflowEndpointGroupId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsgroundstation-aws_ResourceTag___TagKey_)   [ groundstation:dataflowEndpointGroupId ](#awsgroundstation-groundstation_dataflowEndpointGroupId)   | 
|   [ GroundStationResource ](https://docs.aws.amazon.com/ground-station/latest/APIReference/API_GroundStationData.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:groundstation:$\{groundStationId\}  |   [ groundstation:groundStationId ](#awsgroundstation-groundstation_groundStationId)   | 
|   [ MissionProfile ](https://docs.aws.amazon.com/ground-station/latest/APIReference/API_MissionProfileListItem.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:mission\-profile/$\{missionProfileId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsgroundstation-aws_ResourceTag___TagKey_)   [ groundstation:missionProfileId ](#awsgroundstation-groundstation_missionProfileId)   | 
|   [ Satellite ](https://docs.aws.amazon.com/ground-station/latest/APIReference/API_SatelliteListItem.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:satellite/$\{satelliteId\}  |   [ groundstation:satelliteId ](#awsgroundstation-groundstation_satelliteId)   | 

## Condition Keys for AWS Ground Station<a name="awsgroundstation-policy-keys"></a>

AWS Ground Station defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   aws:RequestTag/$\{TagKey\}  | Filters access by a key that is present in the request the user makes to the Ground Station service\. | String | 
|   aws:ResourceTag/$\{TagKey\}  | Filters access by a tag key and value pair\. | String | 
|   aws:TagKeys  | Filters access by the list of all the tag key names present in the request the user makes to the Ground Station service\. | String | 
|   groundstation:configId  | Filters access by the ID of a config | String | 
|   groundstation:configType  | Filters access by the type of a config | String | 
|   groundstation:contactId  | Filters access by the ID of a contact | String | 
|   groundstation:dataflowEndpointGroupId  | Filters access by the ID of a dataflow endpoint group | String | 
|   groundstation:groundStationId  | Filters access by the ID of a ground station | String | 
|   groundstation:missionProfileId  | Filters access by the ID of a mission profile | String | 
|   groundstation:satelliteId  | Filters access by the ID of a satellite | String | 