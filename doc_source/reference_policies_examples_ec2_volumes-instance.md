# Amazon EC2: Attach or detach volumes to an EC2 instance<a name="reference_policies_examples_ec2_volumes-instance"></a>

This example shows how you might create a policy that allows EBS volume owners to attach or detach volumes to the specified EC2 instance\. The instance is specified with an ARN in the `Condition` element\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

Amazon EC2 instances can run AWS commands with permissions granted by an [AWS service role for an EC2 instance](id_roles_terms-and-concepts.md#iam-term-service-role-ec2) that is attached to the instance profile\. You can attach this policy to the role, or add this statement to an existing policy\. Only the instance identified by *instance\-id* can attach or detach volumes to instances in the account, including its own\. Other statement elements that might exist in a larger policy are not impacted by the restriction of this one statement\. For more information about creating IAM policies to control access to Amazon EC2 resources, see [Controlling Access to Amazon EC2 Resources](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html) in the *Amazon EC2 User Guide for Linux Instances*\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:AttachVolume",
                "ec2:DetachVolume"
            ],
            "Resource": [
                "arn:aws:ec2:*:*:volume/*",
                "arn:aws:ec2:*:*:instance/*"
            ],
            "Condition": {
                "ArnEquals": {"ec2:SourceInstanceARN": "arn:aws:ec2:*:*:instance/instance-id"}
            }
        }
    ]
}
```