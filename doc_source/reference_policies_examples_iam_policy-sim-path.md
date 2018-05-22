# IAM: Access the Policy Simulator API Based on User Path<a name="reference_policies_examples_iam_policy-sim-path"></a>

This example shows how you might create a policy that allows using the policy simulator API only for those users that have the path `USER-PATH-NAME`\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "iam:GetContextKeysForPrincipalPolicy",
        "iam:SimulatePrincipalPolicy"
      ],
      "Effect": "Allow",
      "Resource":"arn:aws:iam::<ACCOUNTNUMBER>:user/<USER-PATH-NAME>/*"
    }
  ]
}
```

**Note**  
To create a policy that allows using the policy simulator console for those users that have the path `USER-PATH-NAME`, see [IAM: Access the Policy Simulator Console Based on User Path](reference_policies_examples_iam_policy-sim-path-console.md)\.