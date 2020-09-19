# Actions, resources, and condition keys for Identity And Access Management<a name="list_identityandaccessmanagement"></a>

Identity And Access Management \(service prefix: `iam`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/IAM/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) permission policies\.

**Topics**
+ [Actions defined by Identity And Access Management](#identityandaccessmanagement-actions-as-permissions)
+ [Resource types defined by Identity And Access Management](#identityandaccessmanagement-resources-for-iam-policies)
+ [Condition keys for Identity And Access Management](#identityandaccessmanagement-policy-keys)

## Actions defined by Identity And Access Management<a name="identityandaccessmanagement-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_identityandaccessmanagement.html)

## Resource types defined by Identity And Access Management<a name="identityandaccessmanagement-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#identityandaccessmanagement-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ access\-report ](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_access-advisor-view-data-orgs.html)  |  arn:$\{Partition\}:iam::$\{Account\}:access\-report/$\{EntityPath\}  |  | 
|   [ assumed\-role ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html)  |  arn:$\{Partition\}:iam::$\{Account\}:assumed\-role/$\{RoleName\}/$\{RoleSessionName\}  |  | 
|   [ federated\-user ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html)  |  arn:$\{Partition\}:iam::$\{Account\}:federated\-user/$\{UserName\}  |  | 
|   [ group ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html)  |  arn:$\{Partition\}:iam::$\{Account\}:group/$\{GroupNameWithPath\}  |  | 
|   [ instance\-profile ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html)  |  arn:$\{Partition\}:iam::$\{Account\}:instance\-profile/$\{InstanceProfileNameWithPath\}  |  | 
|   [ mfa ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html)  |  arn:$\{Partition\}:iam::$\{Account\}:mfa/$\{MfaTokenIdWithPath\}  |  | 
|   [ oidc\-provider ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_create_oidc.html)  |  arn:$\{Partition\}:iam::$\{Account\}:oidc\-provider/$\{OidcProviderName\}  |  | 
|   [ policy ](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html)  |  arn:$\{Partition\}:iam::$\{Account\}:policy/$\{PolicyNameWithPath\}  |  | 
|   [ role ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)  |  arn:$\{Partition\}:iam::$\{Account\}:role/$\{RoleNameWithPath\}  |   [ iam:ResourceTag/$\{TagKey\} ](#identityandaccessmanagement-iam_ResourceTag___TagKey_)   | 
|   [ saml\-provider ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html)  |  arn:$\{Partition\}:iam::$\{Account\}:saml\-provider/$\{SamlProviderName\}  |  | 
|   [ server\-certificate ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_server-certs.html)  |  arn:$\{Partition\}:iam::$\{Account\}:server\-certificate/$\{CertificateNameWithPath\}  |  | 
|   [ sms\-mfa ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_sms.html)  |  arn:$\{Partition\}:iam::$\{Account\}:sms\-mfa/$\{MfaTokenIdWithPath\}  |  | 
|   [ user ](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)  |  arn:$\{Partition\}:iam::$\{Account\}:user/$\{UserNameWithPath\}  |   [ iam:ResourceTag/$\{TagKey\} ](#identityandaccessmanagement-iam_ResourceTag___TagKey_)   | 

## Condition keys for Identity And Access Management<a name="identityandaccessmanagement-policy-keys"></a>

Identity And Access Management defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ iam:AWSServiceName ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_AWSServiceName)  | Filters access by the AWS service to which this role is attached | String | 
|   [ iam:AssociatedResourceArn ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_AssociatedResourceArn)  | Filters by the resource that the role will be used on behalf of | ARN | 
|   [ iam:OrganizationsPolicyId ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_OrganizationsPolicyId)  | Filters access by the ID of an AWS Organizations policy | String | 
|   [ iam:PassedToService ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_PassedToService)  | Filters access by the AWS service to which this role is passed | String | 
|   [ iam:PermissionsBoundary ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_PermissionsBoundary)  | Filters access if the specified policy is set as the permissions boundary on the IAM entity \(user or role\) | String | 
|   [ iam:PolicyARN ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_PolicyARN)  | Filters access by the ARN of an IAM policy | ARN | 
|   [ iam:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html#ck_ResourceTag)  | Filters access by the tags attached to an IAM entity \(user or role\)\. | String | 