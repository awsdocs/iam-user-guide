# Listing IAM groups<a name="id_groups_manage_list"></a>

You can list all the groups in your account, list the users in a group, and list the groups a user belongs to\. If you use the AWS CLI or AWS API, you can list all the groups with a particular path prefix\. 

**To list all the groups in your account**

Do any of the following:
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups**\. 
+ AWS CLI: [aws iam list\-groups](https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups.html)
+ AWS API: [ListGroups](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroups.html) 

**To list the users in a specific group**

Do any of the following:
+  [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups**, choose the name of the group, and then choose the **Users** tab\. 
+ AWS CLI: [aws iam get\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html)
+ AWS API: [GetGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html)

**To list all the groups that a user is in**

Do any of the following:
+  [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Users**, choose the user name, and then choose the **Groups** tab\. 
+ AWS CLI: [aws iam list\-groups\-for\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups-for-user.html)
+ AWS API: [ListGroupsForUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html)