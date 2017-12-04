# Actions and Condition Context Keys for Amazon S3<a name="list_s3"></a>

Amazon S3 \(service prefix: s3\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon S3**

For information about using the following Amazon S3 API actions in an IAM policy, see [Specifying Permissions in a Policy](http://docs.aws.amazon.com/AmazonS3/latest/dev/using-with-s3-actions.html) in the *Amazon Simple Storage Service Developer Guide*\.

+ `[s3:GetBucketLocation](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETlocation.html)`

+ `[s3:GetBucketCORS](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETcors.html)`

+ `[s3:GetIpConfiguration]()`

+ `[s3:GetAnalyticsConfiguration]()`

+ `[s3:PutObject](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPUT.html)`

+ `[s3:ListMultipartUploadParts](http://docs.aws.amazon.com/AmazonS3/latest/API/mpUploadListParts.html)`

+ `[s3:DeleteBucketWebsite](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketDELETEwebsite.html)`

+ `[s3:PutBucketWebsite](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTwebsite.html)`

+ `[s3:DeleteObjectTagging]()`

+ `[s3:GetObjectVersionForReplication]()`

+ `[s3:GetBucketAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETacl.html)`

+ `[s3:PutLifecycleConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTlifecycle.html)`

+ `[s3:DeleteBucket](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketDELETE.html)`

+ `[s3:GetBucketPolicy](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETpolicy.html)`

+ `[s3:GetObject](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGET.html)`

+ `[s3:PutIpConfiguration]()`

+ `[s3:GetLifecycleConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETlifecycle.html)`

+ `[s3:DeleteObjectVersionTagging]()`

+ `[s3:PutObjectTagging]()`

+ `[s3:PutReplicationConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTreplication.html)`

+ `[s3:GetObjectTorrent](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETtorrent.html)`

+ `[s3:HeadBucket]()`

+ `[s3:GetBucketVersioning](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETversioningStatus.html)`

+ `[s3:PutAccelerateConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTaccelerate.html)`

+ `[s3:ListAllMyBuckets](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTServiceGET.html)`

+ `[s3:GetReplicationConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGetReplication.html)`

+ `[s3:DeleteObjectVersion](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectDELETE.html)`

+ `[s3:PutObjectVersionTagging]()`

+ `[s3:GetBucketNotification](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETnotification.html)`

+ `[s3:PutMetricsConfiguration]()`

+ `[s3:PutBucketRequestPayment](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTrequestPaymentPUT.html)`

+ `[s3:GetBucketLogging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETlogging.html)`

+ `[s3:GetInventoryConfiguration]()`

+ `[s3:PutBucketNotification](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTnotification.html)`

+ `[s3:GetBucketTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETtagging.html)`

+ `[s3:PutBucketVersioning](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTVersioningStatus.html)`

+ `[s3:PutBucketCORS](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTcors.html)`

+ `[s3:ListBucketByTags]()`

+ `[s3:DeleteObject](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectDELETE.html)`

+ `[s3:GetObjectVersionTorrent](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETtorrent.html)`

+ `[s3:ObjectOwnerOverrideToBucketOwner]()`

+ `[s3:ReplicateDelete](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr-how-setup.html#replication-iam-role-intro)`

+ `[s3:GetObjectVersion](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGET.html)`

+ `[s3:ListBucketVersions](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETVersion.html)`

+ `[s3:ListBucket](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGET.html)`

+ `[s3:PutBucketTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTtagging.html)`

+ `[s3:AbortMultipartUpload](http://docs.aws.amazon.com/AmazonS3/latest/API/mpUploadAbort.html)`

+ `[s3:PutBucketAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTacl.html)`

+ `[s3:GetMetricsConfiguration]()`

+ `[s3:PutBucketPolicy](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTpolicy.html)`

+ `[s3:GetBucketRequestPayment](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTrequestPaymentGET.html)`

+ `[s3:ReplicateObject](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr-how-setup.html#replication-iam-role-intro)`

+ `[s3:PutObjectVersionAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPUTacl.html#objectPutAclVersions)`

+ `[s3:GetObjectAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETacl.html)`

+ `[s3:GetBucketWebsite](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETwebsite.html)`

+ `[s3:ReplicateTags]()`

+ `[s3:ListObjects]()`

+ `[s3:PutObjectAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPUTacl.html)`

+ `[s3:PutAnalyticsConfiguration]()`

+ `[s3:ListBucketMultipartUploads](http://docs.aws.amazon.com/AmazonS3/latest/API/mpUploadListMPUpload.html)`

+ `[s3:GetObjectTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETtagging.html)`

+ `[s3:PutInventoryConfiguration]()`

+ `[s3:GetAccelerateConfiguration](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETaccelerate.html)`

+ `[s3:RestoreObject](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectPOSTrestore.html)`

+ `[s3:GetObjectVersionTagging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTObjectGETtagging.html)`

+ `[s3:DeleteBucketPolicy](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketDELETEpolicy.html)`

+ `[s3:GetObjectVersionAcl](http://docs.aws.amazon.com/AmazonS3/latest/API/objectGetAclVersions.html)`

+ `[s3:PutBucketLogging](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTlogging.html)`

+ `[s3:CreateBucket](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUT.html)`

**Condition context keys for Amazon S3**

For information about using the following Amazon S3 conditions in an IAM policy, see [Specifying Conditions in a Policy](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#object-keys-in-amazon-s3-policies) in the *Amazon Simple Storage Service Developer Guide*\.

Amazon S3 has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `s3:ExistingObjectTag/<key>`

+ `s3:LocationConstraint`

+ `s3:RequestObjectTag/<key>`

+ `s3:RequestObjectTagKeys`

+ `s3:VersionId`

+ `s3:authtype`

+ `s3:delimiter`

+ `s3:locationconstraint`

+ `s3:max-keys`

+ `s3:prefix`

+ `s3:signatureage`

+ `s3:signatureversion`

+ `s3:versionid`

+ `s3:x-amz-acl`

+ `s3:x-amz-content-sha256`

+ `s3:x-amz-copy-source`

+ `s3:x-amz-grant-full-control`

+ `s3:x-amz-grant-read`

+ `s3:x-amz-grant-read-acp`

+ `s3:x-amz-grant-write`

+ `s3:x-amz-grant-write-acp`

+ `s3:x-amz-metadata-directive`

+ `s3:x-amz-server-side-encryption`

+ `s3:x-amz-server-side-encryption-aws-kms-key-id`

+ `s3:x-amz-storage-class`

+ `s3:x-amz-website-redirect-location`