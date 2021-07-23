# Deleting an IAM user group<a name="id_groups_manage_delete"></a>

When you delete a user group in the AWS Management Console, the console automatically removes all group members, detaches all attached managed policies, and deletes all inline policies\. However, because IAM does not automatically delete policies that refer to the user group as a resource, you must be careful when you delete a user group\. Before you delete your user group, you must manually check all of your policies to find any policies that mention the group by name\. For example, if John is the manager of the testing part of the organization\. John has a policy attached to his IAM user entity that lets him add and remove users from the Test user group\. If an administrator deletes the group, the administrator must also delete the policy attached to John\. 

**To find policies that refer to a user group as a resource**

1. From the navigation pane of the IAM console, choose **Policies**\.

1. Sort by the **Type** column to find your **Customer managed** custom policies\.

1. Choose the policy name of the policy to delete\.

1. Choose the **Permissions** tab, and then choose **Policy summary**\.

1. Choose **IAM** from the list of services, if it exists\.

1. Look for the name of your user group in the **Resource** column\.

1. Choose **Delete policy** to delete the policy\.

In contrast, when you use the AWS CLI, Tools for Windows PowerShell, or AWS API to delete a user group, you must first remove the users in the group\. Then delete any inline policies embedded in the user group\. Next, detach any managed policies that are attached to the group\. Only then can you delete the user group itself\.

## Deleting an IAM user group \(console\)<a name="id_groups_manage_delete_console"></a>

You can delete an IAM user group from the AWS Management Console\.

**To delete an IAM user group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **User groups**\. 

1. In the list of user groups, select the check box next to the names of the user groups to delete\. You can use the search box to filter the list of user groups by type, permissions, and user group name\.

1. Choose **Delete**\.

1. In the confirmation box, if you want to delete a single user group, type the user group name and choose **Delete**\. If you want to delete multiple user groups, type the number of user groups to delete followed by **user groups** and choose **Delete**\. For example, if you delete three user groups, type **3 user groups**\.

## Deleting an IAM user group \(AWS CLI\)<a name="id_groups_manage_delete_cli"></a>

You can delete an IAM user group from the AWS CLI\.

**To delete an IAM user group \(AWS CLI\)**

1. Remove all users from the user group\.
   + [aws iam get\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html) \(to get the list of users in the user group\), and [aws iam remove\-user\-from\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html) \(to remove a user from the user group\) 

1. Delete all inline policies embedded in the user group\.
   + [aws iam list\-group\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-group-policies.html) \(to get a list of the user group's inline policies\), and [aws iam delete\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-group-policy.html) \(to delete the user group's inline policies\) 

1. Detach all managed policies attached to the user group\.
   + [aws iam list\-attached\-group\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html) \(to get a list of the managed policies attached to the user group\), and [aws iam detach\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/detach-group-policy.html) \(to detach a managed policy from the user group\) 

1. Delete the user group\.
   + [aws iam delete\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-group.html)

## Deleting an IAM user group \(AWS API\)<a name="id_groups_manage_delete_api"></a>

You can use the AWS API to delete an IAM user group\.

**To delete an IAM user group \(AWS API\)**

1. Remove all users from the user group\.
   + [GetGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html) \(to get the list of users in the user group\) and [RemoveUserFromGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html) \(to remove a user from the user group\) 

1. Delete all inline policies embedded in the user group\.
   + [ListGroupPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupPolicies.html) \(to get a list of the user group's inline policies\) and [DeleteGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteGroupPolicy.html) \(to delete the user group's inline policies\) 

1. Detach all managed policies attached to the user group\.
   + [ListAttachedGroupPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedGroupPolicies.html) \(to get a list of the managed policies attached to the user group\) and [DetachGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachGroupPolicy.html) \(to detach a managed policy from the user group\)

1. Delete the user group\.
   +  [DeleteGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteGroup.html) 