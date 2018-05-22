# Actions, Resources, and Condition Keys for Identity And Access Management<a name="list_identityandaccessmanagement"></a>

Identity And Access Management \(service prefix: `iam`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/IAM/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/IAM/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) permission policies\.

**Topics**
+ [Actions Defined by Identity And Access Management](#identityandaccessmanagement-actions-as-permissions)
+ [Resources Defined by IAM](#identityandaccessmanagement-resources-for-iam-policies)
+ [Condition Keys for Identity And Access Management](#identityandaccessmanagement-policy-keys)

## Actions Defined by Identity And Access Management<a name="identityandaccessmanagement-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_identityandaccessmanagement.html)

## Resources Defined by IAM<a name="identityandaccessmanagement-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#identityandaccessmanagement-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html) | arn:$\{Partition\}:iam::$\{Account\}:assumed\-role/$\{RoleName\}/$\{RoleSessionName\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html) | arn:$\{Partition\}:iam::$\{Account\}:federated\-user/$\{UserName\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_Group.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_Group.html) | arn:$\{Partition\}:iam::$\{Account\}:group/$\{GroupNameWithPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_Group.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_Group.html) | arn:$\{Partition\}:iam::$\{Account\}:$\{GroupPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_InstanceProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_InstanceProfile.html) | arn:$\{Partition\}:iam::$\{Account\}:instance\-profile/$\{InstanceProfileNameWithPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_MFADevice.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_MFADevice.html) | arn:$\{Partition\}:iam::$\{Account\}:mfa/$\{Path\}/$\{MfaTokenId\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetOpenIDConnectProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetOpenIDConnectProvider.html) | arn:$\{Partition\}:iam::$\{Account\}:oidc\-provider/$\{OidcProviderName\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_Policy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_Policy.html) | arn:$\{Partition\}:iam::$\{Account\}:policy/$\{PolicyNameWithPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_Policy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_Policy.html) | arn:$\{Partition\}:iam::$\{Account\}:$\{PolicyPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_Role.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_Role.html) | arn:$\{Partition\}:iam::$\{Account\}:role/$\{RoleNameWithPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_Role.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_Role.html) | arn:$\{Partition\}:iam::$\{Account\}:$\{RolePath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetSAMLProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetSAMLProvider.html) | arn:$\{Partition\}:iam::$\{Account\}:saml\-provider/$\{SamlProviderName\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ServerCertificate.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ServerCertificate.html) | arn:$\{Partition\}:iam::$\{Account\}:server\-certificate/$\{CertificateNameWithPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ServerCertificate.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ServerCertificate.html) | arn:$\{Partition\}:iam::$\{Account\}:$\{ServerCertificatePath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_sms.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_sms.html) | arn:$\{Partition\}:iam::$\{Account\}:sms\-mfa/$\{MfaTokenIdWithPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_User.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_User.html) | arn:$\{Partition\}:iam::$\{Account\}:user/$\{UserNameWithPath\} |  | 
| [http://docs.aws.amazon.com/IAM/latest/APIReference/API_User.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_User.html) | arn:$\{Partition\}:iam::$\{Account\}:$\{UserPath\} |  | 

## Condition Keys for Identity And Access Management<a name="identityandaccessmanagement-policy-keys"></a>

Identity And Access Management defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#available-keys-for-iam](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#available-keys-for-iam) | The ARN of an IAM policy\. | ARN | 
| iam:PassedToService | The AWS service to which this role is passed\. | String | 
| iam:AWSServiceName | The AWS service to which this role is attached\. | String | 