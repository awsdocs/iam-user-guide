# Amazon RDS: Allows Full RDS Database Access Within a Specific Region<a name="reference_policies_examples_rds_region"></a>

This example shows how you might create a policy that allows full RDS database access within a specific region\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

```
{
  "Version": "2012-10-17",
  "Statement": [
      {
          "Effect": "Allow",
          "Action": "rds:*",
          "Resource": [
              "arn:aws:rds:<REGION>:<ACCOUNTNUMBER>:*"
          ]
      },
      {
          "Effect": "Allow",
          "Action": [
              "rds:Describe*"
          ],
          "Resource": [
              "*"
          ]
      }
  ]
}
```