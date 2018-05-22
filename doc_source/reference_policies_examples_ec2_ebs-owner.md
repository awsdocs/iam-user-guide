# Amazon EC2: Attach or Detach Amazon EBS Volumes to EC2 Instances Based on Tags<a name="reference_policies_examples_ec2_ebs-owner"></a>

This example shows how you might create a policy that allows EBS volume owners to attach or detach their EBS volumes defined using the tag `volume_user` to EC2 instances that are tagged as development instances \(`department=dev`\)\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

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
      "Resource": "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:instance/*",
      "Condition": {"StringEquals": {"ec2:ResourceTag/department": "dev"}}
    },
    {
      "Effect": "Allow",
      "Action": [
        "ec2:AttachVolume",
        "ec2:DetachVolume"
      ],
      "Resource": "arn:aws:ec2:<REGION>:<ACCOUNTNUMBER>:volume/*",
      "Condition": {"StringEquals": {"ec2:ResourceTag/volume_user": "${aws:username}"}}
    }
  ]
}
```