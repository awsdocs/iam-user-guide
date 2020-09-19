# Actions, resources, and condition keys for AWS Identity Store<a name="list_awsidentitystore"></a>

AWS Identity Store \(service prefix: `identitystore`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/singlesignon/latest/IdentityStoreAPIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS Identity Store](#awsidentitystore-actions-as-permissions)
+ [Resource types defined by AWS Identity Store](#awsidentitystore-resources-for-iam-policies)
+ [Condition keys for AWS Identity Store](#awsidentitystore-policy-keys)

## Actions defined by AWS Identity Store<a name="awsidentitystore-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DescribeGroup ](https://docs.aws.amazon.com/singlesignon/latest/IdentityStoreAPIReference/API_DescribeGroup.html)  | Retrieves information about group from the directory that AWS Identity Store provides by default | Read |  |  |  | 
|   [ DescribeUser ](https://docs.aws.amazon.com/singlesignon/latest/IdentityStoreAPIReference/API_DescribeUser.html)  | Retrieves information about user from the directory that AWS Identity Store provides by default | Read |  |  |  | 
|   [ ListGroups ](https://docs.aws.amazon.com/singlesignon/latest/IdentityStoreAPIReference/API_ListGroups.html)  | Search for groups within the associated directory | List |  |  |  | 
|   [ ListUsers ](https://docs.aws.amazon.com/singlesignon/latest/IdentityStoreAPIReference/API_ListUsers.html)  | Search for users within the associated directory | List |  |  |  | 

## Resource types defined by AWS Identity Store<a name="awsidentitystore-resources-for-iam-policies"></a>

AWS Identity Store does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Identity Store, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS Identity Store<a name="awsidentitystore-policy-keys"></a>

Identity Store has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.