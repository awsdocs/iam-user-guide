# Actions, Resources, and Condition Keys for AWS Ground Station<a name="list_awsgroundstation"></a>

AWS Ground Station \(service prefix: `groundstation`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/ground-station/latest/ug/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/ground-station/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/ground-station/latest/ug/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Ground Station](#awsgroundstation-actions-as-permissions)
+ [Resources Defined by Ground Station](#awsgroundstation-resources-for-iam-policies)
+ [Condition Keys for AWS Ground Station](#awsgroundstation-policy-keys)

## Actions Defined by AWS Ground Station<a name="awsgroundstation-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsgroundstation.html)

## Resources Defined by Ground Station<a name="awsgroundstation-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsgroundstation-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ Config ](https://docs.aws.amazon.com/ground-station/latest/ug/resources/API_Config.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:config/$\{configType\}/$\{configId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsgroundstation-aws_ResourceTag___TagKey_)   [ groundstation:configId ](#awsgroundstation-groundstation_configId)   [ groundstation:configType ](#awsgroundstation-groundstation_configType)   | 
|   [ Contact ](https://docs.aws.amazon.com/ground-station/latest/ug/resources/API_Contact.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:contact/$\{contactId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsgroundstation-aws_ResourceTag___TagKey_)   [ groundstation:contactId ](#awsgroundstation-groundstation_contactId)   | 
|   [ DataflowEndpointGroup ](https://docs.aws.amazon.com/ground-station/latest/ug/resources/API_DataflowEndpointGroup.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:dataflow\-endpoint\-group/$\{dataflowEndpointGroupId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsgroundstation-aws_ResourceTag___TagKey_)   [ groundstation:dataflowEndpointGroupId ](#awsgroundstation-groundstation_dataflowEndpointGroupId)   | 
|   [ GroundStationResource ](https://docs.aws.amazon.com/ground-station/latest/ug/resources/API_GroundStationResource.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:groundstation:$\{groundStationId\}  |   [ groundstation:groundStationId ](#awsgroundstation-groundstation_groundStationId)   | 
|   [ MissionProfile ](https://docs.aws.amazon.com/ground-station/latest/ug/resources/API_MissionProfile.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:mission\-profile/$\{missionProfileId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsgroundstation-aws_ResourceTag___TagKey_)   [ groundstation:missionProfileId ](#awsgroundstation-groundstation_missionProfileId)   | 
|   [ Satellite ](https://docs.aws.amazon.com/ground-station/latest/ug/resources/API_Satellite.html)  |  arn:$\{Partition\}:groundstation:$\{Region\}:$\{Account\}:satellite/$\{satelliteId\}  |   [ groundstation:satelliteId ](#awsgroundstation-groundstation_satelliteId)   | 

## Condition Keys for AWS Ground Station<a name="awsgroundstation-policy-keys"></a>

AWS Ground Station defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   aws:RequestTag/$\{TagKey\}  |  | String | 
|   aws:ResourceTag/$\{TagKey\}  |  | String | 
|   aws:TagKeys  |  | String | 
|   groundstation:configId  |  | String | 
|   groundstation:configType  |  | String | 
|   groundstation:contactId  |  | String | 
|   groundstation:dataflowEndpointGroupId  |  | String | 
|   groundstation:groundStationId  |  | String | 
|   groundstation:missionProfileId  |  | String | 
|   groundstation:satelliteId  |  | String | 