# Actions, resources, and condition keys for AWS Elemental MediaStore<a name="list_awselementalmediastore"></a>

AWS Elemental MediaStore \(service prefix: `mediastore`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/mediastore/latest/ug/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/mediastore/latest/apireference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/mediastore/latest/ug/IAM-user-create.html) permission policies\.

**Topics**
+ [Actions defined by AWS Elemental MediaStore](#awselementalmediastore-actions-as-permissions)
+ [Resource types defined by AWS Elemental MediaStore](#awselementalmediastore-resources-for-iam-policies)
+ [Condition keys for AWS Elemental MediaStore](#awselementalmediastore-policy-keys)

## Actions defined by AWS Elemental MediaStore<a name="awselementalmediastore-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateContainer ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_CreateContainer.html)  | Grants permission to create containers\. | Write |  |  |  | 
|   [ DeleteContainer ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_DeleteContainer.html)  | Grants permission to delete any container in the current account\. | Write |  |  |  | 
|   [ DeleteContainerPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_DeleteContainerPolicy.html)  | Grants permission to delete the access policy of any container in the current account\. | Permissions management |  |  |  | 
|   [ DeleteCorsPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_DeleteCorsPolicy.html)  | Grants permission to delete the CORS policy from any container in the current account\. | Write |  |  |  | 
|   [ DeleteLifecyclePolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_DeleteLifecyclePolicy.html)  | Grants permission to delete the lifecycle policy from any container in the current account\. | Write |  |  |  | 
|   [ DeleteMetricPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_DeleteMetricPolicy.html)  | Grants permission to delete the metric policy from any container in the current account\. | Write |  |  |  | 
|   [ DeleteObject ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_objstore_DeleteObject.html)  | Grants permission to delete objects\. | Write |  |  |  | 
|   [ DescribeContainer ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_DescribeContainer.html)  | Grants permission to retrieve details on any container in the current account\. | List |  |  |  | 
|   [ DescribeObject ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_objstore_DescribeObject.html)  | Grants permission to retrieve object metadata\. | List |  |  |  | 
|   [ GetContainerPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_GetContainerPolicy.html)  | Grants permission to retrieve the access policy of any container in the current account\. | Read |  |  |  | 
|   [ GetCorsPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_GetCorsPolicy.html)  | Grants permission to retrieve the CORS policy of any container in the current account\. | Read |  |  |  | 
|   [ GetLifecyclePolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_GetLifecyclePolicy.html)  | Grants permission to retrieve the lifecycle policy that is assigned to any container in the current account\. | Read |  |  |  | 
|   [ GetMetricPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_GetMetricPolicy.html)  | Grants permission to retrieve the metric policy that is assigned to any container in the current account\. | Read |  |  |  | 
|   [ GetObject ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_objstore_GetObject.html)  | Grants permission to retrieve objects\. | Read |  |  |  | 
|   [ ListContainers ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_ListContainers.html)  | Grants permission to retrieve a list of containers in the current account\. | List |  |  |  | 
|   [ ListItems ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_objstore_ListItems.html)  | Grants permission to retrieve a list of objects and folders in the current account\. | List |  |  |  | 
|   [ ListTagsForResource ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_ListTagsForResource.html)  | Grants permission to list tags on any container in the current account\. | Read |  |  |  | 
|   [ PutContainerPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_PutContainerPolicy.html)  | Grants permission to create or replace the access policy of any container in the current account\. | Permissions management |  |  |  | 
|   [ PutCorsPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_PutCorsPolicy.html)  | Grants permission to add or modify the CORS policy of any container in the current account\. | Write |  |  |  | 
|   [ PutLifecyclePolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_PutLifecyclePolicy.html)  | Grants permission to add or modify the lifecycle policy that is assigned to any container in the current account\. | Write |  |  |  | 
|   [ PutMetricPolicy ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_PutMetricPolicy.html)  | Grants permission to add or modify the metric policy that is assigned to any container in the current account\. | Write |  |  |  | 
|   [ PutObject ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_objstore_PutObject.html)  | Grants permission to upload objects\. | Write |  |  |  | 
|   [ StartAccessLogging ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_StartAccessLogging.html)  | Grants permission to enable access logging on any container in the current account\. | Write |  |  |  | 
|   [ StopAccessLogging ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_StopAccessLogging.html)  | Grants permission to disable access logging on any container in the current account\. | Write |  |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_TagResource.html)  | Grants permission to add tags to any container in the current account\. | Tagging |  |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/mediastore/latest/apireference/API_UntagResource.html)  | Grants permission to remove tags from any container in the current account\. | Tagging |  |  |  | 

## Resource types defined by AWS Elemental MediaStore<a name="awselementalmediastore-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awselementalmediastore-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ container ](https://docs.aws.amazon.com/mediastore/latest/ug/containers.html)  |  arn:$\{Partition\}:mediastore:$\{Region\}:$\{Account\}:container/$\{ContainerName\}  |  | 

## Condition keys for AWS Elemental MediaStore<a name="awselementalmediastore-policy-keys"></a>

MediaStore has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.