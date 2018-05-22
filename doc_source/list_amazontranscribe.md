# Actions, Resources, and Condition Keys for Amazon Transcribe<a name="list_amazontranscribe"></a>

Amazon Transcribe \(service prefix: `transcribe`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/transcribe/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/transcribe/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/transcribe/latest/dg/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Transcribe](#amazontranscribe-actions-as-permissions)
+ [Resources Defined by Transcribe](#amazontranscribe-resources-for-iam-policies)
+ [Condition Keys for Amazon Transcribe](#amazontranscribe-policy-keys)

## Actions Defined by Amazon Transcribe<a name="amazontranscribe-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/transcribe/latest/dg/API_GetTranscriptionJob.html](http://docs.aws.amazon.com/transcribe/latest/dg/API_GetTranscriptionJob.html) | Returns information about a transcription job\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/transcribe/latest/dg/API_ListTranscriptionJobs.html](http://docs.aws.amazon.com/transcribe/latest/dg/API_ListTranscriptionJobs.html) | Lists transcription jobs with the specified status\. | List |  |  |  | 
| [http://docs.aws.amazon.com/transcribe/latest/dg/API_StartTranscriptionJob.html](http://docs.aws.amazon.com/transcribe/latest/dg/API_StartTranscriptionJob.html) | Starts an asynchronous job to transcribe speech to text\. | Write |  |  |  | 

## Resources Defined by Transcribe<a name="amazontranscribe-resources-for-iam-policies"></a>

Transcribe has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Transcribe<a name="amazontranscribe-policy-keys"></a>

Transcribe has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.