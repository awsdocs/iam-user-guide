# Actions, Resources, and Condition Keys for AWS Step Functions<a name="list_awsstepfunctions"></a>

AWS Step Functions \(service prefix: `states`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/step-functions/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/step-functions/latest/apireference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/step-functions/latest/dg/procedure-create-iam-role.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Step Functions](#awsstepfunctions-actions-as-permissions)
+ [Resources Defined by Step Functions](#awsstepfunctions-resources-for-iam-policies)
+ [Condition Keys for AWS Step Functions](#awsstepfunctions-policy-keys)

## Actions Defined by AWS Step Functions<a name="awsstepfunctions-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_CreateActivity.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_CreateActivity.html) | Creates an activity\. Activities must poll Step Functions using the GetActivityTask and respond using SendTask\* API calls\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_CreateStateMachine.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_CreateStateMachine.html) | Creates a state machine\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_DeleteActivity.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DeleteActivity.html) | Deletes an activity\. | Write | [activity\*](#awsstepfunctions-activity)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_DeleteStateMachine.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DeleteStateMachine.html) | Deletes a state machine\. | Write | [statemachine\*](#awsstepfunctions-statemachine)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeActivity.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeActivity.html) | Describes an activity\. | Read | [activity\*](#awsstepfunctions-activity)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeExecution.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeExecution.html) | Describes an execution\. | Read | [execution\*](#awsstepfunctions-execution)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeStateMachine.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeStateMachine.html) | Describes a state machine\. | Read | [statemachine\*](#awsstepfunctions-statemachine)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeStateMachineForExecution.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeStateMachineForExecution.html) | Describes state machine for an execution\. | Read | [execution\*](#awsstepfunctions-execution)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_GetActivityTask.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_GetActivityTask.html) | Used by workers to retrieve a task \(with the specified activity ARN\) which has been scheduled for execution by a running state machine\. | Write | [activity\*](#awsstepfunctions-activity)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_GetExecutionHistory.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_GetExecutionHistory.html) | Returns the history of the specified execution as a list of events\. By default, the results are returned in ascending order of the timeStamp of the events\. | Read | [execution\*](#awsstepfunctions-execution)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListActivities.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListActivities.html) | Lists the existing activities\. The results may be split into multiple pages\. | List |  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListExecutions.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListExecutions.html) | Lists the executions of a state machine that meet the filtering criteria\. The results may be split into multiple pages\. | Read | [statemachine\*](#awsstepfunctions-statemachine)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListStateMachines.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListStateMachines.html) | Lists the existing state machines\. The results may be split into multiple pages\. | List |  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskFailure.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskFailure.html) | Used by workers to report that the task identified by the taskToken failed\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskHeartbeat.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskHeartbeat.html) | Used by workers to report to the service that the task represented by the specified taskToken is still making progress\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskSuccess.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskSuccess.html) | Used by workers to report that the task identified by the taskToken completed successfully\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_StartExecution.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_StartExecution.html) | Starts a state machine execution\. | Write | [statemachine\*](#awsstepfunctions-statemachine)  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_StopExecution.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_StopExecution.html) | Stops an execution\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/step-functions/latest/apireference/API_UpdateStateMachine.html](http://docs.aws.amazon.com/step-functions/latest/apireference/API_UpdateStateMachine.html) | Updates a state machine\. | Write | [statemachine\*](#awsstepfunctions-statemachine)  |  |  | 

## Resources Defined by Step Functions<a name="awsstepfunctions-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsstepfunctions-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/step-functions/latest/dg/concepts-activities.html](http://docs.aws.amazon.com/step-functions/latest/dg/concepts-activities.html) | arn:$\{Partition\}:states:$\{Region\}:$\{Account\}:activity:$\{ActivityName\} |  | 
| [http://docs.aws.amazon.com/step-functions/latest/dg/concepts-state-machine-executions.html](http://docs.aws.amazon.com/step-functions/latest/dg/concepts-state-machine-executions.html) | arn:$\{Partition\}:states:$\{Region\}:$\{Account\}:execution:$\{StateMachineName\}:$\{ExecutionId\} |  | 
| [http://docs.aws.amazon.com/step-functions/latest/dg/concepts-amazon-states-language.html](http://docs.aws.amazon.com/step-functions/latest/dg/concepts-amazon-states-language.html) | arn:$\{Partition\}:states:$\{Region\}:$\{Account\}:stateMachine:$\{StateMachineName\} |  | 

## Condition Keys for AWS Step Functions<a name="awsstepfunctions-policy-keys"></a>

Step Functions has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.