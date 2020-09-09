# IAM: Access the policy simulator API based on user path<a name="reference_policies_examples_iam_policy-sim-path"></a>

This example shows how you might create a policy that allows using the policy simulator API only for those users that have the path `Department/Development`\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

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
            "Resource": "arn:aws:iam::*:user/Department/Development/*"
        }
    ]
}
```

**Note**  
To create a policy that allows using the policy simulator console for those users that have the path `Department/Development`, see [IAM: Access the policy simulator console based on user path](reference_policies_examples_iam_policy-sim-path-console.md)\.