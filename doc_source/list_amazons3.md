# Actions, Resources, and Condition Keys for Amazon S3<a name="list_amazons3"></a>

Amazon S3 \(service prefix: `s3`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonS3/latest/dev/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AmazonS3/latest/API/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon S3](#amazons3-actions-as-permissions)
+ [Resource Types Defined by Amazon S3](#amazons3-resources-for-iam-policies)
+ [Condition Keys for Amazon S3](#amazons3-policy-keys)

## Actions Defined by Amazon S3<a name="amazons3-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazons3.html)

## Resource Types Defined by Amazon S3<a name="amazons3-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazons3-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ accesspoint ](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-points.html)  |  arn:$\{Partition\}:s3:$\{Region\}:$\{Account\}:accesspoint/$\{AccessPointName\}  |  | 
|   [ bucket ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html)  |  arn:$\{Partition\}:s3:::$\{BucketName\}  |  | 
|   [ object ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingObjects.html)  |  arn:$\{Partition\}:s3:::$\{BucketName\}/$\{ObjectName\}  |  | 
|   [ job ](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops-managing-jobs.html)  |  arn:$\{Partition\}:s3:$\{Region\}:$\{Account\}:job/$\{JobId\}  |  | 

## Condition Keys for Amazon S3<a name="amazons3-policy-keys"></a>

Amazon S3 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ s3:AccessPointNetworkOrigin ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | The network type from which traffic may be received by the access point involved in the request | String | 
|   [ s3:DataAccessPointAccount ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | The AWS Account ID of the account that owns the data operations access point involved in the request | String | 
|   [ s3:DataAccessPointArn ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | The ARN of the data operations access point involved in the request | String | 
|   s3:ExistingJobOperation  |  | String | 
|   s3:ExistingJobPriority  |  | Numeric | 
|   [ s3:ExistingObjectTag/<key> ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  | Enables you to verify that an existing object tag has the specific tag key and value\. | String | 
|   s3:JobSuspendedCause  |  | String | 
|   [ s3:LocationConstraint ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies)  | Enables you to restrict users to creating buckets in only a specific region\. | String | 
|   s3:RequestJobOperation  |  | String | 
|   s3:RequestJobPriority  |  | Numeric | 
|   [ s3:RequestObjectTag/<key> ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  | Restrict the tag keys and values that you want to allow on objects\. | String | 
|   [ s3:RequestObjectTagKeys ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  |  restrict the tag keys that you want to allow on objects\. | String | 
|   [ s3:VersionId ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables you to limit the permission for the s3:PutObjectVersionTagging action to a specific object version\. | String | 
|   s3:authtype  |  | String | 
|   [ s3:delimiter ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies)  | Enables you to require the user to specify the delimiter parameter in the GET Bucket Object versions request\. | String | 
|   [ s3:locationconstraint ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies)  | Enables you to restrict the user to creating a bucket in only a specific region\. | String | 
|   [ s3:max\-keys ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies)  | Enables you to limit the number of keys Amazon S3 returns in response to ListBucket requests by requiring the user to specify the max\-keys parameter\. | Numeric | 
|   [ s3:object\-lock\-legal\-hold ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables enforcement of the specified object legal hold status | String | 
|   [ s3:object\-lock\-mode ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables enforcement of the specified object retention mode | String | 
|   [ s3:object\-lock\-remaining\-retention\-days ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables enforcement of an object relative to the remaining retention days | String | 
|   [ s3:object\-lock\-retain\-until\-date ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables enforcement of a specific retain\-until\-date | String | 
|   [ s3:prefix ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies)  | Enables you to limit the response of the ListBucket API to key names with specific prefix\. | String | 
|   [ s3:signatureage ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#AvailableKeys-iamV2)  |  | Numeric | 
|   [ s3:signatureversion ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#AvailableKeys-iamV2)  |  | String | 
|   [ s3:versionid ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  |  | String | 
|   [ s3:x\-amz\-acl ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables you to require specific access permissions when uploading an object\. | String | 
|   [ s3:x\-amz\-content\-sha256 ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  |  | String | 
|   [ s3:x\-amz\-copy\-source ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables you to restrict the copy source to a specific bucket, a specific folder in the bucket, or a specific object in a bucket\. | String | 
|   s3:x\-amz\-grant\-full\-control  |  | String | 
|   s3:x\-amz\-grant\-read  |  | String | 
|   s3:x\-amz\-grant\-read\-acp  |  | String | 
|   s3:x\-amz\-grant\-write  |  | String | 
|   s3:x\-amz\-grant\-write\-acp  |  | String | 
|   [ s3:x\-amz\-metadata\-directive ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables you to enforce certain behavior \(COPY vs\. REPLACE\) when objects are uploaded\. | String | 
|   [ s3:x\-amz\-server\-side\-encryption ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies)  | Enables you to require the user to specify this header in the request to ensure that objects the user uploads are encrypted when they are saved\. | String | 
|   [ s3:x\-amz\-server\-side\-encryption\-aws\-kms\-key\-id ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies)  |  | String | 
|   s3:x\-amz\-storage\-class  |  | String | 
|   s3:x\-amz\-website\-redirect\-location  |  | String | 