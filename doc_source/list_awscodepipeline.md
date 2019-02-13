# Actions, Resources, and Condition Keys for AWS CodePipeline<a name="list_awscodepipeline"></a>

AWS CodePipeline \(service prefix: `codepipeline`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/codepipeline/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/codepipeline/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/codepipeline/latest/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CodePipeline](#awscodepipeline-actions-as-permissions)
+ [Resources Defined by CodePipeline](#awscodepipeline-resources-for-iam-policies)
+ [Condition Keys for AWS CodePipeline](#awscodepipeline-policy-keys)

## Actions Defined by AWS CodePipeline<a name="awscodepipeline-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions |
| --- | --- | --- | --- | --- | --- |
|   [ AcknowledgeJob ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_AcknowledgeJob.html)  | 	Returns information about a specified job and whether that job has been received by the job worker. | Write |  |  |  |
|   [ AcknowlegeThirdPartyJob ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_AcknowledgeThirdPartyJob.html)  | Confirms a job worker has received the specified job. Only used for partner actions. | Write |  |  |  |
|   [ CreateCustomActionType ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_CreateCustomActionType.html)  | Create a custom action you can use in the pipelines associated with your AWS account. | Write | [ actiontype* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-actiontype) |  |  |
|   [ CreatePipeline ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_CreatePipeline.html)  | Create a uniquely named pipeline. | Write | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |
|   [ DeleteCustomActionType ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_DeleteCustomActionType.html)  | Delete a custom action.	 | Write | [ actiontype* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-actiontype) |  |  |
|   [ DeletePipeline ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_DeletePipeline.html)  | Delete a specified pipeline.	 | Write | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |
|   [ DeleteWebhook ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_DeleteWebhook.html)  | Delete a specified webhook.	 | Write | [ webhook* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-webhook) |  |  |
|   [ DeregisterWebhookWithThirdParty ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_DeregisterWebhookWithThirdParty.html)  | Remove the registration of a webhook with the third party specified in its configuration. | Write | [ webhook* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-webhook) |  |  |
|   [ DisableStageTransition ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_DisableStageTransition.html)  | Prevent revisions from transitioning to the next stage in a pipeline.	 | Write | [ stage* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-stage) |  |  |
|   [ EnableStageTransition ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_EnableStageTransition.html)  | Enable revisions to transition to the next stage in a pipeline.	 | Write | [ stage* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-stage) |  |  |
|   [ GetJobDetails ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetJobDetails.html)  | Returns information about a job. | Read |  |  |  |
|   [ GetPipeline ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetPipeline.html)  | Retrieve information about a pipeline structure.	 | Read | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |
|   [ GetPipelineExecution ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetPipelineExecution.html)  | Returns information about an execution of a pipeline, including details about artifacts, the pipeline execution ID, and the name, version, and status of the pipeline	 | Read | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |
|   [ GetPipelineState ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetPipelineState.html)  | Retrieve information about the current state of the stages and actions of a pipeline.	| Read | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |
|   [ GetThirdPartyJobDetails ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_GetThirdPartyJobDetails.html)  | Requests the details of a job for a third party action. Only used for partner actions.	 | Read |  |  |  |
|   [ ListActionTypes ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_ListActionTypes.html)  | Retrieve a summary of all the action types available for pipelines in your account. | Read | [ actiontype* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-actiontype) |  |  |
|   [ ListPipelineExecutions ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_ListPipelineExecutions.html)  | Gets a summary of the most recent executions for a pipeline.	 | List | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |
|   [ ListPipelines ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_ListPipelines.html)  | Get a summary of all the pipelines associated with your AWS account.	 | List | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |
|   [ ListWebhooks ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_ListWebhooks.html)  | Get all the webhooks associated with your AWS account.	 | List | [ webhook* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-webhook) |  |  |
|   [ PollForJobs ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PollForJobs.html)  | Returns information about any jobs for AWS CodePipeline to act upon. | Write | [ actiontype* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-actiontype) |  |  |
|   [ PollForThirdPartyJobs ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutActionRevision.html)  | Determines whether there are any third party jobs for a job worker to act on. Only used for partner actions. | Write |  |  |  |
|   [ PutActionRevision ](https://docs.aws.amazon.com/cloudfront/latest/APIReference/API_ListTagsForResource.html)  | Edit actions within a pipeline. | Write | [action* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-action) |  |  |
|   [ PutApprovalResult ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutApprovalResult.html)  | Provides the response to a manual approval request to AWS CodePipeline. Valid responses include Approved and Rejected. | Write |  |  |  |
|   [ PutJobFailureResult ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutJobFailureResult.html)  | Represents the failure of a job as returned to the pipeline by a job worker. Only used for custom actions.	| Write |  |  |  |
|   [ PutJobSuccessResult ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutJobSuccessResult.html)  | Represents the success of a job as returned to the pipeline by a job worker. Only used for custom actions.	| Write |  |  |  |
|   [ PutThirdPartyJobFailureResult ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutThirdPartyJobFailureResult.html)  | Represents the failure of a third party job as returned to the pipeline by a job worker. Only used for partner actions. | Write |  |  |  |
|   [ PutThirdPartyJobSuccessResult ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutThirdPartyJobSuccessResult.html)  | Represents the success of a third party job as returned to the pipeline by a job worker. Only used for partner actions. | Write |  |  |  |
|   [ PutWebhook ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_PutWebhook.html)  | Create or update a webhook. | Write | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) [ webhook* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-webhook) |  |  |
|   [ RegisterWebhookWithThirdParty	](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_RegisterWebhookWithThirdParty.html)  | Register a webhook with the third party specified in its configuration.| Write | [ webhook* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-webhook) |  |  |
|   [ RetryStageExecution ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_RetryStageExecution.html)  | Resumes the pipeline execution by retrying the last failed actions in a stage.	| Write | [ stage* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-stage) |  |  |
|   [ StartPipelineExecution ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_StartPipelineExecution.html)  | Run the most recent revision through the pipeline.	| Write | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |
|   [ UpdatePipeline ](https://docs.aws.amazon.com/codepipeline/latest/APIReference/API_UpdatePipeline.html)  | Update a pipeline with changes to the structure of the pipeline.	| Write | [ pipeline* ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html#awscodepipeline-pipeline) |  |  |  |

[\[See the AWS documentation website for more details\]](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html)

## Resources Defined by CodePipeline<a name="awscodepipeline-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodepipeline-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys |
| --- | --- | --- |
|   [ action ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:$\{PipelineName\}/$\{StageName\}/$\{ActionName\}  |  |
|   [ actiontype ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:actiontype:$\{Owner\}/$\{Category\}/$\{Provider\}/$\{Version\}  |  |
|   [ pipeline ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:$\{PipelineName\}  |  |
|   [ stage ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:$\{PipelineName\}/$\{StageName\}  |  |
|   [ webhook ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:webhook:$\{WebhookName\}  |  |

## Condition Keys for AWS CodePipeline<a name="awscodepipeline-policy-keys"></a>

CodePipeline has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.
