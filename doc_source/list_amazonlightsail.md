# Actions, resources, and condition keys for Amazon Lightsail<a name="list_amazonlightsail"></a>

Amazon Lightsail \(service prefix: `lightsail`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://lightsail.aws.amazon.com/ls/docs/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://lightsail.aws.amazon.com/ls/docs/how-to/article/create-policy-that-grants-access-to-amazon-lightsail) permission policies\.

**Topics**
+ [Actions defined by Amazon Lightsail](#amazonlightsail-actions-as-permissions)
+ [Resource types defined by Amazon Lightsail](#amazonlightsail-resources-for-iam-policies)
+ [Condition keys for Amazon Lightsail](#amazonlightsail-policy-keys)

## Actions defined by Amazon Lightsail<a name="amazonlightsail-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonlightsail.html)

## Resource types defined by Amazon Lightsail<a name="amazonlightsail-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonlightsail-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ Domain ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_Domain.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:Domain/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ Instance ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_Instance.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:Instance/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ InstanceSnapshot ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_InstanceSnapshot.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:InstanceSnapshot/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ KeyPair ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_KeyPair.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:KeyPair/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ StaticIp ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StaticIp.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:StaticIp/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ Disk ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_Disk.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:Disk/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ DiskSnapshot ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DiskSnapshot.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:DiskSnapshot/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ LoadBalancer ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_LoadBalancer.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:LoadBalancer/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ PeeredVpc ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/PeeredVpc.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:PeeredVpc/$\{Id\}  |  | 
|   [ LoadBalancerTlsCertificate ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/LoadBalancerTlsCertificate.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:LoadBalancerTlsCertificate/$\{Id\}  |  | 
|   [ ExportSnapshotRecord ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ExportSnapshotRecord.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:ExportSnapshotRecord/$\{Id\}  |  | 
|   [ CloudFormationStackRecord ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CloudFormationStackRecord.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:CloudFormationStackRecord/$\{Id\}  |  | 
|   [ RelationalDatabase ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_RelationalDatabase.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:RelationalDatabase/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 
|   [ RelationalDatabaseSnapshot ](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_RelationalDatabaseSnapshot.html)  |  arn:$\{Partition\}:lightsail:$\{Region\}:$\{Account\}:RelationalDatabaseSnapshot/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonlightsail-aws_ResourceTag___TagKey_)   | 

## Condition keys for Amazon Lightsail<a name="amazonlightsail-policy-keys"></a>

Amazon Lightsail defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of tag keys in the request | String | 