# Actions, Resources, and Condition Keys for Amazon Transcribe<a name="list_amazontranscribe"></a>

Amazon Transcribe \(service prefix: `transcribe`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/transcribe/latest/dg/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/transcribe/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/transcribe/latest/dg/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Transcribe](#amazontranscribe-actions-as-permissions)
+ [Resources Defined by Amazon Transcribe](#amazontranscribe-resources-for-iam-policies)
+ [Condition Keys for Amazon Transcribe](#amazontranscribe-policy-keys)

## Actions Defined by Amazon Transcribe<a name="amazontranscribe-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateVocabulary ](https://docs.aws.amazon.com/transcribe/latest/dg/API_CreateVocabulary.html)  | Creates a new custom vocabulary that you can use to change the way Amazon Transcribe handles transcription of an audio file\. | Write |  |  |   s3:GetObject   | 
|   [ DeleteTranscriptionJob ](https://docs.aws.amazon.com/transcribe/latest/dg/API_DeleteTranscriptionJob.html)  | Deletes a previously submitted transcription job along with any other generated results such as the transcription, models, and so on\. | Write |  |  |  | 
|   [ DeleteVocabulary ](https://docs.aws.amazon.com/transcribe/latest/dg/API_DeleteVocabulary.html)  | Deletes a vocabulary from Amazon Transcribe\. | Write |  |  |  | 
|   [ GetTranscriptionJob ](https://docs.aws.amazon.com/transcribe/latest/dg/API_GetTranscriptionJob.html)  | Returns information about a transcription job\. | Read |  |  |  | 
|   [ GetVocabulary ](https://docs.aws.amazon.com/transcribe/latest/dg/API_GetVocabulary.html)  | Gets information about a vocabulary\. | Read |  |  |  | 
|   [ ListTranscriptionJobs ](https://docs.aws.amazon.com/transcribe/latest/dg/API_ListTranscriptionJobs.html)  | Lists transcription jobs with the specified status\. | List |  |  |  | 
|   [ ListVocabularies ](https://docs.aws.amazon.com/transcribe/latest/dg/API_ListVocabularies.html)  | Returns a list of vocabularies that match the specified criteria\. If no criteria are specified, returns the entire list of vocabularies\. | List |  |  |  | 
|   [ StartStreamTranscription ](https://docs.aws.amazon.com/transcribe/latest/dg/API_StartStreamTranscription.html)  | Starts a bidirectional HTTP2 stream to transcribe speech to text in real time\. | Write |  |  |  | 
|   [ StartTranscriptionJob ](https://docs.aws.amazon.com/transcribe/latest/dg/API_StartTranscriptionJob.html)  | Starts an asynchronous job to transcribe speech to text\. | Write |  |  |   s3:GetObject   | 
|   [ UpdateVocabulary ](https://docs.aws.amazon.com/transcribe/latest/dg/API_UpdateVocabulary.html)  | Updates an existing vocabulary with new values\. The UpdateVocabulary operation overwrites all of the existing information with the values that you provide in the request\. | Write |  |  |   s3:GetObject   | 

## Resources Defined by Amazon Transcribe<a name="amazontranscribe-resources-for-iam-policies"></a>

Amazon Transcribe has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Transcribe<a name="amazontranscribe-policy-keys"></a>

Transcribe has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.