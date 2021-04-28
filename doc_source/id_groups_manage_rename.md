# Renaming an IAM user group<a name="id_groups_manage_rename"></a>

When you change a user group's name or path, the following happens: 
+ Any policies attached to the user group stay with the group under the new name\.
+ The user group retains all its users under the new name\.
+ The unique ID for the user group remains the same\. For more information about unique IDs, see [Unique identifiers](reference_identifiers.md#identifiers-unique-ids)\. 

IAM does not automatically update policies that refer to the user group as a resource to use the new name\. Therefore, you must be careful when you rename a user group\. Before you rename your user group, you must manually check all of your policies to find any policies where that user group is mentioned by name\. For example, let's say Bob is the manager of the testing part of the organization\. Bob has a policy attached to his IAM user entity that lets him add and remove users from the Test user group\. If an administrator changes the name of the user group \(or changes the group path\), the administrator must also update the policy attached to Bob to use the new name or path\. Otherwise Bob won't be able to add and remove users from the user group\. 

**To find policies that refer to a user group as a resource:**

1. From the navigation pane of the IAM console, choose **Policies**\.

1. From the **Filter policies** menu, select the **Customer managed** check box to filter the policies to show only your custom policies\.

1. Choose the arrow next to each policy name to expand the policy summary\.

1. Choose **IAM** from the list of services, if it exists\.

1. Look for the name of your user group in the **Resource** column\.

1. Choose **Edit policy** to change the name of your user group in the policy\.

**To change the name of an IAM user group**

Do any of the following:
+  [AWS Management Console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **User groups** and then select the group name\. Choose **Edit**\. Type the new user group name and then choose **Save changes**\.
+ AWS CLI: [aws iam update\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/update-group.html) 
+ AWS API: [UpdateGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateGroup.html) 