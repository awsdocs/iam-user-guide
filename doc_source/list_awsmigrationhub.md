# Actions, Resources, and Condition Keys for AWS Migration Hub<a name="list_awsmigrationhub"></a>

AWS Migration Hub \(service prefix: `mgh`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/migrationhub/latest/ug/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/migrationhub/latest/ug/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/migrationhub/latest/ug/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Migration Hub](#awsmigrationhub-actions-as-permissions)
+ [Resources Defined by Migration Hub](#awsmigrationhub-resources-for-iam-policies)
+ [Condition Keys for AWS Migration Hub](#awsmigrationhub-policy-keys)

## Actions Defined by AWS Migration Hub<a name="awsmigrationhub-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_AssociateCreatedArtifact.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_AssociateCreatedArtifact.html) | Associate a given AWS artifact to a MigrationTask | Write | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_AssociateDiscoveredResource.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_AssociateDiscoveredResource.html) | Associate a given ADS resource to a MigrationTask | Write | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_CreateProgressUpdateStream.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_CreateProgressUpdateStream.html) | Create a ProgressUpdateStream | Write | [progressUpdateStream\*](#awsmigrationhub-progressUpdateStream)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_DeleteProgressUpdateStream.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_DeleteProgressUpdateStream.html) | Delete a ProgressUpdateStream | Write | [progressUpdateStream\*](#awsmigrationhub-progressUpdateStream)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_DescribeApplicationState.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_DescribeApplicationState.html) | Get an Application Discovery Service Application's state | Read |  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_DescribeMigrationTask.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_DescribeMigrationTask.html) | Describe a MigrationTask | Read | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_DisassociateCreatedArtifact.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_DisassociateCreatedArtifact.html) | Disassociate a given AWS artifact from a MigrationTask | Write | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_DisassociateDiscoveredResource.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_DisassociateDiscoveredResource.html) | Disassociate a given ADS resource from a MigrationTask | Write | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_ImportMigrationTask.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_ImportMigrationTask.html) | Import a MigrationTask | Write | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_ListCreatedArtifacts.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_ListCreatedArtifacts.html) | List associated created artifacts for a MigrationTask | List | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_ListDiscoveredResources.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_ListDiscoveredResources.html) | List associated ADS resources from MigrationTask | List | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_ListMigrationTasks.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_ListMigrationTasks.html) | List MigrationTasks | List |  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_ListProgressUpdateStreams.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_ListProgressUpdateStreams.html) | List ProgressUpdateStreams | List |  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_NotifyApplicationState.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_NotifyApplicationState.html) | Update an Application Discovery Service Application's state | Write |  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_NotifyMigrationTaskState.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_NotifyMigrationTaskState.html) | Notify latest MigrationTask state | Write | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_PutResourceAttributes.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_PutResourceAttributes.html) | Put ResourceAttributes | Write | [migrationTask\*](#awsmigrationhub-migrationTask)  |  |  | 

## Resources Defined by Migration Hub<a name="awsmigrationhub-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsmigrationhub-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_MigrationTask.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_MigrationTask.html) | arn:$\{Partition\}:mgh:$\{Region\}:$\{Account\}:progressUpdateStream/$\{Stream\}/migrationTask/$\{Task\} |  | 
| [http://docs.aws.amazon.com/migrationhub/latest/ug/API_ProgressUpdateStreamSummary.html](http://docs.aws.amazon.com/migrationhub/latest/ug/API_ProgressUpdateStreamSummary.html) | arn:$\{Partition\}:mgh:$\{Region\}:$\{Account\}:progressUpdateStream/$\{Stream\} |  | 

## Condition Keys for AWS Migration Hub<a name="awsmigrationhub-policy-keys"></a>

Migration Hub has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.