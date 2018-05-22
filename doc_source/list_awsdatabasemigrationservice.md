# Actions, Resources, and Condition Keys for AWS Database Migration Service<a name="list_awsdatabasemigrationservice"></a>

AWS Database Migration Service \(service prefix: `dms`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/dms/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/dms/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/dms/latest/userguide/CHAP_Security.IAMPermissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Database Migration Service](#awsdatabasemigrationservice-actions-as-permissions)
+ [Resources Defined by DMS](#awsdatabasemigrationservice-resources-for-iam-policies)
+ [Condition Keys for AWS Database Migration Service](#awsdatabasemigrationservice-policy-keys)

## Actions Defined by AWS Database Migration Service<a name="awsdatabasemigrationservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_AddTagsToResource.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_AddTagsToResource.html) | Adds metadata tags to a DMS resource, including replication instance, endpoint, security group, and migration task | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_CreateEndpoint.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_CreateEndpoint.html) | Creates an endpoint using the provided settings | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_CreateReplicationInstance.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_CreateReplicationInstance.html) | Creates the replication instance using the specified parameters | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_CreateReplicationSubnetGroup.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_CreateReplicationSubnetGroup.html) | Creates a replication subnet group given a list of the subnet IDs in a VPC | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_CreateReplicationTask.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_CreateReplicationTask.html) | Creates a replication task using the specified parameters | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteEndpoint.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteEndpoint.html) | Deletes the specified endpoint | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteEventSubscription.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteEventSubscription.html) | Deletes an AWS DMS event subscription\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteReplicationInstance.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteReplicationInstance.html) | Deletes the specified replication instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteReplicationSubnetGroup.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteReplicationSubnetGroup.html) | Deletes a subnet group | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteReplicationTask.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DeleteReplicationTask.html) | Deletes the specified replication task | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeAccountAttributes.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeAccountAttributes.html) | Lists all of the AWS DMS attributes for a customer account | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeCertificates.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeCertificates.html) | Provides a description of the certificate\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeConnections.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeConnections.html) | Describes the status of the connections that have been made between the replication instance and an endpoint | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEndpointTypes.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEndpointTypes.html) | Returns information about the type of endpoints available | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEndpoints.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEndpoints.html) | Returns information about the endpoints for your account in the current region | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEventCategories.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEventCategories.html) | Lists categories for all event source types, or, if specified, for a specified source type\.  | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEventSubscriptions.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEventSubscriptions.html) | Lists all the event subscriptions for a customer account\.  | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEvents.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeEvents.html) | Lists events for a given source identifier and source type\.  | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeOrderableReplicationInstances.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeOrderableReplicationInstances.html) | Returns information about the replication instance types that can be created in the specified region | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeRefreshSchemasStatus.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeRefreshSchemasStatus.html) | Returns the status of the RefreshSchemas operation | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeReplicationInstances.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeReplicationInstances.html) | Returns information about replication instances for your account in the current region | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeReplicationSubnetGroups.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeReplicationSubnetGroups.html) | Returns information about the replication subnet groups | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeReplicationTasks.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeReplicationTasks.html) | Returns information about replication tasks for your account in the current region | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeSchemas.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeSchemas.html) | Returns information about the schema for the specified endpoint | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeTableStatistics.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_DescribeTableStatistics.html) | Returns table statistics on the database migration task, including table name, rows inserted, rows updated, and rows deleted | Read |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_ListTagsForResource.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_ListTagsForResource.html) | Lists all tags for an AWS DMS resource | List |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyEndpoint.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyEndpoint.html) | Modifies the specified endpoint | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyEventSubscription.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyEventSubscription.html) | Modifies an existing AWS DMS event notification subscription\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyReplicationInstance.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyReplicationInstance.html) | Modifies the replication instance to apply new settings | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyReplicationSubnetGroup.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyReplicationSubnetGroup.html) | Modifies the settings for the specified replication subnet group | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyReplicationTask.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_ModifyReplicationTask.html) | Modifies the specified replication task\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_RefreshSchemas.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_RefreshSchemas.html) | Populates the schema for the specified endpoint | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_RemoveTagsFromResource.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_RemoveTagsFromResource.html) | Removes metadata tags from a DMS resource | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_StartReplicationTask.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_StartReplicationTask.html) | Starts the replication task | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_StopReplicationTask.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_StopReplicationTask.html) | Stops the replication task | Write |  |  |  | 
| [http://docs.aws.amazon.com/dms/latest/APIReference/API_TestConnection.html](http://docs.aws.amazon.com/dms/latest/APIReference/API_TestConnection.html) | Tests the connection between the replication instance and the endpoint | Read |  |  |  | 

## Resources Defined by DMS<a name="awsdatabasemigrationservice-resources-for-iam-policies"></a>

DMS has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Database Migration Service<a name="awsdatabasemigrationservice-policy-keys"></a>

DMS has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.