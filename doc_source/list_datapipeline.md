# Actions, resources, and condition keys for Data Pipeline<a name="list_datapipeline"></a>

Data Pipeline \(service prefix: `datapipeline`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/datapipeline/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-control-access.html) permission policies\.

**Topics**
+ [Actions defined by Data Pipeline](#datapipeline-actions-as-permissions)
+ [Resource types defined by Data Pipeline](#datapipeline-resources-for-iam-policies)
+ [Condition keys for Data Pipeline](#datapipeline-policy-keys)

## Actions defined by Data Pipeline<a name="datapipeline-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ ActivatePipeline ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ActivatePipeline.html)  | Validates the specified pipeline and starts processing pipeline tasks\. If the pipeline does not pass validation, activation fails\. | Write |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   [ datapipeline:workerGroup ](#datapipeline-datapipeline_workerGroup)   |  | 
|   [ AddTags ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_AddTags.html)  | Adds or modifies tags for the specified pipeline\. | Tagging |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ CreatePipeline ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_CreatePipeline.html)  | Creates a new, empty pipeline\. | Write |  |   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ DeactivatePipeline ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DeactivatePipeline.html)  | Deactivates the specified running pipeline\. | Write |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   [ datapipeline:workerGroup ](#datapipeline-datapipeline_workerGroup)   |  | 
|   [ DeletePipeline ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DeletePipeline.html)  | Deletes a pipeline, its pipeline definition, and its run history\. | Write |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ DescribeObjects ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DescribeObjects.html)  | Gets the object definitions for a set of objects associated with the pipeline\. | Read |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ DescribePipelines ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DescribePipelines.html)  | Retrieves metadata about one or more pipelines\. | List |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ EvaluateExpression ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_EvaluateExpression.html)  | Task runners call EvaluateExpression to evaluate a string in the context of the specified object\. | Read |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ GetAccountLimits ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_GetAccountLimits.html)  | Description for GetAccountLimits | List |  |  |  | 
|   [ GetPipelineDefinition ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_GetPipelineDefinition.html)  | Gets the definition of the specified pipeline\. | Read |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   [ datapipeline:workerGroup ](#datapipeline-datapipeline_workerGroup)   |  | 
|   [ ListPipelines ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ListPipelines.html)  | Lists the pipeline identifiers for all active pipelines that you have permission to access\. | List |  |  |  | 
|   [ PollForTask ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PollForTask.html)  | Task runners call PollForTask to receive a task to perform from AWS Data Pipeline\. | Write |  |   [ datapipeline:workerGroup ](#datapipeline-datapipeline_workerGroup)   |  | 
|   [ PutAccountLimits ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PutAccountLimits.html)  | Description for PutAccountLimits | Write |  |  |  | 
|   [ PutPipelineDefinition ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PutPipelineDefinition.html)  | Adds tasks, schedules, and preconditions to the specified pipeline\. | Write |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   [ datapipeline:workerGroup ](#datapipeline-datapipeline_workerGroup)   |  | 
|   [ QueryObjects ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_QueryObjects.html)  | Queries the specified pipeline for the names of objects that match the specified set of conditions\. | Read |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ RemoveTags ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_RemoveTags.html)  | Removes existing tags from the specified pipeline\. | Tagging |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ ReportTaskProgress ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskProgress.html)  | Task runners call ReportTaskProgress when assigned a task to acknowledge that it has the task\. | Write |  |  |  | 
|   [ ReportTaskRunnerHeartbeat ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskRunnerHeartbeat.html)  | Task runners call ReportTaskRunnerHeartbeat every 15 minutes to indicate that they are operational\. | Write |  |  |  | 
|   [ SetStatus ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_SetStatus.html)  | Requests that the status of the specified physical or logical pipeline objects be updated in the specified pipeline\. | Write |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   |  | 
|   [ SetTaskStatus ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_SetTaskStatus.html)  | Task runners call SetTaskStatus to notify AWS Data Pipeline that a task is completed and provide information about the final status\. | Write |  |  |  | 
|   [ ValidatePipelineDefinition ](https://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ValidatePipelineDefinition.html)  | Validates the specified pipeline definition to ensure that it is well formed and can be run without error\. | Read |  |   [ datapipeline:PipelineCreator ](#datapipeline-datapipeline_PipelineCreator)   [ datapipeline:Tag ](#datapipeline-datapipeline_Tag)   [ datapipeline:workerGroup ](#datapipeline-datapipeline_workerGroup)   |  | 

## Resource types defined by Data Pipeline<a name="datapipeline-resources-for-iam-policies"></a>

Data Pipeline does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Data Pipeline, specify `“Resource”: “*”` in your policy\.

## Condition keys for Data Pipeline<a name="datapipeline-policy-keys"></a>

Data Pipeline defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ datapipeline:PipelineCreator ](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-example-tag-policies.html#ex3)  | The IAM user that created the pipeline\. | ARN | 
|   [ datapipeline:Tag ](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-control-access-tags)  | A customer\-specified key/value pair that can be attached to a resource\. | ARN | 
|   [ datapipeline:workerGroup ](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-control-access-workergroup)  | The name of a worker group for which a Task Runner retrieves work\. | ARN | 