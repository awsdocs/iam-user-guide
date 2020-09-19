# Actions, resources, and condition keys for AWS Lake Formation<a name="list_awslakeformation"></a>

AWS Lake Formation \(service prefix: `lakeformation`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/lake-formation/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/lake-formation/latest/dg/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/lake-formation/latest/dg/security-data-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS Lake Formation](#awslakeformation-actions-as-permissions)
+ [Resource types defined by AWS Lake Formation](#awslakeformation-resources-for-iam-policies)
+ [Condition keys for AWS Lake Formation](#awslakeformation-policy-keys)

## Actions defined by AWS Lake Formation<a name="awslakeformation-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchGrantPermissions ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Grants data lake permissions to one or more principals in a batch\. | Permissions management |  |  |  | 
|   [ BatchRevokePermissions ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Revokes data lake permissions from one or more principals in a batch\. | Permissions management |  |  |  | 
|   [ DeregisterResource ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Deregisters a registered location\. | Write |  |  |  | 
|   [ DescribeResource ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Describes a registered location\. | Read |  |  |  | 
|   [ GetDataAccess ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Grants virtual data lake access permissions\. | Write |  |  |  | 
|   [ GetDataLakeSettings ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Retrieves data lake settings such as the list of data lake administrators and database and table default permissions\. | Read |  |  |  | 
|   [ GetEffectivePermissionsForPath ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Retrieves permissions attached to resources in the given path\. | Read |  |  |  | 
|   [ GrantPermissions ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Grants data lake permissions to a principal\. | Permissions management |  |  |  | 
|   [ ListPermissions ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Lists permissions filtered by principal or resource\. | List |  |  |  | 
|   [ ListResources ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Lists registered locations\. | List |  |  |  | 
|   [ PutDataLakeSettings ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Overwrites data lake settings such as the list of data lake administrators and database and table default permissions\. | Permissions management |  |  |  | 
|   [ RegisterResource ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Registers a new location to be managed by Lake Formation\. | Write |  |  |  | 
|   [ RevokePermissions ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Revokes data lake permissions from a principal\. | Permissions management |  |  |  | 
|   [ UpdateResource ](https://docs.aws.amazon.com/lake-formation/latest/dg/aws-lake-formation-api.html)  | Updates a registered location\. | Write |  |  |  | 

## Resource types defined by AWS Lake Formation<a name="awslakeformation-resources-for-iam-policies"></a>

AWS Lake Formation does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Lake Formation, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS Lake Formation<a name="awslakeformation-policy-keys"></a>

Lake Formation has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.