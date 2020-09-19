# Actions, resources, and condition keys for AWS Cost and Usage Report<a name="list_awscostandusagereport"></a>

AWS Cost and Usage Report \(service prefix: `cur`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/api-reference.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/control-access-billing.html) permission policies\.

**Topics**
+ [Actions defined by AWS Cost and Usage Report](#awscostandusagereport-actions-as-permissions)
+ [Resource types defined by AWS Cost and Usage Report](#awscostandusagereport-resources-for-iam-policies)
+ [Condition keys for AWS Cost and Usage Report](#awscostandusagereport-policy-keys)

## Actions defined by AWS Cost and Usage Report<a name="awscostandusagereport-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DeleteReportDefinition ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/delete-report-definition.html)  | Delete Cost and Usage Report Definition | Write |   [ cur\* ](#awscostandusagereport-cur)   |  |  | 
|   [ DescribeReportDefinitions ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/describe-report-definitions.html)  | Get Cost and Usage Report Definitions | Read |  |  |  | 
|   [ ModifyReportDefinition ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/modify-report-definition.html)  | Modify Cost and Usage Report Definition | Write |   [ cur\* ](#awscostandusagereport-cur)   |  |  | 
|   [ PutReportDefinition ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/put-report-definition.html)  | Write Cost and Usage Report Definition | Write |   [ cur\* ](#awscostandusagereport-cur)   |  |  | 

## Resource types defined by AWS Cost and Usage Report<a name="awscostandusagereport-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscostandusagereport-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ cur ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-reports.html#enhanced-reports)  |  arn:$\{Partition\}:cur:$\{Region\}:$\{Account\}:definition/$\{ReportName\}  |  | 

## Condition keys for AWS Cost and Usage Report<a name="awscostandusagereport-policy-keys"></a>

Cost and Usage Report has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.