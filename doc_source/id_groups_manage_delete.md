# Deleting an IAM group<a name="id_groups_manage_delete"></a>

When you delete a group in the AWS Management Console, the console automatically removes all group members, detaches all attached managed policies, and deletes all inline policies\. However, because IAM does not automatically delete policies that refer to the group as a resource, you must be careful when you delete a group\. Before you delete your group, you must manually check all of your policies to find any policies where that group is mentioned by name\. For example, let's say John is the manager of the testing part of the organization\. John has a policy attached to his IAM user entity that lets him add and remove users from the Test group\. If an administrator deletes the group, the administrator must also delete the policy attached to John\. 

**To find policies that refer to a group as a resource**

1. From the navigation pane of the IAM console, choose **Policies**\.

1. From the **Policy type** drop\-down list, choose **Customer managed** to filter the policies to show only your custom policies\.

1. Choose the arrow next to each policy name to expand the policy summary\.

1. Choose **IAM** from the list of services, if it exists\.

1. Look for the name of your group in the **Resource** column\.

1. Choose **Delete policy** to delete the policy\.

In contrast, when you use the AWS CLI, Tools for Windows PowerShell, or AWS API to delete a group, you must first remove the users in the group\. Then delete any inline policies embedded in the group\. Next, detach any managed policies that are attached to the group\. Only then can you delete the group itself\.

## Deleting an IAM group \(console\)<a name="id_groups_manage_delete_console"></a>

You can delete an IAM group from the AWS Management Console\.

**To delete an IAM group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups**\. 

1. In the list of groups, select the check box next to the name of the group to delete\. You can use the **Filter** menu and the search box to filter the list of policies\. 

1. Click **Group Actions**, then click **Delete Group**\.

1. In the confirmation box, click **Yes, Delete**\.

## Deleting an IAM group \(AWS CLI\)<a name="id_groups_manage_delete_cli"></a>

You can delete an IAM group from the AWS CLI\.

**To delete an IAM group \(AWS CLI\)**

1. Remove all users from the group\.
   + [aws iam get\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html) \(to get the list of users in the group\), and [aws iam remove\-user\-from\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html) \(to remove a user from the group\) 

1. Delete all inline policies embedded in the group\.
   + [aws iam list\-group\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-group-policies.html) \(to get a list of the group's inline policies\), and [aws iam delete\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-group-policy.html) \(to delete the group's inline policies\) 

1. Detach all managed policies attached to the group\.
   + [aws iam list\-attached\-group\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html) \(to get a list of the managed policies attached to the group\), and [aws iam detach\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/detach-group-policy.html) \(to detach a managed policy from the group\) 

1. Delete the group\.
   + [aws iam delete\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-group.html)

## Deleting an IAM group \(AWS API\)<a name="id_groups_manage_delete_api"></a>

You can use the AWS API to delete an IAM group\.

**To delete an IAM group \(AWS API\)**

1. Remove all users from the group\.
   + [GetGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html) \(to get the list of users in the group\) and [RemoveUserFromGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html) \(to remove a user from the group\) 

1. Delete all inline policies embedded in the group\.
   + [ListGroupPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupPolicies.html) \(to get a list of the group's inline policies\) and [DeleteGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteGroupPolicy.html) \(to delete the group's inline policies\) 

1. Detach all managed policies attached to the group\.
   + [ListAttachedGroupPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedGroupPolicies.html) \(to get a list of the managed policies attached to the group\) and [DetachGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachGroupPolicy.html) \(to detach a managed policy from the group\)

1. Delete the group\.
   +  [DeleteGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteGroup.html) 