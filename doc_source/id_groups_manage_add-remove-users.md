# Adding and removing users in an IAM group<a name="id_groups_manage_add-remove-users"></a>

Use groups to apply the same permissions policies across multiple users at once\. You can then add users to or remove users from an IAM group\. This is useful as people enter and leave your organization\.

## View policy access<a name="groups-remove_prerequisites"></a>

Before you change the permissions for a policy, you should review its recent service\-level activity\. This is important because you don't want to remove access from a principal \(person or application\) who is using it\. For more information about viewing last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

## Add or remove a user in a group \(console\)<a name="groups-add-remove-console"></a>

You can use the AWS Management Console to add or remove a user from a group\.

**To add a user to an IAM group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups** and then choose the name of the group\.

1. Choose the **Users** tab and then choose **Add Users to Group**\. Select the check box next to the users you want to add\.

1. Choose **Add Users**\.

**To remove a user from an IAM group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups** and then choose the name of the group\.

1. Choose the **Users** tab and then choose **Remove Users from Group**\. Select the check box next to the users you want to remove\.

1. Choose **Remove Users**\.

## Add or remove a user in a group \(AWS CLI\)<a name="groups-add-remove-cli"></a>

You can use the AWS CLI to add or remove a user from a group\.

**To add a user to an IAM group \(AWS CLI\)**
+ Use the following command:
  + [aws iam add\-user\-to\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/add-user-to-group.html)

**To remove a user from an IAM group \(AWS CLI\)**
+ Use the following command:
  + [aws iam remove\-user\-from\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html) 

## Add or remove a user in a group \(AWS API\)<a name="groups-add-remove-api"></a>

You can use the AWS API to add or remove a user in a group\.

**To add a user to an IAM group \(AWS API\)**
+ Complete the following operation:
  + [AddUserToGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_AddUserToGroup.html) 

**To remove a user from an IAM group \(AWS API\)**
+ Complete the following operation:
  + [RemoveUserFromGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html) 