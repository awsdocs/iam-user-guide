# IAM: Add a Specific Tag with Specific Values<a name="reference_policies_examples_iam-add-tag-user-role"></a>

This example shows how you might create a policy that allows adding only the tag key `CostCenter` and either the tag value `A-123` or the tag value `B-456` to any IAM user or role\. This policy allows you to limit tagging to a specific tag key and set of tag values\. This policy also grants the permissions necessary to complete this action on the console\. To use this policy, replace the red italicized text in the example policy with your own information\. 

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
            "Condition": [
                {"StringEquals": {"aws:RequestTag/<CostCenter>": [
                    "<A-123>",
                    "<B-456>"
                ]}},
                {"ForAllValues:StringEquals": {"aws:TagKeys": "<CostCenter>"}}
            ]
        }
    ]
}
```