# Creating IAM user groups<a name="id_groups_create"></a>

To set up a user group, you need to create the group\. Then give the group permissions based on the type of work that you expect the users in the group to do\. Finally, add users to the group\.

For information about the permissions that you need in order to create a user group, see [Permissions required to access IAM resources](access_permissions-required.md)\. 

**To create an IAM user group and attach policies \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **User groups** and then choose **Create group**\.

1. For **User group name**, type the name of the group\.
**Note**  
The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\. Group names can be a combination of up to 128 letters, digits, and these characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at sign \(@\), underscore \(\_\), and hyphen \(\-\)\. Names must be unique within an account\. They are not distinguished by case\. For example, you cannot create groups named both **ADMINS** and **admins**\.

1. In the list of users, select the check box for each user that you want to add to the group\.

1. In the list of policies, select the check box for each policy that you want to apply to all members of the group\.

1. Choose **Create group**\.

For an example of how to set up an `Administrators` user group, see [Creating your first IAM admin user and user group](getting-started_create-admin-group.md)\.

**To create IAM user groups \(AWS CLI or AWS API\)**  
Use one of the following:
+ AWS CLI: [aws iam create\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/create-group.html) 
+ AWS API: [CreateGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateGroup.html) 