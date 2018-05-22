# Actions, Resources, and Condition Keys for Amazon S3<a name="list_amazons3"></a>

Amazon S3 \(service prefix: `s3`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AmazonS3/latest/dev/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AmazonS3/latest/API/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon S3](#amazons3-actions-as-permissions)
+ [Resources Defined by S3](#amazons3-resources-for-iam-policies)
+ [Condition Keys for Amazon S3](#amazons3-policy-keys)

## Actions Defined by Amazon S3<a name="amazons3-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazons3.html)

## Resources Defined by S3<a name="amazons3-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazons3-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html) | arn:$\{Partition\}:s3:::$\{BucketName\} |  | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingObjects.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingObjects.html) | arn:$\{Partition\}:s3:::$\{BucketName\}/$\{ObjectName\} |  | 

## Condition Keys for Amazon S3<a name="amazons3-policy-keys"></a>

Amazon S3 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies) | Enables you to verify that an existing object tag has the specific tag key and value\. | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to restrict users to creating buckets in only a specific region\. | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies) | Restrict the tag keys and values that you want to allow on objects\. | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies) |  restrict the tag keys that you want to allow on objects\. | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to limit the permission for the s3:PutObjectVersionTagging action to a specific object version\. | String | 
| s3:authtype |  | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to require the user to specify the delimiter parameter in the GET Bucket Object versions request\. | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to restrict the user to creating a bucket in only a specific region\. | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to limit the number of keys Amazon S3 returns in response to ListBucket requests by requiring the user to specify the max\-keys parameter\. | Numeric | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to limit the response of the ListBucket API to key names with specific prefix\. | String | 
| s3:signatureage |  | Numeric | 
| s3:signatureversion |  | String | 
| s3:versionid |  | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to require specific access permissions when uploading an object\. | String | 
| s3:x\-amz\-content\-sha256 |  | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to restrict the copy source to a specific bucket, a specific folder in the bucket, or a specific object in a bucket\. | String | 
| s3:x\-amz\-grant\-full\-control |  | String | 
| s3:x\-amz\-grant\-read |  | String | 
| s3:x\-amz\-grant\-read\-acp |  | String | 
| s3:x\-amz\-grant\-write |  | String | 
| s3:x\-amz\-grant\-write\-acp |  | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to enforce certain behavior \(COPY vs\. REPLACE\) when objects are uploaded\. | String | 
| [http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to require the user to specify this header in the request to ensure that objects the user uploads are encrypted when they are saved\. | String | 
| s3:x\-amz\-server\-side\-encryption\-aws\-kms\-key\-id |  | String | 
| s3:x\-amz\-storage\-class |  | String | 
| s3:x\-amz\-website\-redirect\-location |  | String | 