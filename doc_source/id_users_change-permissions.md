# Changing permissions for an IAM user<a name="id_users_change-permissions"></a>

You can change the permissions for an IAM user in your AWS account by changing its group memberships, by copying permissions from an existing user, by attaching policies directly to a user, or by setting a [permissions boundary](access_policies_boundaries.md)\. A permissions boundary controls the maximum permissions that a user can have\. Permissions boundaries are an advanced AWS feature\.

For information about the permissions that you need in order to modify the permissions for a user, see [Permissions required to access IAM resources](access_permissions-required.md)\.

**Topics**
+ [View user access](#users-modify_prerequisites)
+ [Adding permissions to a user \(console\)](#users_change_permissions-add-console)
+ [Changing permissions for a user \(console\)](#users_change_permissions-change-console)
+ [Removing a permissions policy from a user \(console\)](#users_change_permissions-remove-policy-console)
+ [Removing the permissions boundary from a user \(console\)](#users_change_permissions-remove-boundary-console)
+ [Adding and removing a user's permissions \(AWS CLI or AWS API\)](#users_change_permissions-add-programmatic)

## View user access<a name="users-modify_prerequisites"></a>

Before you change the permissions for a user, you should review its recent service\-level activity\. This is important because you don't want to remove access from a principal \(person or application\) who is using it\. For more information about viewing last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

## Adding permissions to a user \(console\)<a name="users_change_permissions-add-console"></a>

IAM offers three ways to add permissions policies to a user:
+ **Add user to group** – Make the user a member of a group\. The policies from the group are attached to the user\.
+ **Copy permissions from existing user** – Copy all group memberships, attached managed policies, inline policies, and any existing permissions boundaries from the source user\.
+ **Attach policies directly to user** – Attach a managed policy directly to the user\. As a [best practice](best-practices.md#use-groups-for-permissions), we recommend that you instead attach your policies to a group and then make users members of the appropriate groups\.

**Important**  
If the user has a permissions boundary, then you cannot add more permissions to a user than are allowed by the permissions boundary\.

### Adding permissions by adding the user to a group<a name="users_change_permissions-add-group-console"></a>

Adding a user to a group affects the user immediately\.<a name="by-add-users-to-group"></a>

**To add permissions to a user by adding the user to a group**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Review the current group memberships for users in the **Groups** column of the console\. If necessary, add the column to the users table by completing the following steps:

   1. Above the table on the far right, choose the settings symbol \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In the **Manage Columns** dialog box, select the **Groups** column\. Optionally, you can also clear the check box for any column headings that you do not want to appear in the users table\.

   1. Choose **Close** to return to the list of users\.

   The **Groups** column tells you to which groups the user belongs\. The column includes the group names for up to two groups\. If the user is a member of three or more groups, the first two groups are shown \(ordered alphabetically\), and the number of additional group memberships is included\. For example, if the user belongs to Group A, Group B, Group C, and Group D, then the field contains the value **Group A, Group B \+ 2 more**\. To see the total number of groups to which the user belongs, you can add the **Group count** column to the users table\.

1. Choose the name of the user whose permissions you want to modify\. 

1. Choose the **Permissions** tab, and then choose **Add permissions**\. Choose **Add user to group**\. 

1. Select the check box for each group that you want the user to join\. The list shows each group's name and the policies that the user receives if made a member of that group\.

1. \(Optional\) In addition to selecting from existing groups, you can choose **Create group** to define a new group:

   1. In the new tab, for **Group name**, type a name for your new group\.
**Note**  
The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\. Group names can be a combination of up to 128 letters, digits, and these characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at sign \(@\), and hyphen \(\-\)\. Names must be unique within an account\. They are not distinguished by case\. For example, you cannot create two groups named *TESTGROUP* and *testgroup*\.

   1. Select one or more check boxes for the managed policies that you want to attach to the group\. You can also create a new managed policy by choosing **Create policy**\. If you do, return to this browser tab or window when the new policy is done; choose **Refresh**; and then choose the new policy to attach it to your group\. For more information, see [Creating IAM policies](access_policies_create.md)\.

   1. Choose **Create group**\.

   1. Return to the original tab, refresh your list of groups\. Then select the check box for your new group\.

1. Choose **Next: Review** to see the list of group memberships to be added to the user\. Then choose **Add permissions**\.

### Adding permissions by copying from another user<a name="users_change_permissions-add-copy-console"></a>

Copying permissions affects the user immediately\.<a name="by-copying-user"></a>

**To add permissions to a user by copying permissions from another user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Users** in the navigation pane, choose the name of the user whose permissions you want to modify, and then choose the **Permissions** tab\.

1. Choose **Add permissions**, and then choose **Copy permissions from existing user**\. The list displays available users along with their group memberships and attached policies\. If the full list of groups or policies don't fit on one line, you can choose the link for **and *n* more**\. Doing that opens a new browser tab and see the full list of policies \(**Permissions** tab\) and groups \(**Groups** tab\)\.

1. Select the radio button next to the user whose permissions you want to copy\. 

1. Choose **Next: Review** to see the list of changes that are to be made to the user\. Then choose **Add permissions**\.

### Adding permissions by attaching policies directly to the user<a name="users_change_permissions-add-directly-console"></a>

Attaching policies affects the user immediately\.<a name="by-direct-attach-policy"></a>

**To add permissions to a user by directly attaching managed policies**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Users** in the navigation pane, choose the name of the user whose permissions you want to modify, and then choose the **Permissions** tab\.

1. Choose **Add permissions**, and then choose **Attach existing policies directly to user**\. 

1. Select one or more check boxes for the managed policies that you want to attach to the user\. You can also create a new managed policy by choosing **Create policy**\. If you do, return to this browser tab or window when the new policy is done\. Choose **Refresh**; and then select the check box for the new policy to attach it to your user\. For more information, see [Creating IAM policies](access_policies_create.md)\.

1. Choose **Next: Review** to see the list of policies that are to be attached to the user\. Then choose **Add permissions**\.

### Setting the permissions boundary for a user<a name="users_change_permissions-set-boundary-console"></a>

Setting a permissions boundary affects the user immediately\.

**To set the permissions boundary for a user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user whose permissions boundary you want to change\. 

1. Choose the **Permissions** tab\. If necessary, open the **Permissions boundary** section and then choose **Set boundary**\.

1. Select the policy that you want to use for the permissions boundary\.

1. Choose **Set boundary**\.

## Changing permissions for a user \(console\)<a name="users_change_permissions-change-console"></a>

IAM allows you to change the permissions that are associated with a user in the following ways:
+ **Edit a permissions policy** – Edit a user's inline policy, the inline policy of the user's group, or edit a managed policy that is attached to the user directly or from a group\. If the user has a permissions boundary, then you cannot provide more permissions than are allowed by the policy that was used as the user's permissions boundary\.
+ **Changing the permissions boundary** – Change the policy that is used as the permissions boundary for the user\. This can expand or restrict the maximum permissions that a user can have\. 

### Editing a permissions policy attached to a user<a name="users_change_permissions-edit-policy-console"></a>

Changing permissions affects the user immediately\.

**To edit a user's attached managed policies**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user whose permissions policy you want to change\. 

1. Choose the **Permissions** tab\. If necessary, open the **Permissions policies** section\.

1. Choose the name of the policy that you want to edit to view details about the policy\. Choose the **Used as** tab to view other entities that might be affected if you edit the policy\. 

1. Choose the **Permissions tab** and review the permissions granted by the policy\. Then choose **Edit policy**\. 

1. Edit the policy using the **Visual editor** tab or the **JSON** tab\. For more information, see [Editing IAM policies](access_policies_manage-edit.md)\.

1. Choose **Review policy**, review the policy summary, and then choose **Save changes**\.

### Changing the permissions boundary for a user<a name="users_change_permissions-change-boundary-console"></a>

Changing a permissions boundary affects the user immediately\.

**To change the policy used to set the permissions boundary for a user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user whose permissions boundary you want to change\. 

1. Choose the **Permissions** tab\. If necessary, open the **Permissions boundary** section and then choose **Change boundary**\.

1. Select the policy that you want to use for the permissions boundary\.

1. Choose **Change boundary**\.

## Removing a permissions policy from a user \(console\)<a name="users_change_permissions-remove-policy-console"></a>

Removing a policy affects the user immediately\.

**To revoke permissions for IAM users**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user whose permissions boundary you want to remove\. 

1. Choose the **Permissions** tab\. 

1. If you want to revoke permissions by removing an existing policy, view the **Policy type** to understand how the user is getting that policy before choosing **X** to remove the policy:
   + If the policy applies because of group membership, then choosing **X** removes the user from the group\. Remember that you might have multiple policies attached to a single group\. If you remove a user from a group, the user loses access to *all* policies that it received through that group membership\.
   + If the policy is a managed policy attached directly to the user, then choosing **X** detaches the policy from the user\. This does not affect the policy itself or any other entity that the policy might be attached to\.
   + If the policy is an inline embedded policy, then choosing **X** removes the policy from IAM\. Inline policies that are attached directly to a user exist only on that user\.

## Removing the permissions boundary from a user \(console\)<a name="users_change_permissions-remove-boundary-console"></a>

Removing a permissions boundary affects the user immediately\.

**To remove the permissions boundary from a user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user whose permissions boundary you want to remove\. 

1. Choose the **Permissions** tab\. If necessary, open the **Permissions boundary** section and then choose **Remove boundary**\.

1. Choose **Remove** to confirm that you want to remove the permissions boundary\.

## Adding and removing a user's permissions \(AWS CLI or AWS API\)<a name="users_change_permissions-add-programmatic"></a>

To add or remove permissions programmatically, you must add or remove the group memberships, attach or detach the managed policies, or add or delete the inline policies\. For more information, see the following topics:
+ [Adding and removing users in an IAM group](id_groups_manage_add-remove-users.md)
+ [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md)