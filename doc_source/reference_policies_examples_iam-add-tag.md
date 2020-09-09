# IAM: Add a specific tag to a user with a specific tag<a name="reference_policies_examples_iam-add-tag"></a>

This example shows how you might create a policy that allows adding the tag key `Department` with the tag values `Marketing`, `Development`, or `QualityAssurance` to an IAM user\. That user must already include the tag key–value pair `JobFunction = manager`\. You can use this policy to require that a manager belong to only one of three departments\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

The `ListTagsForAllUsers` statement allows the viewing of tags for all users in your account\. 

The first condition in the `TagManagerWithSpecificDepartment` statement uses the `StringEquals` condition operator\. The condition returns true if both parts of the condition are true\. The user to be tagged must already have the `JobFunction=Manager` tag\. The request must include the `Department` tag key with one of the listed tag values\. 

The second condition uses the `ForAllValues:StringEquals` condition operator\. The condition returns true if all of the tag keys in the request match the key in the policy\. This means that the only tag key in the request must be `Department`\. For more information about using `ForAllValues`, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ListTagsForAllUsers",
            "Effect": "Allow",
            "Action": [
                "iam:ListUserTags",
                "iam:ListUsers"
            ],
            "Resource": "*"
        },
        {
            "Sid": "TagManagerWithSpecificDepartment",
            "Effect": "Allow",
            "Action": "iam:TagUser",
            "Resource": "*",
            "Condition": {"StringEquals": {
                "iam:ResourceTag/JobFunction": "Manager",
                "aws:RequestTag/Department": [
                    "Marketing",
                    "Development",
                    "QualityAssurance"
                    ]
                },
                "ForAllValues:StringEquals": {"aws:TagKeys": "Department"}
            }
        }
    ]
}
```