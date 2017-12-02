# Listing IAM Groups<a name="id_groups_manage_list"></a>

You can list all the groups in your account, list the users in a group, and list the groups a user belongs to\. If you use the AWS CLI, Tools for Windows PowerShell, or AWS API, you can list all the groups with a particular path prefix 

To list all the groups in your account 

+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups**\.

+ AWS CLI: [aws iam list\-groups](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-groups.html)

+ Tools for Windows PowerShell: [Get\-IAMGroups](http://alpha-docs-aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMGroups.html&tocid=Get-IAMGroups)

+ AWS API: [ListGroups](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListGroups.html) 

To list the users in a specific group

+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups**, choose the name of the group, and then choose the **Users** tab\. 

+ AWS CLI: [aws iam get\-group](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/get-group.html)

+ Tools for Windows PowerShell: [Get\-IAMGroup](http://alpha-docs-aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMGroup.html&tocid=Get-IAMGroup)

+ AWS API: [GetGroup](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html)

To list all the groups that a user is in

+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, chose **Users**, choose the user name, and then choose the **Groups** tab\. 

+ AWS CLI: [aws iam list\-groups\-for\-user](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-groups-for-user.html)

+ Tools for Windows PowerShell: [Get\-IAMGroupForUser](http://alpha-docs-aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMGroupForUser.html&tocid=Get-IAMGroupForUser)

+ AWS API: [ListGroupsForUser](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html)