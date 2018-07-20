# Actions, Resources, and Condition Keys for Amazon AppStream 2\.0<a name="list_amazonappstream2.0"></a>

Amazon AppStream 2\.0 \(service prefix: `appstream`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/appstream2/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/appstream2/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/appstream2/latest/developerguide/controlling-access.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon AppStream 2\.0](#amazonappstream2.0-actions-as-permissions)
+ [Resources Defined by AppStream 2\.0](#amazonappstream2.0-resources-for-iam-policies)
+ [Condition Keys for Amazon AppStream 2\.0](#amazonappstream2.0-policy-keys)

## Actions Defined by Amazon AppStream 2\.0<a name="amazonappstream2.0-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonappstream2.0.html)

## Resources Defined by AppStream 2\.0<a name="amazonappstream2.0-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonappstream2.0-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ fleet ](http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts)  |  arn:$\{Partition\}:appstream:$\{Region\}:$\{Account\}:fleet/$\{FleetName\}  |  | 
|   [ image ](http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts)  |  arn:$\{Partition\}:appstream:$\{Region\}:$\{Account\}:image/$\{ImageName\}  |  | 
|   [ image\-builder ](http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts)  |  arn:$\{Partition\}:appstream:$\{Region\}:$\{Account\}:image\-builder/$\{ImageBuilderName\}  |  | 
|   [ stack ](http://docs.aws.amazon.com/appstream2/latest/developerguide/what-is-appstream.html#what-is-concepts)  |  arn:$\{Partition\}:appstream:$\{Region\}:$\{Account\}:stack/$\{StackName\}  |  | 

## Condition Keys for Amazon AppStream 2\.0<a name="amazonappstream2.0-policy-keys"></a>

Amazon AppStream 2\.0 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ appstream:userId ](http://docs.aws.amazon.com/appstream2/latest/developerguide/external-identity-providers-setting-up-saml.html#external-identity-providers-embed-inline-policy-for-IAM-role)  | Filters access by the ID of the AppStream 2\.0 user\. | String | 