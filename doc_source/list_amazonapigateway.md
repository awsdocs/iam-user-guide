# Actions, Resources, and Condition Keys for Amazon API Gateway<a name="list_amazonapigateway"></a>

Amazon API Gateway \(service prefix: `execute-api`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/apigateway/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/apigateway/api-reference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-control-access-to-api.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon API Gateway](#amazonapigateway-actions-as-permissions)
+ [Resources Defined by ExecuteAPI](#amazonapigateway-resources-for-iam-policies)
+ [Condition Keys for Amazon API Gateway](#amazonapigateway-policy-keys)

## Actions Defined by Amazon API Gateway<a name="amazonapigateway-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/apigateway/api-reference/api-gateway-caching.html](http://docs.aws.amazon.com/apigateway/api-reference/api-gateway-caching.html) | Used to invalidate API cache upon a client request | Write | [execute\-api\-general\*](#amazonapigateway-execute-api-general)  |  |  | 
| [http://docs.aws.amazon.com/apigateway/api-reference/how-to-call-api.html](http://docs.aws.amazon.com/apigateway/api-reference/how-to-call-api.html) | Used to invoke an API upon a client request | Write | [execute\-api\-general\*](#amazonapigateway-execute-api-general)  |  |  | 

## Resources Defined by ExecuteAPI<a name="amazonapigateway-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonapigateway-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| execute\-api\-general | arn:$\{Partition\}:execute\-api:$\{Region\}:$\{Account\}:$\{ApiId\}/$\{Stage\}/$\{Method\}/$\{ApiSpecificResourcePath\} |  | 

## Condition Keys for Amazon API Gateway<a name="amazonapigateway-policy-keys"></a>

ExecuteAPI has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.