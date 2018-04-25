# Changing Permissions for an IAM User<a name="id_users_change-permissions"></a>

You can change the permissions for an IAM user in your AWS account by changing its group memberships or by attaching and detaching managed policies\. A user gets its permissions through one of the following methods:

**Group membership**  
+ Add or remove a user from a group\.
+ Add, remove, or edit a managed policy attached to the group\. This policy can be an [AWS managed policy](access_policies_managed-vs-inline.md#aws-managed-policies) or a [customer managed policy](access_policies_managed-vs-inline.md#customer-managed-policies) that you create\.
+ Add, remove, or edit a group's [inline policies](access_policies_managed-vs-inline.md#inline-policies)\.

**Direct policy attachment**  
+ Add, remove, or edit a managed policy attached directly to a user\. This policy can be an [AWS managed policy](access_policies_managed-vs-inline.md#aws-managed-policies) or a [customer managed policy](access_policies_managed-vs-inline.md#customer-managed-policies) that you create\.
+ Add, remove, or edit a user's [inline policies](access_policies_managed-vs-inline.md#inline-policies)\.

For information about the permissions that you need in order to modify the permissions for a user, see [Permissions Required to Access IAM Resources](access_permissions-required.md)\.

## Adding Permissions to a New or Existing User \(Console\)<a name="w3ab1c19c19c25b9"></a>

You can change permissions associated with a user through one of three techniques:
+ [**Add user to group**](#by-add-users-to-group) – Make the user a member of a group that already has policies attached\. Every member of the group receives the permissions granted by the group's policies\.
+ [**Copy permissions from existing user**](#by-copying-user) – Copy all group memberships and attached managed policies as well as all inline policies embedded in the source user\.
+ [**Attach policies directly to user**](#by-direct-attach-policy) – Attach a managed policy directly to the user\. As a [best practice](best-practices.md#use-groups-for-permissions), we recommend that you instead attach your policies to a group and then make users members of the appropriate groups\.

### Adding Permissions by Adding the User to a Group<a name="w3ab1c19c19c25b9b6"></a><a name="by-add-users-to-group"></a>

**To add permissions to a user by adding the user to a group**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Review the current group memberships for users in the **Groups** column of the console\. If necessary, add the column to the users table by completing the following steps:

   1. Above the table on the far right, choose the settings symbol \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In the **Manage Columns** dialog box, select the **Groups** column\. Optionally, you can also clear the check box for any column headings that you do not want to appear in the users table\.

   1. Choose **Close** to return to the list of users\.

   The **Groups** column tells you to which groups the user belongs\. The field includes the group names for up to two groups\. If the user is a member of three or more groups, the first two groups are shown \(ordered\.alphabetically\), and the number of additional group memberships is included\. For example, if the user belongs to Group A, Group B, Group C, and Group D, then the field contains the value **Group A, Group B \+ 2 more**\. To see the total number of groups to which the user belongs, you can add the **Group count** column to the users table\.

1. Choose the name of the user whose permissions you want to modify\. 

1. Choose the **Permissions** tab, and then choose **Add permissions**\. Under **Grant permissions** choose **Add user to group**\. 

1. Select the check box for each group that you want the user to join\. The list shows each group's name and the policies that the user receives if made a member of that group\. The permissions in each selected group apply to the user as soon as you complete the process\.

1. \(Optional\) In addition to selecting from existing groups, you can choose **Create group** to define a new group:

   1. For **Group name**, type a name for your new group\.
**Note**  
Group names can be a combination of up to 128 letters, digits, and these characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at sign \(@\), and hyphen \(\-\)\. Names must be unique within an account\. They are not distinguished by case\. For example, you cannot create two groups named *TESTGROUP* and *testgroup*\. For more information about limitations on IAM entities, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\. 

   1. Select one or more check boxes for the managed policies that you want to attach to the group\. You can also create a new managed policy by choosing **Create policy**\. If you do, return to this browser tab or window when the new policy is done; choose **Refresh**; and then choose the new policy to attach it to your group\. For more information, see [Creating IAM Policies](access_policies_create.md)\.

   1. Choose **Create group**\.

   1. Back in the list of groups, select the check box for your new group\.

1. Choose **Next: Review** to see the list of group memberships to be added to the user\. Then choose **Add permissions**\.

The new permissions affect the user immediately\.

### Adding Permissions by Copying from Another User<a name="w3ab1c19c19c25b9b8"></a><a name="by-copying-user"></a>

**To add permissions to a user by copying permissions from another user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Users** in the navigation pane, choose the name of the user whose permissions you want to modify, and then choose the **Permissions** tab\.

1. Choose **Add permissions**, and then under **Grant permissions** choose **Copy permissions from existing user**\. The list displays available users along with their group memberships and attached policies\. If the full list of groups or policies don't fit on one line, you can choose the link for **and *n* more**\. Doing that opens a new browser tab and see the full list of policies \(**Permissions** tab\) and groups \(**Groups** tab\)\.

1. Select the radio button next to the user whose permissions you want to copy\. 

1. Choose **Next: Review** to see the list of changes that are to be made to the user\. Then choose **Add permissions**\.

The new permissions affect the user immediately\.

### Adding Permissions by Attaching Policies Directly to the User<a name="w3ab1c19c19c25b9c10"></a><a name="by-direct-attach-policy"></a>

**To add permissions to a user by directly attaching managed policies**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Users** in the navigation pane, choose the name of the user whose permissions you want to modify, and then choose the **Permissions** tab\.

1. Choose **Add permissions**, and then under **Grant permissions**, choose **Attach existing policies directly to user**\. 

1. Select one or more check boxes for the managed policies that you want to attach to the group\. You can also create a new managed policy by choosing **Create policy**\. If you do, return to this browser tab or window when the new policy is done\. Choose **Refresh**; and then select the check box for the new policy to attach it to your user\. For more information, see [Creating IAM Policies](access_policies_create.md)\.

1. Choose **Next: Review** to see the list of policies that are to be attached to the user\. Then choose **Add permissions**\.

The new permissions affect the user immediately\.

## Removing Permissions from an Existing User \(Console\)<a name="w3ab1c19c19c25c11"></a>

**To revoke permissions for IAM users**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**, choose the name of the user whose permissions you want to modify, and then choose the **Permissions** tab\.

   The **Permissions** tab displays each policy that applies to the user, and how the user gets that policy\.

1. If you want to revoke permissions by removing an existing policy, view the **Policy type** to understand how the user is getting that policy before choosing **X** to remove the policy:
   + If the policy applies because of group membership, then choosing **X** removes the user from the group\. Because you might have multiple policies attached from a single group, if you remove a user from a group, the user loses access to *all* policies that it received through that group membership\.\.
   + If the policy is a managed policy attached directly to the user, then choosing **X** detaches the policy from the user\. This does not affect the policy itself or any other entity that the policy might be attached to\.
   + If the policy is an inline embedded policy, then choosing **X** removes the policy from IAM\. Inline policies that are attached directly to a user exist only on that user\.

## Adding and Removing Permissions from a User \(AWS API, AWS CLI, Tools for Windows PowerShell\)<a name="w3ab1c19c19c25c13"></a>

To add or remove permissions programmatically, you must add or remove the group memberships, attach or detach the managed policies, or add or delete the inline policies\. For more information, see the following topics:
+ [Adding and Removing Users in an IAM Group](id_groups_manage_add-remove-users.md)
+ [Attaching or Detaching IAM Policies \(AWS CLI or AWS API\)](access_policies_manage-attach-detach.md#attach-detach-managed-policy-cli-api)
+ [Attaching and Detaching IAM Policies](access_policies_manage-attach-detach.md)