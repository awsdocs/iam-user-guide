# Actions, resources, and condition keys for AWS Security Hub<a name="list_awssecurityhub"></a>

AWS Security Hub \(service prefix: `securityhub`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/securityhub/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/securityhub/1.0/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS Security Hub](#awssecurityhub-actions-as-permissions)
+ [Resource types defined by AWS Security Hub](#awssecurityhub-resources-for-iam-policies)
+ [Condition keys for AWS Security Hub](#awssecurityhub-policy-keys)

## Actions defined by AWS Security Hub<a name="awssecurityhub-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awssecurityhub.html)

## Resource types defined by AWS Security Hub<a name="awssecurityhub-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awssecurityhub-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ hub ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:$\{Region\}:$\{Account\}:hub/default  |   [ aws:ResourceTag/$\{TagKey\} ](#awssecurityhub-aws_ResourceTag___TagKey_)   | 
|   [ product ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:$\{Region\}:$\{Account\}:product/$\{Company\}/$\{ProductId\}  |  | 

## Condition keys for AWS Security Hub<a name="awssecurityhub-policy-keys"></a>

AWS Security Hub defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of tag keys in the request | String | 
|   [ securityhub:ASFFSyntaxPath/$\{ASFFSyntaxPath\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-asffsyntaxpath)  | Filters access based on the presence of specific fields and values in the request | String | 
|   [ securityhub:TargetAccount ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#conditions)  | Filters access based on the presence of AwsAccountId field in the requests | String | 