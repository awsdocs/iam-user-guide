# Actions and Condition Context Keys for Amazon Simple Workflow Service<a name="list_swf"></a>

Amazon Simple Workflow Service \(service prefix: swf\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon Simple Workflow Service**

For information about using the following Amazon SWF API actions in an IAM policy, see [Using IAM to Manage Access to Amazon SWF Resources](http://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html) in the *Amazon Simple Workflow Service Developer Guide*\.
+ `[swf:CancelTimer](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CancelTimer.html)`
+ `[swf:CancelWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CancelWorkflowExecution.html)`
+ `[swf:CompleteWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CompleteWorkflowExecution.html)`
+ `[swf:ContinueAsNewWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ContinueAsNewWorkflowExecution.html)`
+ `[swf:CountClosedWorkflowExecutions](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CountClosedWorkflowExecutions.html)`
+ `[swf:CountOpenWorkflowExecutions](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CountOpenWorkflowExecutions.html)`
+ `[swf:CountPendingActivityTasks](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CountPendingActivityTasks.html)`
+ `[swf:CountPendingDecisionTasks](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_CountPendingDecisionTasks.html)`
+ `[swf:DeprecateActivityType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DeprecateActivityType.html)`
+ `[swf:DeprecateDomain](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DeprecateDomain.html)`
+ `[swf:DeprecateWorkflowType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DeprecateWorkflowType.html)`
+ `[swf:DescribeActivityType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DescribeActivityType.html)`
+ `[swf:DescribeDomain](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DescribeDomain.html)`
+ `[swf:DescribeWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DescribeWorkflowExecution.html)`
+ `[swf:DescribeWorkflowType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_DescribeWorkflowType.html)`
+ `[swf:FailWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_FailWorkflowExecution.html)`
+ `[swf:GetWorkflowExecutionHistory](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_GetWorkflowExecutionHistory.html)`
+ `[swf:ListActivityTypes](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListActivityTypes.html)`
+ `[swf:ListClosedWorkflowExecutions](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListClosedWorkflowExecutions.html)`
+ `[swf:ListDomains](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListDomains.html)`
+ `[swf:ListOpenWorkflowExecutions](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListOpenWorkflowExecutions.html)`
+ `[swf:ListWorkflowTypes](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ListWorkflowTypes.html)`
+ `[swf:PollForActivityTask](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_PollForActivityTask.html)`
+ `[swf:PollForDecisionTask](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_PollForDecisionTask.html)`
+ `[swf:RecordActivityTaskHeartbeat](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RecordActivityTaskHeartbeat.html)`
+ `[swf:RecordMarker](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RecordMarker.html)`
+ `[swf:RegisterActivityType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RegisterActivityType.html)`
+ `[swf:RegisterDomain](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RegisterDomain.html)`
+ `[swf:RegisterWorkflowType](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RegisterWorkflowType.html)`
+ `[swf:RequestCancelActivityTask](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RequestCancelActivityTask.html)`
+ `[swf:RequestCancelExternalWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RequestCancelExternalWorkflowExecution.html)`
+ `[swf:RequestCancelWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RequestCancelWorkflowExecution.html)`
+ `[swf:RespondActivityTaskCanceled](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RespondActivityTaskCanceled.html)`
+ `[swf:RespondActivityTaskCompleted](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RespondActivityTaskCompleted.html)`
+ `[swf:RespondActivityTaskFailed](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RespondActivityTaskFailed.html)`
+ `[swf:RespondDecisionTaskCompleted](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_RespondDecisionTaskCompleted.html)`
+ `[swf:ScheduleActivityTask](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_ScheduleActivityTask.html)`
+ `[swf:SignalExternalWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_SignalExternalWorkflowExecution.html)`
+ `[swf:SignalWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_SignalWorkflowExecution.html)`
+ `[swf:StartChildWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_StartChildWorkflowExecution.html)`
+ `[swf:StartTimer](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_StartTimer.html)`
+ `[swf:StartWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_StartWorkflowExecution.html)`
+ `[swf:TerminateWorkflowExecution](http://docs.aws.amazon.com/amazonswf/latest/apireference/API_TerminateWorkflowExecution.html)`

**Condition context keys for Amazon Simple Workflow Service**

For information about using the following Amazon SWF condition keys in an IAM policy, see [API Summary](http://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html#swf-dev-iam.api) in the *Amazon Simple Workflow Service Developer Guide*\. Each API lists the condition keys that you can use with that API call\.

Amazon Simple Workflow Service has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ ` swf:workflowType.name`
+ `swf:activityType.name`
+ `swf:activityType.version`
+ `swf:defaultTaskList.name`
+ `swf:name`
+ `swf:tagFilter.tag`
+ `swf:tagList.member.0`
+ `swf:tagList.member.1`
+ `swf:tagList.member.2`
+ `swf:tagList.member.3`
+ `swf:tagList.member.4`
+ `swf:taskList.name`
+ `swf:typeFilter.name`
+ `swf:typeFilter.version`
+ `swf:version`
+ `swf:workflowType.name`
+ `swf:workflowType.version`