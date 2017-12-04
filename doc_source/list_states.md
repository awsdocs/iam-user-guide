# Actions and Condition Context Keys for AWS Step Functions<a name="list_states"></a>

AWS Step Functions \(service prefix: states\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS Step Functions**

AWS Step Functions is capable of executing code and accessing AWS resources \(such as data stored in Amazon S3 buckets\), so to maintain security, you must grant Step Functions access to those resources\. You do this for Step Functions with an IAM role\. For information about creating this role, see [Creating IAM Roles for Use with AWS Step Functions](http://docs.aws.amazon.com/step-functions/latest/dg/procedure-create-iam-role.html) in the *AWS Step Functions Developer Guide*\.

+ `[states:DeleteStateMachine](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DeleteStateMachine.html)`

+ `[states:DescribeExecution](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeExecution.html)`

+ `[states:StopExecution](http://docs.aws.amazon.com/step-functions/latest/apireference/API_StopExecution.html)`

+ `[states:ListExecutions](http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListExecutions.html)`

+ `[states:GetExecutionHistory](http://docs.aws.amazon.com/step-functions/latest/apireference/API_GetExecutionHistory.html)`

+ `[states:DescribeStateMachine](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeStateMachine.html)`

+ `[states:SendTaskSuccess](http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskSuccess.html)`

+ `[states:DeleteActivity](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DeleteActivity.html)`

+ `[states:GetActivityTask](http://docs.aws.amazon.com/step-functions/latest/apireference/API_GetActivityTask.html)`

+ `[states:DescribeActivity](http://docs.aws.amazon.com/step-functions/latest/apireference/API_DescribeActivity.html)`

+ `[states:ListStateMachines](http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListStateMachines.html)`

+ `[states:CreateStateMachine](http://docs.aws.amazon.com/step-functions/latest/apireference/API_CreateStateMachine.html)`

+ `[states:StartExecution](http://docs.aws.amazon.com/step-functions/latest/apireference/API_StartExecution.html)`

+ `[states:SendTaskFailure](http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskFailure.html)`

+ `[states:ListActivities](http://docs.aws.amazon.com/step-functions/latest/apireference/API_ListActivities.html)`

+ `[states:CreateActivity](http://docs.aws.amazon.com/step-functions/latest/apireference/API_CreateActivity.html)`

+ `[states:SendTaskHeartbeat](http://docs.aws.amazon.com/step-functions/latest/apireference/API_SendTaskHeartbeat.html)`

**Condition context keys for AWS Step Functions**

AWS Step Functions has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.