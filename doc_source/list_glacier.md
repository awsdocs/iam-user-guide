# Actions and Condition Context Keys for Amazon Glacier<a name="list_glacier"></a>

Amazon Glacier \(service prefix: glacier\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon Glacier**

For information about using the following Amazon Glacier API actions in an IAM policy, see [Access Control Using AWS Identity and Access Management \(IAM\)](http://docs.aws.amazon.com/amazonglacier/latest/dev/using-iam-with-amazon-glacier.html) in the *Amazon Glacier Developer Guide*\.

+ `[glacier:PurchaseProvisionedCapacity]()`

+ `[glacier:DescribeJob](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-describe-job-get.html)`

+ `[glacier:GetJobOutput](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-job-output-get.html)`

+ `[glacier:CreateVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-put.html)`

+ `[glacier:GetDataRetrievalPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-GetDataRetrievalPolicy.html)`

+ `[glacier:DeleteVaultAccessPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-DeleteVaultAccessPolicy.html)`

+ `[glacier:GetVaultLock](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-GetVaultLock.html)`

+ `[glacier:DescribeVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-get.html)`

+ `[glacier:SetVaultNotifications](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-notifications-put.html)`

+ `[glacier:AddTagsToVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-AddTagsToVault.html)`

+ `[glacier:UploadMultipartPart](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-upload-part.html)`

+ `[glacier:InitiateMultipartUpload](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-initiate-upload.html)`

+ `[glacier:AbortMultipartUpload](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-abort-upload.html)`

+ `[glacier:ListProvisionedCapacity]()`

+ `[glacier:SetVaultAccessPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-SetVaultAccessPolicy.html)`

+ `[glacier:ListMultipartUploads](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-list-uploads.html)`

+ `[glacier:InitiateVaultLock](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-InitiateVaultLock.html)`

+ `[glacier:DeleteVaultNotifications](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-notifications-delete.html)`

+ `[glacier:CompleteVaultLock](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-CompleteVaultLock.html)`

+ `[glacier:ListTagsForVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-ListTagsForVault.html)`

+ `[glacier:InitiateJob](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-initiate-job-post.html)`

+ `[glacier:ListParts](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-list-parts.html)`

+ `[glacier:DeleteVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-delete.html)`

+ `[glacier:DeleteArchive](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-archive-delete.html)`

+ `[glacier:GetVaultNotifications](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-notifications-get.html)`

+ `[glacier:GetVaultAccessPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-GetVaultAccessPolicy.html)`

+ `[glacier:RemoveTagsFromVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-RemoveTagsFromVault.html)`

+ `[glacier:CompleteMultipartUpload](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-complete-upload.html)`

+ `[glacier:SetDataRetrievalPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-SetDataRetrievalPolicy.html)`

+ `[glacier:UploadArchive](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-archive-post.html)`

+ `[glacier:AbortVaultLock](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-AbortVaultLock.html)`

+ `[glacier:ListVaults](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vaults-get.html)`

+ `[glacier:ListJobs](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-jobs-get.html)`

**Condition context keys for Amazon Glacier**

Amazon Glacier has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `glacier:ArchiveAgeInDays`

+ `glacier:ResourceTag/`