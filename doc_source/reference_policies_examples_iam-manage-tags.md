# IAM: Manage a specific tag<a name="reference_policies_examples_iam-manage-tags"></a>

This example shows how you might create an identity\-based policy that allows adding and removing the IAM tag with the tag key `Department` from IAM entities \(users and roles\)\. This policy does not limit the value of the `Department` tag\. This policy grants the permissions necessary to complete this action programmatically from the AWS API or AWS CLI\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "iam:TagUser",
            "iam:TagRole",
            "iam:UntagUser",
            "iam:UntagRole"

        ],
        "Resource": "*",
        "Condition": {"ForAllValues:StringEquals": {"aws:TagKeys": "Department"}}
    }
}
```