# Actions, Resources, and Condition Keys for Amazon Glacier<a name="list_amazonglacier"></a>

Amazon Glacier \(service prefix: `glacier`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/amazonglacier/latest/dev/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/amazonglacier/latest/dev/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/amazonglacier/latest/dev/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Glacier](#amazonglacier-actions-as-permissions)
+ [Resources Defined by Glacier](#amazonglacier-resources-for-iam-policies)
+ [Condition Keys for Amazon Glacier](#amazonglacier-policy-keys)

## Actions Defined by Amazon Glacier<a name="amazonglacier-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [AbortMultipartUpload](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-abort-upload.html) | Aborts a multipart upload identified by the upload ID |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [AbortVaultLock](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-AbortVaultLock.html) | Aborts the vault locking process if the vault lock is not in the Locked state |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [AddTagsToVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-AddTagsToVault.html) | Adds the specified tags to a vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [CompleteMultipartUpload](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-complete-upload.html) | Completes a multipart upload process |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [CompleteVaultLock](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-CompleteVaultLock.html) | Completes the vault locking process |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [CreateVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-put.html) | Creates a new vault with the specified name |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [DeleteArchive](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-archive-delete.html) | Deletes an archive from a vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [DeleteVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-delete.html) | Deletes a vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [DeleteVaultAccessPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-DeleteVaultAccessPolicy.html) | Deletes the access policy associated with the specified vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [DeleteVaultNotifications](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-notifications-delete.html) | Deletes the notification configuration set for a vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [DescribeJob](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-describe-job-get.html) | Returns information about a job you previously initiated |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [DescribeVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-get..html) | Returns information about a vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [GetDataRetrievalPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-GetDataRetrievalPolicy.html) | Returns the current data retrieval policy for the account and region specified in the GET request |   |  |  |  | 
| [GetJobOutput](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-job-output-get.html) | Downloads the output of the job you initiated |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [GetVaultAccessPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-GetVaultAccessPolicy.html) | Retrieves the access\-policy subresource set on the vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [GetVaultLock](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-GetVaultLock.html) | Retrieves attributes from the lock\-policy subresource set on the specified vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [GetVaultNotifications](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-notifications-get.html) | Retrieves the notification\-configuration subresource set on the vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [InitiateJob](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-initiate-job-post.html) | Initiates a job of the specified type |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [InitiateMultipartUpload](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-initiate-upload.html) | Initiates a multipart upload |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [InitiateVaultLock](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-InitiateVaultLock.html) | Initiates the vault locking process |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [ListJobs](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-jobs-get.html) | Lists jobs for a vault that are in\-progress and jobs that have recently finished |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [ListMultipartUploads](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-list-uploads.html) | Lists in\-progress multipart uploads for the specified vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [ListParts](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-multipart-list-parts.html) | Lists the parts of an archive that have been uploaded in a specific multipart upload |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [ListProvisionedCapacity](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-ListProvisionedCapacity.html) | This operation lists the provisioned capacity for the specified AWS account\. |   |  |  |  | 
| [ListTagsForVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-ListTagsForVault.html) | Lists all the tags attached to a vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [ListVaults](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vaults-get.html) | Lists all vaults |   |  |  |  | 
| [PurchaseProvisionedCapacity](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-PurchaseProvisionedCapacity.html) | This operation purchases a provisioned capacity unit for an AWS account\. |   |  |  |  | 
| [RemoveTagsFromVault](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-RemoveTagsFromVault.html) | Removes one or more tags from the set of tags attached to a vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [SetDataRetrievalPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-SetDataRetrievalPolicy.html) | Sets and then enacts a data retrieval policy in the region specified in the PUT request |   |  |  |  | 
| [SetVaultAccessPolicy](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-SetVaultAccessPolicy.html) | Configures an access policy for a vault and will overwrite an existing policy |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [SetVaultNotifications](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-vault-notifications-put.html) | Configures vault notifications |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [UploadArchive](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-archive-post.html) | Adds an archive to a vault |   | [vault\*](#amazonglacier-vault)  |  |  | 
| [UploadMultipartPart](http://docs.aws.amazon.com/amazonglacier/latest/dev/api-upload-part.html) | Uploads a part of an archive |   | [vault\*](#amazonglacier-vault)  |  |  | 

## Resources Defined by Glacier<a name="amazonglacier-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonglacier-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [vault](http://docs.aws.amazon.com/amazonglacier/latest/dev/working-with-vaults.html) | arn:$\{Partition\}:glacier:$\{Region\}:$\{Account\}:vaults/$\{VaultName\} |  | 

## Condition Keys for Amazon Glacier<a name="amazonglacier-policy-keys"></a>

Amazon Glacier defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [glacier:ArchiveAgeInDays](http://docs.aws.amazon.com/amazonglacier/latest/dev/access-control-overview.html#specifying-conditions) | How long an archive has been stored in the vault, in days\. | String | 
| [glacier:ResourceTag/](http://docs.aws.amazon.com/amazonglacier/latest/dev/access-control-overview.html#specifying-conditions) | A customer\-defined tag\. | String | 