# Actions, Resources, and Condition Keys for AWS Performance Insights<a name="list_awsperformanceinsights"></a>

AWS Performance Insights \(service prefix: `pi`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by AWS Performance Insights](#awsperformanceinsights-actions-as-permissions)
+ [Resources Defined by Performance Insights](#awsperformanceinsights-resources-for-iam-policies)
+ [Condition Keys for AWS Performance Insights](#awsperformanceinsights-policy-keys)

## Actions Defined by AWS Performance Insights<a name="awsperformanceinsights-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   DescribeDimensionKeys  | For a specific time period, retrieve the top N dimension keys for a metric\. | Read |   [ metric\-resource\* ](#awsperformanceinsights-metric-resource)   |  |  | 
|   GetResourceMetrics  | Retrieve PI metrics for a set of data sources, over a time period\. | Read |   [ metric\-resource\* ](#awsperformanceinsights-metric-resource)   |  |  | 

## Resources Defined by Performance Insights<a name="awsperformanceinsights-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsperformanceinsights-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   metric\-resource  |  arn:$\{Partition\}:pi:$\{Region\}:$\{Account\}:metrics/$\{ServiceType\}/$\{Identifier\}  |  | 

## Condition Keys for AWS Performance Insights<a name="awsperformanceinsights-policy-keys"></a>

Performance Insights has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.