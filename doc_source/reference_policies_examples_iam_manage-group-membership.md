# IAM: Allows managing a group's membership programmatically and in the console<a name="reference_policies_examples_iam_manage-group-membership"></a>

This example shows how you might create a policy that allows updating the membership of the group called `MarketingTeam`\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

What does this policy do?
+ The `ViewGroups` statement allows allows the user to list all the users and groups in the AWS Management Console\. It also allows the user to view basic information about the users in the account\. These permissions must be in their own statement because they do not support or do not need to specify a resource ARN\. Instead the permissions specify `"Resource" : "*"`\.
+ The `ViewEditThisGroup` statement allows the user to view information about the `MarketingTeam` group, and to add and remove users from that group\.

This policy does not allow the user to view or edit the permissions of the users or the `MarketingTeam` group\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ViewGroups",
            "Effect": "Allow",
            "Action": [
                "iam:ListGroups",
                "iam:ListUsers",
                "iam:GetUser",
                "iam:ListGroupsForUser"
            ],
            "Resource": "*"
        },
        {
            "Sid": "ViewEditThisGroup",
            "Effect": "Allow",
            "Action": [
                "iam:AddUserToGroup",
                "iam:RemoveUserFromGroup",
                "iam:GetGroup"
            ],
            "Resource": "arn:aws:iam::*:group/MarketingTeam"
        }
    ]
}
```