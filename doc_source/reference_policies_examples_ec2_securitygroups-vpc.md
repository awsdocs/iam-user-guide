# Amazon EC2: Allows managing EC2 security groups associated with a specific VPC, programmatically and in the console<a name="reference_policies_examples_ec2_securitygroups-vpc"></a>

This example shows how you might create an IAM policy that allows managing Amazon EC2 security groups associated with a specific virtual private cloud \(VPC\)\. This policy defines permissions for programmatic and console access\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

```
{
   "Version": "2012-10-17",
   "Statement": [{
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
         "StringEquals": {
            "aws:Department": "Test"
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