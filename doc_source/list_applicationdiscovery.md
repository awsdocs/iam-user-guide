# Actions, Resources, and Condition Keys for Application Discovery<a name="list_applicationdiscovery"></a>

Application Discovery \(service prefix: `discovery`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/application-discovery/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/application-discovery/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/application-discovery/latest/userguide/before_you_install.html#appdisc-user-policy) permission policies\.

**Topics**
+ [Actions Defined by Application Discovery](#applicationdiscovery-actions-as-permissions)
+ [Resources Defined by Application Discovery](#applicationdiscovery-resources-for-iam-policies)
+ [Condition Keys for Application Discovery](#applicationdiscovery-policy-keys)

## Actions Defined by Application Discovery<a name="applicationdiscovery-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_AssociateConfigurationItemsToApplication.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_AssociateConfigurationItemsToApplication.html) | Associates one or more configuration items with an application\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_CreateApplication.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_CreateApplication.html) | Creates an application with the given name and description\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_CreateTags.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_CreateTags.html) | Creates one or more tags for configuration items\. Tags are metadata that help you categorize IT assets\. This API accepts a list of multiple configuration items\. | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DeleteApplications.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DeleteApplications.html) | Deletes a list of applications and their associations with configuration items\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DeleteTags.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DeleteTags.html) | Deletes the association between configuration items and one or more tags\. This API accepts a list of multiple configuration items\. | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeAgents.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeAgents.html) | Lists agents or the Connector by ID or lists all agents/Connectors associated with your user account if you did not specify an ID\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeConfigurations.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeConfigurations.html) | Retrieves attributes for a list of configuration item IDs\. All of the supplied IDs must be for the same asset type \(server, application, process, or connection\)\. Output fields are specific to the asset type selected\. For example, the output for a server configuration item includes a list of attributes about the server, such as host name, operating system, and number of network cards\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeExportConfigurations.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeExportConfigurations.html) | Retrieves the status of a given export process\. You can retrieve status from a maximum of 100 processes\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeTags.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DescribeTags.html) | Retrieves a list of configuration items that are tagged with a specific tag\. Or retrieves a list of all tags assigned to a specific configuration item\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DisassociateConfigurationItemsFromApplication.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_DisassociateConfigurationItemsFromApplication.html) | Disassociates one or more configuration items from an application\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ExportConfigurations.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ExportConfigurations.html) | Exports all discovered configuration data to an Amazon S3 bucket or an application that enables you to view and evaluate the data\. Data includes tags and tag associations, processes, connections, servers, and system performance\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_GetDiscoverySummary.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_GetDiscoverySummary.html) | Retrieves a short summary of discovered assets\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ListConfigurations.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ListConfigurations.html) | Retrieves a list of configuration items according to criteria you specify in a filter\. The filter criteria identify relationship requirements\. | List |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ListServerNeighbors.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_ListServerNeighbors.html) | Retrieves a list of servers which are one network hop away from a specified server\. | List |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StartDataCollectionByAgentIds.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StartDataCollectionByAgentIds.html) | Instructs the specified agents or Connectors to start collecting data\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StartExportTask.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StartExportTask.html) | Export the configuration data about discovered configuration items and relationships to an S3 bucket in a specified format\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StopDataCollectionByAgentIds.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_StopDataCollectionByAgentIds.html) | Instructs the specified agents or Connectors to stop collecting data\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_UpdateApplication.html](http://docs.aws.amazon.com/application-discovery/latest/APIReference/API_UpdateApplication.html) | Updates metadata about an application\. | Write |  |  |  | 

## Resources Defined by Application Discovery<a name="applicationdiscovery-resources-for-iam-policies"></a>

Application Discovery has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Application Discovery<a name="applicationdiscovery-policy-keys"></a>

Application Discovery has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.