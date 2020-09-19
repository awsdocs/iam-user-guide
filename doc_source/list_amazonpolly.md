# Actions, resources, and condition keys for Amazon Polly<a name="list_amazonpolly"></a>

Amazon Polly \(service prefix: `polly`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/polly/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/polly/latest/dg/API_Reference.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/polly/latest/dg/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Polly](#amazonpolly-actions-as-permissions)
+ [Resource types defined by Amazon Polly](#amazonpolly-resources-for-iam-policies)
+ [Condition keys for Amazon Polly](#amazonpolly-policy-keys)

## Actions defined by Amazon Polly<a name="amazonpolly-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DeleteLexicon ](https://docs.aws.amazon.com/polly/latest/dg/API_DeleteLexicon.html)  | Deletes the specified pronunciation lexicon stored in an AWS Region | Write |   [ lexicon\* ](#amazonpolly-lexicon)   |  |  | 
|   [ DescribeVoices ](https://docs.aws.amazon.com/polly/latest/dg/API_DescribeVoices.html)  | Returns the list of voices that are available for use when requesting speech synthesis\. | List |  |  |  | 
|   [ GetLexicon ](https://docs.aws.amazon.com/polly/latest/dg/API_GetLexicon.html)  | Returns the content of the specified pronunciation lexicon stored in an AWS Region\. | Read |   [ lexicon\* ](#amazonpolly-lexicon)   |  |  | 
|   [ GetSpeechSynthesisTask ](https://docs.aws.amazon.com/polly/latest/dg/API_GetSpeechSynthesisTask.html)  | Enables the user to get information about specific speech synthesis task\. | Read |  |  |  | 
|   [ ListLexicons ](https://docs.aws.amazon.com/polly/latest/dg/API_ListLexicons.html)  | Returns a list of pronunciation lexicons stored in an AWS Region\. | List |  |  |  | 
|   [ ListSpeechSynthesisTasks ](https://docs.aws.amazon.com/polly/latest/dg/API_ListSpeechSynthesisTasks.html)  | Enables the user to list requested speech synthesis tasks\. | List |  |  |  | 
|   [ PutLexicon ](https://docs.aws.amazon.com/polly/latest/dg/API_PutLexicon.html)  | Stores a pronunciation lexicon in an AWS Region\. | Write |  |  |  | 
|   [ StartSpeechSynthesisTask ](https://docs.aws.amazon.com/polly/latest/dg/API_StartSpeechSynthesisTask.html)  | Enables the user to synthesize long inputs to provided S3 location\. | Write |   [ lexicon ](#amazonpolly-lexicon)   |  |   s3:PutObject   | 
|   [ SynthesizeSpeech ](https://docs.aws.amazon.com/polly/latest/dg/API_SynthesizeSpeech.html)  | Synthesizes UTF\-8 input, plain text or SSML, to a stream of bytes\. | Read |   [ lexicon ](#amazonpolly-lexicon)   |  |  | 

## Resource types defined by Amazon Polly<a name="amazonpolly-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonpolly-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ lexicon ](https://docs.aws.amazon.com/polly/latest/dg/managing-lexicons.html)  |  arn:$\{Partition\}:polly:$\{Region\}:$\{Account\}:lexicon/$\{LexiconName\}  |  | 

## Condition keys for Amazon Polly<a name="amazonpolly-policy-keys"></a>

Polly has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.