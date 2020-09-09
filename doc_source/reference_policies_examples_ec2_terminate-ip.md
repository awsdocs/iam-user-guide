# Amazon EC2: Limits terminating EC2 instances to an IP address range<a name="reference_policies_examples_ec2_terminate-ip"></a>

This example shows how you might create a policy that limits EC2 instances by allowing the action, but explicitly denying access when the request comes from outside the specified IP range\. The policy is useful when the IP addresses for your company are within the specified ranges\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

If this policy is used in combination with other policies that allow the `ec2:TerminateInstances` action \(such as the [AmazonEC2FullAccess](https://aws-iam-console-beta-dev2.integ.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AmazonEC2FullAccess) AWS managed policy\), then access is denied\. This is because an explicit deny statement takes precedence over allow statements\. For more information, see [Determining whether a request is allowed or denied within an account](reference_policies_evaluation-logic.md#policy-eval-denyallow)\.

**Important**  
The `aws:SourceIp` condition key denies access to an AWS service, such as AWS CloudFormation, that makes calls on your behalf\. For more information about using the `aws:SourceIp` condition key, see [AWS global condition context keys](reference_policies_condition-keys.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": ["ec2:TerminateInstances"],
            "Resource": ["*"]
        },
        {
            "Effect": "Deny",
            "Action": ["ec2:TerminateInstances"],
            "Condition": {
                "NotIpAddress": {
                    "aws:SourceIp": [
                        "192.0.2.0/24",
                        "203.0.113.0/24"
                    ]
                }
            },
            "Resource": ["*"]
        }
    ]
}
```