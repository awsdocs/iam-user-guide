# Actions, resources, and condition keys for AWS Resource Access Manager<a name="list_awsresourceaccessmanager"></a>

AWS Resource Access Manager \(service prefix: `ram`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/ram/latest/userguide/what-is-resource-access-manager.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/ram/latest/APIReference/API_Operations.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/ram/latest/userguide/control-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS Resource Access Manager](#awsresourceaccessmanager-actions-as-permissions)
+ [Resource types defined by AWS Resource Access Manager](#awsresourceaccessmanager-resources-for-iam-policies)
+ [Condition keys for AWS Resource Access Manager](#awsresourceaccessmanager-policy-keys)

## Actions defined by AWS Resource Access Manager<a name="awsresourceaccessmanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsresourceaccessmanager.html)

## Resource types defined by AWS Resource Access Manager<a name="awsresourceaccessmanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsresourceaccessmanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ resource\-share ](https://docs.aws.amazon.com/ram/latest/APIReference/API_ResourceShare.html)  |  arn:$\{Partition\}:ram:$\{Region\}:$\{Account\}:resource\-share/$\{ResourcePath\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsresourceaccessmanager-aws_ResourceTag___TagKey_)   [ ram:AllowsExternalPrincipals ](#awsresourceaccessmanager-ram_AllowsExternalPrincipals)   [ ram:ResourceShareName ](#awsresourceaccessmanager-ram_ResourceShareName)   | 
|   [ resource\-share\-invitation ](https://docs.aws.amazon.com/ram/latest/APIReference/API_ResourceShareInvitation.html)  |  arn:$\{Partition\}:ram:$\{Region\}:$\{Account\}:resource\-share\-invitation/$\{ResourcePath\}  |  | 
|   [ permission ](https://docs.aws.amazon.com/ram/latest/APIReference/API_ResourceSharePermissionDetail.html)  |  arn:$\{Partition\}:ram::$\{Account\}:permission/$\{ResourcePath\}  |   [ ram:PermissionArn ](#awsresourceaccessmanager-ram_PermissionArn)   | 

## Condition keys for AWS Resource Access Manager<a name="awsresourceaccessmanager-policy-keys"></a>

AWS Resource Access Manager defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Specifies a tag key and value pair that must be used when creating or tagging a resource share\. If users don't pass these specific tags, or if they don't specify tags at all, the request fails\. | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Indicates that the action can only be performed on resources that have the specified tag key and value pair\. | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Specifies the tag keys that can be used when creating or tagging a resource share | String | 
|   [ ram:AllowsExternalPrincipals ](https://docs.aws.amazon.com/ram/latest/userguide/iam-policies.html#iam-policies-condition)  | Indicates that the action can only be performed on resource shares that allow or deny sharing with external principals\. For example, specify true if the action can only be performed on resource shares that allow sharing with external principals\. External principals are AWS accounts that are outside of its AWS organization  | Bool | 
|   [ ram:PermissionArn ](https://docs.aws.amazon.com/ram/latest/userguide/iam-policies.html#iam-policies-condition)  | Indicates that the action can only be performed on a resource using the specified Permission ARN\. | Arn | 
|   [ ram:Principal ](https://docs.aws.amazon.com/ram/latest/userguide/iam-policies.html#iam-policies-condition)  | Principals with the specified format can be associated to or disassociated from a resource share | String | 
|   [ ram:RequestedAllowsExternalPrincipals ](https://docs.aws.amazon.com/ram/latest/userguide/iam-policies.html#iam-policies-condition)  | The request must have the specified value for 'allowExternalPrincipals'\. External principals are AWS accounts that are outside of its AWS Organization | Bool | 
|   [ ram:RequestedResourceType ](https://docs.aws.amazon.com/ram/latest/userguide/iam-policies.html#iam-policies-condition)  | Indicates that the action can only be performed on the specified resource type | String | 
|   [ ram:ResourceArn ](https://docs.aws.amazon.com/ram/latest/userguide/iam-policies.html#iam-policies-condition)  | Indicates that the action can only be performed on a resource with the specified ARN\. | Arn | 
|   [ ram:ResourceShareName ](https://docs.aws.amazon.com/ram/latest/userguide/iam-policies.html#iam-policies-condition)  | Indicates that the action can only be performed on a resource share with the specified name\. | String | 
|   [ ram:ShareOwnerAccountId ](https://docs.aws.amazon.com/ram/latest/userguide/iam-policies.html#iam-policies-condition)  | Indicates that the action can only be performed on resource shares owned by a specific account\. For example, you can use this condition key to specify which resource share invitations can be accepted or rejected based on the resource share owner’s account ID\. | String | 