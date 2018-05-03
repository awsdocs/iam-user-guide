# AWS: Denies Access to AWS Based on the Source IP<a name="reference_policies_examples_aws_deny-ip"></a>

This example shows how you might create a policy that denies access to all AWS actions in the account when the request comes from outside the specified IP range\. The policy is useful when the IP addresses for your company are within the specified ranges\. This policy also provides the permissions necessary to complete this action on the console\. To use this policy, replace the red text in the example policy with your own information\.

The `aws:SourceIp` condition key denies access to an AWS service, such as AWS CloudFormation, that makes calls on your behalf\. For more information about using the `aws:SourceIp` condition key, see [AWS Global Condition Context Keys](reference_policies_condition-keys.md)\.

**Important**  
This policy does not allow any actions\. Use this policy in combination with other policies that allow specific actions\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Deny",
    "Action": "*",
    "Resource": "*",
    "Condition": {"NotIpAddress": {"aws:SourceIp": [
      "192.0.2.0/24",
      "203.0.113.0/24"
    ]}}
  }
}
```