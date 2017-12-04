# Amazon EC2: Allows Launching EC2 Instances in a Specific Subnet, Programmatically and in the Console<a name="reference_policies_examples_ec2_instances-subnet"></a>

This example shows how you might create a policy that allows listing information for all EC2 objects and launching EC2 instances in a specific subnet\. This policy also provides the permissions necessary to complete this action on the console\. To use this policy, replace the red text in the example policy with your own information\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:Describe*",
                "ec2:GetConsole*"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "ec2:RunInstances",
            "Resource": [
                "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:subnet/subnet-<SUBNET-ID>",
                "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:network-interface/*",
                "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:instance/*",
                "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:volume/*",
                "arn:aws:ec2:<REGION>::image/ami-*",
                "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:key-pair/*",
                "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:security-group/*"
            ]
        }
    ]
}
```