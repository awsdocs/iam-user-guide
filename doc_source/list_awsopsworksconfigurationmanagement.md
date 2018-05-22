# Actions, Resources, and Condition Keys for AWS OpsWorks Configuration Management<a name="list_awsopsworksconfigurationmanagement"></a>

AWS OpsWorks Configuration Management \(service prefix: `opsworks-cm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/opsworks/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/opsworks/latest/userguide/workingsecurity.html) permission policies\.

**Topics**
+ [Actions Defined by AWS OpsWorks Configuration Management](#awsopsworksconfigurationmanagement-actions-as-permissions)
+ [Resources Defined by OpsworksCM](#awsopsworksconfigurationmanagement-resources-for-iam-policies)
+ [Condition Keys for AWS OpsWorks Configuration Management](#awsopsworksconfigurationmanagement-policy-keys)

## Actions Defined by AWS OpsWorks Configuration Management<a name="awsopsworksconfigurationmanagement-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_AssociateNode.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_AssociateNode.html) | Associate a node to a configuration management server\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_CreateBackup.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_CreateBackup.html) | Create a backup for the specified server\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_CreateServer.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_CreateServer.html) | Create a new server\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DeleteBackup.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DeleteBackup.html) | Delete the specified backup and possibly its S3 bucket\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DeleteServer.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DeleteServer.html) | Deletes the specified server with his corresponding CF stack and possibly the S3 bucket\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeAccountAttributes.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeAccountAttributes.html) | Describe the service limits for the user's account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeBackups.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeBackups.html) | Describe a single backup, all backups of a specified server or all backups of the user's account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeEvents.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeEvents.html) | Describe all events of the specified server\. | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeNodeAssociationStatus.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeNodeAssociationStatus.html) | Describe the association status for the specified node token and the specified server\. | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeServers.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeServers.html) | Describes the specified server or all servers of the user's account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DisassociateNode.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DisassociateNode.html) | Disassociates a specified node from a server\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_RestoreServer.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_RestoreServer.html) | Applies a backup to specified server\. Possibly swaps out the ec2\-instance if specified\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_StartMaintenance.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_StartMaintenance.html) | Start the server maintenance immediately\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_UpdateServer.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_UpdateServer.html) | Update general server settings\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_UpdateServerEngineAttributes.html](http://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_UpdateServerEngineAttributes.html) | Update server settings specific to the configuration management type\. | Write |  |  |  | 

## Resources Defined by OpsworksCM<a name="awsopsworksconfigurationmanagement-resources-for-iam-policies"></a>

OpsworksCM has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS OpsWorks Configuration Management<a name="awsopsworksconfigurationmanagement-policy-keys"></a>

OpsworksCM has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.