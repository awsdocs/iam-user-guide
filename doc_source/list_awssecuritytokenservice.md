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
| iam | arn:$\{Partition\}:iam::$\{Account\}:$\{RelativeId\} |  | 
| role | arn:$\{Partition\}:iam::$\{Account\}:role/$\{RoleNameWithPath\} |  | 
| sts | arn:$\{Partition\}:sts::$\{Account\}:$\{RelativeId\} |  | 
| user | arn:$\{Partition\}:iam::$\{Account\}:user/$\{UserNameWithPath\} |  | 

## Condition Keys for AWS Security Token Service<a name="awssecuritytokenservice-policy-keys"></a>

AWS Security Token Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| <web\-identity\-provider>:aud |  | String | 
| <web\-identity\-provider>:oaud |  | String | 
| <web\-identity\-provider>:sub |  | String | 
| aws:FederatedProvider |  | String | 
| saml:namequalifier |  | String | 
| saml:sub |  | String | 
| saml:sub\_type |  | String | 
| saml:aud |  | String | 
| saml:iss |  | String | 
| saml:doc |  | String | 
| saml:cn |  | String | 
| saml:commonName |  | String | 
| saml:eduorghomepageuri |  | String | 
| saml:eduorgidentityauthnpolicyuri |  | String | 
| saml:eduorglegalname |  | String | 
| saml:eduorgsuperioruri |  | String | 
| saml:eduorgwhitepagesuri |  | String | 
| saml:edupersonaffiliation |  | String | 
| saml:edupersonassurance |  | String | 
| saml:edupersonentitlement |  | String | 
| saml:edupersonnickname |  | String | 
| saml:edupersonorgdn |  | String | 
| saml:edupersonorgunitdn |  | String | 
| saml:edupersonprimaryaffiliation |  | String | 
| saml:edupersonprimaryorgunitdn |  | String | 
| saml:edupersonprincipalname |  | String | 
| saml:edupersonscopedaffiliation |  | String | 
| saml:edupersontargetedid |  | String | 
| saml:givenName |  | String | 
| saml:mail |  | String | 
| saml:name |  | String | 
| saml:organizationStatus |  | String | 
| saml:primaryGroupSID |  | String | 
| saml:surname |  | String | 
| saml:uid |  | String | 
| saml:x500UniqueIdentifier |  | String | 
| sts:ExternalId |  | String | 