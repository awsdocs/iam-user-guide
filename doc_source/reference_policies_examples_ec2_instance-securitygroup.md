# Amazon EC2: Allows starting or stopping an EC2 instance and modifying a security group, programmatically and in the console<a name="reference_policies_examples_ec2_instance-securitygroup"></a>

This example shows how you might create a policy that allows starting or stopping a specific EC2 instance and modifying a specific security group\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "ec2:DescribeInstances",
                "ec2:DescribeSecurityGroups",
                "ec2:DescribeSecurityGroupReferences",
                "ec2:DescribeStaleSecurityGroups"
            ],
            "Resource": "*",
            "Effect": "Allow"
        },
        {
            "Action": [
                "ec2:AuthorizeSecurityGroupEgress",
                "ec2:AuthorizeSecurityGroupIngress",
                "ec2:RevokeSecurityGroupEgress",
                "ec2:RevokeSecurityGroupIngress",
                "ec2:StartInstances",
                "ec2:StopInstances"
            ],
            "Resource": [
                "arn:aws:ec2:*:*:instance/i-instance-id",
                "arn:aws:ec2:*:*:security-group/sg-security-group-id"
            ],
            "Effect": "Allow"
        }
    ]
}
```