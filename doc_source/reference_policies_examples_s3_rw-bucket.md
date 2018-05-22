# Amazon S3: Allows Read and Write Access to a Specific S3 Bucket<a name="reference_policies_examples_s3_rw-bucket"></a>

This example shows how you might create a policy that allows `Read` and `Write` access to a specific S3 bucket\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

```
{
   "Version": "2012-10-17",
   "Statement": [
     {
       "Effect": "Allow",
       "Action": ["s3:ListBucket"],
       "Resource": ["arn:aws:s3:::<BUCKET-NAME>"]
     },
     {
       "Effect": "Allow",
       "Action": [
         "s3:PutObject",
         "s3:GetObject"
       ],
       "Resource": ["arn:aws:s3:::<BUCKET-NAME>/*"]
     }
   ]
 }
```

**Note**  
To allow `Read` and `Write` access to a specific Amazon S3 bucket and also include additional permissions for console access, see [Amazon S3: Allows Read and Write Access to a Specific S3 Bucket, Programmatically and in the Console](reference_policies_examples_s3_rw-bucket-console.md)\.