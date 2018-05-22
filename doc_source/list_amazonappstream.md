# Actions, Resources, and Condition Keys for Amazon AppStream<a name="list_amazonappstream"></a>

Amazon AppStream \(service prefix: `appstream`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/appstream2/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/appstream2/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/appstream2/latest/developerguide/controlling-access.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon AppStream](#amazonappstream-actions-as-permissions)
+ [Resources Defined by AppStream](#amazonappstream-resources-for-iam-policies)
+ [Condition Keys for Amazon AppStream](#amazonappstream-policy-keys)

## Actions Defined by Amazon AppStream<a name="amazonappstream-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonappstream.html)

## Resources Defined by AppStream<a name="amazonappstream-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonappstream-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts](http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts) | arn:$\{Partition\}:appstream:$\{Region\}:$\{Account\}:fleet/$\{FleetName\} |  | 
| [http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts](http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts) | arn:$\{Partition\}:appstream:$\{Region\}:$\{Account\}:image/$\{ImageName\} |  | 
| [http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts](http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts) | arn:$\{Partition\}:appstream:$\{Region\}:$\{Account\}:image\-builder/$\{ImageBuilderName\} |  | 
| [http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts](http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts) | arn:$\{Partition\}:appstream:$\{Region\}:$\{Account\}:stack/$\{StackName\} |  | 

## Condition Keys for Amazon AppStream<a name="amazonappstream-policy-keys"></a>

Amazon AppStream defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| appstream:userId |  | String | 