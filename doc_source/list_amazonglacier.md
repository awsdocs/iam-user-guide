# Actions, Resources, and Condition Keys for Amazon Glacier<a name="list_amazonglacier"></a>

Amazon Glacier \(service prefix: `glacier`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/amazonglacier/latest/dev/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/amazonglacier/latest/dev/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/amazonglacier/latest/dev/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Glacier](#amazonglacier-actions-as-permissions)
+ [Resources Defined by Glacier](#amazonglacier-resources-for-iam-policies)
+ [Condition Keys for Amazon Glacier](#amazonglacier-policy-keys)

## Actions Defined by Amazon Glacier<a name="amazonglacier-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonglacier.html)

## Resources Defined by Glacier<a name="amazonglacier-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonglacier-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/amazonglacier/latest/dev/working-with-vaults.html](http://docs.aws.amazon.com/amazonglacier/latest/dev/working-with-vaults.html) | arn:$\{Partition\}:glacier:$\{Region\}:$\{Account\}:vaults/$\{VaultName\} |  | 

## Condition Keys for Amazon Glacier<a name="amazonglacier-policy-keys"></a>

Amazon Glacier defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/amazonglacier/latest/dev/access-control-overview.html#specifying-conditions](http://docs.aws.amazon.com/amazonglacier/latest/dev/access-control-overview.html#specifying-conditions) | How long an archive has been stored in the vault, in days\. | String | 
| [http://docs.aws.amazon.com/amazonglacier/latest/dev/access-control-overview.html#specifying-conditions](http://docs.aws.amazon.com/amazonglacier/latest/dev/access-control-overview.html#specifying-conditions) | A customer\-defined tag\. | String | 