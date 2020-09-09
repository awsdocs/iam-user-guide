# IAM: Access the policy simulator API<a name="reference_policies_examples_iam_policy-sim"></a>

This example shows how you might create a policy that allows using the policy simulator API for policies attached to a user, group, or role in the current AWS account\. This policy also allows access to simulate less sensitive policies passed to the API as strings\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "iam:GetContextKeysForCustomPolicy",
                "iam:GetContextKeysForPrincipalPolicy",
                "iam:SimulateCustomPolicy",
                "iam:SimulatePrincipalPolicy"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

**Note**  
To allow a user to access the policy simulator console to simulate policies attached to a user, group, or role in the current AWS account, see [IAM: Access the policy simulator console](reference_policies_examples_iam_policy-sim-console.md)\.