# Actions, resources, and condition keys for Amazon Data Lifecycle Manager<a name="list_amazondatalifecyclemanager"></a>

Amazon Data Lifecycle Manager \(service prefix: `dlm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/dlm/latest/APIReference/Welcome.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/dlm/latest/APIReference/API_Operations.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazondatalifecyclemanager.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Data Lifecycle Manager](#amazondatalifecyclemanager-actions-as-permissions)
+ [Resource types defined by Amazon Data Lifecycle Manager](#amazondatalifecyclemanager-resources-for-iam-policies)
+ [Condition keys for Amazon Data Lifecycle Manager](#amazondatalifecyclemanager-policy-keys)

## Actions defined by Amazon Data Lifecycle Manager<a name="amazondatalifecyclemanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateLifecyclePolicy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_CreateLifecyclePolicy.html)  | Create a data lifecycle policy to manage the scheduled creation and retention of Amazon EBS snapshots\. You may have up to 100 policies\. | Write |  |   [ aws:RequestTag/$\{TagKey\} ](#amazondatalifecyclemanager-aws_RequestTag___TagKey_)   [ aws:TagKeys ](#amazondatalifecyclemanager-aws_TagKeys)   |  | 
|   [ DeleteLifecyclePolicy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_DeleteLifecyclePolicy.html)  | Delete an existing data lifecycle policy\. In addition, this action halts the creation and deletion of snapshots that the policy specified\. Existing snapshots are not affected\. | Write |   [ policy\* ](#amazondatalifecyclemanager-policy)   |  |  | 
|   [ GetLifecyclePolicies ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_GetLifecyclePolicies.html)  | Returns a list of summary descriptions of data lifecycle policies\. | List |  |  |  | 
|   [ GetLifecyclePolicy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_GetLifecyclePolicy.html)  | Returns a complete description of a single data lifecycle policy\. | Read |   [ policy\* ](#amazondatalifecyclemanager-policy)   |  |  | 
|   [ ListTagsForResource ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_ListTagsForResource.html)  | Grants permission to list the tags associated with a resource\. | Read |   [ policy\* ](#amazondatalifecyclemanager-policy)   |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_TagResource.html)  | Grants permission to add or update tags of a resource\. | Tagging |   [ policy\* ](#amazondatalifecyclemanager-policy)   |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_UntagResource.html)  | Grants permission to remove associated with a resource\. | Tagging |   [ policy\* ](#amazondatalifecyclemanager-policy)   |  |  | 
|   [ UpdateLifecyclePolicy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_UpdateLifecyclePolicy.html)  | Updates an existing data lifecycle policy\. | Write |   [ policy\* ](#amazondatalifecyclemanager-policy)   |  |  | 

## Resource types defined by Amazon Data Lifecycle Manager<a name="amazondatalifecyclemanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazondatalifecyclemanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ policy ](https://docs.aws.amazon.com/dlm/latest/APIReference/API_LifecyclePolicy.html)  |  arn:$\{Partition\}:dlm:$\{Region\}:$\{Account\}:policy/$\{ResourceName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazondatalifecyclemanager-aws_ResourceTag___TagKey_)   | 

## Condition keys for Amazon Data Lifecycle Manager<a name="amazondatalifecyclemanager-policy-keys"></a>

Amazon Data Lifecycle Manager defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of tag keys in the request | String | 