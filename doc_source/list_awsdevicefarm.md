# Actions, resources, and condition keys for AWS Device Farm<a name="list_awsdevicefarm"></a>

AWS Device Farm \(service prefix: `devicefarm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/devicefarm/latest/developerguide/welcome.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Operations.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/devicefarm/latest/developerguide/permissions.html) permission policies\.

**Topics**
+ [Actions defined by AWS Device Farm](#awsdevicefarm-actions-as-permissions)
+ [Resource types defined by AWS Device Farm](#awsdevicefarm-resources-for-iam-policies)
+ [Condition keys for AWS Device Farm](#awsdevicefarm-policy-keys)

## Actions defined by AWS Device Farm<a name="awsdevicefarm-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsdevicefarm.html)

## Resource types defined by AWS Device Farm<a name="awsdevicefarm-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsdevicefarm-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ project ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Project.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:project:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ run ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Run.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:run:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ job ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Job.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:job:$\{ResourceId\}  |  | 
|   [ suite ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Suite.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:suite:$\{ResourceId\}  |  | 
|   [ test ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Test.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:test:$\{ResourceId\}  |  | 
|   [ upload ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Upload.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:upload:$\{ResourceId\}  |  | 
|   [ artifact ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Artifact.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:artifact:$\{ResourceId\}  |  | 
|   [ sample ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Sample.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:sample:$\{ResourceId\}  |  | 
|   [ networkprofile ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_NetworkProfile.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:networkprofile:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ deviceinstance ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeviceInstance.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}::deviceinstance:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ session ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_RemoteAccessSession.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:session:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ devicepool ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DevicePool.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:devicepool:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ device ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_Device.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}::device:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ instanceprofile ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_InstanceProfile.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:instanceprofile:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ vpceconfiguration ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_VPCEConfiguration.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:vpceconfiguration:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ testgrid\-project ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_TestGridProject.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:testgrid\-project:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 
|   [ testgrid\-session ](https://docs.aws.amazon.com/devicefarm/latest/APIReference/API_TestGridSession.html)  |  arn:$\{Partition\}:devicefarm:$\{Region\}:$\{Account\}:testgrid\-session:$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsdevicefarm-aws_ResourceTag___TagKey_)   | 

## Condition keys for AWS Device Farm<a name="awsdevicefarm-policy-keys"></a>

AWS Device Farm defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the allowed set of values for each of the tags | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag\-value assoicated with the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of mandatory tags in the request | String | 