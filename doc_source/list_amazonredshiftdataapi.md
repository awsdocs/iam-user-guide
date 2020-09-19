# Actions, resources, and condition keys for Amazon Redshift Data API<a name="list_amazonredshiftdataapi"></a>

Amazon Redshift Data API \(service prefix: `redshift-data`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/redshift/latest/mgmt/data-api.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/redshift-data/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-authentication-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Redshift Data API](#amazonredshiftdataapi-actions-as-permissions)
+ [Resource types defined by Amazon Redshift Data API](#amazonredshiftdataapi-resources-for-iam-policies)
+ [Condition keys for Amazon Redshift Data API](#amazonredshiftdataapi-policy-keys)

## Actions defined by Amazon Redshift Data API<a name="amazonredshiftdataapi-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CancelStatement ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_CancelStatement.html)  | Grants permission to cancel a running query | Write |  |  |  | 
|   [ DescribeStatement ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_DescribeStatement.html)  | Grants permission to retrieve detailed information about a statement execution | Read |  |  |  | 
|   [ DescribeTable ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_DescribeTable.html)  | Grants permission to retrieve metadata about a particular table | Read |  |  |  | 
|   [ ExecuteStatement ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_ExecuteStatement.html)  | Grants permission to execute a query | Write |  |  |  | 
|   [ GetStatementResult ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_FetchResult.html)  | Grants permission to fetch the result of a query | Read |  |  |  | 
|   [ ListDatabases ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_ListDatabases.html)  | Grants permission to list databases for a given cluster | List |  |  |  | 
|   [ ListSchemas ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_ListSchemas.html)  | Grants permission to list schemas for a given cluster | List |  |  |  | 
|   [ ListStatements ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_ListStatements.html)  | Grants permission to list queries for a given principal | List |  |  |  | 
|   [ ListTables ](https://docs.aws.amazon.com/redshift-data/latest/APIReference/API_ListTables.html)  | Grants permission to list tables for a given cluster | List |  |  |  | 

## Resource types defined by Amazon Redshift Data API<a name="amazonredshiftdataapi-resources-for-iam-policies"></a>

Amazon Redshift Data API does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Redshift Data API, specify `“Resource”: “*”` in your policy\.

## Condition keys for Amazon Redshift Data API<a name="amazonredshiftdataapi-policy-keys"></a>

Redshift Data API has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.