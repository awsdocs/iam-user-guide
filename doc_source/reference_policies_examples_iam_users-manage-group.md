# IAM: Allows specific IAM users to manage a group programmatically and in the console<a name="reference_policies_examples_iam_users-manage-group"></a>

This example shows how you might create a policy that allows specific IAM users to manage the `AllUsers` group\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

What does this policy do?
+ The `AllowAllUsersToListAllGroups` statement allows listing all groups\. This is necessary for console access\. This permission must be in its own statement because it does not support a resource ARN\. Instead the permissions specify `"Resource" : "*"`\.
+ The `AllowAllUsersToViewAndManageThisGroup` statement allows all group actions that can be performed on the group resource type\. It does not allow the `ListGroupsForUser` action, which can be performed on a user resource type and not a group resource type\. For more information about the resource types that you can specify for an IAM action, see [Actions, Resources, and Condition Keys for AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_identityandaccessmanagement.html#identityandaccessmanagement-actions-as-permissions)\.
+ The `LimitGroupManagementAccessToSpecificUsers` statement denies users with the specified names access to write and permissions managment group actions\. When a user specified in the policy attempts to make changes to the group, this statement does not deny the request\. That request is allowed by the `AllowAllUsersToViewAndManageThisGroup` statement\. If other users attempt to perform these operations, the request is denied\. You can view the IAM actions that are defined with the **Write** or **Permissions management** access levels while creating this policy in the IAM console\. To do this, switch from the **JSON** tab to the **Visual editor** tab\. For more information about access levels\. see [Actions, Resources, and Condition Keys for AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_identityandaccessmanagement.html#identityandaccessmanagement-actions-as-permissions)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowAllUsersToListAllGroups",
            "Effect": "Allow",
            "Action": "iam:ListGroups",
            "Resource": "*"
        },
        {
            "Sid": "AllowAllUsersToViewAndManageThisGroup",
            "Effect": "Allow",
            "Action": "iam:*Group*",
            "Resource": "arn:aws:iam::*:group/AllUsers"
        },
        {
            "Sid": "LimitGroupManagementAccessToSpecificUsers",
            "Effect": "Deny",
            "Action": [
                "iam:AddUserToGroup",
                "iam:CreateGroup",
                "iam:RemoveUserFromGroup",
                "iam:DeleteGroup",
                "iam:AttachGroupPolicy",
                "iam:UpdateGroup",
                "iam:DetachGroupPolicy",
                "iam:DeleteGroupPolicy",
                "iam:PutGroupPolicy"
            ],
            "Resource": "arn:aws:iam::*:group/AllUsers",
            "Condition": {
                "StringNotEquals": {
                    "aws:username": [
                        "srodriguez",
                        "mjackson",
                        "adesai"
                    ]
                }
            }
        }
    ]
}
```