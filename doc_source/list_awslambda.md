# Actions, Resources, and Condition Keys for AWS Lambda<a name="list_awslambda"></a>

AWS Lambda \(service prefix: `lambda`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/lambda/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/lambda/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/lambda/lambda-auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Lambda](#awslambda-actions-as-permissions)
+ [Resources Defined by Lambda](#awslambda-resources-for-iam-policies)
+ [Condition Keys for AWS Lambda](#awslambda-policy-keys)

## Actions Defined by AWS Lambda<a name="awslambda-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/lambda/API_AddPermission.html](http://docs.aws.amazon.com/lambda/API_AddPermission.html) | Adds a permission to the resource policy associated with the specified AWS Lambda function\. | Permissions management | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_CreateAlias.html](http://docs.aws.amazon.com/lambda/API_CreateAlias.html) | Creates an alias that points to the specified Lambda function version\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_CreateEventSourceMapping.html](http://docs.aws.amazon.com/lambda/API_CreateEventSourceMapping.html) | Identifies a stream as an event source for a Lambda function\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_CreateFunction.html](http://docs.aws.amazon.com/lambda/API_CreateFunction.html) | Creates a new Lambda function\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_DeleteAlias.html](http://docs.aws.amazon.com/lambda/API_DeleteAlias.html) | Deletes the specified Lambda function alias\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_DeleteEventSourceMapping.html](http://docs.aws.amazon.com/lambda/API_DeleteEventSourceMapping.html) | Removes an event source mapping\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_DeleteFunction.html](http://docs.aws.amazon.com/lambda/API_DeleteFunction.html) | Deletes the specified Lambda function code and configuration\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_DeleteFunctionConcurrency.html](http://docs.aws.amazon.com/lambda/API_DeleteFunctionConcurrency.html) | Remove concurrency limit set on a Lambda function\. | Write | [function\*](#awslambda-function)  |  |  | 
| EnableReplication | Adds a permission to resource policy that gives Lambda replication service permission to get function code and configuration\. | Permissions management | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_GetAccountSettings.html](http://docs.aws.amazon.com/lambda/API_GetAccountSettings.html) | Returns account limits and usage statistics, such as concurrency and code storage\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_GetAlias.html](http://docs.aws.amazon.com/lambda/API_GetAlias.html) | Returns the specified alias information such as the alias ARN, description, and function version it is pointing to\. | Read | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_GetEventSourceMapping.html](http://docs.aws.amazon.com/lambda/API_GetEventSourceMapping.html) | Returns configuration information for the specified event source mapping\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_GetFunction.html](http://docs.aws.amazon.com/lambda/API_GetFunction.html) | Returns the configuration information of the Lambda function and a presigned URL link to the \.zip file you uploaded with CreateFunction so you can download the \.zip file\. | Read | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_GetFunctionConfiguration.html](http://docs.aws.amazon.com/lambda/API_GetFunctionConfiguration.html) | Returns the configuration information of the Lambda function\. | Read | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_GetPolicy.html](http://docs.aws.amazon.com/lambda/API_GetPolicy.html) | Returns the resource policy associated with the specified Lambda function\. | Read | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_InvokeAsync.html](http://docs.aws.amazon.com/lambda/API_InvokeAsync.html) | Submits an invocation request to AWS Lambda\. Is deprecated | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_Invoke.html](http://docs.aws.amazon.com/lambda/API_Invoke.html) | Invokes a specific Lambda function\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_ListAliases.html](http://docs.aws.amazon.com/lambda/API_ListAliases.html) | Returns list of aliases created for a Lambda function\. | List | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_ListEventSourceMappings.html](http://docs.aws.amazon.com/lambda/API_ListEventSourceMappings.html) | Returns a list of event source mappings you created using the CreateEventSourceMapping\. | List |  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_ListFunctions.html](http://docs.aws.amazon.com/lambda/API_ListFunctions.html) | Returns a list of your Lambda functions\. | List |  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_ListTagsForResource.html](http://docs.aws.amazon.com/lambda/API_ListTagsForResource.html) | Lists tags for a Lambda function\. | Read | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_ListVersionsByFunction.html](http://docs.aws.amazon.com/lambda/API_ListVersionsByFunction.html) | List all versions of a function\. | List | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_PublishVersion.html](http://docs.aws.amazon.com/lambda/API_PublishVersion.html) | Publishes a version of your function from the current snapshot of $LATEST\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_PutFunctionConcurrency.html](http://docs.aws.amazon.com/lambda/API_PutFunctionConcurrency.html) | Adds concurrency limit to a Lambda function\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_RemovePermission.html](http://docs.aws.amazon.com/lambda/API_RemovePermission.html) | You can remove individual permissions from an resource policy associated with a Lambda function by providing a statement ID that you provided when you added the permission\. | Permissions management | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_TagResources.html](http://docs.aws.amazon.com/lambda/API_TagResources.html) | Adds tags to a Lambda function\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_UntagResource.html](http://docs.aws.amazon.com/lambda/API_UntagResource.html) | Removes tags from a Lambda function\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_UpdateAlias.html](http://docs.aws.amazon.com/lambda/API_UpdateAlias.html) | Using this API you can update the function version to which the alias points and the alias description\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_UpdateEventSourceMapping.html](http://docs.aws.amazon.com/lambda/API_UpdateEventSourceMapping.html) | You can update an event source mapping\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_UpdateFunctionCode.html](http://docs.aws.amazon.com/lambda/API_UpdateFunctionCode.html) | Updates the code for the specified Lambda function\. | Write | [function\*](#awslambda-function)  |  |  | 
| [http://docs.aws.amazon.com/lambda/API_UpdateFunctionConfiguration.html](http://docs.aws.amazon.com/lambda/API_UpdateFunctionConfiguration.html) | Updates the configuration parameters for the specified Lambda function by using the values provided in the request\. | Write |  |  |  | 

## Resources Defined by Lambda<a name="awslambda-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awslambda-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/lambda/lambda-api-permissions-ref.html](http://docs.aws.amazon.com/lambda/lambda-api-permissions-ref.html) | arn:$\{Partition\}:lambda:$\{Region\}:$\{Account\}:function:$\{FunctionName\} |  | 

## Condition Keys for AWS Lambda<a name="awslambda-policy-keys"></a>

Lambda has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.