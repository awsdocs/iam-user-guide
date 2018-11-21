# IAM: Add a Specific Tag to a User With a Specific Tag<a name="reference_policies_examples_iam-add-tag"></a>

This example shows how you might create a policy that allows adding the tag key `Department` with the tag values `Marketing`, `Development`, or `QualityAssurance` to an IAM user that already includes the tag key–value pair `JobFunction = manager`\. You can use this policy to require that a manager belong to only one of three departments\. This policy also grants the permissions necessary to complete this action on the console\. To use this policy, replace the red italicized text in the example policy with your own information\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ListTagsForAllUsers",
            "Effect": "Allow",
            "Action": "iam:ListUserTags",
            "Resource": "*"
        },
        {
            "Sid": "TagProjectGreenUserWithSpecificTags",
            "Effect": "Allow",
            "Action": "iam:TagUser",
            "Resource": "*",
            "Condition": {"StringEquals": {
                "iam:ResourceTag/<JobFunction>": "<manager>",
                "aws:RequestTag/<Department>": [
                    "<Marketing>",
                    "<Development>",
                    "<QualityAssurance>"
                ]
            }}
        }
    ]
}
```