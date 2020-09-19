# Actions, resources, and condition keys for AWS IoT SiteWise<a name="list_awsiotsitewise"></a>

AWS IoT SiteWise \(service prefix: `iotsitewise`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/iot-sitewise/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/security-iam.html) permission policies\.

**Topics**
+ [Actions defined by AWS IoT SiteWise](#awsiotsitewise-actions-as-permissions)
+ [Resource types defined by AWS IoT SiteWise](#awsiotsitewise-resources-for-iam-policies)
+ [Condition keys for AWS IoT SiteWise](#awsiotsitewise-policy-keys)

## Actions defined by AWS IoT SiteWise<a name="awsiotsitewise-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsiotsitewise.html)

## Resource types defined by AWS IoT SiteWise<a name="awsiotsitewise-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiotsitewise-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ asset ](https://docs.aws.amazon.com/iot-sitewise/latest/APIReference/API_CreateAsset.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:asset/$\{AssetId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotsitewise-aws_ResourceTag___TagKey_)   | 
|   [ asset\-model ](https://docs.aws.amazon.com/iot-sitewise/latest/APIReference/API_CreateAssetModel.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:asset\-model/$\{AssetModelId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotsitewise-aws_ResourceTag___TagKey_)   | 
|   [ gateway ](https://docs.aws.amazon.com/iot-sitewise/latest/APIReference/API_CreateGateway.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:gateway/$\{GatewayId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotsitewise-aws_ResourceTag___TagKey_)   | 
|   [ portal ](https://docs.aws.amazon.com/iot-sitewise/latest/APIReference/API_CreatePortal.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:portal/$\{PortalId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotsitewise-aws_ResourceTag___TagKey_)   | 
|   [ project ](https://docs.aws.amazon.com/iot-sitewise/latest/APIReference/API_CreateProject.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:project/$\{ProjectId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotsitewise-aws_ResourceTag___TagKey_)   | 
|   [ dashboard ](https://docs.aws.amazon.com/iot-sitewise/latest/APIReference/API_CreateDashboard.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:dashboard/$\{DashboardId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotsitewise-aws_ResourceTag___TagKey_)   | 
|   [ access\-policy ](https://docs.aws.amazon.com/iot-sitewise/latest/APIReference/API_CreateAccessPolicy.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:access\-policy/$\{AccessPolicyId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsiotsitewise-aws_ResourceTag___TagKey_)   | 

## Condition keys for AWS IoT SiteWise<a name="awsiotsitewise-policy-keys"></a>

AWS IoT SiteWise defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters access by the tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters access by the tags attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions by the tag keys in the request | String | 
|   [ iotsitewise:assetHierarchyPath ](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/security_iam_service-with-iam.html#security_iam_service-with-iam-id-based-policies-conditionkeys)  | Filters access by an asset hierarchy path, which is the string of asset IDs in the asset's hierarchy, each separated by a forward slash | String | 
|   [ iotsitewise:childAssetId ](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/security_iam_service-with-iam.html#security_iam_service-with-iam-id-based-policies-conditionkeys)  | Filters access by the ID of a child asset being associated to a parent asset | String | 
|   [ iotsitewise:group ](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/security_iam_service-with-iam.html#security_iam_service-with-iam-id-based-policies-conditionkeys)  | Filters access by the ID of an AWS Single Sign\-On group | String | 
|   [ iotsitewise:portal ](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/security_iam_service-with-iam.html#security_iam_service-with-iam-id-based-policies-conditionkeys)  | Filters access by the ID of a portal | String | 
|   [ iotsitewise:project ](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/security_iam_service-with-iam.html#security_iam_service-with-iam-id-based-policies-conditionkeys)  | Filters access by the ID of a project | String | 
|   [ iotsitewise:propertyId ](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/security_iam_service-with-iam.html#security_iam_service-with-iam-id-based-policies-conditionkeys)  | Filters access by the ID of an asset property | String | 
|   [ iotsitewise:user ](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/security_iam_service-with-iam.html#security_iam_service-with-iam-id-based-policies-conditionkeys)  | Filters access by the ID of an AWS Single Sign\-On user | String | 