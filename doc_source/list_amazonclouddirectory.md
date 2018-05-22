# Actions, Resources, and Condition Keys for Amazon Cloud Directory<a name="list_amazonclouddirectory"></a>

Amazon Cloud Directory \(service prefix: `clouddirectory`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/directoryservice/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/UsingWithDS_IAM_AuthNAccess.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Cloud Directory](#amazonclouddirectory-actions-as-permissions)
+ [Resources Defined by Cloud Directory](#amazonclouddirectory-resources-for-iam-policies)
+ [Condition Keys for Amazon Cloud Directory](#amazonclouddirectory-policy-keys)

## Actions Defined by Amazon Cloud Directory<a name="amazonclouddirectory-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonclouddirectory.html)

## Resources Defined by Cloud Directory<a name="amazonclouddirectory-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonclouddirectory-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cd_key_concepts.html#whatisdirectory](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cd_key_concepts.html#whatisdirectory) | arn:$\{Partition\}:clouddirectory:$\{Region\}:$\{Account\}:directory/$\{DirectoryId\}/schema/$\{SchemaName\}/$\{Version\} |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cd_key_concepts.html#whatisdirectory](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cd_key_concepts.html#whatisdirectory) | arn:$\{Partition\}:clouddirectory:$\{Region\}:$\{Account\}:schema/development/$\{SchemaName\} |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cd_key_concepts.html#whatisdirectory](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cd_key_concepts.html#whatisdirectory) | arn:$\{Partition\}:clouddirectory:$\{Region\}:$\{Account\}:directory/$\{DirectoryId\} |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cd_key_concepts.html#whatisdirectory](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/cd_key_concepts.html#whatisdirectory) | arn:$\{Partition\}:clouddirectory:$\{Region\}:$\{Account\}:schema/published/$\{SchemaName\}/$\{Version\} |  | 

## Condition Keys for Amazon Cloud Directory<a name="amazonclouddirectory-policy-keys"></a>

Cloud Directory has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.