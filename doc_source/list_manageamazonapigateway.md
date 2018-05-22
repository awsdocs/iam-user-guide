# Actions, Resources, and Condition Keys for Manage Amazon API Gateway<a name="list_manageamazonapigateway"></a>

Manage Amazon API Gateway \(service prefix: `apigateway`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/apigateway/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/apigateway/api-reference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-control-access-to-api.html) permission policies\.

**Topics**
+ [Actions Defined by Manage Amazon API Gateway](#manageamazonapigateway-actions-as-permissions)
+ [Resources Defined by API Gateway](#manageamazonapigateway-resources-for-iam-policies)
+ [Condition Keys for Manage Amazon API Gateway](#manageamazonapigateway-policy-keys)

## Actions Defined by Manage Amazon API Gateway<a name="manageamazonapigateway-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/apigateway/api-reference/API_DELETE.html](http://docs.aws.amazon.com/apigateway/api-reference/API_DELETE.html) | Used to delete resources | Write | [apigateway\-general\*](#manageamazonapigateway-apigateway-general)  |  |  | 
| [http://docs.aws.amazon.com/apigateway/api-reference/API_GET.html](http://docs.aws.amazon.com/apigateway/api-reference/API_GET.html) | Used to get information about resources | Read | [apigateway\-general\*](#manageamazonapigateway-apigateway-general)  |  |  | 
| [http://docs.aws.amazon.com/apigateway/api-reference/API_HEAD.html](http://docs.aws.amazon.com/apigateway/api-reference/API_HEAD.html) | Same as GET but does not return the resource representation\. Used in testing scenarios | Read | [apigateway\-general\*](#manageamazonapigateway-apigateway-general)  |  |  | 
| [http://docs.aws.amazon.com/apigateway/api-reference/API_OPTIONS.html](http://docs.aws.amazon.com/apigateway/api-reference/API_OPTIONS.html) | Used by callers to get information about available communication options for the target service | Read | [apigateway\-general\*](#manageamazonapigateway-apigateway-general)  |  |  | 
| [http://docs.aws.amazon.com/apigateway/api-reference/API_PATCH.html](http://docs.aws.amazon.com/apigateway/api-reference/API_PATCH.html) | Used to update resources | Write | [apigateway\-general\*](#manageamazonapigateway-apigateway-general)  |  |  | 
| [http://docs.aws.amazon.com/apigateway/api-reference/API_POST.html](http://docs.aws.amazon.com/apigateway/api-reference/API_POST.html) | Used to create child resources | Write | [apigateway\-general\*](#manageamazonapigateway-apigateway-general)  |  |  | 
| [http://docs.aws.amazon.com/apigateway/api-reference/API_PUT.html](http://docs.aws.amazon.com/apigateway/api-reference/API_PUT.html) | Used to update resources \(and, although not recommended, can be used to create child resources\) | Write | [apigateway\-general\*](#manageamazonapigateway-apigateway-general)  |  |  | 

## Resources Defined by API Gateway<a name="manageamazonapigateway-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#manageamazonapigateway-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/apigateway/latest/developerguide/permissions.html](http://docs.aws.amazon.com/apigateway/latest/developerguide/permissions.html) | arn:$\{Partition\}:apigateway:$\{Region\}::$\{ApiGatewayResourcePath\} |  | 

## Condition Keys for Manage Amazon API Gateway<a name="manageamazonapigateway-policy-keys"></a>

API Gateway has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.