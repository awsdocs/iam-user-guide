# Creating IAM Groups<a name="id_groups_create"></a>

To set up a group, you need to create the group, give it permissions based on the type of work that you expect the users in the group to do, and then add users to the group\. 

For information about the permissions that you need in order to create a group, see [Permissions Required to Access IAM Resources](access_permissions-required.md)\. 

**To create an IAM group and attach policies \(AWS Management Console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Groups** and then click **Create New Group**\.

1. In the **Group Name** box, type the name of the group and then click **Next Step**\.
**Important**  
Group names must be unique within an account\. They are not distinguished by case, for example, you cannot create groups named both "ADMINS" and "admins"\.

1. In the list of policies, select the check box for each policy that you want to apply to all members of the group\. Then click **Next Step**\.

1. Click **Create Group**\.

For an example of how to set up an `Administrators` group, see [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)\.

**To create IAM groups and attach policies \(AWS CLI, Tools for Windows PowerShell, AWS API\)**  
Use one of the following commands to create a group:
+ AWS CLI: [aws iam create\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/create-group.html) 
+ Tools for Windows PowerShell: [New\-IAMGroup](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMGroup.html&tocid=New-IAMGroup)
+ AWS API: [CreateGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateGroup.html) 