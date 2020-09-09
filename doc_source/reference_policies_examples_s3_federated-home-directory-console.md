# Amazon S3: Allows federated users access to their S3 home directory, programmatically and in the console<a name="reference_policies_examples_s3_federated-home-directory-console"></a>

This example shows how you might create a policy that allows federated users to access their own home directory bucket object in S3\. The home directory is a bucket that includes a `home` folder and folders for individual federated users\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

The `${aws:userid}` variable in this policy resolves to `role-id:specified-name`\. The `role-id` part of the federated user ID is a unique identifier assigned to the federated user's role during creation\. For more information, see [Unique identifiers](reference_identifiers.md#identifiers-unique-ids)\. The `specified-name` is the [RoleSessionName parameter](https://docs.aws.amazon.com/IAM/latest/APIReference/API_AssumeRole.html#API_AssumeRoleWithWebIdentity_RequestParameters) passed to the `AssumeRoleWithWebIdentity` request when the federated user assumed their role\.

You can view the role ID using the AWS CLI command `aws iam get-role --role-name specified-name`\. For example, imagine that you specify the friendly name `John` and the CLI returns the role ID `AROAXXT2NJT7D3SIQN7Z6`\. In this case, the federated user ID is `AROAXXT2NJT7D3SIQN7Z6:John`\. This policy then allows the federated user John to access the Amazon S3 bucket with prefix `AROAXXT2NJT7D3SIQN7Z6:John`\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListAllMyBuckets",
                "s3:GetBucketLocation"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::bucket-name",
            "Condition": {
                "StringLike": {
                    "s3:prefix": [
                        "",
                        "home/",
                        "home/${aws:userid}/*"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::bucket-name/home/${aws:userid}",
                "arn:aws:s3:::bucket-name/home/${aws:userid}/*"
            ]
        }
    ]
}
```