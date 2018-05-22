# Actions, Resources, and Condition Keys for AWS Resource Groups<a name="list_awsresourcegroups"></a>

AWS Resource Groups \(service prefix: `resource-groups`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/resource-groups/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/resource-groups/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/resource-groups/latest/userguide/workingsecurity.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Resource Groups](#awsresourcegroups-actions-as-permissions)
+ [Resources Defined by Resource Groups](#awsresourcegroups-resources-for-iam-policies)
+ [Condition Keys for AWS Resource Groups](#awsresourcegroups-policy-keys)

## Actions Defined by AWS Resource Groups<a name="awsresourcegroups-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_CreateGroup.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_CreateGroup.html) | Creates a group with a specified name, description, and resource query\. | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_DeleteGroup.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_DeleteGroup.html) | Deletes a specified resource group | Write |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_GetGroup.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_GetGroup.html) | Gets information of a specified resource group | Read |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_GetGroupQuery.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_GetGroupQuery.html) | Gets the query associated with a specified resource group | Read |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_GetTags.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_GetTags.html) | Gets the tags associated with a specified resource group | Read |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_ListGroupResources.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_ListGroupResources.html) | Lists the resources that are member of a specified resource group | List |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_ListGroups.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_ListGroups.html) | Lists all resource groups | List |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_SearchResources.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_SearchResources.html) | Returns a list of AWS resource identifiers matching the given query | List |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_Tag.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_Tag.html) | Tags a specified resource group | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_Untag.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_Untag.html) | Removes tags associated with a specified resource group | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_UpdateGroup.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_UpdateGroup.html) | Updates a specified resource group | Write |  |  |  | 
| [http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_UpdateGroupQuery.html](http://docs.aws.amazon.com/resource-groups/latest/APIReference/API_UpdateGroupQuery.html) | Updates the query associated with a specified resource group | Write |  |  |  | 

## Resources Defined by Resource Groups<a name="awsresourcegroups-resources-for-iam-policies"></a>

Resource Groups has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Resource Groups<a name="awsresourcegroups-policy-keys"></a>

Resource Groups has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.