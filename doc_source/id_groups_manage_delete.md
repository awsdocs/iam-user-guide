# Deleting an IAM Group<a name="id_groups_manage_delete"></a>

When you delete a group in the AWS Management Console, the console automatically removes all group members, detaches all attached managed policies, and deletes all inline policies\. However, because IAM does not automatically delete policies that refer to the group as a resource, you must be careful when you delete a group\. Before you delete your group, you must manually check all of your policies to find any polcies where that group is mentioned by name\. For example, let's say Bob is the manager of the testing part of the organization, and he has a policy attached to his IAM user entity that lets him add and remove users from the Test group\. If an an admin deletes the group, the admin also needs to delete the policy attached to Bob\. 

**To find policies that refer to a group as a resource:**

1. From the navigation pane of the IAM console, choose **Policies**\.

1. From the **Policy type** drop\-down list, choose **Customer managed** to filter the policies to show only your custom policies\.

1. Choose the arrow next to each policy name to expand the policy summary\.

1. Choose **IAM** from the list of services, if it exists\.

1. Look for the name of your group in the **Resource** column\.

1. Choose **Delete policy** to delete the policy\.

In contrast, when you use the AWS CLI, Tools for Windows PowerShell, or AWS API to delete a group, you must first remove the users in the group, delete any inline policies embedded in the group, and detach any managed policies attached to the group before you can delete the group\. 

**To delete an IAM group \(AWS Management Console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, select **Groups**\. 

1. In the list of groups, select the check box next to the name of the group to delete\. You can use the **Filter** menu and the search box to filter the list of policies\. 

1. Click **Group Actions**, then click **Delete Group**\.

1. In the confirmation box, click **Yes, Delete**\.

**To delete an IAM group \(AWS CLI, Tools for Windows PowerShell, AWSAPI\)**

1. Remove all users from the group\.
   + CLI: [aws iam get\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html) \(to get the list of users in the group\), and [aws iam remove\-user\-from\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html) \(to remove a user from the group\) 
   + Tools for Windows PowerShell: 

     ```
     (Get-IAMGroup -GroupName "GroupToDelete").Users | Remove-IAMUserFromGroup -GroupName "GroupToDelete" -Force
     ```
   + AWS API: [GetGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html) \(to get the list of users in the group\), and [RemoveUserFromGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html) \(to remove a user from the group\) 

1. Delete all inline policies embedded in the group\.
   + CLI: [aws iam list\-group\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-group-policies.html) \(to get a list of the group's inline policies\), and [aws iam delete\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-group-policy.html) \(to delete the group's inline policies\) 
   + Tools for Windows PowerShell: 

     ```
     Get-IAMGroupPolicies -GroupName "GroupToReplace" | % { Remove-IAMGroupPolicy -GroupName "GroupToReplace" -PolicyName $_ -Force}
     ```
   +  AWS API: [ListGroupPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupPolicies.html) \(to get a list of the group's inline policies\), and [DeleteGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteGroupPolicy.html) \(to delete the group's inline policies\) 

1. Detach all managed policies attached to the group\.
   + CLI: [aws iam list\-attached\-group\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html) \(to get a list of the managed policies attached to the group\), and [aws iam detach\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-group-policy.html) \(to detach a managed policy from the group\) 
   + Tools for Windows PowerShell: 

     ```
     Get-IAMAttachedUserPolicies -UserName "UserToDelete" | % { Unregister-IAMUserPolicy -PolicyArn $_.PolicyArn -UserName -UserName "UserToDelete" -Force }
     ```
   + AWS API: [ListAttachedGroupPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedGroupPolicies.html) \(to get a list of the managed policies attached to the group'\), and [DetachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachGroupPolicy.html) \(to detach a managed policy from the group\)

1. Delete the group\.
   + CLI: [aws iam delete\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-group.html)
   + Tools for Windows PowerShell: [Remove\-IAMGroup](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMGroup.html&tocid=Remove-IAMGroup)
   + AWS API: [DeleteGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteGroup.html) 