# Actions, Resources, and Condition Keys for Amazon SNS<a name="list_amazonsns"></a>

Amazon SNS \(service prefix: `sns`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/sns/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/sns/latest/api/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon SNS](#amazonsns-actions-as-permissions)
+ [Resources Defined by SNS](#amazonsns-resources-for-iam-policies)
+ [Condition Keys for Amazon SNS](#amazonsns-policy-keys)

## Actions Defined by Amazon SNS<a name="amazonsns-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsns.html)

## Resources Defined by SNS<a name="amazonsns-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsns-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/sns/latest/dg/CreateTopic.html](http://docs.aws.amazon.com/sns/latest/dg/CreateTopic.html) | arn:$\{Partition\}:sns:$\{Region\}:$\{Account\}:$\{TopicName\} |  | 

## Condition Keys for Amazon SNS<a name="amazonsns-policy-keys"></a>

Amazon SNS defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#w2ab1c11c23c19](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#w2ab1c11c23c19) | The URL, email address, or ARN from a Subscribe request or a previously confirmed subscription\. | String | 
| [http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#w2ab1c11c23c19](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#w2ab1c11c23c19) | The protocol value from a Subscribe request or a previously confirmed subscription\. | String | 