# Actions, Resources, and Condition Keys for AWS Security Token Service<a name="list_awssecuritytokenservice"></a>

AWS Security Token Service \(service prefix: `sts`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/IAM/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/STS/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Security Token Service](#awssecuritytokenservice-actions-as-permissions)
+ [Resources Defined by STS](#awssecuritytokenservice-resources-for-iam-policies)
+ [Condition Keys for AWS Security Token Service](#awssecuritytokenservice-policy-keys)

## Actions Defined by AWS Security Token Service<a name="awssecuritytokenservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awssecuritytokenservice.html)

## Resources Defined by STS<a name="awssecuritytokenservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awssecuritytokenservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [iam](url-resources-replace-me) | arn:$\{Partition\}:iam::$\{Account\}:$\{RelativeId\} |  | 
| [role](url-resources-replace-me) | arn:$\{Partition\}:iam::$\{Account\}:role/$\{RoleNameWithPath\} |  | 
| [sts](url-resources-replace-me) | arn:$\{Partition\}:sts::$\{Account\}:$\{RelativeId\} |  | 
| [user](url-resources-replace-me) | arn:$\{Partition\}:iam::$\{Account\}:user/$\{UserNameWithPath\} |  | 

## Condition Keys for AWS Security Token Service<a name="awssecuritytokenservice-policy-keys"></a>

AWS Security Token Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [<web\-identity\-provider>:aud](url-contextkeys-replace-me) |  | String | 
| [<web\-identity\-provider>:oaud](url-contextkeys-replace-me) |  | String | 
| [<web\-identity\-provider>:sub](url-contextkeys-replace-me) |  | String | 
| [aws:FederatedProvider](url-contextkeys-replace-me) |  |  | 
| [saml:namequalifier](url-contextkeys-replace-me) |  | String | 
| [saml:sub](url-contextkeys-replace-me) |  | String | 
| [saml:sub\_type](url-contextkeys-replace-me) |  |  | 
| [saml:aud](url-contextkeys-replace-me) |  |  | 
| [saml:iss](url-contextkeys-replace-me) |  |  | 
| [saml:doc](url-contextkeys-replace-me) |  |  | 