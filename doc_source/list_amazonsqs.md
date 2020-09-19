# Actions, resources, and condition keys for Amazon SQS<a name="list_amazonsqs"></a>

Amazon SQS \(service prefix: `sqs`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon SQS](#amazonsqs-actions-as-permissions)
+ [Resource types defined by Amazon SQS](#amazonsqs-resources-for-iam-policies)
+ [Condition keys for Amazon SQS](#amazonsqs-policy-keys)

## Actions defined by Amazon SQS<a name="amazonsqs-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddPermission ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_AddPermission.html)  | Adds a permission to a queue for a specific principal\. | Permissions management |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ ChangeMessageVisibility ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibility.html)  | Changes the visibility timeout of a specified message in a queue to a new value\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ ChangeMessageVisibilityBatch ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ChangeMessageVisibilityBatch.html)  | Changes the visibility timeout of multiple messages\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ CreateQueue ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_CreateQueue.html)  | Creates a new queue, or returns the URL of an existing one\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ DeleteMessage ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessage.html)  | Deletes the specified message from the specified queue\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ DeleteMessageBatch ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteMessageBatch.html)  | Deletes up to ten messages from the specified queue\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ DeleteQueue ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_DeleteQueue.html)  | Deletes the queue specified by the queue URL, regardless of whether the queue is empty\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ GetQueueAttributes ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueAttributes.html)  | Gets attributes for the specified queue\. | Read |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ GetQueueUrl ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_GetQueueUrl.html)  | Returns the URL of an existing queue\. | Read |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ ListDeadLetterSourceQueues ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListDeadLetterSourceQueues.html)  | Returns a list of your queues that have the RedrivePolicy queue attribute configured with a dead letter queue\. | Read |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ ListQueueTags ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListQueueTags.html)  | Lists tags added to an SQS queue\. | Read |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ ListQueues ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ListQueues.html)  | Returns a list of your queues\. | List |  |  |  | 
|   [ PurgeQueue ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_PurgeQueue.html)  | Deletes the messages in a queue specified by the queue URL\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ ReceiveMessage ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ReceiveMessage.html)  | Retrieves one or more messages, with a maximum limit of 10 messages, from the specified queue\. | Read |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ RemovePermission ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_RemovePermission.html)  | Revokes any permissions in the queue policy that matches the specified Label parameter\. | Permissions management |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ SendMessage ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessage.html)  | Delivers a message to the specified queue\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ SendMessageBatch ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessageBatch.html)  | Delivers up to ten messages to the specified queue\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ SetQueueAttributes ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SetQueueAttributes.html)  | Sets the value of one or more queue attributes\. | Write |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ TagQueue ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_TagQueue.html)  | Add tags to the specified SQS queue\. | Tagging |   [ queue\* ](#amazonsqs-queue)   |  |  | 
|   [ UntagQueue ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_UntagQueue.html)  | Remove tags from the specified SQS queue\. | Tagging |   [ queue\* ](#amazonsqs-queue)   |  |  | 

## Resource types defined by Amazon SQS<a name="amazonsqs-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsqs-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.

**Note**  
The ARN of the queue is used only in IAM permission policies\. In API and CLI calls, you use the queue's URL instead\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ queue ](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-how-it-works.html)  |  arn:$\{Partition\}:sqs:$\{Region\}:$\{Account\}:$\{QueueName\}  |  | 

## Condition keys for Amazon SQS<a name="amazonsqs-policy-keys"></a>

SQS has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.