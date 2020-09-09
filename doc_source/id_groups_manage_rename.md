# Renaming an IAM group<a name="id_groups_manage_rename"></a>

When you change a group's name or path, the following happens: 
+ Any policies attached to the group stay with the group under the new name\.
+ The group retains all its users under the new name\.
+ The unique ID for the group remains the same\. For more information about unique IDs, see [Unique identifiers](reference_identifiers.md#identifiers-unique-ids)\. 

Because IAM does not automatically update policies that refer to the group as a resource to use the new name; you must be careful when you rename a group\. Before you rename your group, you must manually check all of your policies to find any policies where that group is mentioned by name\. For example, let's say Bob is the manager of the testing part of the organization\. Bob has a policy attached to his IAM user entity that lets him add and remove users from the Test group\. If an administrator changes the name of the group \(or changes the group path\), the administrator must also update the policy attached to Bob to use the new name or path\. Otherwise Bob won't be able to add and remove users from the group\. 

**To find policies that refer to a group as a resource:**

1. From the navigation pane of the IAM console, choose **Policies**\.

1. From the **Policy type** drop\-down list, choose **Customer managed** to filter the policies to show only your custom policies\.

1. Choose the arrow next to each policy name to expand the policy summary\.

1. Choose **IAM** from the list of services, if it exists\.

1. Look for the name of your group in the **Resource** column\.

1. Choose **Edit policy** to change the name of your group in the policy\.

**To change the name of an IAM group**

Do any of the following:
+  [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups** and then select the check box next to the group name\. From the **Group Actions** list at the top of the page, choose **Edit Group Name**\. Type the new group name and then choose **Yes, Edit**\.
+ AWS CLI: [aws iam update\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/update-group.html) 
+ AWS API: [UpdateGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateGroup.html) 