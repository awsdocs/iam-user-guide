# Actions, Resources, and Condition Keys for Data Pipeline<a name="list_datapipeline"></a>

Data Pipeline \(service prefix: `datapipeline`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/datapipeline/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-control-access.html) permission policies\.

**Topics**
+ [Actions Defined by Data Pipeline](#datapipeline-actions-as-permissions)
+ [Resources Defined by Data Pipeline](#datapipeline-resources-for-iam-policies)
+ [Condition Keys for Data Pipeline](#datapipeline-policy-keys)

## Actions Defined by Data Pipeline<a name="datapipeline-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ActivatePipeline.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ActivatePipeline.html) | Validates the specified pipeline and starts processing pipeline tasks\. If the pipeline does not pass validation, activation fails\. | Write |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag) [datapipeline:workerGroup](#datapipeline-datapipeline_workerGroup)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_AddTags.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_AddTags.html) | Adds or modifies tags for the specified pipeline\. | Tagging |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_CreatePipeline.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_CreatePipeline.html) | Creates a new, empty pipeline\. | Write |  | [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DeactivatePipeline.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DeactivatePipeline.html) | Deactivates the specified running pipeline\. | Write |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag) [datapipeline:workerGroup](#datapipeline-datapipeline_workerGroup)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DeletePipeline.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DeletePipeline.html) | Deletes a pipeline, its pipeline definition, and its run history\. | Write |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DescribeObjects.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DescribeObjects.html) | Gets the object definitions for a set of objects associated with the pipeline\. | Read |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DescribePipelines.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DescribePipelines.html) | Retrieves metadata about one or more pipelines\. | List |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_EvaluateExpression.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_EvaluateExpression.html) | Task runners call EvaluateExpression to evaluate a string in the context of the specified object\. | Read |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_GetAccountLimits.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_GetAccountLimits.html) | Description for GetAccountLimits | List |  |  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_GetPipelineDefinition.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_GetPipelineDefinition.html) | Gets the definition of the specified pipeline\. | Read |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag) [datapipeline:workerGroup](#datapipeline-datapipeline_workerGroup)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ListPipelines.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ListPipelines.html) | Lists the pipeline identifiers for all active pipelines that you have permission to access\. | List |  |  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PollForTask.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PollForTask.html) | Task runners call PollForTask to receive a task to perform from AWS Data Pipeline\. | Write |  | [datapipeline:workerGroup](#datapipeline-datapipeline_workerGroup)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PutAccountLimits.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PutAccountLimits.html) | Description for PutAccountLimits | Write |  |  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PutPipelineDefinition.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PutPipelineDefinition.html) | Adds tasks, schedules, and preconditions to the specified pipeline\. | Write |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag) [datapipeline:workerGroup](#datapipeline-datapipeline_workerGroup)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_QueryObjects.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_QueryObjects.html) | Queries the specified pipeline for the names of objects that match the specified set of conditions\. | Read |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_RemoveTags.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_RemoveTags.html) | Removes existing tags from the specified pipeline\. | Tagging |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskProgress.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskProgress.html) | Task runners call ReportTaskProgress when assigned a task to acknowledge that it has the task\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskRunnerHeartbeat.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskRunnerHeartbeat.html) | Task runners call ReportTaskRunnerHeartbeat every 15 minutes to indicate that they are operational\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_SetStatus.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_SetStatus.html) | Requests that the status of the specified physical or logical pipeline objects be updated in the specified pipeline\. | Write |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag)  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_SetTaskStatus.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_SetTaskStatus.html) | Task runners call SetTaskStatus to notify AWS Data Pipeline that a task is completed and provide information about the final status\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ValidatePipelineDefinition.html](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ValidatePipelineDefinition.html) | Validates the specified pipeline definition to ensure that it is well formed and can be run without error\. | Read |  | [datapipeline:PipelineCreator](#datapipeline-datapipeline_PipelineCreator) [datapipeline:Tag](#datapipeline-datapipeline_Tag) [datapipeline:workerGroup](#datapipeline-datapipeline_workerGroup)  |  | 

## Resources Defined by Data Pipeline<a name="datapipeline-resources-for-iam-policies"></a>

Data Pipeline has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Data Pipeline<a name="datapipeline-policy-keys"></a>

Data Pipeline defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-example-tag-policies.html#ex3](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-example-tag-policies.html#ex3) | The IAM user that created the pipeline\. | ARN | 
| [http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-control-access-tags](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-control-access-tags) | A customer\-specified key/value pair that can be attached to a resource\. | ARN | 
| [http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-control-access-workergroup](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-control-access-workergroup) | The name of a worker group for which a Task Runner retrieves work\. | ARN | 