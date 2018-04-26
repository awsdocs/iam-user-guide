# IAM: Limits Managed Policies That Can Be Applied to a New IAM User, Group, or Role<a name="reference_policies_examples_iam_limit-managed"></a>

This example shows how you might create a policy that limits customer managed and AWS managed policies that can be applied to a new IAM user, group, or role\. To use this policy, replace the red text in the example policy with your own information\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:ChangePassword",
        "iam:CreateAccessKey",
        "iam:CreateLoginProfile",
        "iam:CreateUser",
        "iam:DeleteAccessKey",
        "iam:DeleteLoginProfile",
        "iam:DeleteUser",
        "iam:UpdateAccessKey",
        "iam:ListAttachedUserPolicies",
        "iam:ListPolicies",
        "iam:ListUserPolicies",
        "iam:ListGroups",
        "iam:ListGroupsForUser",
        "iam:GetPolicy",
        "iam:GetAccountSummary"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "iam:AttachUserPolicy",
        "iam:DetachUserPolicy"
      ],
      "Resource": "*",
      "Condition": {
        "ArnEquals": {
          "iam:PolicyArn": [
            "arn:aws:iam::<ACCOUNTNUMBER>:policy/<MANAGED-POLICY-NAME>",
            "arn:aws:iam::aws:policy/<AWS-MANAGED-POLICY-NAME>"
          ]
        }
      }
    }
  ]
}
```
