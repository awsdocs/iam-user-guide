# IAM: Allows IAM Users to Self\-Manage an MFA Device<a name="reference_policies_examples_iam_mfa-selfmanage"></a>

This example shows how you might create a policy that allows IAM users to self\-manage an MFA device\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\.

**Note**  
If you add these permissions for a user that is signed in to AWS, they might need to sign out and back in to see these changes\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:CreateVirtualMFADevice",
        "iam:EnableMFADevice",
        "iam:ResyncMFADevice",
        "iam:DeleteVirtualMFADevice"
      ],
      "Resource": [
        "arn:aws:iam::*:mfa/${aws:username}",
        "arn:aws:iam::*:user/${aws:username}"
      ]
    },
    {
      "Sid": "AllowUsersToDeactivateTheirOwnVirtualMFADevice",
      "Effect": "Allow",
      "Action": [
        "iam:DeactivateMFADevice"
      ],
      "Resource": [
        "arn:aws:iam::*:mfa/${aws:username}",
        "arn:aws:iam::*:user/${aws:username}"
      ],
      "Condition": {
        "Bool": {
          "aws:MultiFactorAuthPresent": "true"
        }
      }
    },
    {
      "Effect": "Allow",
      "Action": [
        "iam:ListMFADevices",
        "iam:ListVirtualMFADevices",
        "iam:ListUsers"
      ],
      "Resource": "*"
    }
  ]
}
```