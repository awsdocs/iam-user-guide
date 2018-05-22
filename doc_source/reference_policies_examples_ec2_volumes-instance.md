# Amazon EC2: Allows an EC2 Instance to Attach or Detach Volumes<a name="reference_policies_examples_ec2_volumes-instance"></a>

This example shows how you might create a policy that can be attached to a service role\. The policy allows the specified EC2 instance to attach or detach volumes\. The instance is specified with an ARN in the `Condition` element\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

Amazon EC2 instances can run AWS commands with permissions granted by an [AWS service role for an EC2 instance](id_roles_terms-and-concepts.md#iam-term-service-role-ec2) that is attached to the instance profile\. You can attach this policy to the role, or add this statement to an existing policy\. Only the instance identified by *INSTANCE\-ID* can attach or detach volumes to instances in the account, including its own\. Other statement elements that might exist in a larger policy are not impacted by the restriction of this one statement\. For more information about creating IAM policies to control access to Amazon EC2 resources, see [Controlling Access to Amazon EC2 Resources](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html) in the *Amazon EC2 User Guide for Linux Instances*\.

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
        "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:volume/*",
        "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:instance/*"
      ],
      "Condition": {
        "ArnEquals": {
          "ec2:SourceInstanceARN": "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:instance/<INSTANCE-ID>"
        }
      }
    }
  ]
}
```