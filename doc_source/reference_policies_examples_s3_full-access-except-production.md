# Amazon S3: S3 Bucket Access, but Production Bucket Denied Without Recent MFA<a name="reference_policies_examples_s3_full-access-except-production"></a>

This example shows how you might create a policy that allows an Amazon S3 administrator to access any bucket, including updating, adding, and deleting objects\. However, it explicitly denies access to the `Production` bucket if the user has not signed in using MFA within the last thirty minutes\. This policy grants the permissions necessary to perform this action in the console or programmatically using the AWS CLI or AWS API\. To use this policy, replace the red italicized text in the example policy with your own information\.

This policy never allows programmatic access to the `Production` bucket using long\-term user access keys\. To access the `Production` bucket programmatically, the S3 administrator must use MFA\-authenticated temporary credentials using the [GetSessionToken](id_credentials_temp_request.md#api_getsessiontoken) API operation\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ListAllS3Buckets",
            "Effect": "Allow",
            "Action": ["s3:ListAllMyBuckets"],
            "Resource": "arn:aws:s3:::*"
        },
        {
            "Sid": "AllowBucketLevelActions",
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetBucketLocation"
            ],
            "Resource": "arn:aws:s3:::*"
        },
        {
            "Sid": "AllowBucketObjectActions",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:PutObjectAcl",
                "s3:GetObject",
                "s3:GetObjectAcl",
                "s3:DeleteObject"
            ],
            "Resource": "arn:aws:s3:::*/*"
        },
        {
            "Sid": "RequireMFAForProductionBucket",
            "Effect": "Deny",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::Production/*",
                "arn:aws:s3:::Production"
            ],
            "Condition": {
                "NumericGreaterThan": {"aws:MultiFactorAuthAge": "1800"}
            }
        }
    ]
}
```