# Actions, Resources, and Condition Keys for AWS Organizations<a name="list_awsorganizations"></a>

AWS Organizations \(service prefix: `organizations`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/organizations/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/organizations/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Organizations](#awsorganizations-actions-as-permissions)
+ [Resources Defined by Organizations](#awsorganizations-resources-for-iam-policies)
+ [Condition Keys for AWS Organizations](#awsorganizations-policy-keys)

## Actions Defined by AWS Organizations<a name="awsorganizations-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsorganizations.html)

## Resources Defined by Organizations<a name="awsorganizations-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsorganizations-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ account ](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_reference_arn-formats.html)  |  arn:$\{Partition\}:organizations::$\{MasterAccountId\}:account/o\-$\{OrganizationId\}/$\{AccountId\}  |  | 
|   [ handshake ](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_reference_arn-formats.html)  |  arn:$\{Partition\}:organizations::$\{MasterAccountId\}:handshake/o\-$\{OrganizationId\}/$\{HandshakeType\}/h\-$\{HandshakeId\}  |  | 
|   [ organization ](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_reference_arn-formats.html)  |  arn:$\{Partition\}:organizations::$\{MasterAccountId\}:organization/o\-$\{OrganizationId\}  |  | 
|   [ organizationalunit ](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_reference_arn-formats.html)  |  arn:$\{Partition\}:organizations::$\{MasterAccountId\}:ou/o\-$\{OrganizationId\}/ou\-$\{OrganizationalUnitId\}  |  | 
|   [ policy ](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_reference_arn-formats.html)  |  arn:$\{Partition\}:organizations::$\{MasterAccountId\}:policy/o\-$\{OrganizationId\}/$\{PolicyType\}/p\-$\{PolicyId\}  |  | 
|   [ awspolicy ](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_reference_arn-formats.html)  |  arn:$\{Partition\}:organizations::aws:policy/$\{PolicyType\}/p\-$\{PolicyId\}  |  | 
|   [ root ](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_reference_arn-formats.html)  |  arn:$\{Partition\}:organizations::$\{MasterAccountId\}:root/o\-$\{OrganizationId\}/r\-$\{RootId\}  |  | 

## Condition Keys for AWS Organizations<a name="awsorganizations-policy-keys"></a>

AWS Organizations defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ organizations:ServicePrincipal ](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_permissions_overview.html#orgs_permissions_conditionkeys)  | Enables you to filter the request to only the specified service principal names\. | String | 