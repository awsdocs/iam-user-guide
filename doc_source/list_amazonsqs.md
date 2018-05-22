# Actions, Resources, and Condition Keys for Amazon SQS<a name="list_amazonsqs"></a>

Amazon SQS \(service prefix: `sqs`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon SQS](#amazonsqs-actions-as-permissions)
+ [Resources Defined by SQS](#amazonsqs-resources-for-iam-policies)
+ [Condition Keys for Amazon SQS](#amazonsqs-policy-keys)

## Actions Defined by Amazon SQS<a name="amazonsqs-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_AddPermission.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_AddPermission.html) | Adds a permission to a queue for a specific principal\. | Permissions management | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibility.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibility.html) | Changes the visibility timeout of a specified message in a queue to a new value\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibilityBatch.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibilityBatch.html) | Changes the visibility timeout of multiple messages\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_CreateQueue.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_CreateQueue.html) | Creates a new queue, or returns the URL of an existing one\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessage.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessage.html) | Deletes the specified message from the specified queue\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessageBatch.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessageBatch.html) | Deletes up to ten messages from the specified queue\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteQueue.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteQueue.html) | Deletes the queue specified by the queue URL, regardless of whether the queue is empty\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueAttributes.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueAttributes.html) | Gets attributes for the specified queue\. | Read | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueUrl.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueUrl.html) | Returns the URL of an existing queue\. | Read | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListDeadLetterSourceQueues.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListDeadLetterSourceQueues.html) | Returns a list of your queues that have the RedrivePolicy queue attribute configured with a dead letter queue\. | Read | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListQueueTags.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListQueueTags.html) | Lists tags added to an SQS queue\. | Read | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListQueues.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListQueues.html) | Returns a list of your queues\. | List |  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_PurgeQueue.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_PurgeQueue.html) | Deletes the messages in a queue specified by the queue URL\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ReceiveMessage.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ReceiveMessage.html) | Retrieves one or more messages, with a maximum limit of 10 messages, from the specified queue\. | Read | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_RemovePermission.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_RemovePermission.html) | Revokes any permissions in the queue policy that matches the specified Label parameter\. | Permissions management | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessage.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessage.html) | Delivers a message to the specified queue\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessageBatch.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessageBatch.html) | Delivers up to ten messages to the specified queue\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SetQueueAttributes.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SetQueueAttributes.html) | Sets the value of one or more queue attributes\. | Write | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_TagQueue.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_TagQueue.html) | Add tags to the specified SQS queue\. | Tagging | [queue\*](#amazonsqs-queue)  |  |  | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_UntagQueue.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_UntagQueue.html) | Remove tags from the specified SQS queue\. | Tagging | [queue\*](#amazonsqs-queue)  |  |  | 

## Resources Defined by SQS<a name="amazonsqs-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsqs-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.

The ARN of the queue is used only in IAM permission policies\. In API and CLI calls, you use the queue's URL instead\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-how-it-works.html](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-how-it-works.html) | arn:$\{Partition\}:sqs:$\{Region\}:$\{Account\}:$\{QueueName\} |  | 

## Condition Keys for Amazon SQS<a name="amazonsqs-policy-keys"></a>

SQS has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.