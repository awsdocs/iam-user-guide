# Actions, resources, and condition keys for Amazon Translate<a name="list_amazontranslate"></a>

Amazon Translate \(service prefix: `translate`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/translate/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/translate/latest/dg/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/translate/latest/dg/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Translate](#amazontranslate-actions-as-permissions)
+ [Resource types defined by Amazon Translate](#amazontranslate-resources-for-iam-policies)
+ [Condition keys for Amazon Translate](#amazontranslate-policy-keys)

## Actions defined by Amazon Translate<a name="amazontranslate-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DeleteTerminology ](https://docs.aws.amazon.com/translate/latest/dg/API_DeleteTerminology.html)  | A synchronous action that deletes a custom terminology\. | Write |  |  |  | 
|   [ DescribeTextTranslationJob ](https://docs.aws.amazon.com/translate/latest/dg/API_DescribeTextTranslationJob.html)  | Gets the properties associated with an asynchronous batch translation job including name, ID, status, source and target languages, input/output S3 buckets, and so on\. | Read |  |  |  | 
|   [ GetTerminology ](https://docs.aws.amazon.com/translate/latest/dg/API_GetTerminology.html)  | Retrieves a custom terminology\. | Read |  |  |  | 
|   [ ImportTerminology ](https://docs.aws.amazon.com/translate/latest/dg/API_ImportTerminology.html)  | Creates or updates a custom terminology, depending on whether or not one already exists for the given terminology name\. | Write |  |  |  | 
|   [ ListTerminologies ](https://docs.aws.amazon.com/translate/latest/dg/API_ListTerminologies.html)  | Provides a list of custom terminologies associated with your account\. | Read |  |  |  | 
|   [ ListTextTranslationJobs ](https://docs.aws.amazon.com/translate/latest/dg/API_ListTextTranslationJobs.html)  | Gets a list of the batch translation jobs that you have submitted\. | Read |  |  |  | 
|   [ StartTextTranslationJob ](https://docs.aws.amazon.com/translate/latest/dg/API_StartTextTranslationJob.html)  | Starts an asynchronous batch translation job\. Batch translation jobs can be used to translate large volumes of text across multiple documents at once\. | Write |  |  |  | 
|   [ StopTextTranslationJob ](https://docs.aws.amazon.com/translate/latest/dg/API_StopTextTranslationJob.html)  | Stops an asynchronous batch translation job that is in progress\. | Write |  |  |  | 
|   [ TranslateText ](https://docs.aws.amazon.com/translate/latest/dg/API_TranslateText.html)  | Translate text from a source language to a target language\. | Read |  |  |  | 

## Resource types defined by Amazon Translate<a name="amazontranslate-resources-for-iam-policies"></a>

Amazon Translate does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Translate, specify `“Resource”: “*”` in your policy\.

## Condition keys for Amazon Translate<a name="amazontranslate-policy-keys"></a>

Translate has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.