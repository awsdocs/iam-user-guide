# Managing IAM Users<a name="id_users_manage"></a>

Amazon Web Services offers multiple tools for managing the IAM users in your AWS account\.

**Topics**
+ [Listing IAM Users](#id_users_manage_list)
+ [Renaming an IAM User](#id_users_renaming)
+ [Deleting an IAM User](#id_users_deleting)

## Listing IAM Users<a name="id_users_manage_list"></a>

You can list the IAM users in your AWS account or in a specific IAM group, and list all the groups that a user is in\. For information about the permissions that you need in order to list users, see [Permissions Required to Access IAM Resources](access_permissions-required.md)\. 

### To list all the users in the account<a name="w3ab1c19c19c23b7b4"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Users**\. The console displays the users in your AWS account\. 
+ AWS CLI: [aws iam list\-users](http://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html)
+ Tools for Windows PowerShell: [Get\-IAMUsers](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMUsers.html&tocid=Get-IAMUsers)
+ AWS API: [ListUsers](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html) 

### To list the users in a specific group<a name="w3ab1c19c19c23b7b6"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups**, choose the name of the group, and then choose the **Users** tab\. 
+ AWS CLI: [aws iam get\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html)
+ Tools for Windows PowerShell: [Get\-IAMGroup](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMGroup.html&tocid=Get-IAMGroup)
+ AWS API: [GetGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html)

### To list all the groups that a user is in<a name="w3ab1c19c19c23b7b8"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Users**, choose the user name, and then choose the **Groups** tab\. 
+ AWS CLI: [aws iam list\-groups\-for\-user](http://docs.aws.amazon.com/cli/latest/reference/iam/list-groups-for-user.html)
+ Tools for Windows PowerShell: [Get\-IAMGroupForUser](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMGroupForUser.html&tocid=Get-IAMGroupForUser)
+ AWS API: [ListGroupsForUser](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html)

## Renaming an IAM User<a name="id_users_renaming"></a>

To change a user's name or path, you must use the AWS CLI, Tools for Windows PowerShell, or AWS API\. There is no option in the console to rename a user\. For information about the permissions that you need in order to rename a user, see [Permissions Required to Access IAM Resources](access_permissions-required.md)\. 

When you change a user's name or path, the following happens: 
+ Any policies attached to the user stay with the user under the new name\.
+ The user stays in the same groups under the new name\.
+ The unique ID for the user remains the same\. For more information about unique IDs, see [Unique IDs](reference_identifiers.md#identifiers-unique-ids)\.
+ Any resource or role policies that refer to the user *as a principal* \(the user is being granted access\) are automatically updated to use the new name or path\. For example, any queue\-based policies in Amazon SQS or resource\-based policies in Amazon S3 are automatically updated to use the new name and path\. 

IAM does not automatically update policies that refer to the user *as a resource* to use the new name or path; you must manually do that\. For example, imagine that user `Bob` has a policy attached to him that lets him manage his security credentials\. If an administrator renames `Bob` to `Robert`, the administrator also needs to update that policy to change the resource from this:

```
arn:aws:iam::111122223333:user/division_abc/subdivision_xyz/Bob
```

to this:

```
arn:aws:iam::111122223333:user/division_abc/subdivision_xyz/Robert
```

This is true also if an administrator changes the path; the administrator needs to update the policy to reflect the new path for the user\. 

### To rename a user<a name="w3ab1c19c19c23b9c18"></a>
+ AWS CLI: [aws iam update\-user](http://docs.aws.amazon.com/cli/latest/reference/iam/update-user.html)
+ Tools for Windows PowerShell: [Update\-IAMUser](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMUser.html&tocid=Update-IAMUser)
+ AWS API: [UpdateUser](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateUser.html) 

## Deleting an IAM User<a name="id_users_deleting"></a>

You might delete an IAM user from your account if someone quits your company\. If the user is only temporarily away from your company, you can disable the user's credentials instead of deleting the user entirely from the AWS account\. That way, you can prevent the user from accessing the AWS account's resources during the absence but you can re\-enable the user later\.

For more information about disabling credentials, see [Managing Access Keys for IAM Users](id_credentials_access-keys.md)\. For information about the permissions that you need in order to delete a user, see [Permissions Required to Access IAM Resources](access_permissions-required.md)\. 

**Topics**
+ [Deleting an IAM User \(AWS Management Console\)](#id_users_deleting_console)
+ [Deleting an IAM User \(AWS CLI and Tools for Windows PowerShell\)](#id_users_deleting_cli)

### Deleting an IAM User \(AWS Management Console\)<a name="id_users_deleting_console"></a>

When you use the AWS Management Console to delete an IAM user, IAM automatically deletes the following information for you: 
+ The user
+ Any group memberships—that is, the user is removed from any IAM groups that the user was a member of 
+ Any password associated with the user
+ Any access keys belonging to the user
+ All inline policies embedded in the user \(policies that are applied to a user via group permissions are not affected\) 
**Note**  
Any managed policies attached to the user are detached from the user when the user is deleted\. Managed policies are not deleted when you delete a user\. 
+ Any associated MFA device

**To use the AWS Management Console to delete an IAM user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**, and then select the check box next to the user name that you want to delete, not the name or row itself\. 

1. At the top of the page, choose **Delete user**\. 

1. In the confirmation dialog box, wait for the service last accessed data to load before you review the data\. The dialog box shows when each of the selected users last accessed an AWS service\. If you attempt to delete a user that has been active within the last 30 days, you must select an additional check box to confirm that you want to delete the active user\. If you want to proceed, choose **Yes, Delete**\. 

### Deleting an IAM User \(AWS CLI and Tools for Windows PowerShell\)<a name="id_users_deleting_cli"></a>

Unlike the AWS Management Console, when you delete a user with the AWS CLI or Tools for Windows PowerShell you have to delete the items attached to the user manually\. This procedure illustrates the process\. For a complete PowerShell code snippet, see the example in [Remove\-IAMUser](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccessKey.html&tocid=Remove-IAMAccessKey)\.

**To use the AWS CLI to delete a user from your account**

1. Delete the user's keys and certificates\. This helps ensure that the user can't access your AWS account's resources anymore\. Note that when you delete a security credential, it's gone forever and can't be retrieved\. 

   [aws iam delete\-access\-key](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html) and [aws iam delete\-signing\-certificate](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-signing-certificate.html) 

1. Delete the user's password, if the user has one\.

   [aws iam delete\-login\-profile](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-login-profile.html)

1. Deactivate the user's MFA device, if the user has one\.

   [aws iam deactivate\-mfa\-device](http://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html) 

1. Detach any policies that are attached to the user\. 

   [aws iam list\-attached\-user\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-user-policies.html) \(to list the policies attached to the user\) and [http://docs.aws.amazon.com/cli/latest/reference/iam/detach-user-policy.html](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-user-policy.html) \(to detach the policies\) 

1. Get a list of any groups the user was in, and remove the user from those groups\. 

   [aws iam list\-groups\-for\-user](http://docs.aws.amazon.com/cli/latest/reference/iam/list-groups-for-user.html) and [aws iam remove\-user\-from\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html) 

1. Delete the user\.

   [aws iam delete\-user](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-user.html) 

**To use the Tools for Windows PowerShell to delete a user from your account**

1. Delete the user's keys and certificates\. This helps ensure that the user can't access your AWS account's resources anymore\. Note that when you delete a security credential, it's gone forever and can't be retrieved\.

   [Remove\-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccessKey.html&tocid=Remove-IAMAccessKey) and [Remove\-IAMSigningCertificate](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMSigningCertificate.html&tocid=Remove-IAMSigningCertificate)

1. Delete the user's password, if the user has one\.

   [Remove\-IAMLoginProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMLoginProfile.html&tocid=Remove-IAMLoginProfile)

1. Deactivate the user's MFA device, if the user has one\.

   [Disable\-IAMMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Disable-IAMMFADevice.html&tocid=Disable-IAMMFADevice)

1. Detach any policies that are attached to the user\. 

   [Get\-IAMAttachedUserPolicies](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAttachedUserPolicies.html&tocid=Get-IAMAttachedUserPolicies) \(to list the policies attached to the user\) and [Remove\-IAMUserPolicy](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMUserPolicy.html&tocid=Remove-IAMUserPolicy) \(to detach the policies\)\.

1. Get a list of any groups the user was in, and remove the user from those groups\. 

   [Get\-IAMGroupForUser](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMGroupForUser.html&tocid=Remove-IAMGroupForUser) and [Remove\-IAMUserFromGroup](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMUserFromGroup.html&tocid=Remove-IAMUserFromGroup)\.

1. Delete the user\.

   [Remove\-IAMUser](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMUser.html&tocid=Remove-IAMUser)