# Actions and Condition Context Keys for Data Pipeline<a name="list_datapipeline"></a>

Data Pipeline \(service prefix: datapipeline\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Data Pipeline**

For information about using the following AWS Data Pipeline API actions in an IAM policy, see [Controlling Access to Pipelines and Resources](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-control-access.html) in the *AWS Data Pipeline Developer Guide*\.

+ `[datapipeline:QueryObjects](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_QueryObjects.html)`

+ `[datapipeline:GetAccountLimits](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_GetAccountLimits.html)`

+ `[datapipeline:ValidatePipelineDefinition](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ValidatePipelineDefinition.html)`

+ `[datapipeline:DeactivatePipeline](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DeactivatePipeline.html)`

+ `[datapipeline:ListPipelines](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ListPipelines.html)`

+ `[datapipeline:CreatePipeline](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_CreatePipeline.html)`

+ `[datapipeline:ReportTaskProgress](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskProgress.html)`

+ `[datapipeline:ActivatePipeline](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ActivatePipeline.html)`

+ `[datapipeline:EvaluateExpression](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_EvaluateExpression.html)`

+ `[datapipeline:DescribeObjects](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DescribeObjects.html)`

+ `[datapipeline:RemoveTags](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_RemoveTags.html)`

+ `[datapipeline:PutPipelineDefinition](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PutPipelineDefinition.html)`

+ `[datapipeline:GetPipelineDefinition](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_GetPipelineDefinition.html)`

+ `[datapipeline:PutAccountLimits](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PutAccountLimits.html)`

+ `[datapipeline:DeletePipeline](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DeletePipeline.html)`

+ `[datapipeline:PollForTask](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_PollForTask.html)`

+ `[datapipeline:SetTaskStatus](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_SetTaskStatus.html)`

+ `[datapipeline:DescribePipelines](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_DescribePipelines.html)`

+ `[datapipeline:SetStatus](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_SetStatus.html)`

+ `[datapipeline:AddTags](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_AddTags.html)`

+ `[datapipeline:ReportTaskRunnerHeartbeat](http://docs.aws.amazon.com/datapipeline/latest/APIReference/API_ReportTaskRunnerHeartbeat.html)`

**Condition context keys for Data Pipeline**

Data Pipeline has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `[datapipeline:PipelineCreator](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-policy-syntax)`

+ `[datapipeline:Tag](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-policy-syntax)`

+ `[datapipeline:workerGroup](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-resourcebased-access.html#dp-policy-syntax)`