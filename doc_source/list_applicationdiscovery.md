# Actions, resources, and condition keys for Application Discovery<a name="list_applicationdiscovery"></a>

Application Discovery \(service prefix: `discovery`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/application-discovery/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/application-discovery/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/application-discovery/latest/userguide/before_you_install.html#appdisc-user-policy) permission policies\.

**Topics**
+ [Actions defined by Application Discovery](#applicationdiscovery-actions-as-permissions)
+ [Resource types defined by Application Discovery](#applicationdiscovery-resources-for-iam-policies)
+ [Condition keys for Application Discovery](#applicationdiscovery-policy-keys)

## Actions defined by Application Discovery<a name="applicationdiscovery-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateConfigurationItemsToApplication ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_AssociateConfigurationItemsToApplication.html)  | Associates one or more configuration items with an application\. | Write |  |  |  | 
|   [ BatchDeleteImportData ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_BatchDeleteImportData.html)  | Deletes one or more Migration Hub import tasks, each identified by their import ID\. Each import task has a number of records, which can identify servers or applications\. | Write |  |  |  | 
|   [ CreateApplication ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_CreateApplication.html)  | Creates an application with the given name and description\. | Write |  |  |  | 
|   [ CreateTags ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_CreateTags.html)  | Creates one or more tags for configuration items\. Tags are metadata that help you categorize IT assets\. This API accepts a list of multiple configuration items\. | Tagging |  |  |  | 
|   [ DeleteApplications ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DeleteApplications.html)  | Deletes a list of applications and their associations with configuration items\. | Write |  |  |  | 
|   [ DeleteTags ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DeleteTags.html)  | Deletes the association between configuration items and one or more tags\. This API accepts a list of multiple configuration items\. | Tagging |  |  |  | 
|   [ DescribeAgents ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeAgents.html)  | Lists agents or the Connector by ID or lists all agents/Connectors associated with your user account if you did not specify an ID\. | Read |  |  |  | 
|   [ DescribeConfigurations ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeConfigurations.html)  | Retrieves attributes for a list of configuration item IDs\. All of the supplied IDs must be for the same asset type \(server, application, process, or connection\)\. Output fields are specific to the asset type selected\. For example, the output for a server configuration item includes a list of attributes about the server, such as host name, operating system, and number of network cards\. | Read |  |  |  | 
|   [ DescribeContinuousExports ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeContinuousExports.html)  | Lists exports as specified by ID\. All continuous exports associated with your user account can be listed if you call DescribeContinuousExports as is without passing any parameters\. | Read |  |  |  | 
|   [ DescribeExportConfigurations ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeExportConfigurations.html)  | Retrieves the status of a given export process\. You can retrieve status from a maximum of 100 processes\. | Read |  |  |  | 
|   [ DescribeExportTasks ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeExportTasks.html)  | Retrieve status of one or more export tasks\. You can retrieve the status of up to 100 export tasks\. | Read |  |  |  | 
|   [ DescribeImportTasks ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeImportTasks.html)  | Returns an array of import tasks for your account, including status information, times, IDs, the Amazon S3 Object URL for the import file, and more\. | List |  |  |  | 
|   [ DescribeTags ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeTags.html)  | Retrieves a list of configuration items that are tagged with a specific tag\. Or retrieves a list of all tags assigned to a specific configuration item\. | Read |  |  |  | 
|   [ DisassociateConfigurationItemsFromApplication ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DisassociateConfigurationItemsFromApplication.html)  | Disassociates one or more configuration items from an application\. | Write |  |  |  | 
|   [ ExportConfigurations ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ExportConfigurations.html)  | Exports all discovered configuration data to an Amazon S3 bucket or an application that enables you to view and evaluate the data\. Data includes tags and tag associations, processes, connections, servers, and system performance\. | Write |  |  |  | 
|   [ GetDiscoverySummary ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_GetDiscoverySummary.html)  | Retrieves a short summary of discovered assets\. | Read |  |  |  | 
|   [ ListConfigurations ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ListConfigurations.html)  | Retrieves a list of configuration items according to criteria you specify in a filter\. The filter criteria identify relationship requirements\. | List |  |  |  | 
|   [ ListServerNeighbors ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ListServerNeighbors.html)  | Retrieves a list of servers which are one network hop away from a specified server\. | List |  |  |  | 
|   [ StartContinuousExport ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StartContinuousExport.html)  | Start the continuous flow of agent's discovered data into Amazon Athena\. | Write |  |  |  | 
|   [ StartDataCollectionByAgentIds ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StartDataCollectionByAgentIds.html)  | Instructs the specified agents or Connectors to start collecting data\. | Write |  |  |  | 
|   [ StartExportTask ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StartExportTask.html)  | Export the configuration data about discovered configuration items and relationships to an S3 bucket in a specified format\. | Write |  |  |  | 
|   [ StartImportTask ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StartImportTask.html)  | Starts an import task\. The Migration Hub import feature allows you to import details of your on\-premises environment directly into AWS without having to use the Application Discovery Service \(ADS\) tools such as the Discovery Connector or Discovery Agent\. This gives you the option to perform migration assessment and planning directly from your imported data including the ability to group your devices as applications and track their migration status\. | Write |  |  |  | 
|   [ StopContinuousExport ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StopContinuousExport.html)  | Stop the continuous flow of agent's discovered data into Amazon Athena\. | Write |  |  |  | 
|   [ StopDataCollectionByAgentIds ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StopDataCollectionByAgentIds.html)  | Instructs the specified agents or Connectors to stop collecting data\. | Write |  |  |  | 
|   [ UpdateApplication ](https://docs.aws.amazon.com/application-discovery/latest/APIReference/API_UpdateApplication.html)  | Updates metadata about an application\. | Write |  |  |  | 

## Resource types defined by Application Discovery<a name="applicationdiscovery-resources-for-iam-policies"></a>

Application Discovery does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Application Discovery, specify `“Resource”: “*”` in your policy\.

## Condition keys for Application Discovery<a name="applicationdiscovery-policy-keys"></a>

Application Discovery has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.