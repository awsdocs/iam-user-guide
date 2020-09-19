# Actions, resources, and condition keys for AWS OpsWorks Configuration Management<a name="list_awsopsworksconfigurationmanagement"></a>

AWS OpsWorks Configuration Management \(service prefix: `opsworks-cm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/opsworks/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/opsworks/latest/userguide/workingsecurity.html) permission policies\.

**Topics**
+ [Actions defined by AWS OpsWorks Configuration Management](#awsopsworksconfigurationmanagement-actions-as-permissions)
+ [Resource types defined by AWS OpsWorks Configuration Management](#awsopsworksconfigurationmanagement-resources-for-iam-policies)
+ [Condition keys for AWS OpsWorks Configuration Management](#awsopsworksconfigurationmanagement-policy-keys)

## Actions defined by AWS OpsWorks Configuration Management<a name="awsopsworksconfigurationmanagement-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateNode ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_AssociateNode.html)  | Associate a node to a configuration management server\. | Write |  |  |  | 
|   [ CreateBackup ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_CreateBackup.html)  | Create a backup for the specified server\. | Write |  |  |  | 
|   [ CreateServer ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_CreateServer.html)  | Create a new server\. | Write |  |  |  | 
|   [ DeleteBackup ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DeleteBackup.html)  | Delete the specified backup and possibly its S3 bucket\. | Write |  |  |  | 
|   [ DeleteServer ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DeleteServer.html)  | Deletes the specified server with his corresponding CF stack and possibly the S3 bucket\. | Write |  |  |  | 
|   [ DescribeAccountAttributes ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeAccountAttributes.html)  | Describe the service limits for the user's account\. | List |  |  |  | 
|   [ DescribeBackups ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeBackups.html)  | Describe a single backup, all backups of a specified server or all backups of the user's account\. | List |  |  |  | 
|   [ DescribeEvents ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeEvents.html)  | Describe all events of the specified server\. | List |  |  |  | 
|   [ DescribeNodeAssociationStatus ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeNodeAssociationStatus.html)  | Describe the association status for the specified node token and the specified server\. | List |  |  |  | 
|   [ DescribeServers ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DescribeServers.html)  | Describes the specified server or all servers of the user's account\. | List |  |  |  | 
|   [ DisassociateNode ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_DisassociateNode.html)  | Disassociates a specified node from a server\. | Write |  |  |  | 
|   [ RestoreServer ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_RestoreServer.html)  | Applies a backup to specified server\. Possibly swaps out the ec2\-instance if specified\. | Write |  |  |  | 
|   [ StartMaintenance ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_StartMaintenance.html)  | Start the server maintenance immediately\. | Write |  |  |  | 
|   [ UpdateServer ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_UpdateServer.html)  | Update general server settings\. | Write |  |  |  | 
|   [ UpdateServerEngineAttributes ](https://docs.aws.amazon.com/opsworks-cm/latest/APIReference/API_UpdateServerEngineAttributes.html)  | Update server settings specific to the configuration management type\. | Write |  |  |  | 

## Resource types defined by AWS OpsWorks Configuration Management<a name="awsopsworksconfigurationmanagement-resources-for-iam-policies"></a>

AWS OpsWorks Configuration Management does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS OpsWorks Configuration Management, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS OpsWorks Configuration Management<a name="awsopsworksconfigurationmanagement-policy-keys"></a>

OpsworksCM has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.