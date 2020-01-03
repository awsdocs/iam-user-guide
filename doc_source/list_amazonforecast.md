# Actions, Resources, and Condition Keys for Amazon Forecast<a name="list_amazonforecast"></a>

Amazon Forecast \(service prefix: `forecast`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/forecast/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/forecast/latest/dg/api-reference.html)\.

**Topics**
+ [Actions Defined by Amazon Forecast](#amazonforecast-actions-as-permissions)
+ [Resource Types Defined by Amazon Forecast](#amazonforecast-resources-for-iam-policies)
+ [Condition Keys for Amazon Forecast](#amazonforecast-policy-keys)

## Actions Defined by Amazon Forecast<a name="amazonforecast-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonforecast.html)

## Resource Types Defined by Amazon Forecast<a name="amazonforecast-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonforecast-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   dataset  |  arn:$\{Partition\}:forecast:$\{Region\}:$\{Account\}:dataset/$\{ResourceId\}  |  | 
|   datasetGroup  |  arn:$\{Partition\}:forecast:$\{Region\}:$\{Account\}:dataset\-group/$\{ResourceId\}  |  | 
|   datasetImportJob  |  arn:$\{Partition\}:forecast:$\{Region\}:$\{Account\}:dataset\-import\-job/$\{ResourceId\}  |  | 
|   algorithm  |  arn:$\{Partition\}:forecast:::algorithm/$\{ResourceId\}  |  | 
|   predictor  |  arn:$\{Partition\}:forecast:$\{Region\}:$\{Account\}:predictor/$\{ResourceId\}  |  | 
|   forecast  |  arn:$\{Partition\}:forecast:$\{Region\}:$\{Account\}:forecast/$\{ResourceId\}  |  | 
|   forecastExport  |  arn:$\{Partition\}:forecast:$\{Region\}:$\{Account\}:forecast\-export\-job/$\{ResourceId\}  |  | 

## Condition Keys for Amazon Forecast<a name="amazonforecast-policy-keys"></a>

Forecast has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.