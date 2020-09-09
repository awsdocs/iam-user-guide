# Troubleshooting IAM and Amazon S3<a name="troubleshoot_iam-s3"></a>

Use the information here to help you troubleshoot and fix issues that you might encounter when working with Amazon S3 and IAM\.

## How do I grant anonymous access to an Amazon S3 bucket?<a name="troubleshoot_iam-s3_anonymous-bucket-access"></a>

You use an Amazon S3 bucket policy that specifies a wildcard \(\*\) in the `principal` element, which means anyone can access the bucket\. With anonymous access, anyone \(including users without an AWS account\) will be able to access the bucket\. For a sample policy, see [ Example Cases for Amazon S3 Bucket Policies](https://docs.aws.amazon.com/AmazonS3/latest/dev/AccessPolicyLanguage_UseCases_s3_a.html) in the *Amazon Simple Storage Service Developer Guide*\.

## I'm signed in as an AWS account root user; why can't I access an Amazon S3 bucket under my account?<a name="troubleshoot_iam-s3_root-bucket-access"></a>

In some cases, you might have an IAM user with full access to IAM and Amazon S3\. If the IAM user assigns a bucket policy to an Amazon S3 bucket and doesn't specify the AWS account root user as a principal, the root user is denied access to that bucket\. However, as the root user, you can still access the bucket\. To do that, modify the bucket policy to allow root user access from the Amazon S3 console or the AWS CLI\. Use the following principal, replacing *123456789012* with the ID of the AWS account\.

```
"Principal": { "AWS": "arn:aws:iam::123456789012:root" }
```