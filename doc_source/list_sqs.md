# Actions and Condition Context Keys for Amazon SQS<a name="list_sqs"></a>

Amazon SQS \(service prefix: sqs\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon SQS**

For information about using the following Amazon SQS API actions in an IAM policy, see [Amazon SQS Actions](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/UsingIAM.html#UsingWithSQS_Actions) in the *Amazon Simple Queue Service Developer Guide*\.

+ `[sqs:DeleteQueue](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteQueue.html)`

+ `[sqs:PurgeQueue](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_PurgeQueue.html)`

+ `[sqs:ChangeMessageVisibilityBatch](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibilityBatch.html)`

+ `[sqs:SendMessageBatch](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessageBatch.html)`

+ `[sqs:ListDeadLetterSourceQueues](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListDeadLetterSourceQueues.html)`

+ `[sqs:AddPermission](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_AddPermission.html)`

+ `[sqs:ListQueueTags](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListQueueTags.html)`

+ `[sqs:ChangeMessageVisibility](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibility.html)`

+ `[sqs:DeleteMessage](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessage.html)`

+ `[sqs:SetQueueAttributes](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SetQueueAttributes.html)`

+ `[sqs:GetQueueAttributes](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueAttributes.html)`

+ `[sqs:ReceiveMessage](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ReceiveMessage.html)`

+ `[sqs:DeleteMessageBatch](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessageBatch.html)`

+ `[sqs:CreateQueue](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_CreateQueue.html)`

+ `[sqs:RemovePermission](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_RemovePermission.html)`

+ `[sqs:UntagQueue](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_UntagQueue.html)`

+ `[sqs:GetQueueUrl](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueUrl.html)`

+ `[sqs:ListQueues](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListQueues.html)`

+ `[sqs:TagQueue](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_TagQueue.html)`

+ `[sqs:SendMessage](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessage.html)`

**Condition context keys for Amazon SQS**

For information about using condition keys in an IAM policy to control access to SQS resources, see [Amazon SQS Keys](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/UsingIAM.html#amazon-sqs-keys) in the *Amazon Simple Queue Service Developer Guide*\.

Amazon SQS has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.