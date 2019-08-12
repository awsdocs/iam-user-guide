# Actions, Resources, and Condition Keys for Amazon WorkMail<a name="list_amazonworkmail"></a>

Amazon WorkMail \(service prefix: `workmail`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/workmail/latest/adminguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/workmail/latest/adminguide/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/workmail/latest/adminguide/iam_users_groups.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon WorkMail](#amazonworkmail-actions-as-permissions)
+ [Resources Defined by Amazon WorkMail](#amazonworkmail-resources-for-iam-policies)
+ [Condition Keys for Amazon WorkMail](#amazonworkmail-policy-keys)

## Actions Defined by Amazon WorkMail<a name="amazonworkmail-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddMembersToGroup ](https://docs.aws.amazon.com/workmail/latest/adminguide/groups_overview.html) \[permission only\] | Adds a list of members \(users or groups\) to a group\. | Write |  |  |  | 
|   [ AssociateDelegateToResource ](${APIReferenceDocPage}API_AssociateDelegateToResource.html)  | Adds a member \(user or group\) to the resource's set of delegates\. | Write |  |  |  | 
|   [ AssociateMemberToGroup ](${APIReferenceDocPage}API_AssociateMemberToGroup.html)  | Adds a member \(user or group\) to the group's set\. | Write |  |  |  | 
|   [ CreateAlias ](${APIReferenceDocPage}API_CreateAlias.html)  | Adds an alias to the set of a given member \(user or group\) of WorkMail\. | Write |  |  |  | 
|   [ CreateGroup ](${APIReferenceDocPage}API_CreateGroup.html)  | Creates a group that can be used in WorkMail by calling the RegisterToWorkMail operation\. | Write |  |  |  | 
|   [ CreateMailDomain ](https://docs.aws.amazon.com/workmail/latest/adminguide/add_domain.html) \[permission only\] | Creates a mail domain\. | Write |  |  |  | 
|   [ CreateMailUser ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-users.html) \[permission only\] | Creates a user in the directory and the WorkMail storage but does not enable the user for mail\. | Write |  |  |  | 
|   [ CreateOrganization ](https://docs.aws.amazon.com/workmail/latest/adminguide/add_new_organization.html) \[permission only\] | Creates an organization, either using an existing directory or creates a new directory on\-the\-fly\. Also creates and enables the complementary mail domain\. Optionally creates KMS key | Write |  |  |  | 
|   [ CreateResource ](${APIReferenceDocPage}API_CreateResource.html)  | Creates a new WorkMail resource\.  | Write |  |  |  | 
|   [ CreateUser ](${APIReferenceDocPage}API_CreateUser.html)  | Creates a user who can be used in WorkMail by calling the RegisterToWorkMail operation\. | Write |  |  |  | 
|   [ DeleteAlias ](${APIReferenceDocPage}API_DeleteAlias.html)  | Remove one or more specified aliases from a set of aliases for a given user\. | Write |  |  |  | 
|   [ DeleteGroup ](${APIReferenceDocPage}API_DeleteGroup.html)  | Deletes a group from WorkMail\. | Write |  |  |  | 
|   [ DeleteMailDomain ](https://docs.aws.amazon.com/workmail/latest/adminguide/remove_domain.html) \[permission only\] | Removes an unused mail domain from an organization | Write |  |  |  | 
|   [ DeleteMailboxPermissions ](${APIReferenceDocPage}API_DeleteMailboxPermissions.html)  | Deletes permissions granted to a member \(user or group\)\. | Write |  |  |  | 
|   [ DeleteMobileDevice ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-devices.html#remove_mobile_device) \[permission only\] | Removes a mobile device from a user | Write |  |  |  | 
|   [ DeleteOrganization ](https://docs.aws.amazon.com/workmail/latest/adminguide/remove_organization.html) \[permission only\] | Removes an organization from an account, either removing the directory from directory services or leaving it available for re\-use | Write |  |  |  | 
|   [ DeleteResource ](${APIReferenceDocPage}API_DeleteResource.html)  | Deletes the specified resource\. | Write |  |  |  | 
|   [ DeleteUser ](${APIReferenceDocPage}API_DeleteUser.html)  | Deletes a user from WorkMail and all subsequent systems\. The action cannot be undone\. | Write |  |  |  | 
|   [ DeregisterFromWorkMail ](${APIReferenceDocPage}API_DeregisterFromWorkMail.html)  | Mark a user, group, or resource as no longer used in WorkMail\. | Write |  |  |  | 
|   [ DescribeDirectories ](https://docs.aws.amazon.com/workmail/latest/adminguide/add_new_organization.html) \[permission only\] | Shows a list of directories available for use in creating an organization | List |  |  |  | 
|   [ DescribeGroup ](${APIReferenceDocPage}API_DescribeGroup.html)  | Returns the data available for the group\. | List |  |  |  | 
|   [ DescribeKmsKeys ](https://docs.aws.amazon.com/workmail/latest/adminguide/add_new_organization.html) \[permission only\] | Shows a list of KMS Keys available for use in creating an organization | List |  |  |  | 
|   [ DescribeMailDomains ](https://docs.aws.amazon.com/workmail/latest/adminguide/domains_overview.html) \[permission only\] | Shows the details of all mail domains associated with the organization | List |  |  |  | 
|   [ DescribeMailGroups ](https://docs.aws.amazon.com/workmail/latest/adminguide/groups_overview.html) \[permission only\] | Shows the details of all groups associated with the organization | List |  |  |  | 
|   [ DescribeMailUsers ](https://docs.aws.amazon.com/workmail/latest/adminguide/users_overview.html) \[permission only\] | Shows the details of all users associated with the orgaization | List |  |  |  | 
|   [ DescribeOrganization ](${APIReferenceDocPage}API_DescribeOrganization.html)  | Provides more information regarding a given organization based on its identifier\. | List |  |  |  | 
|   [ DescribeOrganizations ](https://docs.aws.amazon.com/workmail/latest/adminguide/organizations_overview.html) \[permission only\] | Shows a summary of all organizations associated with the account | List |  |  |  | 
|   [ DescribeResource ](${APIReferenceDocPage}API_DescribeResource.html)  | Returns the data available for the resource\. | List |  |  |  | 
|   [ DescribeUser ](${APIReferenceDocPage}API_DescribeUser.html)  | Provides information regarding the user\. | List |  |  |  | 
|   [ DisableMailGroups ](https://docs.aws.amazon.com/workmail/latest/adminguide/remove_group.html) \[permission only\] | Disable a mail group when it is not being used and, to allow it to be deleted | Write |  |  |  | 
|   [ DisableMailUsers ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-mailboxes.html#delete_user_mailbox) \[permission only\] | Disable a user mailbox when it is no longer being used, and to allow it to be deleted | Write |  |  |  | 
|   [ DisassociateDelegateFromResource ](${APIReferenceDocPage}API_DisassociateDelegateFromResource.html)  | Removes a member from the resource's set of delegates\. | Write |  |  |  | 
|   [ DisassociateMemberFromGroup ](${APIReferenceDocPage}API_DisassociateMemberFromGroup.html)  | Removes a member from a group\. | Write |  |  |  | 
|   [ EnableMailDomain ](https://docs.aws.amazon.com/workmail/latest/adminguide/add_domain.html) \[permission only\] | Enable a mail domain in the organization | Write |  |  |  | 
|   [ EnableMailGroups ](https://docs.aws.amazon.com/workmail/latest/adminguide/enable_existing_group.html) \[permission only\] | Enable a mail group after it has been created to allow it to receive mail | Write |  |  |  | 
|   [ EnableMailUsers ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-users.html#enable_existing_user) \[permission only\] | Enable a user's mailbox after it has been created to allow it to receive mail | Write |  |  |  | 
|   [ GetMailDomainDetails ](https://docs.aws.amazon.com/workmail/latest/adminguide/domains_overview.html) \[permission only\] | Get the details of the mail domain | Read |  |  |  | 
|   [ GetMailGroupDetails ](https://docs.aws.amazon.com/workmail/latest/adminguide/groups_overview.html) \[permission only\] | Get the details of the mail group | Read |  |  |  | 
|   [ GetMailUserDetails ](https://docs.aws.amazon.com/workmail/latest/adminguide/users_overview.html) \[permission only\] | Get the details of the user's mailbox and account | Read |  |  |  | 
|   [ GetMailboxDetails ](${APIReferenceDocPage}API_GetMailboxDetails.html)  | Returns the details of the user's mailbox\. | Read |  |  |  | 
|   [ GetMobileDeviceDetails ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-devices.html) \[permission only\] | Get the details of the mobile device | Read |  |  |  | 
|   [ GetMobileDevicesForUser ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-devices.html) \[permission only\] | Get a list of the mobile devices associated with the user | Read |  |  |  | 
|   [ GetMobilePolicyDetails ](https://docs.aws.amazon.com/workmail/latest/adminguide/edit_organization_mobile_policy.html) \[permission only\] | Get the details of the mobile device policy associated with the organization | Read |  |  |  | 
|   [ ListAliases ](${APIReferenceDocPage}API_ListAliases.html)  | Creates a paginated call to list the aliases associated with a given entity\. | List |  |  |  | 
|   [ ListGroupMembers ](${APIReferenceDocPage}API_ListGroupMembers.html)  | Returns an overview of the members of a group\. Users and groups can be members of a group\. | List |  |  |  | 
|   [ ListGroups ](${APIReferenceDocPage}API_ListGroups.html)  | Returns summaries of the organization's groups\. | List |  |  |  | 
|   [ ListMailboxPermissions ](${APIReferenceDocPage}API_ListMailboxPermissions.html)  | Lists the mailbox permissions associated with a user, group, or resource mailbox\. | List |  |  |  | 
|   [ ListMembersInMailGroup ](https://docs.aws.amazon.com/workmail/latest/adminguide/groups_overview.html) \[permission only\] | Get a list of all the members in a mail group | Read |  |  |  | 
|   [ ListOrganizations ](${APIReferenceDocPage}API_ListOrganizations.html)  | Returns summaries of the customer's non\-deleted organizations\. | List |  |  |  | 
|   [ ListResourceDelegates ](${APIReferenceDocPage}API_ListResourceDelegates.html)  | Lists the delegates associated with a resource\. | List |  |  |  | 
|   [ ListResources ](${APIReferenceDocPage}API_ListResources.html)  | Returns summaries of the organization's resources\. | List |  |  |  | 
|   [ ListUsers ](${APIReferenceDocPage}API_ListUsers.html)  | Returns summaries of the organization's users\. | List |  |  |  | 
|   [ PutMailboxPermissions ](${APIReferenceDocPage}API_PutMailboxPermissions.html)  | Sets permissions for a user, group, or resource\. This replaces any pre\-existing permissions\. | Write |  |  |  | 
|   [ RegisterToWorkMail ](${APIReferenceDocPage}API_RegisterToWorkMail.html)  | Registers an existing and disabled user, group, or resource for use by associating a mailbox and calendaring capabilities\. | Write |  |  |  | 
|   [ RemoveMembersFromGroup ](https://docs.aws.amazon.com/workmail/latest/adminguide/groups_overview.html) \[permission only\] | Remove members from a mail group | Write |  |  |  | 
|   [ ResetPassword ](${APIReferenceDocPage}API_ResetPassword.html)  | Allows the administrator to reset the password for a user\. | Write |  |  |  | 
|   [ ResetUserPassword ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-users.html#reset_user_password) \[permission only\] | Reset the password for a user's account | Write |  |  |  | 
|   [ SearchMembers ](https://docs.aws.amazon.com/workmail/latest/adminguide/groups_overview.html) \[permission only\] | Prefix search to find a specific user in a mail group | Read |  |  |  | 
|   [ SetAdmin ](https://docs.aws.amazon.com/workmail/latest/adminguide/users_overview.html) \[permission only\] | Mark a user as being an administrator | Write |  |  |  | 
|   [ SetDefaultMailDomain ](https://docs.aws.amazon.com/workmail/latest/adminguide/default_domain.html) \[permission only\] | Set the default mail domain for the organization | Write |  |  |  | 
|   [ SetMailGroupDetails ](https://docs.aws.amazon.com/workmail/latest/adminguide/add_new_group.html) \[permission only\] | Set the details of the mail group which has just been created | Write |  |  |  | 
|   [ SetMailUserDetails ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-users.html) \[permission only\] | Set the details for the user account which has just been created | Write |  |  |  | 
|   [ SetMobilePolicyDetails ](https://docs.aws.amazon.com/workmail/latest/adminguide/edit_organization_mobile_policy.html) \[permission only\] | Set the details of a mobile policy associated with the organization | Write |  |  |  | 
|   [ UpdateMailboxQuota ](${APIReferenceDocPage}API_UpdateMailboxQuota.html)  | Updates the maximum size \(in MB\) of the user's mailbox\. | Write |  |  |  | 
|   [ UpdatePrimaryEmailAddress ](${APIReferenceDocPage}API_UpdatePrimaryEmailAddress.html)  | Updates the primary email for a user, group, or resource\. | Write |  |  |  | 
|   [ UpdateResource ](${APIReferenceDocPage}API_UpdateResource.html)  | Updates data for the resource\. To retrieve the latest information, it must be preceded by a DescribeResource call\. | Write |  |  |  | 
|   [ WipeMobileDevice ](https://docs.aws.amazon.com/workmail/latest/adminguide/manage-devices.html#remote_wipe_device) \[permission only\] | Remotely wipe the mobile device associated with a user's account | Write |  |  |  | 

## Resources Defined by Amazon WorkMail<a name="amazonworkmail-resources-for-iam-policies"></a>

Amazon WorkMail has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon WorkMail<a name="amazonworkmail-policy-keys"></a>

WorkMail has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.