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
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_BatchGetItem.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_BatchGetItem.html) | The BatchGetItem action returns the attributes of one or more items from one or more tables\. | Read | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_BatchWriteItem.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_BatchWriteItem.html) | The BatchWriteItem action operation puts or deletes multiple items in one or more tables\. | Write | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateCluster.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateCluster.html) | The CreateCluster action creates a DAX cluster\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateParameterGroup.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateParameterGroup.html) | The CreateParameterGroup action creates collection of parameters that you apply to all of the nodes in a DAX cluster\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateSubnetGroup.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_CreateSubnetGroup.html) | The CreateSubnetGroup action creates a new subnet group\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DecreaseReplicationFactor.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DecreaseReplicationFactor.html) | The DecreaseReplicationFactor action removes one or more nodes from a DAX cluster\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteCluster.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteCluster.html) | The DeleteCluster action deletes a previously provisioned DAX cluster\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DeleteItem.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DeleteItem.html) | The DeleteItem action deletes a single item in a table by primary key\. | Write | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteParameterGroup.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteParameterGroup.html) | The DeleteParameterGroup action deletes the specified parameter group\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteSubnetGroup.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DeleteSubnetGroup.html) | The DeleteSubnetGroup action deletes a subnet group\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeClusters.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeClusters.html) | The DescribeClusters action returns information about all provisioned DAX clusters\. | List |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeDefaultParameters.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeDefaultParameters.html) | The DescribeDefaultParameters action returns the default system parameter information for DAX\. | List |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeEvents.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeEvents.html) | The DescribeEvents action returns events related to DAX clusters and parameter groups\. | List |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeParameterGroups.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeParameterGroups.html) | The DescribeParameterGroups action returns a list of parameter group descriptions\. | List |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeParameters.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeParameters.html) | The DescribeParameters action returns the detailed parameter list for a particular parameter group\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeSubnetGroups.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_DescribeSubnetGroups.html) | The DescribeSubnetGroups action returns a list of subnet group descriptions\. | List |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeTable.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeTable.html) | Returns information about the table | Read | [application\*](#amazondynamodbacceleratordax-application)  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_GetItem.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_GetItem.html) | The GetItem action returns a set of attributes for the item with the given primary key\. | Read | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_IncreaseReplicationFactor.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_IncreaseReplicationFactor.html) | The IncreaseReplicationFactor action adds one or more nodes to a DAX cluster\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_ListTables.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_ListTables.html) | Returns information about the table | List | [application\*](#amazondynamodbacceleratordax-application)  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_ListTags.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_ListTags.html) | The ListTags action returns a list all of the tags for a DAX cluster\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_PutItem.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_PutItem.html) | The PutItem action creates a new item, or replaces an old item with a new item\. | Write | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Query.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Query.html) | The Query action finds items based on primary key values\. You can query any table or secondary index that has a composite primary key \(a partition key and a sort key\)\. | Read | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_RebootNode.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_RebootNode.html) | The RebootNode action reboots a single node of a DAX cluster\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Scan.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Scan.html) | The Scan action returns one or more items and item attributes by accessing every item in a table or a secondary index\. | Read | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_TagResource.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_TagResource.html) | The TagResource action associates a set of tags with a DAX resource\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UntagResource.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UntagResource.html) | The UntagResource action removes the association of tags from a DAX resource\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateCluster.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateCluster.html) | The UpdateCluster action modifies the settings for a DAX cluster\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_UpdateItem.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_UpdateItem.html) | The UpdateItem action edits an existing item's attributes, or adds a new item to the table if it does not already exist\. | Write | [application\*](#amazondynamodbacceleratordax-application)  |  | dynamodb:DescribeTable  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateParameterGroup.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateParameterGroup.html) | The UpdateParameterGroup action modifies the parameters of a parameter group\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateSubnetGroup.html](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_dax_UpdateSubnetGroup.html) | The UpdateSubnetGroup action modifies an existing subnet group\. | Write |  |  |  | 

## Resources Defined by DynamoDBAccelerator<a name="amazondynamodbacceleratordax-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazondynamodbacceleratordax-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.access-control.html](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.access-control.html) | arn:$\{Partition\}:dax:$\{Region\}:$\{Account\}:cache/$\{ClusterName\} |  | 

## Condition Keys for Amazon DynamoDB Accelerator \(DAX\)<a name="amazondynamodbacceleratordax-policy-keys"></a>

DynamoDBAccelerator has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.