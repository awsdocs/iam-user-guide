# Adding and Removing Users in an IAM Group<a name="id_groups_manage_add-remove-users"></a>

At any time, you can add users to or remove users from an IAM group\. This is useful as people enter and leave your organization\.

**To add a user to an IAM group**

Do any of the following:
+  [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups** and then choose the name of the group\. Choose the **Users** tab and then choose **Add Users to Group**\. Select the users you want to add and then choose **Add Users to Group**\.
+ AWS CLI: [aws iam add\-user\-to\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/add-user-to-group.html)
+ AWS API: [AddUserToGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AddUserToGroup.html) 

**To remove a user from an IAM group**

Do any of the following:
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups** and then choose the name of the group\. Choose the **Users** tab and then choose **Remove Users from Group**\. Select the users you want to remove and then choose **Remove Users from Group**\.
+ AWS CLI: [aws iam remove\-user\-from\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/remove-user-from-group.html) 
+ AWS API: [RemoveUserFromGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html) 