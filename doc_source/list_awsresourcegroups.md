# Actions, Resources, and Condition Keys for AWS Resource Groups<a name="list_awsresourcegroups"></a>

AWS Resource Groups \(service prefix: `resource-groups`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/ARG/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/ARG/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/ARG/latest/userguide/workingsecurity.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Resource Groups](#awsresourcegroups-actions-as-permissions)
+ [Resources Defined by Resource Groups](#awsresourcegroups-resources-for-iam-policies)
+ [Condition Keys for AWS Resource Groups](#awsresourcegroups-policy-keys)

## Actions Defined by AWS Resource Groups<a name="awsresourcegroups-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateGroup ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_CreateGroup.html)  | Creates a group with a specified name, description, and resource query\. | Tagging |  |  |  | 
|   [ DeleteGroup ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_DeleteGroup.html)  | Deletes a specified resource group | Write |  |  |  | 
|   [ GetGroup ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_GetGroup.html)  | Gets information of a specified resource group | Read |  |  |  | 
|   [ GetGroupQuery ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_GetGroupQuery.html)  | Gets the query associated with a specified resource group | Read |  |  |  | 
|   [ GetTags ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_GetTags.html)  | Gets the tags associated with a specified resource group | Read |  |  |  | 
|   [ ListGroupResources ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_ListGroupResources.html)  | Lists the resources that are member of a specified resource group | List |  |  |  | 
|   [ ListGroups ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_ListGroups.html)  | Lists all resource groups | List |  |  |  | 
|   [ SearchResources ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_SearchResources.html)  | Returns a list of AWS resource identifiers matching the given query | List |  |  |  | 
|   [ Tag ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_Tag.html)  | Tags a specified resource group | Tagging |  |  |  | 
|   [ Untag ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_Untag.html)  | Removes tags associated with a specified resource group | Tagging |  |  |  | 
|   [ UpdateGroup ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_UpdateGroup.html)  | Updates a specified resource group | Write |  |  |  | 
|   [ UpdateGroupQuery ](http://docs.aws.amazon.com/ARG/latest/APIReference/API_UpdateGroupQuery.html)  | Updates the query associated with a specified resource group | Write |  |  |  | 

## Resources Defined by Resource Groups<a name="awsresourcegroups-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsresourcegroups-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ group ](http://docs.aws.amazon.com/ARG/latest/userguide/welcome.html)  |  arn:$\{Partition\}:resource\-groups:$\{Region\}:$\{Account\}:group/$\{GroupName\}  |  | 

## Condition Keys for AWS Resource Groups<a name="awsresourcegroups-policy-keys"></a>

Resource Groups has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.