# Actions, Resources, and Condition Keys for Amazon Comprehend<a name="list_amazoncomprehend"></a>

Amazon Comprehend \(service prefix: `comprehend`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/comprehend/latest/dg/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/comprehend/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/comprehend/latest/dg/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Comprehend](#amazoncomprehend-actions-as-permissions)
+ [Resources Defined by Comprehend](#amazoncomprehend-resources-for-iam-policies)
+ [Condition Keys for Amazon Comprehend](#amazoncomprehend-policy-keys)

## Actions Defined by Amazon Comprehend<a name="amazoncomprehend-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchDetectDominantLanguage ](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectDominantLanguage.html)  | Detects the language or languages present in the list of text documents\. | Read |  |  |  | 
|   [ BatchDetectEntities ](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectEntities.html)  | Detects the named entities \("People", "Places", "Locations", etc\) within the given list of text documents\. | Read |  |  |  | 
|   [ BatchDetectKeyPhrases ](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectKeyPhrases.html)  | Detects the phrases in the list of text documents that are most indicative of the content\. | Read |  |  |  | 
|   [ BatchDetectSentiment ](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectSentiment.html)  | Detects the sentiment of a text in the list of documents \(Positive, Negative, Neutral, or Mixed\)\. | Read |  |  |  | 
|   [ BatchDetectSyntax ](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectSyntax.html)  | Detects syntactic information \(like Part of Speech, Tokens\) in a list of text documents\. | Read |  |  |  | 
|   [ DescribeDominantLanguageDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeDominantLanguageDetectionJob.html)  | Gets the properties associated with a dominant language detection job\. | Read |  |  |  | 
|   [ DescribeEntitiesDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeEntitiesDetectionJob.html)  | Gets the properties associated with an entities detection job\. | Read |  |  |  | 
|   [ DescribeKeyPhrasesDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeKeyPhrasesDetectionJob.html)  | Gets the properties associated with a key phrases detection job\. | Read |  |  |  | 
|   [ DescribeSentimentDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeSentimentDetectionJob.html)  | Gets the properties associated with a sentiment detection job\. | Read |  |  |  | 
|   [ DescribeTopicsDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeTopicsDetectionJob.html)  | Gets the properties associated with a topic detection job\. | Read |  |  |  | 
|   [ DetectDominantLanguage ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectDominantLanguage.html)  | Detects the language or languages present in the text\. | Read |  |  |  | 
|   [ DetectEntities ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectEntities.html)  | Detects the named entities \("People", "Places", "Locations", etc\) within the given text document\. | Read |  |  |  | 
|   [ DetectKeyPhrases ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectKeyPhrases.html)  | Detects the phrases in the text that are most indicative of the content\. | Read |  |  |  | 
|   [ DetectSentiment ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectSentiment.html)  | Detects the sentiment of a text in a document \(Positive, Negative, Neutral, or Mixed\)\. | Read |  |  |  | 
|   [ DetectSyntax ](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectSyntax.html)  | Detects syntactic information \(like Part of Speech, Tokens\) in a text document\. | Read |  |  |  | 
|   [ ListDominantLanguageDetectionJobs ](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListDominantLanguageDetectionJobs.html)  | Gets a list of the dominant language detection jobs that you have submitted\. | Read |  |  |  | 
|   [ ListEntitiesDetectionJobs ](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListEntitiesDetectionJobs.html)  | Gets a list of the entity detection jobs that you have submitted\. | Read |  |  |  | 
|   [ ListKeyPhrasesDetectionJobs ](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListKeyPhrasesDetectionJobs.html)  | Get a list of key phrase detection jobs that you have submitted\. | Read |  |  |  | 
|   [ ListSentimentDetectionJobs ](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListSentimentDetectionJobs.html)  | Gets a list of sentiment detection jobs that you have submitted\. | Read |  |  |  | 
|   [ ListTopicsDetectionJobs ](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListTopicsDetectionJobs.html)  | Gets a list of the topic detection jobs that you have submitted\. | Read |  |  |  | 
|   [ StartDominantLanguageDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartDominantLanguageDetectionJob.html)  | Starts an asynchronous dominant language detection job for a collection of documents\. | Write |  |  |  | 
|   [ StartEntitiesDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartEntitiesDetectionJob.html)  | Starts an asynchronous entity detection job for a collection of documents\. | Write |  |  |  | 
|   [ StartKeyPhrasesDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartKeyPhrasesDetectionJob.html)  | Starts an asynchronous key phrase detection job for a collection of documents\. | Write |  |  |  | 
|   [ StartSentimentDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartSentimentDetectionJob.html)  | Starts an asynchronous sentiment detection job for a collection of documents\. | Write |  |  |  | 
|   [ StartTopicsDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartTopicsDetectionJob.html)  | Starts an asynchronous job to detect the most common topics in the collection of documents and the phrases associated with each topic\. | Write |  |  |  | 
|   [ StopDominantLanguageDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopDominantLanguageDetectionJob.html)  | Stops a dominant language detection job\. | Write |  |  |  | 
|   [ StopEntitiesDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopEntitiesDetectionJob.html)  | Stops an entity detection job\. | Write |  |  |  | 
|   [ StopKeyPhrasesDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopKeyPhrasesDetectionJob.html)  | Stops a key phrase detection job\. | Write |  |  |  | 
|   [ StopSentimentDetectionJob ](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopSentimentDetectionJob.html)  | Stops a sentiment detection job\. | Write |  |  |  | 

## Resources Defined by Comprehend<a name="amazoncomprehend-resources-for-iam-policies"></a>

Amazon Comprehend has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Comprehend<a name="amazoncomprehend-policy-keys"></a>

Comprehend has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.