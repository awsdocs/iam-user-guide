# Actions, Resources, and Condition Keys for AWS Backup<a name="list_awsbackup"></a>

AWS Backup \(service prefix: `backup`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/aws-backup/latest/devguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/aws-backup/latest/devguide/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/aws-backup/latest/devguide/security-considerations.html#authentication) permission policies\.

**Topics**
+ [Actions Defined by AWS Backup](#awsbackup-actions-as-permissions)
+ [Resources Defined by AWS Backup](#awsbackup-resources-for-iam-policies)
+ [Condition Keys for AWS Backup](#awsbackup-policy-keys)

## Actions Defined by AWS Backup<a name="awsbackup-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateBackupPlan ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_CreateBackupPlan.html)  | Creates a new backup plan | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ CreateBackupSelection ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_CreateBackupSelection.html)  | Creates a new resource assignment in a backup plan\. | Write |  |  |  | 
|   [ CreateBackupVault ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_CreateBackupVault.html)  | Creates a new backup vault\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ DeleteBackupPlan ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DeleteBackupPlan.html)  | Deletes a backup plan\. | Write |  |  |  | 
|   [ DeleteBackupSelection ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DeleteBackupSelection.html)  | Deletes a resource assignment from a backup plan\. | Write |  |  |  | 
|   [ DeleteBackupVault ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DeleteBackupVault.html)  | Deletes a backup vault\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ DeleteBackupVaultAccessPolicy ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DeleteBackupVaultAccessPolicy.html)  | Deletes backup vault access policy\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ DeleteBackupVaultNotifications ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DeleteBackupVaultNotifications.html)  | Remove notifications from backup vault\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ DeleteRecoveryPoint ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DeleteRecoveryPoint.html)  | Deletes a recovery point from a backup vault\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ DescribeBackupJob ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DescribeBackupJob.html)  | Describes a backup job | List |  |  |  | 
|   [ DescribeBackupVault ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DescribeBackupVault.html)  | Creates a new backup vault with the specified name\. | Read |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ DescribeProtectedResource ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DescribeProtectedResource.html)  | Describes a protected resource\. | Read |  |  |  | 
|   [ DescribeRecoveryPoint ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DescribeRecoveryPoint.html)  | Describes a recovery point\. | Read |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ DescribeRestoreJob ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_DescribeRestoreJob.html)  | Describes a restore job\. | Read |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ ExportBackupPlanTemplate ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ExportBackupPlanTemplate.html)  | Exports a backup plan as a JSON\. | Read |  |  |  | 
|   [ GetBackupPlan ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_GetBackupPlan.html)  | Gets a backup plan\. | Read |  |  |  | 
|   [ GetBackupPlanFromJSON ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_GetBackupPlanFromJSON.html)  | Transforms a JSON to a backup plan\. | Read |  |  |  | 
|   [ GetBackupPlanFromTemplate ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_GetBackupPlanFromTemplate.html)  | Transforms a template to a backup plan\. | Read |  |  |  | 
|   [ GetBackupSelection ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_GetBackupSelection.html)  | Gets a backup plan resource assignment\. | Read |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ GetBackupVaultAccessPolicy ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_GetBackupVaultAccessPolicy.html)  | Gets backup vault access policy\. | Read |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ GetBackupVaultNotifications ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_GetBackupVaultNotifications.html)  | Gets backup vault notifications\. | Read |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ GetRecoveryPointRestoreMetadata ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_GetRecoveryPointRestoreMetadata.html)  | Gets recovery point restore metadata\. | Read |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ GetSupportedResourceTypes ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_GetSupportedResourceTypes.html)  | Gets supported resource types\. | Read |  |  |  | 
|   [ ListBackupJobs ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListBackupJobs.html)  | Lists backup jobs\. | List |  |  |  | 
|   [ ListBackupPlanTemplates ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListBackupPlanTemplates.html)  | Lists backup plan templates provided by AWS Backup\. | List |  |  |  | 
|   [ ListBackupPlanVersions ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListBackupPlanVersions.html)  | Lists backup plan versions\. | List |  |  |  | 
|   [ ListBackupPlans ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListBackupPlans.html)  | Lists backup plans\. | List |  |  |  | 
|   [ ListBackupSelections ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListBackupSelections.html)  | Lists resource assignments for a specific backup plan\. | List |  |  |  | 
|   [ ListBackupVaults ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListBackupVaults.html)  | Lists backup vaults\. | List |  |  |  | 
|   [ ListProtectedResources ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListProtectedResources.html)  | Lists protected resources by AWS Backup\. | List |  |  |  | 
|   [ ListRecoveryPointsByBackupVault ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListRecoveryPointsByBackupVault.html)  | Lists recovery points inside a backup vault\. | List |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ ListRecoveryPointsByResource ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListRecoveryPointsByResource.html)  | Lists recovery points for a resource\. | List |  |  |  | 
|   [ ListRestoreJobs ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListRestoreJobs.html)  | Lists restore jobs\. | List |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ ListTags ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_ListTags.html)  | Lists tags for a resource\. | List |  |  |  | 
|   [ PutBackupVaultAccessPolicy ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_PutBackupVaultAccessPolicy.html)  | Adds an access policy to the backup vault\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ PutBackupVaultNotifications ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_PutBackupVaultNotifications.html)  | Adds an SNS topic to the backup vault\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ StartBackupJob ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_StartBackupJob.html)  | Starts a new backup job\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ StartRestoreJob ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_StartRestoreJob.html)  | Starts a new restore job\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ StopBackupJob ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_StopBackupJob.html)  | Stops a backup job\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_TagResource.html)  | Tags a resource\. | Write |  |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_UntagResource.html)  | Untags a resource\. | Write |  |  |  | 
|   [ UpdateBackupPlan ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_UpdateBackupPlan.html)  | Updates a backup plan\. | Write |  |  |  | 
|   [ UpdateRecoveryPointLifecycle ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_UpdateRecoveryPointLifecycle.html)  | Updates the lifecycle of the recovery point\. | Write |   [ backupVault\* ](#awsbackup-backupVault)   |  |  | 

## Resources Defined by AWS Backup<a name="awsbackup-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsbackup-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ backupVault ](https://docs.aws.amazon.com/aws-backup/latest/devguide/vaults.html)  |  arn:$\{Partition\}:backup::$\{Account\}:backup\-vault:$\{BackupVaultName\}  |  | 

## Condition Keys for AWS Backup<a name="awsbackup-policy-keys"></a>

Backup has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.