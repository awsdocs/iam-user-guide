# Actions, Resources, and Condition Keys for AWS Backup storage<a name="list_awsbackupstorage"></a>

AWS Backup storage \(service prefix: `backup-storage`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/aws-backup/latest/devguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/aws-backup/latest/devguide/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/aws-backup/latest/devguide/security-considerations.html#authentication) permission policies\.

**Topics**
+ [Actions Defined by AWS Backup storage](#awsbackupstorage-actions-as-permissions)
+ [Resource Types Defined by AWS Backup storage](#awsbackupstorage-resources-for-iam-policies)
+ [Condition Keys for AWS Backup storage](#awsbackupstorage-policy-keys)

## Actions Defined by AWS Backup storage<a name="awsbackupstorage-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ MountCapsule ](https://docs.aws.amazon.com/aws-backup/latest/devguide/API_CreateBackupVault.html) \[permission only\] | Associates a KMS key to a backup vault | Write |  |  |  | 

## Resource Types Defined by AWS Backup storage<a name="awsbackupstorage-resources-for-iam-policies"></a>

AWS Backup storage does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Backup storage, specify `“Resource”: “*”` in your policy\.

## Condition Keys for AWS Backup storage<a name="awsbackupstorage-policy-keys"></a>

Backup Storage has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.