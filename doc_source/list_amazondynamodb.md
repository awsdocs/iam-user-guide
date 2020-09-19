# Actions, resources, and condition keys for Amazon DynamoDB<a name="list_amazondynamodb"></a>

Amazon DynamoDB \(service prefix: `dynamodb`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon DynamoDB](#amazondynamodb-actions-as-permissions)
+ [Resource types defined by Amazon DynamoDB](#amazondynamodb-resources-for-iam-policies)
+ [Condition keys for Amazon DynamoDB](#amazondynamodb-policy-keys)

## Actions defined by Amazon DynamoDB<a name="amazondynamodb-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazondynamodb.html)

## Resource types defined by Amazon DynamoDB<a name="amazondynamodb-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazondynamodb-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ index ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.PrimaryKey)  |  arn:$\{Partition\}:dynamodb:$\{Region\}:$\{Account\}:table/$\{TableName\}/index/$\{IndexName\}  |  | 
|   [ stream ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.Streams)  |  arn:$\{Partition\}:dynamodb:$\{Region\}:$\{Account\}:table/$\{TableName\}/stream/$\{StreamLabel\}  |  | 
|   [ table ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.TablesItemsAttributes)  |  arn:$\{Partition\}:dynamodb:$\{Region\}:$\{Account\}:table/$\{TableName\}  |  | 
|   [ backup ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorks.html)  |  arn:$\{Partition\}:dynamodb:$\{Region\}:$\{Account\}:table/$\{TableName\}/backup/$\{BackupName\}  |  | 
|   [ global\-table ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/globaltables_HowItWorks.html)  |  arn:$\{Partition\}:dynamodb::$\{Account\}:global\-table/$\{GlobalTableName\}  |  | 

## Condition keys for Amazon DynamoDB<a name="amazondynamodb-policy-keys"></a>

Amazon DynamoDB defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.

**Note**  
For information about how to use context keys to refine DynamoDB access using an IAM policy, see [Using IAM Policy Conditions for Fine\-Grained Access Control](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html) in the *Amazon DynamoDB Developer Guide*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ dynamodb:Attributes ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys)  | Filter based on the attribute \(field or column\) names of the table\. | String | 
|   [ dynamodb:EnclosingOperation ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys)  | Used to block Transactions APIs calls and allow the non\-Transaction APIs calls and vice\-versa\. | String | 
|   [ dynamodb:LeadingKeys ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys)  | Filters based on the partition key of the table\. | String | 
|   [ dynamodb:ReturnConsumedCapacity ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys)  | Filter based on the ReturnConsumedCapacity parameter of a request\. Contains either "TOTAL" or "NONE"\. | String | 
|   [ dynamodb:ReturnValues ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys)  | Filter based on the ReturnValues parameter of request\. Contains one of the following: "ALL\_OLD", "UPDATED\_OLD","ALL\_NEW","UPDATED\_NEW", or "NONE"\. | String | 
|   [ dynamodb:Select ](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys)  | Filter based on the Select parameter of a Query or Scan request\. | String | 