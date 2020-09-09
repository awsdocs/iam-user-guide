# IAM: Assume roles that have a specific tag<a name="reference_policies_examples_iam-assume-tagged-role"></a>

This example shows how you might create a policy that allows an IAM user to assume roles with the tag key\-value pair `Project = ExampleCorpABC`\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

If a role with this tag exists in the same account as the user, then the user can assume that role\. If a role with this tag exists in an account other than the user's, it requires additional permissions\. The cross\-account role's trust policy must also allow the user or all members of the user's account to assume the role\. For information about using roles for cross\-account access, see [Providing access to an IAM user in another AWS account that you own](id_roles_common-scenarios_aws-accounts.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "",
            "Effect": "Allow",
            "Action": "sts:AssumeRole",
            "Resource": "*",
            "Condition": {
                "StringEquals": {"iam:ResourceTag/Project": "ExampleCorpABC"}
            }
        }
    ]
}
```