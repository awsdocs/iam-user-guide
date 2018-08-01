# Actions, Resources, and Condition Keys for Amazon Athena<a name="list_amazonathena"></a>

Amazon Athena \(service prefix: `athena`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/athena/latest/ug/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/athena/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/athena/latest/ug/access.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Athena](#amazonathena-actions-as-permissions)
+ [Resources Defined by Athena](#amazonathena-resources-for-iam-policies)
+ [Condition Keys for Amazon Athena](#amazonathena-policy-keys)

## Actions Defined by Amazon Athena<a name="amazonathena-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchGetNamedQuery ](http://docs.aws.amazon.com/athena/latest/APIReference/API_BatchGetNamedQuery.html)  | Grants permissions to get information about one or more named queries\. | Read |  |  |  | 
|   [ BatchGetQueryExecution ](http://docs.aws.amazon.com/athena/latest/APIReference/API_BatchGetQueryExecution.html)  | Grants permissions to get information about one or more query executions\. | Read |  |  |  | 
|   [ CancelQueryExecution ](http://docs.aws.amazon.com/athena/latest/APIReference/API_StopQueryExecution.html)  | Deprecated\. Applies only to AWS services and principals that use Athena JDBC driver earlier than 1\.1\.0\. Use StopQueryExecution otherwise\. | Write |  |  |  | 
|   [ CreateNamedQuery ](http://docs.aws.amazon.com/athena/latest/APIReference/API_CreateNamedQuery.html)  | Grants permissions to create a named query\. | Write |  |  |  | 
|   [ DeleteNamedQuery ](http://docs.aws.amazon.com/athena/latest/APIReference/API_DeleteNamedQuery.html)  | Grants permissions to delete a named query specified\. | Write |  |  |  | 
|   [ GetCatalogs ](https://docs.aws.amazon.com/athena/latest/ug/connect-with-previous-jdbc.html#jdbc-prev-version-policies)  | Applies only to AWS services managed policy and principals that use an Athena JDBC driver version 1\.1\.0\. Grants permissions to enable access to databases and tables\. | Read |  |  |  | 
|   [ GetExecutionEngine ](https://docs.aws.amazon.com/athena/latest/ug/connect-with-previous-jdbc.html#jdbc-prev-version-policies)  | Applies only to AWS services managed policy and principals that use an Athena JDBC driver version 1\.1\.0\. Grants permissions to enable access to the specified database and table\. | Read |  |  |  | 
|   [ GetExecutionEngines ](https://docs.aws.amazon.com/athena/latest/ug/connect-with-previous-jdbc.html#jdbc-prev-version-policies)  | Applies only to AWS services managed policy and principals that use an Athena JDBC driver version 1\.1\.0\. Grants permissions to enable access to databases and tables\. | Read |  |  |  | 
|   [ GetNamedQuery ](http://docs.aws.amazon.com/athena/latest/APIReference/API_GetNamedQuery.html)  | Grants permissions to get information about the specified named query\. | Read |  |  |  | 
|   [ GetNamespace ](https://docs.aws.amazon.com/athena/latest/ug/connect-with-previous-jdbc.html#jdbc-prev-version-policies)  | Applies only to AWS services managed policy and principals that use an Athena JDBC driver version 1\.1\.0\. Grants permissions to enable access to the specified database and table\. | Read |  |  |  | 
|   [ GetNamespaces ](https://docs.aws.amazon.com/athena/latest/ug/connect-with-previous-jdbc.html#jdbc-prev-version-policies)  | Applies only to AWS services managed policy and principals that use an Athena JDBC driver version 1\.1\.0\. Grants permissions to enable access to databases and tables\. | Read |  |  |  | 
|   [ GetQueryExecution ](http://docs.aws.amazon.com/athena/latest/APIReference/API_GetQueryExecution.html)  | Grants permissions to get information about the specified query execution\. | Read |  |  |  | 
|   [ GetQueryExecutions ](http://docs.aws.amazon.com/athena/latest/APIReference/API_ListQueryExecutions.html)  | Deprecated\. Applies only to AWS services and principals that use Athena JDBC driver earlier than 1\.1\.0\. Use ListQueryExecutions otherwise\. | Read |  |  |  | 
|   [ GetQueryResults ](http://docs.aws.amazon.com/athena/latest/APIReference/API_GetQueryResults.html)  | Grants permissions to get the query results\. | Read |  |  |  | 
|   [ GetQueryResultsStream ](https://docs.aws.amazon.com/athena/latest/ug/connect-with-previous-jdbc.html#jdbc-prev-version-policies)  | Grants permissions to get the query results stream\. | Read |  |  |  | 
|   [ GetTable ](https://docs.aws.amazon.com/athena/latest/ug/connect-with-previous-jdbc.html#jdbc-prev-version-policies)  | Applies only to AWS services managed policy and principals that use an Athena JDBC driver version 1\.1\.0\. Grants permissions to enable access to the specified table\. | Read |  |  |  | 
|   [ GetTables ](https://docs.aws.amazon.com/athena/latest/ug/connect-with-previous-jdbc.html#jdbc-prev-version-policies)  | Applies only to AWS services managed policy and principals that use an Athena JDBC driver version 1\.1\.0\. Grants permissions to enable access to tables\. | Read |  |  |  | 
|   [ ListNamedQueries ](http://docs.aws.amazon.com/athena/latest/APIReference/API_ListNamedQueries.html)  | Grants permissions to return a list of named queries in Amazon Athena for the specified AWS account\. | List |  |  |  | 
|   [ ListQueryExecutions ](http://docs.aws.amazon.com/athena/latest/APIReference/API_ListQueryExecutions.html)  | Grants permissions to return a list of query executions for the specified AWS account\. | List |  |  |  | 
|   [ RunQuery ](http://docs.aws.amazon.com/athena/latest/APIReference/API_startQueryExecution.html)  | Deprecated\. Applies only to AWS services and principals that use Athena JDBC driver earlier than 1\.1\.0\. Use StartQueryExecution otherwise\. | Write |  |  |  | 
|   [ StartQueryExecution ](http://docs.aws.amazon.com/athena/latest/APIReference/API_StartQueryExecution.html)  | Grants permissions to start a query execution using an SQL query provided as a string\. | Write |  |  |  | 
|   [ StopQueryExecution ](http://docs.aws.amazon.com/athena/latest/APIReference/API_StopQueryExecution.html)  | Grants permissions to stop the specified query execution\. | Write |  |  |  | 

## Resources Defined by Athena<a name="amazonathena-resources-for-iam-policies"></a>

Amazon Athena has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Athena<a name="amazonathena-policy-keys"></a>

Athena has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.