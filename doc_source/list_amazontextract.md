# Actions, Resources, and Condition Keys for Amazon Textract<a name="list_amazontextract"></a>

Amazon Textract \(service prefix: `textract`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/textract/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/textract/latest/dg/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/textract/latest/dg/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Textract](#amazontextract-actions-as-permissions)
+ [Resource Types Defined by Amazon Textract](#amazontextract-resources-for-iam-policies)
+ [Condition Keys for Amazon Textract](#amazontextract-policy-keys)

## Actions Defined by Amazon Textract<a name="amazontextract-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AnalyzeDocument ](https://docs.aws.amazon.com/textract/latest/dg/API_AnalyzeDocument.html)  | Detects instances of real\-world document entities within an image provided as input\. | Read |  |  |   s3:GetObject   | 
|   [ DetectDocumentText ](https://docs.aws.amazon.com/textract/latest/dg/API_DetectDocumentText.html)  | Detects text in document images\. | Read |  |  |   s3:GetObject   | 
|   [ GetDocumentAnalysis ](https://docs.aws.amazon.com/textract/latest/dg/API_GetDocumentAnalysis.html)  | Returns information about a document analysis job\. | Read |  |  |  | 
|   [ GetDocumentTextDetection ](https://docs.aws.amazon.com/textract/latest/dg/API_GetDocumentTextDetection.html)  | Returns information about a document text detection job\. | Read |  |  |  | 
|   [ StartDocumentAnalysis ](https://docs.aws.amazon.com/textract/latest/dg/API_StartDocumentAnalysis.html)  | Starts an asynchronous job to detect instances of real\-world document entities within an image or pdf provided as input\. | Write |  |  |   s3:GetObject   | 
|   [ StartDocumentTextDetection ](https://docs.aws.amazon.com/textract/latest/dg/API_StartDocumentTextDetection.html)  | Starts an asynchronous job to detect text in document images or pdfs\. | Write |  |  |   s3:GetObject   | 

## Resource Types Defined by Amazon Textract<a name="amazontextract-resources-for-iam-policies"></a>

Amazon Textract does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Textract, specify `“Resource”: “*”` in your policy\.

## Condition Keys for Amazon Textract<a name="amazontextract-policy-keys"></a>

Textract has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.