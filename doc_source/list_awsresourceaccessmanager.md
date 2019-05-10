# Actions, Resources, and Condition Keys for AWS Resource Access Manager<a name="list_awsresourceaccessmanager"></a>

AWS Resource Access Manager \(service prefix: `ram`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/ram/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/ram/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/ram/latest/userguide/control-access.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Resource Access Manager](#awsresourceaccessmanager-actions-as-permissions)
+ [Resources Defined by Resource Access Manager](#awsresourceaccessmanager-resources-for-iam-policies)
+ [Condition Keys for AWS Resource Access Manager](#awsresourceaccessmanager-policy-keys)

## Actions Defined by AWS Resource Access Manager<a name="awsresourceaccessmanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsresourceaccessmanager.html)

## Resources Defined by Resource Access Manager<a name="awsresourceaccessmanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsresourceaccessmanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ resource\-share ](https://docs.aws.amazon.com/ram/latest/APIReference/API_ResourceShare.html)  |  arn:$\{Partition\}:ram:$\{Region\}:$\{Account\}:resource\-share/$\{ResourcePath\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsresourceaccessmanager-aws_ResourceTag___TagKey_)   | 
|   [ resource\-share\-invitation ](https://docs.aws.amazon.com/ram/latest/APIReference/API_ResourceShareInvitation.html)  |  arn:$\{Partition\}:ram:$\{Region\}:$\{Account\}:resource\-share\-invitation/$\{ResourcePath\}  |  | 
|   [ resource ](https://docs.aws.amazon.com/ram/latest/APIReference/API_Resource.html)  |  arn:$\{Partition\}:$\{Service\}:$\{Region\}:\#\{Account\}:$\{ResourceType\}/$\{ResourcePath\}  |  | 
|   [ principal ](https://docs.aws.amazon.com/ram/latest/APIReference/API_Principal.html)  |  arn:$\{Partition\}:iam::$\{Account\}:root  |  | 

## Condition Keys for AWS Resource Access Manager<a name="awsresourceaccessmanager-policy-keys"></a>

AWS Resource Access Manager defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   aws:RequestTag/$\{TagKey\}  |  | String | 
|   aws:ResourceTag/$\{TagKey\}  |  | String | 
|   aws:TagKeys  |  | String | 
|   ram:AllowsExternalPrincipals  | Resource shares can only be acted on if the share allows external principals | Bool | 
|   ram:Principals  | Principals with the specified format can be associated to or disassociated from a resource share | String | 
|   ram:RequestedResourceType  | Resources of RequestedResourceType can be associated with the specified resource share | String | 
|   ram:ResourceArns  | Resources with the specified arn format can be associated to or disassociated from a resource share | Arn | 
|   ram:ResourceShareNames  | Resource shares with the following names can be used in specified action | String | 
|   ram:ShareOwnerAccountIds  | Resource share invitations can only be accepted/rejected if owned by the specified account id | String | 