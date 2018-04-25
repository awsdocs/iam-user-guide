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

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [AbortMultipartUpload](http://docs.aws.amazon.com/AmazonS3/latest/API/mpUploadAbort.html) | Aborts a multipart upload\. |   | [object\*](#amazons3-object)  |  |  | 
| [CreateBucket](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUT.html) | Creates a new bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [DeleteBucket](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketDELETE.html) | Deletes the bucket named in the URI |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [DeleteBucketPolicy](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketDELETEpolicy.html) | Delete the policy on a specified bucket |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [DeleteBucketWebsite](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketDELETEwebsite.html) | Removes the website configuration for a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [DeleteObject](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectDELETE.html) | Removes the null version \(if there is one\) of an object and inserts a delete marker, which becomes the current version of the object\. |   | [object\*](#amazons3-object)  |  |  | 
| [DeleteObjectTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectDELETEtagging.html) | This implementation of the DELETE operation uses the tagging subresource to remove the entire tag set from the specified object\. |   | [object\*](#amazons3-object)  |  |  | 
| [DeleteObjectVersion](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectDELETE.html) | To remove a specific version of a object, you must be the bucket owner and you must use the versionId subresource\. |   | [object\*](#amazons3-object)  |  |  | 
| [DeleteObjectVersionTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectDELETEtagging.html) | DELETE Object tagging \(for a Specific Version of the Object\) |   | [object\*](#amazons3-object)  |  |  | 
| [GetAccelerateConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETaccelerate.html) | This implementation of the GET operation uses the accelerate subresource to return the Transfer Acceleration state of a bucket, which is either Enabled or Suspended\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetAnalyticsConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETAnalyticsConfig.html) | This implementation of the GET operation returns an analytics configuration \(identified by the analytics configuration ID\) from the bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETacl.html) | Return the access control list \(ACL\) of a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketCORS](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETcors.html) | Returns the cors configuration information set for the bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketLocation](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETlocation.html) | Return a bucket's region\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketLogging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETlogging.html) | Return the logging status of a bucket and the permissions users have to view and modify that status\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketNotification](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETnotification.html) | Return the notification configuration of a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketPolicy](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETpolicy.html) | Return the policy of a specified bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketRequestPayment](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTrequestPaymentGET.html) | Return the request payment configuration of a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETtagging.html) | Return the tag set associated with the bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketVersioning](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETversioningStatus.html) | Return the versioning state of a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetBucketWebsite](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETwebsite.html) | Returns the website configuration associated with a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetInventoryConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETInventoryConfig.html) | This implementation of the GET operation returns an inventory configuration \(identified by the inventory configuration ID\) from the bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| GetIpConfiguration |  |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetLifecycleConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETlifecycle.html) | Returns the lifecycle configuration information set on the bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetMetricsConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETMetricConfiguration.html) | Gets a metrics configuration for the CloudWatch request metrics \(specified by the metrics configuration ID\) from the bucket\. Note that this doesn't include the daily storage metrics\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [GetObject](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGET.html) | Retrieves objects from Amazon S3\. |   | [object\*](#amazons3-object)  |  |  | 
| [GetObjectAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETacl.html) | Return the access control list \(ACL\) of an object\. |   | [object\*](#amazons3-object)  |  |  | 
| [GetObjectTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETtagging.html) | This implementation of the GET operation returns the tags associated with an object\. You send the GET request against the tagging subresource associated with the object\. |   | [object\*](#amazons3-object)  |  |  | 
| [GetObjectTorrent](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETtorrent.html) | return torrent files from a bucket\. |   | [object\*](#amazons3-object)  |  |  | 
| [GetObjectVersion](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGET.html) | To return a different version, use the versionId subresource\. |   | [object\*](#amazons3-object)  |  |  | 
| [GetObjectVersionAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/objectGetAclVersions.html) | To return ACL information about a different version, use the versionId subresource\. |   | [object\*](#amazons3-object)  |  |  | 
| GetObjectVersionForReplication |  |   | [object\*](#amazons3-object)  |  |  | 
| [GetObjectVersionTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETtagging.html) | GET Object tagging \(for a Specific Version of the Object\) |   | [object\*](#amazons3-object)  |  |  | 
| [GetObjectVersionTorrent](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETtorrent.html) | To return Torrent files about a different version, use the versionId subresource\. |   | [object\*](#amazons3-object)  |  |  | 
| [GetReplicationConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETreplication.html) | Returns the replication configuration information set on the bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [ListAllMyBuckets](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTServiceGET.html) | Returns a list of all buckets owned by the authenticated sender of the request\. |   |  |  |  | 
| [ListBucket](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGET.html) | Returns some or all \(up to 1000\) of the objects in a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| ListBucketByTags |  |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [ListBucketMultipartUploads](http://docs.aws.amazon.com/AmazonS3/latest/API/mpUploadListMPUpload.html) | Lists in\-progress multipart uploads\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [ListBucketVersions](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETVersion.html) | Use the versions subresource to list metadata about all of the versions of objects in a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [ListMultipartUploadParts](http://docs.aws.amazon.com/AmazonS3/latest/API/mpUploadListParts.html) | Lists the parts that have been uploaded for a specific multipart upload\. |   | [object\*](#amazons3-object)  |  |  | 
| ObjectOwnerOverrideToBucketOwner |  |   | [object\*](#amazons3-object)  |  |  | 
| [PutAccelerateConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTaccelerate.html) | This implementation of the PUT operation uses the accelerate subresource to set the Transfer Acceleration state of an existing bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutAnalyticsConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTAnalyticsConfig.html) | This implementation of the PUT operation adds an analytics configuration \(identified by the analytics ID\) to the bucket\. You can have up to 1,000 analytics configurations per bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTacl.html) | Set the permissions on an existing bucket using access control lists \(ACL\)\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketCORS](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTcors.html) | Sets the cors configuration for your bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketLogging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTlogging.html) | Set the logging parameters for a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketNotification](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTnotification.html) | Enables you to receive notifications when certain events happen in your bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketPolicy](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTpolicy.html) | Add to or replace a policy on a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketRequestPayment](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTrequestPaymentPUT.html) | Set the request payment configuration of a bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTtagging.html) | Add a set of tags to an existing bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketVersioning](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTVersioningStatus.html) | Set the versioning state of an existing bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutBucketWebsite](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTwebsite.html) | Sets the configuration of the website that is specified in the website subresource\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutInventoryConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTInventoryConfig.html) | This implementation of the PUT operation adds an inventory configuration \(identified by the inventory ID\) to the bucket\. You can have up to 1,000 inventory configurations per bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| PutIpConfiguration |  |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutLifecycleConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTlifecycle.html) | Creates a new lifecycle configuration for the bucket or replaces an existing lifecycle configuration\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutMetricsConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTMetricConfiguration.html) | Sets or updates a metrics configuration for the CloudWatch request metrics \(specified by the metrics configuration ID\) from the bucket\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| [PutObject](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPUT.html) | Adds an object to a bucket\. |   | [object\*](#amazons3-object)  |  |  | 
| [PutObjectAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPUTacl.html) | Set the access control list \(ACL\) permissions for an object that already exists in a bucket\. |   | [object\*](#amazons3-object)  |  |  | 
| [PutObjectTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPUTtagging.html) | This implementation of the PUT operation uses the tagging subresource to add a set of tags to an existing object\. |   | [object\*](#amazons3-object)  |  |  | 
| [PutObjectVersionAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPUTacl.html#objectPutAclVersions) | The ACL of an object is set at the object version level\. |   | [object\*](#amazons3-object)  |  |  | 
| [PutObjectVersionTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPUTtagging.html) | PUT Object tagging \(for a Specific Version of the Object\) |   | [object\*](#amazons3-object)  |  |  | 
| [PutReplicationConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTreplication.html) | In a versioning\-enabled bucket, this operation creates a new replication configuration \(or replaces an existing one, if present\)\. |   | [bucket\*](#amazons3-bucket)  |  |  | 
| ReplicateDelete |  |   | [object\*](#amazons3-object)  |  |  | 
| ReplicateObject |  |   | [object\*](#amazons3-object)  |  |  | 
| ReplicateTags |  |   | [object\*](#amazons3-object)  |  |  | 
| [RestoreObject](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPOSTrestore.html) | Restores a temporary copy of an archived object\. |   | [object\*](#amazons3-object)  |  |  | 

## Resources Defined by S3<a name="amazons3-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazons3-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [bucket](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html) | arn:$\{Partition\}:s3:::$\{BucketName\} |  | 
| [object](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingObjects.html) | arn:$\{Partition\}:s3:::$\{BucketName\}/$\{ObjectName\} |  | 

## Condition Keys for Amazon S3<a name="amazons3-policy-keys"></a>

Amazon S3 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [s3:ExistingObjectTag/<key>](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) | Enables you to verify that an existing object tag has the specific tag key and value\. | String | 
| [s3:LocationConstraint](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to restrict users to creating buckets in only a specific region\. | String | 
| [s3:RequestObjectTag/<key>](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) | Restrict the tag keys and values that you want to allow on objects\. | String | 
| [s3:RequestObjectTagKeys](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  restrict the tag keys that you want to allow on objects\. | String | 
| [s3:VersionId](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to limit the permission for the s3:PutObjectVersionTagging action to a specific object version\. | String | 
| [s3:authtype](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:delimiter](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to require the user to specify the delimiter parameter in the GET Bucket Object versions request\. | String | 
| [s3:locationconstraint](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to restrict the user to creating a bucket in only a specific region\. | String | 
| [s3:max\-keys](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to limit the number of keys Amazon S3 returns in response to the GetBucket and ListObjects requests by requiring the user to specify the max\-keys parameter\. | Numeric | 
| [s3:prefix](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#bucket-keys-in-amazon-s3-policies) | Enables you to limit the response of the GetBucket and ListObjects APIs to key names with specific prefix\. | String | 
| [s3:signatureage](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | Numeric | 
| [s3:signatureversion](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:versionid](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-acl](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to require specific access permissions when uploading an object\. | String | 
| [s3:x\-amz\-content\-sha256](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-copy\-source](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to restrict the copy source to a specific bucket, a specific folder in the bucket, or a specific object in a bucket\. | String | 
| [s3:x\-amz\-grant\-full\-control](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-grant\-read](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-grant\-read\-acp](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-grant\-write](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-grant\-write\-acp](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-metadata\-directive](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to enforce certain behavior \(COPY vs\. REPLACE\) when objects are uploaded\. | String | 
| [s3:x\-amz\-server\-side\-encryption](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) | Enables you to require the user to specify this header in the request to ensure that objects the user uploads are encrypted when they are saved\. | String | 
| [s3:x\-amz\-server\-side\-encryption\-aws\-kms\-key\-id](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-storage\-class](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 
| [s3:x\-amz\-website\-redirect\-location](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) |  | String | 