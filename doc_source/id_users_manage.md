# Managing IAM users<a name="id_users_manage"></a>

Amazon Web Services offers multiple tools for managing the IAM users in your AWS account\. You can list the IAM users in your account or in a group, or list all groups that a user is a member of\. You can rename or change the path of an IAM user\. You can also delete an IAM user from your AWS account\.

For more information about adding, changing, or removing managed policies for an IAM user, see [Changing permissions for an IAM user](id_users_change-permissions.md)\. For information about managing inline policies for IAM users, see [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md), [Editing IAM policies](access_policies_manage-edit.md), and [Deleting IAM policies](access_policies_manage-delete.md)\. As a best practice, use managed policies instead of inline policies\.

 For information about managing IAM user passwords, see [Managing passwords for IAM users](id_credentials_passwords_admin-change-user.md),

**Topics**
+ [View user access](#users-manage_prerequisites)
+ [Listing IAM users](#id_users_manage_list)
+ [Renaming an IAM user](#id_users_renaming)
+ [Deleting an IAM user](#id_users_deleting)

## View user access<a name="users-manage_prerequisites"></a>

Before you delete a user, you should review its recent service\-level activity\. This is important because you don't want to remove access from a principal \(person or application\) who is using it\. For more information about viewing last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

## Listing IAM users<a name="id_users_manage_list"></a>

You can list the IAM users in your AWS account or in a specific IAM group, and list all the groups that a user is in\. For information about the permissions that you need in order to list users, see [Permissions required to access IAM resources](access_permissions-required.md)\. 

### To list all the users in the account<a name="id_users_manage_list-users"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Users**\. The console displays the users in your AWS account\. 
+ AWS CLI: [aws iam list\-users](https://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html)
+ AWS API: [ListUsers](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html) 

### To list the users in a specific group<a name="id_users_manage_list-users-group"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups**, choose the name of the group, and then choose the **Users** tab\. 
+ AWS CLI: [aws iam get\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html)
+ AWS API: [GetGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html)

### To list all the groups that a user is in<a name="id_users_manage_list-groups-users"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Users**, choose the user name, and then choose the **Groups** tab\. 
+ AWS CLI: [aws iam list\-groups\-for\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups-for-user.html)
+ AWS API: [ListGroupsForUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html)

## Renaming an IAM user<a name="id_users_renaming"></a>

To change a user's name or path, you must use the AWS CLI, Tools for Windows PowerShell, or AWS API\. There is no option in the console to rename a user\. For information about the permissions that you need in order to rename a user, see [Permissions required to access IAM resources](access_permissions-required.md)\. 

When you change a user's name or path, the following happens: 
+ Any policies attached to the user stay with the user under the new name\.
+ The user stays in the same groups under the new name\.
+ The unique ID for the user remains the same\. For more information about unique IDs, see [Unique identifiers](reference_identifiers.md#identifiers-unique-ids)\.
+ Any resource or role policies that refer to the user *as a principal* \(the user is being granted access\) are automatically updated to use the new name or path\. For example, any queue\-based policies in Amazon SQS or resource\-based policies in Amazon S3 are automatically updated to use the new name and path\. 

IAM does not automatically update policies that refer to the user *as a resource* to use the new name or path; you must manually do that\. For example, imagine that user `Richard` has a policy attached to him that lets him manage his security credentials\. If an administrator renames `Richard` to `Rich`, the administrator also needs to update that policy to change the resource from this:

```
arn:aws:iam::111122223333:user/division_abc/subdivision_xyz/Richard
```

to this:

```
arn:aws:iam::111122223333:user/division_abc/subdivision_xyz/Rich
```

This is true also if an administrator changes the path; the administrator needs to update the policy to reflect the new path for the user\. 

### To rename a user<a name="id_users_manage_list-users-rename"></a>
+ AWS CLI: [aws iam update\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/update-user.html)
+ AWS API: [UpdateUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateUser.html) 

## Deleting an IAM user<a name="id_users_deleting"></a>

You might delete an IAM user from your account if someone quits your company\. If the user is only temporarily away from your company, you can disable the user's credentials instead of deleting the user entirely from the AWS account\. That way, you can prevent the user from accessing the AWS account's resources during the absence but you can re\-enable the user later\.

For more information about disabling credentials, see [Managing access keys for IAM users](id_credentials_access-keys.md)\. For information about the permissions that you need in order to delete a user, see [Permissions required to access IAM resources](access_permissions-required.md)\. 

**Topics**
+ [Deleting an IAM user \(console\)](#id_users_deleting_console)
+ [Deleting an IAM user \(AWS CLI\)](#id_users_deleting_cli)

### Deleting an IAM user \(console\)<a name="id_users_deleting_console"></a>

When you use the AWS Management Console to delete an IAM user, IAM automatically deletes the following information for you: 
+ The user
+ Any group memberships—that is, the user is removed from any IAM groups that the user was a member of 
+ Any password associated with the user
+ Any access keys belonging to the user
+ All inline policies embedded in the user \(policies that are applied to a user via group permissions are not affected\) 
**Note**  
Any managed policies attached to the user are detached from the user when the user is deleted\. Managed policies are not deleted when you delete a user\. 
+ Any associated MFA device

**To delete an IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**, and then select the check box next to the user name that you want to delete, not the name or row itself\. 

1. At the top of the page, choose **Delete user**\. 

1. In the confirmation dialog box, wait for the last accessed information to load before you review the data\. The dialog box shows when each of the selected users last accessed an AWS service\. If you attempt to delete a user that has been active within the last 30 days, you must select an additional check box to confirm that you want to delete the active user\. If you want to proceed, choose **Yes, Delete**\. 

### Deleting an IAM user \(AWS CLI\)<a name="id_users_deleting_cli"></a>

Unlike the AWS Management Console, when you delete a user with the AWS CLI, you must delete the items attached to the user manually\. This procedure illustrates the process\. 

**To delete a user from your account \(AWS CLI\)**

1. Delete the user's password, if the user has one\.

   `[aws iam delete\-login\-profile](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-login-profile.html)`

1. Delete the user's access keys, if the user has them\.

   `[aws iam list\-access\-keys](https://docs.aws.amazon.com/cli/latest/reference/iam/list-access-keys.html)` \(to list the user's access keys\) and `[aws iam delete\-access\-key](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html)`

1. Delete the user's signing certificate\. Note that when you delete a security credential, it's gone forever and can't be retrieved\.

   `[aws iam list\-signing\-certificates](https://docs.aws.amazon.com/cli/latest/reference/iam/list-signing-certificates.html)` \(to list the user's signing certificates\) and `[aws iam delete\-signing\-certificate](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-signing-certificate.html)`

1. Delete the user's SSH public key, if the user has them\.

   `[aws iam list\-ssh\-public\-keys](https://docs.aws.amazon.com/cli/latest/reference/iam/list-ssh-public-keys.html)` \(to list the user's SSH public keys\) and `[aws iam delete\-ssh\-public\-key](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-ssh-public-key.html)`

1. Delete the user's Git credentials\.

   `[aws iam list\-service\-specific\-credentials](https://docs.aws.amazon.com/cli/latest/reference/iam/list-service-specific-credentials.html)` \(to list the user's git credentials\) and `[aws iam delete\-service\-specific\-credential](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-service-specific-credential.html)`

1. Deactivate the user's multi\-factor authentication \(MFA\) device, if the user has one\.

   `[aws iam list\-mfa\-devices](https://docs.aws.amazon.com/cli/latest/reference/iam/list-mfa-devices.html)` \(to list the user's MFA devices\), `[aws iam deactivate\-mfa\-device](https://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html)` \(to deactivate the device\), and `[aws iam delete\-virtual\-mfa\-device](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-virtual-mfa-device.html)` \(to permanently delete a virtual MFA device\) 

1. Delete the user's inline policies\. 

   `[aws iam list\-user\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-user-policies.html)` \(to list the inline policies for the user\) and [https://docs.aws.amazon.com/cli/latest/reference/iam/delete-user-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-user-policy.html) \(to delete the policy\) 

1. Detach any managed policies that are attached to the user\. 

   `[aws iam list\-attached\-user\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-user-policies.html)` \(to list the managed policies attached to the user\) and [https://docs.aws.amazon.com/cli/latest/reference/iam/detach-user-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/detach-user-policy.html) \(to detach the policy\) 

1. Remove the user from any groups\. 

   `[aws iam list\-groups\-for\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups-for-user.html)` \(to list the groups to which the user belongs\) and `[aws iam remove\-user\-from\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html)` 

1. Delete the user\.

   `[aws iam delete\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-user.html)` 