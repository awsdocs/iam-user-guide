# Amazon S3: Allows read and write access to objects in an S3 Bucket<a name="reference_policies_examples_s3_rw-bucket"></a>

This example shows how you might create a policy that allows `Read` and `Write` access to objects in a specific S3 bucket\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

The `s3:*Object` action uses a wildcard as part of the action name\. The `AllObjectActions` statement allows the `GetObject`, `DeleteObject`, `PutObject`, and any other Amazon S3 action that ends with the word "Object"\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ListObjectsInBucket",
            "Effect": "Allow",
            "Action": ["s3:ListBucket"],
            "Resource": ["arn:aws:s3:::bucket-name"]
        },
        {
            "Sid": "AllObjectActions",
            "Effect": "Allow",
            "Action": "s3:*Object",
            "Resource": ["arn:aws:s3:::bucket-name/*"]
        }
    ]
}
```

**Note**  
To allow `Read` and `Write` access to an object in an Amazon S3 bucket and also include additional permissions for console access, see [Amazon S3: Allows read and write access to objects in an S3 Bucket, programmatically and in the console](reference_policies_examples_s3_rw-bucket-console.md)\.