# Actions, resources, and condition keys for Amazon Mobile Analytics<a name="list_amazonmobileanalytics"></a>

Amazon Mobile Analytics \(service prefix: `mobileanalytics`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/mobileanalytics/latest/ug/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/mobileanalytics/latest/ug/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/mobileanalytics/latest/ug/access_permissions.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Mobile Analytics](#amazonmobileanalytics-actions-as-permissions)
+ [Resource types defined by Amazon Mobile Analytics](#amazonmobileanalytics-resources-for-iam-policies)
+ [Condition keys for Amazon Mobile Analytics](#amazonmobileanalytics-policy-keys)

## Actions defined by Amazon Mobile Analytics<a name="amazonmobileanalytics-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   GetFinancialReports  | Grant access to financial metrics for an app | Read |  |  |  | 
|   GetReports  | Grant access to standard metrics for an app | Read |  |  |  | 
|   [ PutEvents ](https://docs.aws.amazon.com/mobileanalytics/latest/ug/PutEvents.html)  | The PutEvents operation records one or more events | Write |  |  |  | 

## Resource types defined by Amazon Mobile Analytics<a name="amazonmobileanalytics-resources-for-iam-policies"></a>

Amazon Mobile Analytics does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Mobile Analytics, specify `“Resource”: “*”` in your policy\.

## Condition keys for Amazon Mobile Analytics<a name="amazonmobileanalytics-policy-keys"></a>

Mobile Analytics has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.