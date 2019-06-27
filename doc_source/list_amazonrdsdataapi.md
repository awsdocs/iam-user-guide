# Actions, Resources, and Condition Keys for Amazon RDS Data API<a name="list_amazonrdsdataapi"></a>

Amazon RDS Data API \(service prefix: `rds-data`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/RDS/DataAPIReference)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/RDS/DataAPIReference/API_Operations.html/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/RDS/DataAPIReference/API_Operations.html/) permission policies\.

**Topics**
+ [Actions Defined by Amazon RDS Data API](#amazonrdsdataapi-actions-as-permissions)
+ [Resources Defined by Amazon RDS Data API](#amazonrdsdataapi-resources-for-iam-policies)
+ [Condition Keys for Amazon RDS Data API](#amazonrdsdataapi-policy-keys)

## Actions Defined by Amazon RDS Data API<a name="amazonrdsdataapi-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchExecuteStatement ](https://docs.aws.amazon.com/RDS/DataAPIReference/API_Operations.html/API_BatchExecuteStatement.html)  | Runs a batch SQL statement over an array of data\. | Write |  |  |  | 
|   [ BeginTransaction ](https://docs.aws.amazon.com/RDS/DataAPIReference/API_Operations.html/API_BeginTransaction.html)  | Starts a SQL transaction\. | Write |  |  |  | 
|   [ CommitTransaction ](https://docs.aws.amazon.com/RDS/DataAPIReference/API_Operations.html/API_CommitTransaction.html)  | Ends a SQL transaction started with the BeginTransaction operation and commits the changes\. | Write |  |  |   rds\-data:BeginTransaction   | 
|   [ ExecuteStatement ](https://docs.aws.amazon.com/RDS/DataAPIReference/API_Operations.html/API_ExecuteStatement.html)  | Runs a SQL statement against a database\. | Write |  |  |  | 
|   [ RollbackTransaction ](https://docs.aws.amazon.com/RDS/DataAPIReference/API_Operations.html/API_RollbackTransaction.html)  | Performs a rollback of a transaction\. Rolling back a transaction cancels its changes\. | Write |  |  |   rds\-data:BeginTransaction   | 

## Resources Defined by Amazon RDS Data API<a name="amazonrdsdataapi-resources-for-iam-policies"></a>

Amazon RDS Data API has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon RDS Data API<a name="amazonrdsdataapi-policy-keys"></a>

RDS Data API has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.