# Actions, Resources, and Condition Keys for Amazon Resource Group Tagging API<a name="list_amazonresourcegrouptaggingapi"></a>

Amazon Resource Group Tagging API \(service prefix: `tag`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/obtaining-permissions-for-resource-groups.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Resource Group Tagging API](#amazonresourcegrouptaggingapi-actions-as-permissions)
+ [Resources Defined by Resource Group Tagging](#amazonresourcegrouptaggingapi-resources-for-iam-policies)
+ [Condition Keys for Amazon Resource Group Tagging API](#amazonresourcegrouptaggingapi-policy-keys)

## Actions Defined by Amazon Resource Group Tagging API<a name="amazonresourcegrouptaggingapi-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_GetResources.html](http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_GetResources.html) | Get tagged AWS resources that match the given tag filters | Read |  |  |  | 
| [http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_GetTagKeys.html](http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_GetTagKeys.html) | Get all tagKeys for the account in the specific region | Read |  |  |  | 
| [http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_GetTagValues.html](http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_GetTagValues.html) | Get all tagValues for the account in the specific region | Read |  |  |  | 
| [http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_TagResources.html](http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_TagResources.html) | Add tags to AWS resources | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_UntagResources.html](http://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_UntagResources.html) | Remove tags from AWS resources | Tagging |  |  |  | 

## Resources Defined by Resource Group Tagging<a name="amazonresourcegrouptaggingapi-resources-for-iam-policies"></a>

Resource Group Tagging has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Resource Group Tagging API<a name="amazonresourcegrouptaggingapi-policy-keys"></a>

Resource Group Tagging has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.