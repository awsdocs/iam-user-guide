# Actions, resources, and condition keys for AWS IoT Greengrass<a name="list_awsiotgreengrass"></a>

AWS IoT Greengrass \(service prefix: `greengrass`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/greengrass/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/greengrass/latest/apireference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/greengrass/latest/developerguide/security_iam_service-with-iam.html) permission policies\.

**Topics**
+ [Actions defined by AWS IoT Greengrass](#awsiotgreengrass-actions-as-permissions)
+ [Resource types defined by AWS IoT Greengrass](#awsiotgreengrass-resources-for-iam-policies)
+ [Condition keys for AWS IoT Greengrass](#awsiotgreengrass-policy-keys)

## Actions defined by AWS IoT Greengrass<a name="awsiotgreengrass-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsiotgreengrass.html)

## Resource types defined by AWS IoT Greengrass<a name="awsiotgreengrass-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiotgreengrass-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ connectivityInfo ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-connectivityinfo.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/things/$\{ThingName\}/connectivityInfo  |  | 
|   artifact  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}/deployments/$\{DeploymentId\}/artifacts/lambda/$\{ArtifactId\}  |  | 
|   [ certificateAuthority ](https://docs.aws.amazon.com/greengrass/latest/developerguide/gg-sec.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}/certificateauthorities/$\{CertificateAuthorityId\}  |  | 
|   [ deployment ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-createdeploymentrequest.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}/deployments/$\{DeploymentId\}  |  | 
|   [ bulkDeployment ](https://docs.aws.amazon.com/greengrass/latest/developerguide/bulk-deploy-cli.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/bulk/deployments/$\{BulkDeploymentId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ group ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-groupinformation.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ groupVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-groupversion.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}/versions/$\{VersionId\}  |  | 
|   [ coreDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-core.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/cores/$\{CoreDefinitionId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ coreDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-coredefinitionversion.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/cores/$\{CoreDefinitionId\}/versions/$\{VersionId\}  |  | 
|   [ deviceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-device.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/devices/$\{DeviceDefinitionId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ deviceDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-devicedefinitionversion.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/devices/$\{DeviceDefinitionId\}/versions/$\{VersionId\}  |  | 
|   [ functionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-function.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/functions/$\{FunctionDefinitionId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ functionDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-functiondefinitionversion.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/functions/$\{FunctionDefinitionId\}/versions/$\{VersionId\}  |  | 
|   [ subscriptionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-subscription.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/subscriptions/$\{SubscriptionDefinitionId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ subscriptionDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-subscriptiondefinitionversion.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/subscriptions/$\{SubscriptionDefinitionId\}/versions/$\{VersionId\}  |  | 
|   [ loggerDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-logger.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/loggers/$\{LoggerDefinitionId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ loggerDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-loggerdefinitionversion.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/loggers/$\{LoggerDefinitionId\}/versions/$\{VersionId\}  |  | 
|   [ resourceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-resource.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/resources/$\{ResourceDefinitionId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ resourceDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-resourcedefinitionversion.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/resources/$\{ResourceDefinitionId\}/versions/$\{VersionId\}  |  | 
|   [ connectorDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-connector.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/connectors/$\{ConnectorDefinitionId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotgreengrass-aws_ResourceTag___TagKey_)   | 
|   [ connectorDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/definitions-connectordefinitionversion.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/connectors/$\{ConnectorDefinitionId\}/versions/$\{VersionId\}  |  | 
|   [ thing ](https://docs.aws.amazon.com/iot/latest/developerguide/thing-registry.html)  |  arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:thing/$\{ThingName\}  |  | 

## Condition keys for AWS IoT Greengrass<a name="awsiotgreengrass-policy-keys"></a>

AWS IoT Greengrass defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:CurrentTime ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters access by checking date/time conditions for the current date and time\. | Date | 
|   [ aws:EpochTime ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters access by checking date/time conditions for the current date and time in epoch or Unix time\. | Date | 
|   [ aws:MultiFactorAuthAge ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters access by checking how long ago \(in seconds\) the security credentials validated by multi\-factor authentication \(MFA\) in the request were issued using MFA\. | Numeric | 
|   [ aws:MultiFactorAuthPresent ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters access by checking whether multi\-factor authentication \(MFA\) was used to validate the temporary security credentials that made the current request\. | Boolean | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters create requests based on the allowed set of values for each of the mandatory tags\. | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters actions based on the tag value associated with the resource\. | String | 
|   [ aws:SecureTransport ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters access by checking whether the request was sent using SSL\. | Boolean | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters create requests based on the presence of mandatory tags in the request\. | String | 
|   [ aws:UserAgent ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-globally-available)  | Filters access by the requester's client application\. | String | 