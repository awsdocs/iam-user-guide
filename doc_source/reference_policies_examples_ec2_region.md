# Amazon EC2: Allows Full EC2 Access Within a Specific Region, Programmatically and in the Console<a name="reference_policies_examples_ec2_region"></a>

This example shows how you might create a policy that allows full EC2 access within a specific region\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": "ec2:*",
            "Resource": "*",
            "Effect": "Allow",
            "Condition": {
                "StringEquals": {
                    "ec2:Region": "region"
                }
            }
        }
    ]
}
```