# Actions, Resources, and Condition Keys for Amazon Sumerian<a name="list_amazonsumerian"></a>

Amazon Sumerian \(service prefix: `sumerian`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/sumerian/latest/userguide/)\.

**Topics**
+ [Actions Defined by Amazon Sumerian](#amazonsumerian-actions-as-permissions)
+ [Resource Types Defined by Amazon Sumerian](#amazonsumerian-resources-for-iam-policies)
+ [Condition Keys for Amazon Sumerian](#amazonsumerian-policy-keys)

## Actions Defined by Amazon Sumerian<a name="amazonsumerian-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ Login ](https://docs.aws.amazon.com/sumerian/latest/userguide/sumerian-permissions.html)  | Grant login access to the Sumerian console\. | Write |  |  |  | 
|   [ ViewRelease ](https://docs.aws.amazon.com/sumerian/latest/userguide/sumerian-permissions.html)  | Grant access to view a project release\. | Read |   [ project\* ](#amazonsumerian-project)   |  |  | 

## Resource Types Defined by Amazon Sumerian<a name="amazonsumerian-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsumerian-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   project  |  arn:$\{Partition\}:sumerian:$\{Region\}:$\{Account\}:project:$\{ProjectName\}  |  | 

## Condition Keys for Amazon Sumerian<a name="amazonsumerian-policy-keys"></a>

Sumerian has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.