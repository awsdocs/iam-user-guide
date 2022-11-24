# Preview access<a name="access-analyzer-access-preview"></a>

In addition to helping you identify resources that are shared with an external entity, AWS IAM Access Analyzer also enables you to preview Access Analyzer findings before deploying resource permissions so you can validate that your policy changes grant only intended public and cross\-account access to your resource\. This helps you start with intended external access to your resources\.

You can preview and validate public and cross\-account access to your Amazon S3 buckets in the [Amazon S3 console](https://aws.amazon.com/s3/)\. You can also use Access Analyzer APIs to preview public and cross\-account access for your Amazon S3 buckets, AWS KMS keys, IAM roles, Amazon SQS queues and Secrets Manager secrets by providing proposed permissions for your resource\.

**Topics**
+ [Previewing access in Amazon S3 console](access-analyzer-preview-access-s3-console.md)
+ [Previewing access with Access Analyzer APIs](access-analyzer-preview-access-apis.md)