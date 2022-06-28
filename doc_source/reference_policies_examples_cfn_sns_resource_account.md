# AWS: Deny access to Amazon SNS resources outside your account except CloudFormation<a name="reference_policies_examples_cfn_sns_resource_account"></a>

Using the condition key `aws:ResourceAccount` in your identity\-based policies can impact the user or the role's ability to utilize some AWS services that require interaction with resources in accounts owned by a service\.

This example shows how you might create an IAM policy that denies access to all resources in AWS that don't belong to your account, except for resources that CloudFormation requires for normal operations\. If you use CloudFormation Stack Sets in your environment, Stack Sets send requests to Amazon SNS topics owned by the CloudFormation on behalf of the IAM principal \(user or role\) invoking the Stack Sets APIs\. In that case, the policy using the `aws:ResourceAccount` condition key, without accounting for CloudFormation\-owned resources, denies access to the Amazon SNS topics owned by the service account\. 

To use this policy, replace the *italicized placeholder text* with your information\.

To allow AWS CloudFormation Stack Sets APIs access to resources in your account, use the following statements in your resource policy:
+ The `DenyAllAwsResourcesOutsideAccountExceptSNS` statement uses the `NotAction` element with the `[Deny](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_effect.html)` effect which explicitly denies access to all of the actions *not* listed in the statement and do *not* belong to the listed account\.

   The `NotAction` element indicates the exceptions for the actions in this statement because if the actions are performed on resources created by CloudFormation, the policy denies the actions\.
+ The `DenyAllSNSResourcesOutsideAccountExceptCloudFormation` statement uses the `aws:ResourceAccount` and the [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-calledvia%EF%BB%BF](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-calledvia%EF%BB%BF) condition keys to deny access to Amazon SNS actions excluded in the previous statement\. The statement denies the actions if the resources do not belong to the listed account **AND** if the calling service is not CloudFormation\. This statement allows the actions if the either the resource belongs to the listed account or the listed service principal performs the operation\.

**Important**  
This policy does not allow any actions\. It uses the `Deny` effect which explicitly denies access to all of the resources listed in the statement that do not belong to the listed account\. Use this policy in combination with other policies that allow access to specific resources\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyAllAwsResourcesOutsideAccountExceptSNS",
      "Effect": "Deny",
      "NotAction": [
        "sns:*"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "111122223333"
          ]
        }
      }
    },
    {
      "Sid": "DenyAllSNSResourcesOutsideAccountExceptCloudFormation",
      "Effect": "Deny",
      "Action": [
        "sns:*"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "111122223333"
          ]
        },
        "ForAllValues:StringNotEquals": {
          "aws:CalledVia": [
            "cloudformation.amazonaws.com"
          ]
        }
      }
    }
  ]
}
```