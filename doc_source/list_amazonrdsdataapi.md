# Actions, resources, and condition keys for Amazon RDS Data API<a name="list_amazonrdsdataapi"></a>

Amazon RDS Data API \(service prefix: `rds-data`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/data-api.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/rdsdataservice/latest/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/UsingWithRDS.IAM.html) permission policies\.

**Topics**
+ [Actions defined by Amazon RDS Data API](#amazonrdsdataapi-actions-as-permissions)
+ [Resource types defined by Amazon RDS Data API](#amazonrdsdataapi-resources-for-iam-policies)
+ [Condition keys for Amazon RDS Data API](#amazonrdsdataapi-policy-keys)

## Actions defined by Amazon RDS Data API<a name="amazonrdsdataapi-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchExecuteStatement ](https://docs.aws.amazon.com/rdsdataservice/latest/APIReference/API_BatchExecuteStatement.html)  | Runs a batch SQL statement over an array of data\. | Write |  |  |  | 
|   [ BeginTransaction ](https://docs.aws.amazon.com/rdsdataservice/latest/APIReference/API_BeginTransaction.html)  | Starts a SQL transaction\. | Write |  |  |  | 
|   [ CommitTransaction ](https://docs.aws.amazon.com/rdsdataservice/latest/APIReference/API_CommitTransaction.html)  | Ends a SQL transaction started with the BeginTransaction operation and commits the changes\. | Write |  |  |   rds\-data:BeginTransaction   | 
|   [ ExecuteSql ](https://docs.aws.amazon.com/rdsdataservice/latest/APIReference/API_ExecuteSql.html)  | Runs one or more SQL statements\. This operation is deprecated\. Use the BatchExecuteStatement or ExecuteStatement operation\. | Write |  |  |  | 
|   [ ExecuteStatement ](https://docs.aws.amazon.com/rdsdataservice/latest/APIReference/API_ExecuteStatement.html)  | Runs a SQL statement against a database\. | Write |  |  |  | 
|   [ RollbackTransaction ](https://docs.aws.amazon.com/rdsdataservice/latest/APIReference/API_RollbackTransaction.html)  | Performs a rollback of a transaction\. Rolling back a transaction cancels its changes\. | Write |  |  |   rds\-data:BeginTransaction   | 

## Resource types defined by Amazon RDS Data API<a name="amazonrdsdataapi-resources-for-iam-policies"></a>

Amazon RDS Data API does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon RDS Data API, specify `“Resource”: “*”` in your policy\.

## Condition keys for Amazon RDS Data API<a name="amazonrdsdataapi-policy-keys"></a>

RDS Data API has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.