# Managing IAM users<a name="id_users_manage"></a>

**Note**  
As a [best practice](best-practices.md), we recommend that you require human users to use federation with an identity provider to access AWS using temporary credentials\. If you follow the best practices, you are not managing IAM users and groups\. Instead, your users and groups are managed outside of AWS and are able to access AWS resources as a *federated identity*\. A federated identity is a user from your enterprise user directory, a web identity provider, the AWS Directory Service, the Identity Center directory, or any user that accesses AWS services by using credentials provided through an identity source\. Federated identities use the groups defined by their identity provider\. If you are using AWS IAM Identity Center \(successor to AWS Single Sign\-On\), see [Manage identities in IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/manage-your-identity-source-sso.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide* for information about creating users and groups in IAM Identity Center\.

Amazon Web Services offers multiple tools for managing the IAM users in your AWS account\. You can list the IAM users in your account or in a user group, or list all user groups that a user is a member of\. You can rename or change the path of an IAM user\. If you are moving to using federated identities instead of IAM users, you can delete an IAM user from your AWS account, or deactivate the user\.

For more information about adding, changing, or removing managed policies for an IAM user, see [Changing permissions for an IAM user](id_users_change-permissions.md)\. For information about managing inline policies for IAM users, see [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md), [Editing IAM policies](access_policies_manage-edit.md), and [Deleting IAM policies](access_policies_manage-delete.md)\. As a best practice, use managed policies instead of inline policies\. *AWS managed policies* grant permissions for many common use cases\. Keep in mind that AWS managed policies might not grant least\-privilege permissions for your specific use cases because they are available for use by all AWS customers\. As a result, we recommend that you reduce permissions further by defining [customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#customer-managed-policies) that are specific to your use cases\. For more information, see [AWS managed policies](access_policies_managed-vs-inline.md#aws-managed-policies)\. For more information about AWS managed policies that are designed for specific job functions, see [AWS managed policies for job functions](access_policies_job-functions.md)\.

To learn about validating IAM policies, see [Validating IAM policies](access_policies_policy-validator.md)\.

**Tip**  
[IAM Access Analyzer](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html) can analyze the services and actions that your IAM roles use, and then generate a fine\-grained policy that you can use\. After you test each generated policy, you can deploy the policy to your production environment\. This ensures that you grant only the required permissions to your workloads\. For more information about policy generation, see [IAM Access Analyzer policy generation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-generation.html)\.

For information about managing IAM user passwords, see [Managing passwords for IAM users](id_credentials_passwords_admin-change-user.md),

**Topics**
+ [View user access](#users-manage_prerequisites)
+ [Listing IAM users](#id_users_manage_list)
+ [Renaming an IAM user](#id_users_renaming)
+ [Deleting an IAM user](#id_users_deleting)
+ [Deactivating an IAM user](#id_users_deactivating)

## View user access<a name="users-manage_prerequisites"></a>

Before you delete a user, you should review its recent service\-level activity\. This is important because you don't want to remove access from a principal \(person or application\) who is using it\. For more information about viewing last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

## Listing IAM users<a name="id_users_manage_list"></a>

You can list the IAM users in your AWS account or in a specific IAM user group, and list all the user groups that a user is in\. For information about the permissions that you need in order to list users, see [Permissions required to access IAM resources](access_permissions-required.md)\. 

### To list all the users in the account<a name="id_users_manage_list-users"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Users**\. The console displays the users in your AWS account\. 
+ AWS CLI: [aws iam list\-users](https://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html)
+ AWS API: [ListUsers](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html) 

### To list the users in a specific user group<a name="id_users_manage_list-users-group"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **User groups**, choose the name of the user group, and then choose the **Users** tab\. 
+ AWS CLI: [aws iam get\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html)
+ AWS API: [GetGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html)

### To list all the user groups that a user is in<a name="id_users_manage_list-groups-users"></a>
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Users**, choose the user name, and then choose the **Groups** tab\. 
+ AWS CLI: [aws iam list\-groups\-for\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups-for-user.html)
+ AWS API: [ListGroupsForUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html)

## Renaming an IAM user<a name="id_users_renaming"></a>

To change a user's name or path, you must use the AWS CLI, Tools for Windows PowerShell, or AWS API\. There is no option in the console to rename a user\. For information about the permissions that you need in order to rename a user, see [Permissions required to access IAM resources](access_permissions-required.md)\. 

When you change a user's name or path, the following happens: 
+ Any policies attached to the user stay with the user under the new name\.
+ The user stays in the same user groups under the new name\.
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

You might delete an IAM user from your AWS account if that user quits your company\. If the user is away temporarily, you can deactivate the user's access instead of deleting them from the account as described in [Deactivating an IAM user](#id_users_deactivating)\.

**Topics**
+ [Deleting an IAM user \(console\)](#id_users_deleting_console)
+ [Deleting an IAM user \(AWS CLI\)](#id_users_deleting_cli)

### Deleting an IAM user \(console\)<a name="id_users_deleting_console"></a>

When you use the AWS Management Console to delete an IAM user, IAM automatically deletes the following information for you: 
+ The user
+ Any user group memberships—that is, the user is removed from any IAM user groups that the user was a member of
+ Any password associated with the user
+ Any access keys belonging to the user
+ All inline policies embedded in the user \(policies that are applied to a user via user group permissions are not affected\) 
**Note**  
IAM removes any managed policies attached to the user when you delete the user, but does not delete managed policies\. 
+ Any associated MFA device

**To delete an IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**, and then select the check box next to the user name that you want to delete\. 

1. At the top of the page, choose **Delete**\.

1. In the confirmation dialog box, enter the username in the text input field to confirm the deletion of the user\. Choose ** Delete**\. 

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

1. Remove the user from any user groups\. 

   `[aws iam list\-groups\-for\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups-for-user.html)` \(to list the user groups to which the user belongs\) and `[aws iam remove\-user\-from\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html)` 

1. Delete the user\.

   `[aws iam delete\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-user.html)` 

## Deactivating an IAM user<a name="id_users_deactivating"></a>

You might need to deactivate an IAM user while they are temporarily away from your company\. You can leave their IAM user credentials in place and still block their AWS access\.

To deactivate a user, create and attach a policy to deny the user access to AWS\. You can restore the user's access later\.

Here are two examples of deny policies that you can attach to a user to deny their access\.

The following policy does not include a time limit\. You must remove the policy to restore the user's access\.

```
{
  "Version": "2012-10-17",
  "Statement": [ 
      {
        "Effect": "Deny",
        "Action": "*",
        "Resource": "*"
      } 
   ]
}
```

The following policy includes a condition that starts the policy on December 24, 2024 at 11:59 PM \(UTC\) and ends it on February 28, 2025 at 11:59 PM \(UTC\)\.

```
{
  "Version": "2012-10-17",
  "Statement": [
      {
        "Effect": "Deny",
        "Action": "*",
        "Resource": "*",
        "Condition": {
          "DateGreaterThan": {"aws:CurrentTime": "2024-12-24T23:59:59Z"},
          "DateLessThan": {"aws:CurrentTime": "2025-02-28T23:59:59Z"}
          }
       }
   ]
}
```