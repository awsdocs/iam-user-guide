# Actions, resources, and condition keys for Database Query Metadata Service<a name="list_databasequerymetadataservice"></a>

Database Query Metadata Service \(service prefix: `dbqms`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html) permission policies\.

**Topics**
+ [Actions defined by Database Query Metadata Service](#databasequerymetadataservice-actions-as-permissions)
+ [Resource types defined by Database Query Metadata Service](#databasequerymetadataservice-resources-for-iam-policies)
+ [Condition keys for Database Query Metadata Service](#databasequerymetadataservice-policy-keys)

## Actions defined by Database Query Metadata Service<a name="databasequerymetadataservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateFavoriteQuery ](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html#CreateFavoriteQuery)  | Creates a new favorite query | Write |  |  |  | 
|   CreateQueryHistory  | Add a query to the history | Write |  |  |  | 
|   [ DeleteFavoriteQueries ](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html#DeleteFavoriteQueries)  | Delete saved queries | Write |  |  |  | 
|   [ DeleteQueryHistory ](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html#DeleteQueryHistory)  | Delete a historical query | Write |  |  |  | 
|   [ DescribeFavoriteQueries ](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html#DescribeFavoriteQueries)  | List saved queries and associated metadata | List |  |  |  | 
|   [ DescribeQueryHistory ](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html#DescribeQueryHistory)  | List history of queries that were run | List |  |  |  | 
|   [ GetQueryString ](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html#GetQueryString)  | Retrieve favorite or history query string by id | Read |  |  |  | 
|   [ UpdateFavoriteQuery ](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html#UpdateFavoriteQuery)  | Update saved query and description | Write |  |  |  | 
|   [ UpdateQueryHistory ](https://docs.aws.amazon.com/qldb/latest/developerguide/dbqms-api.html#UpdateQueryHistory)  | Update the query history | Write |  |  |  | 

## Resource types defined by Database Query Metadata Service<a name="databasequerymetadataservice-resources-for-iam-policies"></a>

Database Query Metadata Service does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Database Query Metadata Service, specify `“Resource”: “*”` in your policy\.

## Condition keys for Database Query Metadata Service<a name="databasequerymetadataservice-policy-keys"></a>

DBQMS has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.

**Note**  
$\{ConceptsDocRoot\}