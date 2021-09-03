# Previewing access with Access Analyzer APIs<a name="access-analyzer-preview-access-apis"></a>

You can use [Access Analyzer APIs](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/Welcome.html) to preview public and cross\-account access for your Amazon S3 buckets, AWS KMS keys, IAM roles, Amazon SQS queues and Secrets Manager secrets\. You can preview access by providing proposed permissions for an existing resource you own or a new resource you want to deploy\.

To preview external access to your resource, you must have an active account analyzer for the account and region of the resource\. You must also have the permissions required to use Access Analyzer and preview access\. For more information on enabling Access Analyzer and permissions required, see [Enabling Access Analyzer](access-analyzer-getting-started.md#access-analyzer-enabling)\. 

To preview access for a resource, you can use the `CreateAccessPreview` operation and provide the analyzer ARN and the access control configuration for the resource\. The service returns the unique ID for the access preview, which you can use to check the status of the access preview with the `GetAccessPreview` operation\. When the status is `Completed`, you can use the `ListAccessPreviewFindings` operation to retrieve the findings generated for the access preview\. The `GetAccessPreview` and `ListAccessPreviewFindings` operations will retrieve access previews and findings created within about 24 hours\.

Each finding retrieved contains [finding details](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-findings-view.html) describing the access\. A preview status of the finding describing whether the finding would be `Active`, `Archived`, or `Resolved` after permissions deployment, and a `changeType`\. The `changeType` provides context on how the access preview finding compares to existing access identified in Access Analyzer:
+ **New** – the finding is for newly introduced access\.
+ **Unchanged** – the preview finding is an existing finding that would remain unchanged\.
+ **Changed** – the preview finding is an existing finding with a change in status\.

The `status` and the `changeType` help you understand how the resource configuration would change existing resource access\. If the `changeType` is `Unchanged` or Changed, the finding will also contain the existing ID and status of the finding in Access Analyzer\. For example, a `Changed` finding with preview status `Resolved` and existing status `Active` indicates the existing `Active` finding for the resource would become `Resolved` as a result of the proposed permissions change\.

You can use the `ListAccessPreviews` operation to retrieve a list of access previews for the specified analyzer\. This operation will retrieve information on access preview created within about one hour\.

In general, if the access preview is for an existing resource and you leave a configuration option unspecified, the access preview will use the existing resource configuration by default\. If the access preview is for a new resource and you leave a configuration option unspecified, the access preview will use the default value depending on the resource type\. For configuration cases for each resource type, see below\.

## Preview access to your Amazon S3 bucket<a name="access-analyzer-preview-access-s3-bucket"></a>

To create an access preview for a new Amazon S3 bucket or an existing Amazon S3 bucket that you own, you can propose a bucket configuration by specifying the Amazon S3 bucket policy, bucket ACLs, bucket BPA settings, and Amazon S3 access points attached to the bucket\.

**Note**  
Before attempting to create an access preview for a new bucket, we recommend you call the Amazon S3 [HeadBucket](https://docs.aws.amazon.com/AmazonS3/latest/API/API_HeadBucket.html) operation to check whether the named bucket already exists\. This operation is useful to determine if a bucket exists and you have permission to access it\.

**Bucket policy** – If the configuration is for an existing Amazon S3 bucket and you do not specify the Amazon S3 bucket policy, the access preview uses the existing policy attached to the bucket\. If the access preview is for a new resource and you do not specify the Amazon S3 bucket policy, the access preview assumes a bucket without a policy\. To propose deletion of an existing bucket policy, you can specify an empty string\. For more information about supported bucket policy limits, see [Bucket policy examples](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html)\.

**Bucket ACL grants** – You can propose up to 100 ACL grants per bucket\. If the proposed grant configuration is for an existing bucket, the access preview uses the proposed list of grant configurations in place of the existing grants\. Otherwise, the access preview uses the existing grants for the bucket\.

**Bucket access points** – The analysis supports up to 100 access points per bucket, including up to ten new access points you can propose per bucket\. If the proposed Amazon S3 access point configuration is for an existing bucket, the access preview uses the proposed access point configuration in place of the existing access points\. To propose an access point without a policy, you can provide an empty string as the access point policy\. For more information about access point policy limits, see [Access points restrictions and limitations](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-points-restrictions-limitations.html)\.

**Block public access configuration** – If the proposed configuration is for an existing Amazon S3 bucket and the configuration is not specified, the access preview uses the existing setting\. If the proposed configuration is for a new bucket and the bucket BPA configuration is not specified, the access preview uses `false`\. If the proposed configuration is for a new access point and the access point BPA configuration is not specified, the access preview uses `true`\.

## Preview access to your AWS KMS key<a name="access-analyzer-preview-access-kms-key"></a>

To create an access preview for a new AWS KMS key or an existing AWS KMS key that you own, you can propose a AWS KMS key configuration by specifying the key policy and the AWS KMS grant configuration\.

**AWS KMS key policy** – If the configuration is for an existing key and you do not specify the key policy, the access preview uses the existing policy for the key\. If the access preview is for a new resource and you do not specify the key policy, then the access preview uses the default key policy\. The proposed key policy cannot be an empty string\.

**AWS KMS grants** – The analysis supports up to 100 KMS grants per configuration\*\.\* If the proposed grant configuration is for an existing key, the access preview uses the proposed list of grant configurations in place of the existing grants\. Otherwise, the access preview uses the existing grants for the key\.

## Preview access to your IAM role<a name="access-analyzer-preview-iam-role"></a>

To create an access preview for a new IAM role or an existing IAM role that you own, you can propose an IAM role configuration by specifying the trust policy\.

**Role trust policy** – If the configuration is for a new IAM role, you must specify the trust policy\. If the configuration is for an existing IAM role that you own and you do not propose the trust policy, the access preview uses the existing trust policy for the role\. The proposed trust policy cannot be an empty string\.

## Preview access to your Amazon SQS queue<a name="access-analyzer-preview-sqs-queue"></a>

To create an access preview for a new Amazon SQS queue or an existing Amazon SQS queue that you own, you can propose an Amazon SQS queue configuration by specifying the Amazon SQS policy for the queue\. 

**Amazon SQS queue policy** – If the configuration is for an existing Amazon SQS queue and you do not specify the Amazon SQS policy, the access preview uses the existing Amazon SQS policy for the queue\. If the access preview is for a new resource and you do not specify the policy, the access preview assumes an Amazon SQS queue without a policy\. To propose deletion of an existing Amazon SQS queue policy, you can specify an empty string for the Amazon SQS policy\.

## Preview access to your Secrets Manager secret<a name="access-analyzer-preview-secrets-manager-secret"></a>

To create an access preview for a new Secrets Manager secret or an existing Secrets Manager secret that you own, you can propose a Secrets Manager secret configuration by specifying the secret policy and optional AWS KMS encryption key\.

**Secret policy** – If the configuration is for an existing secret and you do not specify the secret policy, the access preview uses the existing policy for the secret\. If the access preview is for a new resource and you do not specify the policy, the access preview assumes a secret without a policy\. To propose deletion of an existing policy, you can specify an empty string\.

**AWS KMS encryption key** – If the proposed configuration is for a new secret and you do not specify the AWS KMS key ID, the access preview uses the default KMS key of the AWS account\. If you specify an empty string for the AWS KMS key ID, the access preview uses the default KMS key of the AWS account\.