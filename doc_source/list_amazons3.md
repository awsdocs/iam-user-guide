# Actions, resources, and condition keys for Amazon S3<a name="list_amazons3"></a>

Amazon S3 \(service prefix: `s3`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonS3/latest/dev/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AmazonS3/latest/API/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) permission policies\.

**Topics**
+ [Actions defined by Amazon S3](#amazons3-actions-as-permissions)
+ [Resource types defined by Amazon S3](#amazons3-resources-for-iam-policies)
+ [Condition keys for Amazon S3](#amazons3-policy-keys)

## Actions defined by Amazon S3<a name="amazons3-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazons3.html)

## Resource types defined by Amazon S3<a name="amazons3-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazons3-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ accesspoint ](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-points.html)  |  arn:$\{Partition\}:s3:$\{Region\}:$\{Account\}:accesspoint/$\{AccessPointName\}  |  | 
|   [ bucket ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html)  |  arn:$\{Partition\}:s3:::$\{BucketName\}  |  | 
|   [ object ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingObjects.html)  |  arn:$\{Partition\}:s3:::$\{BucketName\}/$\{ObjectName\}  |  | 
|   [ job ](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops-managing-jobs.html)  |  arn:$\{Partition\}:s3:$\{Region\}:$\{Account\}:job/$\{JobId\}  |  | 

## Condition keys for Amazon S3<a name="amazons3-policy-keys"></a>

Amazon S3 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the tags that are passed in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on the tags associated with the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the tag keys that are passed in the request | String | 
|   [ s3:AccessPointNetworkOrigin ](https://docs.aws.amazon.com/AmazonS3/latest/dev/creating-access-points.html#access-points-policies)  | Filters access by the network origin \(Internet or VPC\) | String | 
|   [ s3:DataAccessPointAccount ](https://docs.aws.amazon.com/AmazonS3/latest/dev/creating-access-points.html#access-points-policies)  | Filters access by the AWS Account ID that owns the access point | String | 
|   s3:DataAccessPointArn  | Filters access by an access point Amazon Resource Name \(ARN\) | String | 
|   [ s3:ExistingJobOperation ](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops-job-tags-examples.html)  | Filters access to updating the job priority by operation | String | 
|   [ s3:ExistingJobPriority ](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops-job-tags-examples.html)  | Filters access to cancelling existing jobs by priority range | Numeric | 
|   [ s3:ExistingObjectTag/<key> ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  | Requires that an existing object tag has a specific tag key and value\. | String | 
|   [ s3:JobSuspendedCause ](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops-job-tags-examples.html)  | Filters access to cancelling suspended jobs by a specific job suspended cause \(for example, AWAITING\_CONFIRMATION\) | String | 
|   [ s3:LocationConstraint ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#condition-key-bucket-ops-1)  | Filters access by a specific Region | String | 
|   [ s3:RequestJobOperation ](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops-job-tags-examples.html)  | Filters access to creating jobs by operation | String | 
|   [ s3:RequestJobPriority ](https://docs.aws.amazon.com/AmazonS3/latest/dev/batch-ops-job-tags-examples.html)  | Filters access to creating new jobs by priority range | Numeric | 
|   [ s3:RequestObjectTag/<key> ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  | Restricts the tag keys and values allowed on objects | String | 
|   [ s3:RequestObjectTagKeys ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  | Restricts the tag keys allowed on objects | String | 
|   [ s3:VersionId ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#getobjectversion-limit-access-to-specific-version-3)  | Filters access by a specific object version | String | 
|   [ s3:authType ](https://docs.aws.amazon.com/AmazonS3/latest/API/bucket-policy-s3-sigv4-conditions.html)  | Restricts incoming requests to a specific authentication method | String | 
|   [ s3:delimiter ](https://docs.aws.amazon.com/AmazonS3/latest/dev/walkthrough1.html)  | Requires the delimiter parameter | String | 
|   [ s3:locationconstraint ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#condition-key-bucket-ops-1)  | Filters access by a specific Region | String | 
|   [ s3:max\-keys ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#example-numeric-condition-operators)  | Limits the maximum number of keys returned in a ListBucket request | Numeric | 
|   [ s3:object\-lock\-legal\-hold ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html#object-lock-legal-holds)  | Enables enforcement of the specified object legal hold status | String | 
|   s3:object\-lock\-mode  | Enables enforcement of the specified object retention mode \(COMPLIANCE or GOVERNANCE\) | String | 
|   [ s3:object\-lock\-remaining\-retention\-days ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-managing.html#object-lock-managing-retention-limits)  | Enables enforcement of an object relative to the remaining retention days | String | 
|   [ s3:object\-lock\-retain\-until\-date ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html#object-lock-retention-periods)  | Enables enforcement of a specific retain\-until\-date | String | 
|   [ s3:prefix ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#condition-key-bucket-ops-2)  | Filters access by key name prefix | String | 
|   [ s3:signatureAge ](https://docs.aws.amazon.com/AmazonS3/latest/API/bucket-policy-s3-sigv4-conditions.html)  | Identifies the length of time, in milliseconds, that a signature is valid in an authenticated request | Numeric | 
|   [ s3:signatureversion ](https://docs.aws.amazon.com/AmazonS3/latest/API/bucket-policy-s3-sigv4-conditions.html)  | Identifies the version of AWS Signature that is supported for authenticated requests | String | 
|   [ s3:versionid ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#getobjectversion-limit-access-to-specific-version-3)  | Filters access by a specific object version | String | 
|   [ s3:x\-amz\-acl ](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#permissions)  | Requires the x\-amz\-acl header with a specific canned ACL in a request | String | 
|   [ s3:x\-amz\-content\-sha256 ](https://docs.aws.amazon.com/AmazonS3/latest/API/bucket-policy-s3-sigv4-conditions.html)  | Disallows unsigned content in your bucket | String | 
|   [ s3:x\-amz\-copy\-source ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#putobject-limit-copy-source-3)  | Restricts the copy source to a specific bucket, prefix, or object | String | 
|   [ s3:x\-amz\-grant\-full\-control ](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#permissions)  | Requires the x\-amz\-grant\-full\-control \(full control\) header in a request | String | 
|   [ s3:x\-amz\-grant\-read ](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#permissions)  | Requires the x\-amz\-grant\-read \(read access\) header in a request | String | 
|   [ s3:x\-amz\-grant\-read\-acp ](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#permissions)  | Requires the x\-amz\-grant\-read\-acp \(read permissions for the ACL\) header in a request | String | 
|   [ s3:x\-amz\-grant\-write ](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#permissions)  | Requires the x\-amz\-grant\-write \(write access\) header in a request | String | 
|   [ s3:x\-amz\-grant\-write\-acp ](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#permissions)  | Requires the x\-amz\-grant\-write\-acp \(write permissions for the ACL\) header in a request | String | 
|   [ s3:x\-amz\-metadata\-directive ](https://docs.aws.amazon.com/AmazonS3/latest/API/API_CopyObject.html)  | Enables enforcement of object metadata behavior \(COPY or REPLACE\) when objects are copied | String | 
|   [ s3:x\-amz\-server\-side\-encryption ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html)  | Requires server\-side encryption | String | 
|   [ s3:x\-amz\-server\-side\-encryption\-aws\-kms\-key\-id ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingKMSEncryption.html#require-sse-kms)  | Requires a specific AWS KMS customer managed CMK for server\-side encryption | String | 
|   [ s3:x\-amz\-storage\-class ](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html#sc-howtoset)  | Filters access by storage class | String | 
|   [ s3:x\-amz\-website\-redirect\-location ](https://docs.aws.amazon.com/AmazonS3/latest/dev/how-to-page-redirect.html#page-redirect-using-rest-api)  | Filters access by a specific website redirect location for buckets that are configured as static websites | String | 