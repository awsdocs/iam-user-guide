# Actions, resources, and condition keys for AWS Security Token Service<a name="list_awssecuritytokenservice"></a>

AWS Security Token Service \(service prefix: `sts`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/STS/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions.html) permission policies\.

**Topics**
+ [Actions defined by AWS Security Token Service](#awssecuritytokenservice-actions-as-permissions)
+ [Resource types defined by AWS Security Token Service](#awssecuritytokenservice-resources-for-iam-policies)
+ [Condition keys for AWS Security Token Service](#awssecuritytokenservice-policy-keys)

## Actions defined by AWS Security Token Service<a name="awssecuritytokenservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awssecuritytokenservice.html)

## Resource types defined by AWS Security Token Service<a name="awssecuritytokenservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awssecuritytokenservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ role ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)  |  arn:$\{Partition\}:iam::$\{Account\}:role/$\{RoleNameWithPath\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awssecuritytokenservice-aws_ResourceTag___TagKey_)   | 
|   [ user ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)  |  arn:$\{Partition\}:iam::$\{Account\}:user/$\{UserNameWithPath\}  |  | 

## Condition keys for AWS Security Token Service<a name="awssecuritytokenservice-policy-keys"></a>

AWS Security Token Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ accounts\.google\.com:aud ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_aud)  | Filters actions based on the Google application ID | String | 
|   [ accounts\.google\.com:oaud ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_oaud)  | Filters actions based on the Google audience | String | 
|   [ accounts\.google\.com:sub ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_sub)  | Filters actions based on the subject of the claim \(the Google user ID\) | String | 
|   [ aws:FederatedProvider ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_federatedprovider)  | Filters actions based on the IdP that was used to authenticate the user | String | 
|   [ aws:PrincipalTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-principaltag)  | Filters actions based on the tag associated with the principal that is making the request | String | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the tags that are passed in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on the tags associated with the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the tag keys that are passed in the request | String | 
|   [ cognito\-identity\.amazonaws\.com:amr ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_amr)  | Filters actions based on the login information for Amazon Cognito | String | 
|   [ cognito\-identity\.amazonaws\.com:aud ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_aud)  | Filters actions based on the Amazon Cognito identity pool ID | String | 
|   [ cognito\-identity\.amazonaws\.com:sub ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_sub)  | Filters actions based on the subject of the claim \(the Amazon Cognito user ID\) | String | 
|   [ graph\.facebook\.com:app\_id ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_id)  | Filters actions based on the Facebook application ID | String | 
|   [ graph\.facebook\.com:id ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_id)  | Filters actions based on the Facebook user ID | String | 
|   [ iam:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_ResourceTag)  | Filters actions based on the tags that are attached to the role that is being assumed | String | 
|   [ saml:aud ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_aud)  | Filters actions based on the endpoint URL to which SAML assertions are presented | String | 
|   [ saml:cn ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_cn)  | Filters actions based on the eduOrg attribute | String | 
|   [ saml:commonName ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_commonname)  | Filters actions based on the commonName attribute | String | 
|   [ saml:doc ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_doc)  | Filters actions based on the principal that was used to assume the role | String | 
|   [ saml:eduorghomepageuri ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_eduorghomepageuri)  | Filters actions based on the eduOrg attribute | String | 
|   [ saml:eduorgidentityauthnpolicyuri ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_aud)  | Filters actions based on the eduOrg attribute | String | 
|   [ saml:eduorglegalname ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_eduorglegalname)  | Filters actions based on the eduOrg attribute | String | 
|   [ saml:eduorgsuperioruri ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_eduorgsuperioruri)  | Filters actions based on the eduOrg attribute | String | 
|   [ saml:eduorgwhitepagesuri ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_eduorgwhitepagesuri)  | Filters actions based on the eduOrg attribute | String | 
|   [ saml:edupersonaffiliation ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonaffiliation)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonassurance ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonassurance)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonentitlement ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonentitlement)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonnickname ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonnickname)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonorgdn ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonorgdn)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonorgunitdn ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonorgunitdn)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonprimaryaffiliation ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonprimaryaffiliation)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonprimaryorgunitdn ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonprimaryorgunitdn)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonprincipalname ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonprincipalname)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersonscopedaffiliation ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersonscopedaffiliation)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:edupersontargetedid ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_edupersontargetedid)  | Filters actions based on the eduPerson attribute | String | 
|   [ saml:givenName ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_givenname)  | Filters actions based on the givenName attribute | String | 
|   [ saml:iss ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_iss)  | Filters actions based on the issuer, which is represented by a URN | String | 
|   [ saml:mail ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_mail)  | Filters actions based on the mail attribute | String | 
|   [ saml:name ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_name)  | Filters actions based on the name attribute | String | 
|   [ saml:namequalifier ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_namequalifier)  | Filters actions based on the hash value of the issuer, account ID, and friendly name | String | 
|   [ saml:organizationStatus ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_organizationstatus)  | Filters actions based on the organizationStatus attribute | String | 
|   [ saml:primaryGroupSID ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_primarygroupsid)  | Filters actions based on the primaryGroupSID attribute | String | 
|   [ saml:sub ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_sub)  | Filters actions based on the subject of the claim \(the SAML user ID\) | String | 
|   [ saml:sub\_type ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_subtype)  | Filters actions based on the value persistent, transient, or the full Format URI | String | 
|   [ saml:surname ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_surname)  | Filters actions based on the surname attribute | String | 
|   [ saml:uid ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_uid)  | Filters actions based on the uid attribute | String | 
|   [ saml:x500UniqueIdentifier ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_x500uniqueidentifier)  | Filters actions based on the uid attribute | String | 
|   [ sts:ExternalId ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_externalid)  | Filters actions based on the unique identifier required when you assume a role in another account | String | 
|   [ sts:RoleSessionName ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_rolesessionname)  | Filters actions based on the role session name required when you assume a role | String | 
|   [ sts:TransitiveTagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_TransitiveTagKeys)  | Filters actions based on the transitive tag keys that are passed in the request | String | 
|   [ www\.amazon\.com:app\_id ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_id)  | Filters actions based on the Login with Amazon application ID | String | 
|   [ www\.amazon\.com:user\_id ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_id)  | Filters actions based on the Login with Amazon user ID | String | 