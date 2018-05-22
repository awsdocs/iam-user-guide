# IAM: Access the Policy Simulator Console Based on User Path<a name="reference_policies_examples_iam_policy-sim-path-console"></a>

This example shows how you might create a policy that allows using the policy simulator console only for those users that have the path `USER-PATH-NAME`\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

You can access the IAM Policy Simulator at: [https://policysim\.aws\.amazon\.com/](https://policysim.aws.amazon.com/)

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "iam:GetPolicy",           
        "iam:GetUserPolicy"
      ],
      "Effect": "Allow",
      "Resource": "*"
    },
    {
      "Action": [
        "iam:GetUser",           
        "iam:ListAttachedUserPolicies",           
        "iam:ListGroupsForUser",           
        "iam:ListUserPolicies",           
        "iam:ListUsers"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:iam::<ACCOUNTNUMBER>:user/<USER-PATH-NAME>/*"
    }
  ]
}
```