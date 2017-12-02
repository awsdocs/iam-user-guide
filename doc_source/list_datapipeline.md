# Actions and Condition Context Keys for Data Pipeline<a name="list_datapipeline"></a>

Data Pipeline \(service prefix: datapipeline\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Data Pipeline**

For information about using the following AWS Data Pipeline API actions in an IAM policy, see [Controlling Access to Pipelines and Resources](http://alpha-docs-aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-control-access.html) in the *AWS Data Pipeline Developer Guide*\.

+ `[datapipeline:GetAccountLimits](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_GetAccountLimits.html)`

+ `[datapipeline:QueryObjects](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_QueryObjects.html)`

+ `[datapipeline:ValidatePipelineDefinition](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_ValidatePipelineDefinition.html)`

+ `[datapipeline:CreatePipeline](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_CreatePipeline.html)`

+ `[datapipeline:ListPipelines](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_ListPipelines.html)`

+ `[datapipeline:DeactivatePipeline](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_DeactivatePipeline.html)`

+ `[datapipeline:ReportTaskProgress](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskProgress.html)`

+ `[datapipeline:ActivatePipeline](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_ActivatePipeline.html)`

+ `[datapipeline:EvaluateExpression](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_EvaluateExpression.html)`

+ `[datapipeline:DescribeObjects](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_DescribeObjects.html)`

+ `[datapipeline:RemoveTags](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_RemoveTags.html)`

+ `[datapipeline:PutPipelineDefinition](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_PutPipelineDefinition.html)`

+ `[datapipeline:GetPipelineDefinition](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_GetPipelineDefinition.html)`

+ `[datapipeline:PutAccountLimits](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_PutAccountLimits.html)`

+ `[datapipeline:DeletePipeline](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_DeletePipeline.html)`

+ `[datapipeline:PollForTask](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_PollForTask.html)`

+ `[datapipeline:DescribePipelines](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_DescribePipelines.html)`

+ `[datapipeline:SetTaskStatus](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_SetTaskStatus.html)`

+ `[datapipeline:AddTags](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_AddTags.html)`

+ `[datapipeline:SetStatus](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_SetStatus.html)`

+ `[datapipeline:ReportTaskRunnerHeartbeat](http://alpha-docs-aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskRunnerHeartbeat.html)`

**Condition context keys for Data Pipeline**

Data Pipeline has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `[datapipeline:PipelineCreator](http://alpha-docs-aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-policy-syntax)`

+ `[datapipeline:Tag](http://alpha-docs-aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-policy-syntax)`

+ `[datapipeline:workerGroup](http://alpha-docs-aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-policy-syntax)`