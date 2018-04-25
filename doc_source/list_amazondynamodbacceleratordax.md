# Actions, Resources, and Condition Keys for Amazon DynamoDB Accelerator \(DAX\)<a name="list_amazondynamodbacceleratordax"></a>

Amazon DynamoDB Accelerator \(DAX\) \(service prefix: `dax`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon DynamoDB Accelerator \(DAX\)](#amazondynamodbacceleratordax-actions-as-permissions)
+ [Resources Defined by DynamoDBAccelerator](#amazondynamodbacceleratordax-resources-for-iam-policies)
+ [Condition Keys for Amazon DynamoDB Accelerator \(DAX\)](#amazondynamodbacceleratordax-policy-keys)

## Actions Defined by Amazon DynamoDB Accelerator \(DAX\)<a name="amazondynamodbacceleratordax-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [BatchGetItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_BatchGetItem.html) | The BatchGetItem action returns the attributes of one or more items from one or more tables\. |   | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [BatchWriteItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_BatchWriteItem.html) | The BatchWriteItem action operation puts or deletes multiple items in one or more tables\. |   | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [CreateCluster](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateCluster.html) | The CreateCluster action creates a DAX cluster\. |   |  |  |  | 
| [CreateParameterGroup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateParameterGroup.html) | The CreateParameterGroup action creates collection of parameters that you apply to all of the nodes in a DAX cluster\. |   |  |  |  | 
| [CreateSubnetGroup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateSubnetGroup.html) | The CreateSubnetGroup action creates a new subnet group\. |   |  |  |  | 
| [DecreaseReplicationFactor](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DecreaseReplicationFactor.html) | The DecreaseReplicationFactor action removes one or more nodes from a DAX cluster\. |   |  |  |  | 
| [DeleteCluster](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteCluster.html) | The DeleteCluster action deletes a previously provisioned DAX cluster\. |   |  |  |  | 
| [DeleteItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DeleteItem.html) | The DeleteItem action deletes a single item in a table by primary key\. |   | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [DeleteParameterGroup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteParameterGroup.html) | The DeleteParameterGroup action deletes the specified parameter group\. |   |  |  |  | 
| [DeleteSubnetGroup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteSubnetGroup.html) | The DeleteSubnetGroup action deletes a subnet group\. |   |  |  |  | 
| [DescribeClusters](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeClusters.html) | The DescribeClusters action returns information about all provisioned DAX clusters\. |   |  |  |  | 
| [DescribeDefaultParameters](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeDefaultParameters.html) | The DescribeDefaultParameters action returns the default system parameter information for DAX\. |   |  |  |  | 
| [DescribeEvents](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeEvents.html) | The DescribeEvents action returns events related to DAX clusters and parameter groups\. |   |  |  |  | 
| [DescribeParameterGroups](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeParameterGroups.html) | The DescribeParameterGroups action returns a list of parameter group descriptions\. |   |  |  |  | 
| [DescribeParameters](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeParameters.html) | The DescribeParameters action returns the detailed parameter list for a particular parameter group\. |   |  |  |  | 
| [DescribeSubnetGroups](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeSubnetGroups.html) | The DescribeSubnetGroups action returns a list of subnet group descriptions\. |   |  |  |  | 
| [DescribeTable](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeTable.html) | Returns information about the table |   | [application\*](#amazondynamodbacceleratordax-application)  |  |  | 
| [GetItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_GetItem.html) | The GetItem action returns a set of attributes for the item with the given primary key\. |   | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [IncreaseReplicationFactor](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_IncreaseReplicationFactor.html) | The IncreaseReplicationFactor action adds one or more nodes to a DAX cluster\. |   |  |  |  | 
| [ListTables](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_ListTables.html) | Returns information about the table |   | [application\*](#amazondynamodbacceleratordax-application)  |  |  | 
| [ListTags](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_ListTags.html) | The ListTags action returns a list all of the tags for a DAX cluster\. |   |  |  |  | 
| [PutItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_PutItem.html) | The PutItem action creates a new item, or replaces an old item with a new item\. |   | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [Query](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Query.html) | The Query action finds items based on primary key values\. You can query any table or secondary index that has a composite primary key \(a partition key and a sort key\)\. |   | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [RebootNode](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_RebootNode.html) | The RebootNode action reboots a single node of a DAX cluster\. |   |  |  |  | 
| [Scan](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Scan.html) | The Scan action returns one or more items and item attributes by accessing every item in a table or a secondary index\. |   | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [TagResource](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_TagResource.html) | The TagResource action associates a set of tags with a DAX resource\. |   |  |  |  | 
| [UntagResource](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UntagResource.html) | The UntagResource action removes the association of tags from a DAX resource\. |   |  |  |  | 
| [UpdateCluster](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateCluster.html) | The UpdateCluster action modifies the settings for a DAX cluster\. |   |  |  |  | 
| [UpdateItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_UpdateItem.html) | The UpdateItem action edits an existing item's attributes, or adds a new item to the table if it does not already exist\. |   | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [UpdateParameterGroup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateParameterGroup.html) | The UpdateParameterGroup action modifies the parameters of a parameter group\. |   |  |  |  | 
| [UpdateSubnetGroup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateSubnetGroup.html) | The UpdateSubnetGroup action modifies an existing subnet group\. |   |  |  |  | 

## Resources Defined by DynamoDBAccelerator<a name="amazondynamodbacceleratordax-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazondynamodbacceleratordax-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [application](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.access-control.html) | arn:$\{Partition\}:dax:$\{Region\}:$\{Account\}:cache/$\{ClusterName\} |  | 

## Condition Keys for Amazon DynamoDB Accelerator \(DAX\)<a name="amazondynamodbacceleratordax-policy-keys"></a>

DynamoDBAccelerator has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.