# Actions, resources, and condition keys for AWS Marketplace Catalog<a name="list_awsmarketplacecatalog"></a>

AWS Marketplace Catalog \(service prefix: `aws-marketplace`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_Operations.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/marketplace-catalog/latest/api-reference/api-access-control.html) permission policies\.

**Topics**
+ [Actions defined by AWS Marketplace Catalog](#awsmarketplacecatalog-actions-as-permissions)
+ [Resource types defined by AWS Marketplace Catalog](#awsmarketplacecatalog-resources-for-iam-policies)
+ [Condition keys for AWS Marketplace Catalog](#awsmarketplacecatalog-policy-keys)

## Actions defined by AWS Marketplace Catalog<a name="awsmarketplacecatalog-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CancelChangeSet ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_Operations.htmlAPI_CancelChangeSet.html)  | Cancels a running change set\. | Write |  |  |  | 
|   CompleteTask  | Complete an existing task and submit the content to the associated change\. | Write |  |  |  | 
|   [ DescribeChangeSet ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_Operations.htmlAPI_DescribeChangeSet.html)  | Returns the details of an existing change set\. | Read |  |  |  | 
|   [ DescribeEntity ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_Operations.htmlAPI_DescribeEntity.html)  | Returns the details of an existing entity\. | Read |  |  |  | 
|   DescribeTask  | Returns the details of an existing task\. | Read |  |  |  | 
|   [ ListChangeSets ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_Operations.htmlAPI_ListChangeSets.html)  | Lists existing change sets\. | Read |  |  |  | 
|   [ ListEntities ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_Operations.htmlAPI_ListEntities.html)  | Lists existing entities\. | Read |  |  |  | 
|   ListTasks  | Lists existing tasks\. | List |  |  |  | 
|   [ StartChangeSet ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_Operations.htmlAPI_StartChangeSet.html)  | Requests a new change set\. | Write |  |   [ catalog:ChangeType ](#awsmarketplacecatalog-catalog_ChangeType)   |  | 
|   UpdateTask  | Update the content of an existing task\. | Write |  |  |  | 

## Resource types defined by AWS Marketplace Catalog<a name="awsmarketplacecatalog-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsmarketplacecatalog-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ Entity ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_DescribeEntity.html#API_DescribeEntity_ResponseSyntax)  |  arn:$\{Partition\}:aws\-marketplace:$\{Region\}:$\{Account\}:$\{Catalog\}/$\{EntityType\}/$\{ResourceId\}  |  | 
|   [ ChangeSet ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/API_StartChangeSet.html#API_StartChangeSet_ResponseSyntax)  |  arn:$\{Partition\}:aws\-marketplace:$\{Region\}:$\{Account\}:$\{Catalog\}/ChangeSet/$\{ResourceId\}  |  | 

## Condition keys for AWS Marketplace Catalog<a name="awsmarketplacecatalog-policy-keys"></a>

AWS Marketplace Catalog defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ catalog:ChangeType ](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/api-access-control.html)  | Enables you to verify change type in the StartChangeSet request\. | String | 