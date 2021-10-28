# Adding and removing users in an IAM user group<a name="id_groups_manage_add-remove-users"></a>

Use user groups to apply the same permissions policies across multiple users at once\. You can then add users to or remove users from an IAM user group\. This is useful as people enter and leave your organization\.

## View policy access<a name="groups-remove_prerequisites"></a>

Before you change the permissions for a policy, you should review its recent service\-level activity\. This is important because you don't want to remove access from a principal \(person or application\) who is using it\. For more information about viewing last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

## Add or remove a user in a user group \(console\)<a name="groups-add-remove-console"></a>

You can use the AWS Management Console to add or remove a user from a user group\.

**To add a user to an IAM user group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **User groups** and then choose the name of the group\.

1. Choose the **Users** tab and then choose **Add users**\. Select the check box next to the users you want to add\.

1. Choose **Add users**\.

**To remove a user from an IAM group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **User groups** and then choose the name of the group\.

1. Choose the **Users** tab\. Select the check box next to the users you want to remove and then choose **Remove users**\.

## Add or remove a user in a user group \(AWS CLI\)<a name="groups-add-remove-cli"></a>

You can use the AWS CLI to add or remove a user from a user group\.

**To add a user to an IAM user group \(AWS CLI\)**
+ Use the following command:
  + [aws iam add\-user\-to\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/add-user-to-group.html)

**To remove a user from an IAM user group \(AWS CLI\)**
+ Use the following command:
  + [aws iam remove\-user\-from\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html) 

## Add or remove a user in a user group \(AWS API\)<a name="groups-add-remove-api"></a>

You can use the AWS API to add or remove a user in a user group\.

**To add a user to an IAM group \(AWS API\)**
+ Complete the following operation:
  + [AddUserToGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_AddUserToGroup.html) 

**To remove a user from an IAM user group \(AWS API\)**
+ Complete the following operation:
  + [RemoveUserFromGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html) 