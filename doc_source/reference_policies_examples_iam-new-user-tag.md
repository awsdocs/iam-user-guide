# IAM: Create New Users Only With Specific Tags<a name="reference_policies_examples_iam-new-user-tag"></a>

This example shows how you might create a policy that allows the creation of IAM users but only with the tag key `Department` with either the tag value `Development` or the tag value `QualityAssurance`\. The example also allows the creation of a user with the tag key–value pair `JobFunction = employee`\. You can use this policy to require that new users have a specific job function and department\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the red italicized text in the example policy with your own information\. 

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Sid": "TagUsersWithOnlyTheseTags",
        "Effect": "Allow",
        "Action": "iam:CreateUser",
        "Resource": "*",
        "Condition": {"StringEquals": [
            {"aws:RequestTag/<Department>": [
                "<Development>",
                "<QualityAssurance>"
            ]},
            {"aws:RequestTag/<JobFunction>": "<employee>"}
        ]}
    }]
}
```