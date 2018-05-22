# Actions, Resources, and Condition Keys for Amazon DynamoDB<a name="list_amazondynamodb"></a>

Amazon DynamoDB \(service prefix: `dynamodb`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon DynamoDB](#amazondynamodb-actions-as-permissions)
+ [Resources Defined by DynamoDB](#amazondynamodb-resources-for-iam-policies)
+ [Condition Keys for Amazon DynamoDB](#amazondynamodb-policy-keys)

## Actions Defined by Amazon DynamoDB<a name="amazondynamodb-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazondynamodb.html)

## Resources Defined by DynamoDB<a name="amazondynamodb-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazondynamodb-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorks.html](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/backuprestore_HowItWorks.html) | arn:$\{Partition\}:dynamodb:$\{Region\}:$\{Account\}:table/$\{TableName\}/backup/$\{BackupName\} |  | 
| [https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/globaltables_HowItWorks.html](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/globaltables_HowItWorks.html) | arn:$\{Partition\}:dynamodb::$\{Account\}:global\-table/$\{GlobalTableName\} |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.PrimaryKey](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.PrimaryKey) | arn:$\{Partition\}:dynamodb:$\{Region\}:$\{Account\}:table/$\{TableName\}/index/$\{IndexName\} |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.Streams](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.Streams) | arn:$\{Partition\}:dynamodb:$\{Region\}:$\{Account\}:table/$\{TableName\}/stream/$\{StreamLabel\} |  | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.TablesItemsAttributes](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.htmlHowItWorks.CoreComponents.html#HowItWorks.CoreComponents.TablesItemsAttributes) | arn:$\{Partition\}:dynamodb:$\{Region\}:$\{Account\}:table/$\{TableName\} |  | 

## Condition Keys for Amazon DynamoDB<a name="amazondynamodb-policy-keys"></a>

Amazon DynamoDB defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.

For information about how to use context keys to refine DynamoDB access using an IAM policy, see [Using IAM Policy Conditions for Fine\-Grained Access Control](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html) in the *Amazon DynamoDB Developer Guide*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) | Filter based on the attribute \(field or column\) names of the table\. | String | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) | Filters based on the partition key of the table\. | String | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) | Filter based on the ReturnConsumedCapacity parameter of a request\. Contains either "TOTAL" or "NONE"\. | String | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) | Filter based on the ReturnValues parameter of request\. Contains one of the following: "ALL\_OLD", "UPDATED\_OLD","ALL\_NEW","UPDATED\_NEW", or "NONE"\. | String | 
| [http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) | Filter based on the Select parameter of a Query or Scan request\. | String | 