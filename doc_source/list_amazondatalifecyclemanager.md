# Actions, Resources, and Condition Keys for Amazon Data Lifecycle Manager<a name="list_amazondatalifecyclemanager"></a>

Amazon Data Lifecycle Manager \(service prefix: `dlm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/dlm/latest/APIReference/)\.

**Topics**
+ [Actions Defined by Amazon Data Lifecycle Manager](#amazondatalifecyclemanager-actions-as-permissions)
+ [Resources Defined by Amazon Data Lifecycle Manager](#amazondatalifecyclemanager-resources-for-iam-policies)
+ [Condition Keys for Amazon Data Lifecycle Manager](#amazondatalifecyclemanager-policy-keys)

## Actions Defined by Amazon Data Lifecycle Manager<a name="amazondatalifecyclemanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateLifecyclePolicy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_CreateLifecyclePolicy.html)  | Create a data lifecycle policy to manage the scheduled creation and retention of Amazon EBS snapshots\. You may have up to 100 policies\. | Write |  |  |  | 
|   [ DeleteLifecyclePolicy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_DeleteLifecyclePolicy.html)  | Delete an existing data lifecycle policy\. In addition, this action halts the creation and deletion of snapshots that the policy specified\. Existing snapshots are not affected\. | Write |  |  |  | 
|   [ GetLifecyclePolicies ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_GetLifecyclePolicies.html)  | Returns a list of summary descriptions of data lifecycle policies\. | List |  |  |  | 
|   [ GetLifecyclePolicy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_GetLifecyclePolicy.html)  | Returns a complete description of a single data lifecycle policy\. | Read |  |  |  | 
|   [ UpdateLifecyclePolicy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_UpdateLifecyclePolicy.html)  | Updates an existing data lifecycle policy\. | Write |  |  |  | 

## Resources Defined by Amazon Data Lifecycle Manager<a name="amazondatalifecyclemanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazondatalifecyclemanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   policy  |  arn:$\{Partition\}:dlm:$\{Region\}:$\{Account\}:policy/$\{ResourceName\}  |  | 

## Condition Keys for Amazon Data Lifecycle Manager<a name="amazondatalifecyclemanager-policy-keys"></a>

Data Lifecycle Manager has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.