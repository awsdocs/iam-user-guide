# Actions, Resources, and Condition Keys for AWS X\-Ray<a name="list_awsx-ray"></a>

AWS X\-Ray \(service prefix: `xray`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/xray/latest/devguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/xray/latest/api/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/xray/latest/devguide/xray-permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS X\-Ray](#awsx-ray-actions-as-permissions)
+ [Resource Types Defined by AWS X\-Ray](#awsx-ray-resources-for-iam-policies)
+ [Condition Keys for AWS X\-Ray](#awsx-ray-policy-keys)

## Actions Defined by AWS X\-Ray<a name="awsx-ray-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchGetTraces ](https://docs.aws.amazon.com/xray/latest/api/API_BatchGetTraces.html)  | Retrieves a list of traces specified by ID\. Each trace is a collection of segment documents that originates from a single request\. Use GetTraceSummaries to get a list of trace IDs\. | Read |  |  |  | 
|   [ CreateGroup ](https://docs.aws.amazon.com/xray/latest/api/API_CreateGroup.html)  | Creates a group resource with a name and a filter expression\. | Write |   [ group\* ](#awsx-ray-group)   |  |  | 
|   [ CreateSamplingRule ](https://docs.aws.amazon.com/xray/latest/api/API_CreateSamplingRule.html)  | Creates a rule to control sampling behavior for instrumented applications\. | Write |   [ sampling\-rule\* ](#awsx-ray-sampling-rule)   |  |  | 
|   [ DeleteGroup ](https://docs.aws.amazon.com/xray/latest/api/API_DeleteGroup.html)  | Deletes a group resource\. | Write |   [ group\* ](#awsx-ray-group)   |  |  | 
|   [ DeleteSamplingRule ](https://docs.aws.amazon.com/xray/latest/api/API_DeleteSamplingRule.html)  | Deletes a sampling rule\. | Write |   [ sampling\-rule\* ](#awsx-ray-sampling-rule)   |  |  | 
|   [ GetEncryptionConfig ](https://docs.aws.amazon.com/xray/latest/api/API_GetEncryptionConfig.html)  | Retrieves the current encryption configuration for X\-Ray data\. | Permissions management |  |  |  | 
|   [ GetGroup ](https://docs.aws.amazon.com/xray/latest/api/API_GetGroup.html)  | Retrieves group resource details\. | Read |   [ group\* ](#awsx-ray-group)   |  |  | 
|   [ GetGroups ](https://docs.aws.amazon.com/xray/latest/api/API_GetGroups.html)  | Retrieves all active group details\. | Read |  |  |  | 
|   [ GetSamplingRules ](https://docs.aws.amazon.com/xray/latest/api/API_GetSamplingRules.html)  | Retrieves all sampling rules\. | Read |  |  |  | 
|   [ GetSamplingStatisticSummaries ](https://docs.aws.amazon.com/xray/latest/api/API_GetSamplingStatisticSummaries.html)  | Retrieves information about recent sampling results for all sampling rules\. | Read |  |  |  | 
|   [ GetSamplingTargets ](https://docs.aws.amazon.com/xray/latest/api/API_GetSamplingTargets.html)  | Requests a sampling quota for rules that the service is using to sample requests\. | Read |  |  |  | 
|   [ GetServiceGraph ](https://docs.aws.amazon.com/xray/latest/api/API_GetServiceGraph.html)  | Retrieves a document that describes services that process incoming requests, and downstream services that they call as a result\. | Read |  |  |  | 
|   [ GetTimeSeriesServiceStatistics ](https://docs.aws.amazon.com/xray/latest/api/API_GetTimeSeriesServiceStatistics.html)  | Get an aggregation of service statistics defined by a specific time range bucketed into time intervals\. | Read |  |  |  | 
|   [ GetTraceGraph ](https://docs.aws.amazon.com/xray/latest/api/API_GetTraceGraph.html)  | Retrieves a service graph for one or more specific trace IDs\. | Read |  |  |  | 
|   [ GetTraceSummaries ](https://docs.aws.amazon.com/xray/latest/api/API_GetTraceSummaries.html)  | Retrieves IDs and metadata for traces available for a specified time frame using an optional filter\. To get the full traces, pass the trace IDs to BatchGetTraces\. | Read |  |  |  | 
|   [ PutEncryptionConfig ](https://docs.aws.amazon.com/xray/latest/api/API_PutEncryptionConfig.html)  | Updates the encryption configuration for X\-Ray data\. | Permissions management |  |  |  | 
|   [ PutTelemetryRecords ](https://docs.aws.amazon.com/xray/latest/api/API_PutTelemetryRecords.html)  | Used by the AWS X\-Ray daemon to send telemetry to the service\. | Write |  |  |  | 
|   [ PutTraceSegments ](https://docs.aws.amazon.com/xray/latest/api/API_PutTraceSegments.html)  | Uploads segment documents to AWS X\-Ray\. The X\-Ray SDK generates segment documents and sends them to the X\-Ray daemon, which uploads them in batches\. | Write |  |  |  | 
|   [ UpdateGroup ](https://docs.aws.amazon.com/xray/latest/api/API_UpdateGroup.html)  | Updates a group resource\. | Write |   [ group\* ](#awsx-ray-group)   |  |  | 
|   [ UpdateSamplingRule ](https://docs.aws.amazon.com/xray/latest/api/API_UpdateSamplingRule.html)  | Modifies a sampling rule's configuration\. | Write |   [ sampling\-rule\* ](#awsx-ray-sampling-rule)   |  |  | 

## Resource Types Defined by AWS X\-Ray<a name="awsx-ray-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsx-ray-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ group ](https://docs.aws.amazon.com/xray/latest/devguide/xray-concepts.html#xray-concepts-groups)  |  arn:$\{Partition\}:xray:$\{Region\}:$\{Account\}:group/$\{GroupName\}/$\{Id\}  |  | 
|   [ sampling\-rule ](https://docs.aws.amazon.com/xray/latest/devguide/xray-concepts.html#xray-concepts-sampling)  |  arn:$\{Partition\}:xray:$\{Region\}:$\{Account\}:sampling\-rule/$\{SamplingRuleName\}  |  | 

## Condition Keys for AWS X\-Ray<a name="awsx-ray-policy-keys"></a>

X\-Ray has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.