# Actions, Resources, and Condition Keys for Amazon Neptune<a name="list_amazonneptune"></a>

Amazon Neptune \(service prefix: `neptune-db`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/neptune/latest/userguide/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/neptune/latest/userguide/iam-auth.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Neptune](#amazonneptune-actions-as-permissions)
+ [Resources Defined by Neptune](#amazonneptune-resources-for-iam-policies)
+ [Condition Keys for Amazon Neptune](#amazonneptune-policy-keys)

## Actions Defined by Amazon Neptune<a name="amazonneptune-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ connect ](https://docs.aws.amazon.com/neptune/latest/userguide/https://docs.aws.amazon.com/neptune/latest/userguide/get-started.html)  | Connect to database | Write |   [ database\* ](#amazonneptune-database)   |  |  | 

## Resources Defined by Neptune<a name="amazonneptune-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonneptune-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ database ](https://docs.aws.amazon.com/neptune/latest/userguide/https://docs.aws.amazon.com/neptune/latest/userguide/get-started.html)  |  arn:$\{Partition\}:neptune\-db:$\{Region\}:$\{Account\}:$\{RelativeId\}/database  |  | 

## Condition Keys for Amazon Neptune<a name="amazonneptune-policy-keys"></a>

Neptune has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.