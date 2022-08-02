# AWS: Denies access to AWS based on the source IP<a name="reference_policies_examples_aws_deny-ip"></a>

This example shows how you might create an identity\-based policy that denies access to all AWS actions in the account when the request comes from *principals* outside the specified IP range\. The policy is useful when the IP addresses for your company are within the specified ranges\. The policy does not deny requests made by AWS services using the principal's credentials\. This policy defines permissions for programmatic and console access\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

Be careful using negative conditions in the same policy statement as `"Effect": "Deny"`\. When you do, the actions specified in the policy statement are explicitly denied in all conditions *except* for the ones specified\.

Additionally, this policy includes [multiple condition keys](reference_policies_multi-value-conditions.md) that result in a logical `AND`\. In this policy, all AWS actions are denied when the source IP address is `not` in the specified range `AND` when an AWS service does `not` make the call\.

**Important**  
This policy does not allow any actions\. Use this policy in combination with other policies that allow specific actions\. 

When other policies allow actions, principals can make requests from within the IP address range\. An AWS service can also make requests using the principal's credentials\. When a principal makes a request from outside the IP range, the request is denied\.

For more information about using the `aws:SourceIp` and `aws:ViaAWSService` condition keys, including information about when the `aws:SourceIp` key may not work in your policy, see [AWS global condition context keys](reference_policies_condition-keys.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Deny",
        "Action": "*",
        "Resource": "*",
        "Condition": {
            "NotIpAddress": {
                "aws:SourceIp": [
                    "192.0.2.0/24",
                    "203.0.113.0/24"
                ]
            },
            "Bool": {"aws:ViaAWSService": "false"}
        }
    }
}
```