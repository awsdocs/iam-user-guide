# IAM: Add a specific tag with specific values<a name="reference_policies_examples_iam-add-tag-user-role"></a>

This example shows how you might create a policy that allows adding only the tag key `CostCenter` and either the tag value `A-123` or the tag value `B-456` to any IAM user or role\. You can use this policy to limit tagging to a specific tag key and set of tag values\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

The `ConsoleDisplay` statement allows the viewing of tags for all users and roles in your account\. 

The first condition in the `AddTag` statement uses the `StringEquals` condition operator\. The condition returns true if the request includes the `CostCenter` tag key with one of the listed tag values\. 

The second condition uses the `ForAllValues:StringEquals` condition operator\. The condition returns true if all of the tag keys in the request match the key in the policy\. This means that the only tag key in the request must be `CostCenter`\. For more information about using `ForAllValues`, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ConsoleDisplay",
            "Effect": "Allow",
            "Action": [
                "iam:GetRole",
                "iam:GetUser",
                "iam:ListRoles",
                "iam:ListRoleTags",
                "iam:ListUsers",
                "iam:ListUserTags"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AddTag",
            "Effect": "Allow",
            "Action": [
                "iam:TagUser",
                "iam:TagRole"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws:RequestTag/CostCenter": [
                        "A-123",
                        "B-456"
                    ]
                },
                "ForAllValues:StringEquals": {"aws:TagKeys": "CostCenter"}
            }
        }
    ]
}
```