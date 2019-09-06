# Actions, Resources, and Condition Keys for Amazon QuickSight<a name="list_amazonquicksight"></a>

Amazon QuickSight \(service prefix: `quicksight`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/quicksight/latest/user/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/quicksight/latest/user/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/quicksight/latest/user/working-with-iam.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon QuickSight](#amazonquicksight-actions-as-permissions)
+ [Resources Defined by Amazon QuickSight](#amazonquicksight-resources-for-iam-policies)
+ [Condition Keys for Amazon QuickSight](#amazonquicksight-policy-keys)

## Actions Defined by Amazon QuickSight<a name="amazonquicksight-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateAdmin ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | CreateAdmin enables the user to provision Amazon QuickSight administrators, authors, and readers\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ CreateGroup ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Create a QuickSight group\. | Write |   [ group\* ](#amazonquicksight-group)   |  |  | 
|   [ CreateGroupMembership ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Add a QuickSight user to a QuickSight group\. | Write |   [ group\* ](#amazonquicksight-group)   |   [ quicksight:UserName ](#amazonquicksight-quicksight_UserName)   |  | 
|   [ CreateReader ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | CreateReader enables the user to provision Amazon QuickSight readers\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ CreateUser ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | CreateUser enables the user to provision Amazon QuickSight authors and readers\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ DeleteGroup ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Remove a user group from QuickSight\. | Write |   [ group\* ](#amazonquicksight-group)   |  |  | 
|   [ DeleteGroupMembership ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Remove a user from a group so that he/she is no longer a member of the group\. | Write |   [ group\* ](#amazonquicksight-group)   |   [ quicksight:UserName ](#amazonquicksight-quicksight_UserName)   |  | 
|   [ DeleteUser ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Delete the QuickSight user that is associated with the identity of the IAM user/role making the call\. The IAM user is not deleted as a result of this call\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ DeleteUserByPrincipalId ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Deletes a user identified by its principal ID\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ DescribeGroup ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Return a QuickSight group’s description and ARN\. | Read |   [ group\* ](#amazonquicksight-group)   |  |  | 
|   [ DescribeUser ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Return information about a user, given the user name\. | Read |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ GetDashboardEmbedUrl ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Return a QuickSight dashboard embedding URL\. | Read |   [ dashboard\* ](#amazonquicksight-dashboard)   |  |  | 
|   [ GetGroupMapping ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | GetGroupMapping is used only in Amazon QuickSight Enterprise edition accounts\. It enables the user to use Amazon QuickSight to identify and display the Microsoft Active Directory \(Microsoft Active Directory\) directory groups that are mapped to roles in Amazon QuickSight\. | Read |  |  |  | 
|   [ ListGroupMemberships ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Return a list of member users in a group\. | List |   [ group\* ](#amazonquicksight-group)   |  |  | 
|   [ ListGroups ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Get a list of all user groups in QuickSight\. | List |   [ group\* ](#amazonquicksight-group)   |  |  | 
|   [ ListUserGroups ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Return a list of groups that a given user is a member of\. | List |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ ListUsers ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Return a list of all of the QuickSight users belonging to this account\. | List |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ RegisterUser ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Create a QuickSight user, whose identity is associated with the IAM identity/role specified in the request\. | Write |   [ user\* ](#amazonquicksight-user)   |   [ quicksight:IamArn ](#amazonquicksight-quicksight_IamArn)   [ quicksight:SessionName ](#amazonquicksight-quicksight_SessionName)   |  | 
|   [ SearchDirectoryGroups ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | SearchDirectoryGroups is used only in Amazon QuickSight Enterprise edition accounts\. It enables the user to use Amazon QuickSight to display your Microsoft Active Directory directory groups so that you can choose which ones to map to roles in Amazon QuickSight\. | Write |  |  |  | 
|   [ SetGroupMapping ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | SearchDirectoryGroups is used only in Amazon QuickSight Enterprise edition accounts\. It enables the user to use Amazon QuickSight to display your Microsoft Active Directory directory groups so that you can choose which ones to map to roles in Amazon QuickSight\. | Write |  |  |  | 
|   [ Subscribe ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | Subscribe enables the user to subscribe to Amazon QuickSight\. Enabling this action also allows the user to upgrade the subscription to Enterprise edition\. | Write |  |  |  | 
|   [ Unsubscribe ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | Unsubscribe enables the user to unsubscribe from Amazon QuickSight, which permanently deletes all users and their resources from Amazon QuickSight\. | Write |  |  |  | 
|   [ UpdateGroup ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Change group description\. | Write |   [ group\* ](#amazonquicksight-group)   |  |  | 
|   [ UpdateUser ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | Updates an Amazon QuickSight user\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 

## Resources Defined by Amazon QuickSight<a name="amazonquicksight-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonquicksight-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ user ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  |  arn:$\{Partition\}:quicksight:$\{Region\}:$\{Account\}:user/$\{ResourceId\}  |  | 
|   [ group ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  |  arn:$\{Partition\}:quicksight:$\{Region\}:$\{Account\}:group/$\{ResourceId\}  |  | 
|   [ dashboard ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  |  arn:$\{Partition\}:quicksight:$\{Region\}:$\{Account\}:dashboard/$\{ResourceId\}  |  | 

## Condition Keys for Amazon QuickSight<a name="amazonquicksight-policy-keys"></a>

Amazon QuickSight defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ quicksight:IamArn ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | IAM user ARN or role ARN\. | String | 
|   [ quicksight:SessionName ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | The session name\. | String | 
|   [ quicksight:UserName ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html)  | The user name\. | String | 