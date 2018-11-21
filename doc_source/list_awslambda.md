# Actions, Resources, and Condition Keys for AWS Lambda<a name="list_awslambda"></a>

AWS Lambda \(service prefix: `lambda`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/lambda/latest/dg/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/lambda/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/lambda/latest/dg/lambda-auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Lambda](#awslambda-actions-as-permissions)
+ [Resources Defined by Lambda](#awslambda-resources-for-iam-policies)
+ [Condition Keys for AWS Lambda](#awslambda-policy-keys)

## Actions Defined by AWS Lambda<a name="awslambda-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddPermission ](https://docs.aws.amazon.com/lambda/latest/dg/API_AddPermission.html)  | Adds a permission to the resource policy associated with the specified AWS Lambda function\. | Permissions management |   [ function\* ](#awslambda-function)   |  |  | 
|   [ CreateAlias ](https://docs.aws.amazon.com/lambda/latest/dg/API_CreateAlias.html)  | Creates an alias that points to the specified Lambda function version\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ CreateEventSourceMapping ](https://docs.aws.amazon.com/lambda/latest/dg/API_CreateEventSourceMapping.html)  | Identifies a stream as an event source for a Lambda function\. | Write |  |  |  | 
|   [ CreateFunction ](https://docs.aws.amazon.com/lambda/latest/dg/API_CreateFunction.html)  | Creates a new Lambda function\. | Write |  |  |  | 
|   [ DeleteAlias ](https://docs.aws.amazon.com/lambda/latest/dg/API_DeleteAlias.html)  | Deletes the specified Lambda function alias\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ DeleteEventSourceMapping ](https://docs.aws.amazon.com/lambda/latest/dg/API_DeleteEventSourceMapping.html)  | Removes an event source mapping\. | Write |  |  |  | 
|   [ DeleteFunction ](https://docs.aws.amazon.com/lambda/latest/dg/API_DeleteFunction.html)  | Deletes the specified Lambda function code and configuration\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ DeleteFunctionConcurrency ](https://docs.aws.amazon.com/lambda/latest/dg/API_DeleteFunctionConcurrency.html)  | Remove concurrency limit set on a Lambda function\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   EnableReplication  | Adds a permission to resource policy that gives Lambda replication service permission to get function code and configuration\. | Permissions management |   [ function\* ](#awslambda-function)   |  |  | 
|   [ GetAccountSettings ](https://docs.aws.amazon.com/lambda/latest/dg/API_GetAccountSettings.html)  | Returns account limits and usage statistics, such as concurrency and code storage\. | Read |  |  |  | 
|   [ GetAlias ](https://docs.aws.amazon.com/lambda/latest/dg/API_GetAlias.html)  | Returns the specified alias information such as the alias ARN, description, and function version it is pointing to\. | Read |   [ function\* ](#awslambda-function)   |  |  | 
|   [ GetEventSourceMapping ](https://docs.aws.amazon.com/lambda/latest/dg/API_GetEventSourceMapping.html)  | Returns configuration information for the specified event source mapping\. | Read |  |  |  | 
|   [ GetFunction ](https://docs.aws.amazon.com/lambda/latest/dg/API_GetFunction.html)  | Returns the configuration information of the Lambda function and a presigned URL link to the \.zip file you uploaded with CreateFunction so you can download the \.zip file\. | Read |   [ function\* ](#awslambda-function)   |  |  | 
|   [ GetFunctionConfiguration ](https://docs.aws.amazon.com/lambda/latest/dg/API_GetFunctionConfiguration.html)  | Returns the configuration information of the Lambda function\. | Read |   [ function\* ](#awslambda-function)   |  |  | 
|   [ GetPolicy ](https://docs.aws.amazon.com/lambda/latest/dg/API_GetPolicy.html)  | Returns the resource policy associated with the specified Lambda function\. | Read |   [ function\* ](#awslambda-function)   |  |  | 
|   [ InvokeAsync ](https://docs.aws.amazon.com/lambda/latest/dg/API_InvokeAsync.html)  | Submits an invocation request to AWS Lambda\. Is deprecated | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ InvokeFunction ](https://docs.aws.amazon.com/lambda/latest/dg/API_Invoke.html)  | Invokes a specific Lambda function\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ ListAliases ](https://docs.aws.amazon.com/lambda/latest/dg/API_ListAliases.html)  | Returns list of aliases created for a Lambda function\. | List |   [ function\* ](#awslambda-function)   |  |  | 
|   [ ListEventSourceMappings ](https://docs.aws.amazon.com/lambda/latest/dg/API_ListEventSourceMappings.html)  | Returns a list of event source mappings you created using the CreateEventSourceMapping\. | List |  |  |  | 
|   [ ListFunctions ](https://docs.aws.amazon.com/lambda/latest/dg/API_ListFunctions.html)  | Returns a list of your Lambda functions\. | List |  |  |  | 
|   [ ListTags ](https://docs.aws.amazon.com/lambda/latest/dg/API_ListTagsForResource.html)  | Lists tags for a Lambda function\. | Read |   [ function\* ](#awslambda-function)   |  |  | 
|   [ ListVersionsByFunction ](https://docs.aws.amazon.com/lambda/latest/dg/API_ListVersionsByFunction.html)  | List all versions of a function\. | List |   [ function\* ](#awslambda-function)   |  |  | 
|   [ PublishVersion ](https://docs.aws.amazon.com/lambda/latest/dg/API_PublishVersion.html)  | Publishes a version of your function from the current snapshot of $LATEST\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ PutFunctionConcurrency ](https://docs.aws.amazon.com/lambda/latest/dg/API_PutFunctionConcurrency.html)  | Adds concurrency limit to a Lambda function\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ RemovePermission ](https://docs.aws.amazon.com/lambda/latest/dg/API_RemovePermission.html)  | You can remove individual permissions from an resource policy associated with a Lambda function by providing a statement ID that you provided when you added the permission\. | Permissions management |   [ function\* ](#awslambda-function)   |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/lambda/latest/dg/API_TagResources.html)  | Adds tags to a Lambda function\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/lambda/latest/dg/API_UntagResource.html)  | Removes tags from a Lambda function\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ UpdateAlias ](https://docs.aws.amazon.com/lambda/latest/dg/API_UpdateAlias.html)  | Using this API you can update the function version to which the alias points and the alias description\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ UpdateEventSourceMapping ](https://docs.aws.amazon.com/lambda/latest/dg/API_UpdateEventSourceMapping.html)  | You can update an event source mapping\. | Write |  |  |  | 
|   [ UpdateFunctionCode ](https://docs.aws.amazon.com/lambda/latest/dg/API_UpdateFunctionCode.html)  | Updates the code for the specified Lambda function\. | Write |   [ function\* ](#awslambda-function)   |  |  | 
|   [ UpdateFunctionConfiguration ](https://docs.aws.amazon.com/lambda/latest/dg/API_UpdateFunctionConfiguration.html)  | Updates the configuration parameters for the specified Lambda function by using the values provided in the request\. | Write |   [ function\* ](#awslambda-function)   |  |  | 

## Resources Defined by Lambda<a name="awslambda-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awslambda-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ function ](https://docs.aws.amazon.com/lambda/latest/dg/lambda-api-permissions-ref.html)  |  arn:$\{Partition\}:lambda:$\{Region\}:$\{Account\}:function:$\{FunctionName\}  |  | 

## Condition Keys for AWS Lambda<a name="awslambda-policy-keys"></a>

Lambda has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.