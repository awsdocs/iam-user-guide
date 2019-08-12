# Actions, Resources, and Condition Keys for AWS SSO Directory<a name="list_awsssodirectory"></a>

AWS SSO Directory \(service prefix: `sso-directory`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/singlesignon/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access.html) permission policies\.

**Topics**
+ [Actions Defined by AWS SSO Directory](#awsssodirectory-actions-as-permissions)
+ [Resources Defined by AWS SSO Directory](#awsssodirectory-resources-for-iam-policies)
+ [Condition Keys for AWS SSO Directory](#awsssodirectory-policy-keys)

## Actions Defined by AWS SSO Directory<a name="awsssodirectory-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   AddMemberToGroup  | Adds member to the group in the directory that AWS SSO provides by default | Write |  |  |  | 
|   CreateAlias  | Creates an alias for the directory that AWS SSO provides by default | Write |  |  |  | 
|   CreateGroup  | Creates a group in the directory that AWS SSO provides by default | Write |  |  |  | 
|   CreateUser  | Creates a user in the directory that AWS SSO provides by default | Write |  |  |  | 
|   DeleteGroup  | Deletes a group from the directory that AWS SSO provides by default | Write |  |  |  | 
|   DeleteUser  | Deletes a user from the directory that AWS SSO provides by default | Write |  |  |  | 
|   DescribeDirectory  | Retrieve information about the directory that AWS SSO provides by default | Read |  |  |  | 
|   DescribeGroups  | Retrieves information about group from the directory that AWS SSO provides by default | List |  |  |  | 
|   DescribeUsers  | Retrieves information about user from the directory that AWS SSO provides by default | List |  |  |  | 
|   DisableUser  | Deactivates user in the directory that AWS SSO provides by default | Write |  |  |  | 
|   EnableUser  | Activates user in the directory that AWS SSO provides by default | Write |  |  |  | 
|   ListGroupsForUser  | Lists groups for a user from the directory that AWS SSO provides by default  | List |  |  |  | 
|   ListMembersInGroup  | Retrieves all members that are part of the group in the directory that AWS SSO provides by default | List |  |  |  | 
|   RemoveMemberFromGroup  | Removes member that are part of the group in the directory that AWS SSO provides by default | Write |  |  |  | 
|   UpdateGroup  | Updates information about group in the directory that AWS SSO provides by default | Write |  |  |  | 
|   UpdatePassword  | Updates password by sending password reset link via email or generating one time password for a user in the directory that AWS SSO provides by default | Write |  |  |  | 
|   UpdateUser  | Updates user information in the directory that AWS SSO provides by default | Write |  |  |  | 
|   VerifyEmail  | Verify email address of an User | Write |  |  |  | 

## Resources Defined by AWS SSO Directory<a name="awsssodirectory-resources-for-iam-policies"></a>

AWS SSO Directory has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS SSO Directory<a name="awsssodirectory-policy-keys"></a>

SSO Directory has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.