# Renaming an IAM Group<a name="id_groups_manage_rename"></a>

When you change a group's name or path, the following happens: 
+ Any policies attached to the group stay with the group under the new name\.
+ The group retains all its users under the new name\.
+ The unique ID for the group remains the same\. For more information about unique IDs, see [Unique IDs](reference_identifiers.md#identifiers-unique-ids)\. 

IAM does not automatically update policies that refer to the group as a resource to use the new name; you must manually do that\. For example, let's say Bob is the manager of the testing part of the organization, and he has a policy attached to his IAM user entity that lets him add and remove users from the Test group\. If an an admin changes the name of the group to `Test_1` \(or changes the path for the group\), the admin also needs to update the policy attached to Bob to use the new name \(or new path\)\. Otherwise Bob won't be able to add and remove users from the group\. 

To change the name of an IAM group
+ [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, click **Groups** and then select the check box next to the group name\. From the **Group Actions** list at the top of the page, select **Edit Group Name**\. Type the new group name and then click **Yes, Edit**\.
+ AWS CLI: [aws iam update\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/update-group.html) 
+ Tools for Windows PowerShell: [Update\-IAMGroup](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMGroup.html&tocid=Update-IAMGroup)
+ AWS API: [UpdateGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateGroup.html) 