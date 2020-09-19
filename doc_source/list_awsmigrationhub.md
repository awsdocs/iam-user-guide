# Actions, resources, and condition keys for AWS Migration Hub<a name="list_awsmigrationhub"></a>

AWS Migration Hub \(service prefix: `mgh`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/migrationhub/latest/ug/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/migrationhub/latest/ug/api-reference.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/migrationhub/latest/ug/access_permissions.html) permission policies\.

**Topics**
+ [Actions defined by AWS Migration Hub](#awsmigrationhub-actions-as-permissions)
+ [Resource types defined by AWS Migration Hub](#awsmigrationhub-resources-for-iam-policies)
+ [Condition keys for AWS Migration Hub](#awsmigrationhub-policy-keys)

## Actions defined by AWS Migration Hub<a name="awsmigrationhub-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateCreatedArtifact ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_AssociateCreatedArtifact.html)  | Associate a given AWS artifact to a MigrationTask | Write |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ AssociateDiscoveredResource ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_AssociateDiscoveredResource.html)  | Associate a given ADS resource to a MigrationTask | Write |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ CreateHomeRegionControl ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_CreateHomeRegionControl.html)  | Create a Migration Hub Home Region Control | Write |  |  |  | 
|   [ CreateProgressUpdateStream ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_CreateProgressUpdateStream.html)  | Create a ProgressUpdateStream | Write |   [ progressUpdateStream\* ](#awsmigrationhub-progressUpdateStream)   |  |  | 
|   [ DeleteProgressUpdateStream ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_DeleteProgressUpdateStream.html)  | Delete a ProgressUpdateStream | Write |   [ progressUpdateStream\* ](#awsmigrationhub-progressUpdateStream)   |  |  | 
|   [ DescribeApplicationState ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_DescribeApplicationState.html)  | Get an Application Discovery Service Application's state | Read |  |  |  | 
|   [ DescribeHomeRegionControls ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_DescribeHomeRegionControls.html)  | List Home Region Controls | List |  |  |  | 
|   [ DescribeMigrationTask ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_DescribeMigrationTask.html)  | Describe a MigrationTask | Read |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ DisassociateCreatedArtifact ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_DisassociateCreatedArtifact.html)  | Disassociate a given AWS artifact from a MigrationTask | Write |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ DisassociateDiscoveredResource ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_DisassociateDiscoveredResource.html)  | Disassociate a given ADS resource from a MigrationTask | Write |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ GetHomeRegion ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_GetHomeRegion.html)  | Get the Migration Hub Home Region | Read |  |  |  | 
|   [ ImportMigrationTask ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_ImportMigrationTask.html)  | Import a MigrationTask | Write |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ ListCreatedArtifacts ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_ListCreatedArtifacts.html)  | List associated created artifacts for a MigrationTask | List |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ ListDiscoveredResources ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_ListDiscoveredResources.html)  | List associated ADS resources from MigrationTask | List |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ ListMigrationTasks ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_ListMigrationTasks.html)  | List MigrationTasks | List |  |  |  | 
|   [ ListProgressUpdateStreams ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_ListProgressUpdateStreams.html)  | List ProgressUpdateStreams | List |  |  |  | 
|   [ NotifyApplicationState ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_NotifyApplicationState.html)  | Update an Application Discovery Service Application's state | Write |  |  |  | 
|   [ NotifyMigrationTaskState ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_NotifyMigrationTaskState.html)  | Notify latest MigrationTask state | Write |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 
|   [ PutResourceAttributes ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_PutResourceAttributes.html)  | Put ResourceAttributes | Write |   [ migrationTask\* ](#awsmigrationhub-migrationTask)   |  |  | 

## Resource types defined by AWS Migration Hub<a name="awsmigrationhub-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsmigrationhub-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ progressUpdateStream ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_ProgressUpdateStreamSummary.html)  |  arn:$\{Partition\}:mgh:$\{Region\}:$\{Account\}:progressUpdateStream/$\{Stream\}  |  | 
|   [ migrationTask ](https://docs.aws.amazon.com/migrationhub/latest/ug/API_MigrationTask.html)  |  arn:$\{Partition\}:mgh:$\{Region\}:$\{Account\}:progressUpdateStream/$\{Stream\}/migrationTask/$\{Task\}  |  | 

## Condition keys for AWS Migration Hub<a name="awsmigrationhub-policy-keys"></a>

Migration Hub has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.