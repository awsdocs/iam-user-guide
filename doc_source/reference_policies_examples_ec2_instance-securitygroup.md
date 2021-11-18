# Amazon EC2: Allows starting or stopping an EC2 instance and modifying a security group, programmatically and in the console<a name="reference_policies_examples_ec2_instance-securitygroup"></a>

This example shows how you might create an IAM policy that allows starting or stopping a specific EC2 instance and modifying a specific security group\. This policy defines permissions for programmatic and console access\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeSecurityGroups",
        "ec2:DescribeSecurityGroupRules",
        "ec2:DescribeTags"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "ec2:AuthorizeSecurityGroupIngress",
        "ec2:RevokeSecurityGroupIngress",
        "ec2:AuthorizeSecurityGroupEgress",
        "ec2:RevokeSecurityGroupEgress",
        "ec2:ModifySecurityGroupRules",
        "ec2:UpdateSecurityGroupRuleDescriptionsIngress",
        "ec2:UpdateSecurityGroupRuleDescriptionsEgress"
      ],
      "Resource": [
        "arn:aws:ec2:region:111122223333:security-group/*"
      ],
      "Condition": {
        "ArnEquals": {
          "ec2:Vpc": "arn:aws:ec2:region:111122223333:vpc/vpc-11223344556677889"
        }
      }
    },
    {
      "Effect": "Allow",
      "Action": [
        "ec2:ModifySecurityGroupRules"
      ],
      "Resource": [
        "arn:aws:ec2:region:111122223333:security-group-rule/*"
      ]
    }
  ]
}
```