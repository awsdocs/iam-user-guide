# Actions, resources, and condition keys for AWS Accounts<a name="list_awsaccounts"></a>

AWS Accounts \(service prefix: `account`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/general/latest/gr/regions_manage.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/general/latest/gr/regions_manage.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/general/latest/gr/regions_manage.html) permission policies\.

**Topics**
+ [Actions defined by AWS Accounts](#awsaccounts-actions-as-permissions)
+ [Resource types defined by AWS Accounts](#awsaccounts-resources-for-iam-policies)
+ [Condition keys for AWS Accounts](#awsaccounts-policy-keys)

## Actions defined by AWS Accounts<a name="awsaccounts-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   DisableRegion  | Grants permission to disable a region | Write |  |   [ account:TargetRegion ](#awsaccounts-account_TargetRegion)   |  | 
|   EnableRegion  | Grants permission to enable a region | Write |  |   [ account:TargetRegion ](#awsaccounts-account_TargetRegion)   |  | 
|   ListRegions  | Grants permission to list regions | List |  |  |  | 

## Resource types defined by AWS Accounts<a name="awsaccounts-resources-for-iam-policies"></a>

AWS Accounts does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Accounts, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS Accounts<a name="awsaccounts-policy-keys"></a>

AWS Accounts defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   account:TargetRegion  | Filters access by a list of regions | String | 