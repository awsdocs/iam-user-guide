# Actions, resources, and condition keys for AWS SSO Directory<a name="list_awsssodirectory"></a>

AWS SSO Directory \(service prefix: `sso-directory`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/singlesignon/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/singlesignon/latest/userguide/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS SSO Directory](#awsssodirectory-actions-as-permissions)
+ [Resource types defined by AWS SSO Directory](#awsssodirectory-resources-for-iam-policies)
+ [Condition keys for AWS SSO Directory](#awsssodirectory-policy-keys)

## Actions defined by AWS SSO Directory<a name="awsssodirectory-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddMemberToGroup ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Adds member to the group in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ CompleteVirtualMfaDeviceRegistration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Completes the creation process of a virtual MFA device | Write |  |  |  | 
|   [ CreateAlias ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Creates an alias for the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ CreateBearerToken ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Creates a bearer token for a given provisioning tenant\. | Write |  |  |  | 
|   [ CreateExternalIdPConfigurationForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create an External Identity Provider configuration for the directory | Write |  |  |  | 
|   [ CreateGroup ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Creates a group in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ CreateProvisioningTenant ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Creates a provisioning tenant for a given directory\. | Write |  |  |  | 
|   [ CreateUser ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Creates a user in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ DeleteBearerToken ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Deletes the bearer token\. | Write |  |  |  | 
|   [ DeleteExternalIdPConfigurationForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete an External Identity Provider configuration associated with the directory | Write |  |  |  | 
|   [ DeleteGroup ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Deletes a group from the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ DeleteMfaDeviceForUser ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Deletes a MFA device by device name for a given user | Write |  |  |  | 
|   [ DeleteProvisioningTenant ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Deletes the provisioning tenant\. | Write |  |  |  | 
|   [ DeleteUser ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Deletes a user from the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ DescribeDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve information about the directory that AWS SSO provides by default | Read |  |  |  | 
|   [ DescribeGroups ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieves information about group from the directory that AWS SSO provides by default | List |  |  |  | 
|   [ DescribeUsers ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieves information about user from the directory that AWS SSO provides by default | List |  |  |  | 
|   [ DisableExternalIdPConfigurationForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Disable authentication of end users with an External Identity Provider | Write |  |  |  | 
|   [ DisableUser ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Deactivates user in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ EnableExternalIdPConfigurationForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Enable authentication of end users with an External Identity Provider | Write |  |  |  | 
|   [ EnableUser ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Activates user in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ GetAWSSPConfigurationForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve the AWS SSO Service Provider configurations for the directory | Read |  |  |  | 
|   [ ListBearerTokens ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Lists bearer tokens for a given provisioning tenant\. | List |  |  |  | 
|   [ ListExternalIdPConfigurationsForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | List all the External Identity Provider configurations created for the directory | List |  |  |  | 
|   [ ListGroupsForUser ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Lists groups for a user from the directory that AWS SSO provides by default  | List |  |  |  | 
|   [ ListMembersInGroup ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieves all members that are part of the group in the directory that AWS SSO provides by default | List |  |  |  | 
|   [ ListMfaDevicesForUser ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Lists all active MFA devices and their MFA device metadata for a user | List |  |  |  | 
|   [ ListProvisioningTenants ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Lists provisioning tenants for a given directory\. | List |  |  |  | 
|   [ RemoveMemberFromGroup ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Removes member that are part of the group in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ SearchGroups ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Search for groups within the associated directory | Read |  |  |  | 
|   [ SearchUsers ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Search for users within the associated directory | Read |  |  |  | 
|   [ StartVirtualMfaDeviceRegistration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Begins the creation process of virtual mfa device | Write |  |  |  | 
|   [ UpdateExternalIdPConfigurationForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update an External Identity Provider configuration associated with the directory | Write |  |  |  | 
|   [ UpdateGroup ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Updates information about group in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ UpdatePassword ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Updates password by sending password reset link via email or generating one time password for a user in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ UpdateUser ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Updates user information in the directory that AWS SSO provides by default | Write |  |  |  | 
|   [ VerifyEmail ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Verify email address of an User | Write |  |  |  | 

## Resource types defined by AWS SSO Directory<a name="awsssodirectory-resources-for-iam-policies"></a>

AWS SSO Directory does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS SSO Directory, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS SSO Directory<a name="awsssodirectory-policy-keys"></a>

SSO Directory has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.