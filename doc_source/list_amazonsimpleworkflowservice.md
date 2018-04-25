# Actions, Resources, and Condition Keys for Amazon Simple Workflow Service<a name="list_amazonsimpleworkflowservice"></a>

Amazon Simple Workflow Service \(service prefix: `swf`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/amazonswf/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/amazonswf/latest/apireference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/swf-dev-iam.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Simple Workflow Service](#amazonsimpleworkflowservice-actions-as-permissions)
+ [Resources Defined by SWF](#amazonsimpleworkflowservice-resources-for-iam-policies)
+ [Condition Keys for Amazon Simple Workflow Service](#amazonsimpleworkflowservice-policy-keys)

## Actions Defined by Amazon Simple Workflow Service<a name="amazonsimpleworkflowservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [CancelTimer](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CancelTimer.html) | Description for CancelTimer |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [CancelWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CancelWorkflowExecution.html) | Description for CancelWorkflowExecution |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [CompleteWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CompleteWorkflowExecution.html) | Description for CompleteWorkflowExecution |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [ContinueAsNewWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ContinueAsNewWorkflowExecution.html) | Description for ContinueAsNewWorkflowExecution |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [CountClosedWorkflowExecutions](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CountClosedWorkflowExecutions.html) | Returns the number of closed workflow executions within the given domain that meet the specified filtering criteria\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [CountOpenWorkflowExecutions](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CountOpenWorkflowExecutions.html) | Returns the number of open workflow executions within the given domain that meet the specified filtering criteria\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [CountPendingActivityTasks](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CountPendingActivityTasks.html) | Returns the estimated number of activity tasks in the specified task list\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [CountPendingDecisionTasks](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CountPendingDecisionTasks.html) | Returns the estimated number of decision tasks in the specified task list\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [DeprecateActivityType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DeprecateActivityType.html) | Deprecates the specified activity type\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [DeprecateDomain](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DeprecateDomain.html) | Deprecates the specified domain\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [DeprecateWorkflowType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DeprecateWorkflowType.html) | Deprecates the specified workflow type\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [DescribeActivityType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DescribeActivityType.html) | Returns information about the specified activity type\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [DescribeDomain](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DescribeDomain.html) | Returns information about the specified domain, including description and status\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [DescribeWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DescribeWorkflowExecution.html) | Returns information about the specified workflow execution including its type and some statistics\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [DescribeWorkflowType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DescribeWorkflowType.html) | Returns information about the specified workflow type\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [FailWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_FailWorkflowExecution.html) | Description for FailWorkflowExecution |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [GetWorkflowExecutionHistory](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_GetWorkflowExecutionHistory.html) | Returns the history of the specified workflow execution\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [ListActivityTypes](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListActivityTypes.html) | Returns information about all activities registered in the specified domain that match the specified name and registration status\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [ListClosedWorkflowExecutions](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListClosedWorkflowExecutions.html) | Returns a list of closed workflow executions in the specified domain that meet the filtering criteria\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [ListDomains](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListDomains.html) | Returns the list of domains registered in the account\. |   |  |  |  | 
| [ListOpenWorkflowExecutions](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListOpenWorkflowExecutions.html) | Returns a list of open workflow executions in the specified domain that meet the filtering criteria\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [ListWorkflowTypes](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListWorkflowTypes.html) | Returns information about workflow types in the specified domain\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [PollForActivityTask](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_PollForActivityTask.html) | Used by workers to get an ActivityTask from the specified activity taskList\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [PollForDecisionTask](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_PollForDecisionTask.html) | Used by deciders to get a DecisionTask from the specified decision taskList\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RecordActivityTaskHeartbeat](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RecordActivityTaskHeartbeat.html) | Used by activity workers to report to the service that the ActivityTask represented by the specified taskToken is still making progress\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RecordMarker](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RecordMarker.html) | Description for RecordMarker |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RegisterActivityType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RegisterActivityType.html) | Registers a new activity type along with its configuration settings in the specified domain\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RegisterDomain](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RegisterDomain.html) | Registers a new domain\. |   |  |  |  | 
| [RegisterWorkflowType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RegisterWorkflowType.html) | Registers a new workflow type and its configuration settings in the specified domain\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RequestCancelActivityTask](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RequestCancelActivityTask.html) | Description for RequestCancelActivityTask |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RequestCancelExternalWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RequestCancelExternalWorkflowExecution.html) | Description for RequestCancelExternalWorkflowExecution |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RequestCancelWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RequestCancelWorkflowExecution.html) | Records a WorkflowExecutionCancelRequested event in the currently running workflow execution identified by the given domain, workflowId, and runId\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RespondActivityTaskCanceled](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RespondActivityTaskCanceled.html) | Used by workers to tell the service that the ActivityTask identified by the taskToken was successfully canceled\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RespondActivityTaskCompleted](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RespondActivityTaskCompleted.html) | Used by workers to tell the service that the ActivityTask identified by the taskToken completed successfully with a result \(if provided\)\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RespondActivityTaskFailed](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RespondActivityTaskFailed.html) | Used by workers to tell the service that the ActivityTask identified by the taskToken has failed with reason \(if specified\)\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [RespondDecisionTaskCompleted](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RespondDecisionTaskCompleted.html) | Used by deciders to tell the service that the DecisionTask identified by the taskToken has successfully completed\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [ScheduleActivityTask](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ScheduleActivityTask.html) | Description for ScheduleActivityTask |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [SignalExternalWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_SignalExternalWorkflowExecution.html) | Description for SignalExternalWorkflowExecution |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [SignalWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_SignalWorkflowExecution.html) | Records a WorkflowExecutionSignaled event in the workflow execution history and creates a decision task for the workflow execution identified by the given domain, workflowId and runId\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [StartChildWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_StartChildWorkflowExecution.html) | Description for StartChildWorkflowExecution |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [StartTimer](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_StartTimer.html) | Description for StartTimer |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [StartWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_StartWorkflowExecution.html) | Starts an execution of the workflow type in the specified domain using the provided workflowId and input data\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 
| [TerminateWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_TerminateWorkflowExecution.html) | Records a WorkflowExecutionTerminated event and forces closure of the workflow execution identified by the given domain, runId, and workflowId\. |   | [domain\*](#amazonsimpleworkflowservice-domain)  |  |  | 

## Resources Defined by SWF<a name="amazonsimpleworkflowservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsimpleworkflowservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [domain](http://docs.aws.amazon.com/swf/latest/developerguide/swf-dev-domains.html) | arn:$\{Partition\}:swf::$\{Account\}:domain/$\{DomainName\} |  | 

## Condition Keys for Amazon Simple Workflow Service<a name="amazonsimpleworkflowservice-policy-keys"></a>

Amazon Simple Workflow Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [ swf:workflowType\.name](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only a workflow of the specified type\. | String | 
| [swf:activityType\.name](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only an activity type of the specified name\. | String | 
| [swf:activityType\.version](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Contstrains the policy statement to only an activity type of the specified version\. | String | 
| [swf:defaultTaskList\.name](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a matching defaultTaskList name\. | String | 
| [swf:name](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only activities or workflows with the specified name\. | String | 
| [swf:tagFilter\.tag](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a matching tagFilter\.tag value\. | String | 
| [swf:tagList\.member\.0](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [swf:tagList\.member\.1](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [swf:tagList\.member\.2](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [swf:tagList\.member\.3](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [swf:tagList\.member\.4](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [swf:taskList\.name](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a tasklist with the specified name\. | String | 
| [swf:typeFilter\.name](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a type filter with the specified name\. | String | 
| [swf:typeFilter\.version](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a type filter with the specified version\. | String | 
| [swf:version](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only activities or workflows with the specified version\. | String | 
| [swf:workflowType\.name](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a workflow type of the specified name\. | String | 
| [swf:workflowType\.version](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a workflow type of the specified version\. | String | 