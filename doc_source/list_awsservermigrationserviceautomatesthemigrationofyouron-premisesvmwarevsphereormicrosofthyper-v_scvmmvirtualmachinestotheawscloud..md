# Actions, Resources, and Condition Keys for AWS Server Migration Service automates the migration of your on\-premises VMware vSphere or Microsoft Hyper\-V/SCVMM virtual machines to the AWS Cloud\.<a name="list_awsservermigrationserviceautomatesthemigrationofyouron-premisesvmwarevsphereormicrosofthyper-v_scvmmvirtualmachinestotheawscloud."></a>

AWS Server Migration Service automates the migration of your on\-premises VMware vSphere or Microsoft Hyper\-V/SCVMM virtual machines to the AWS Cloud\. \(service prefix: `sms`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/server-migration-service/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/server-migration-service/latest/userguide/SMS_setup.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Server Migration Service automates the migration of your on\-premises VMware vSphere or Microsoft Hyper\-V/SCVMM virtual machines to the AWS Cloud\.](#awsservermigrationserviceautomatesthemigrationofyouron-premisesvmwarevsphereormicrosofthyper-v_scvmmvirtualmachinestotheawscloud.-actions-as-permissions)
+ [Resources Defined by ServerMigrationService](#awsservermigrationserviceautomatesthemigrationofyouron-premisesvmwarevsphereormicrosofthyper-v_scvmmvirtualmachinestotheawscloud.-resources-for-iam-policies)
+ [Condition Keys for AWS Server Migration Service automates the migration of your on\-premises VMware vSphere or Microsoft Hyper\-V/SCVMM virtual machines to the AWS Cloud\.](#awsservermigrationserviceautomatesthemigrationofyouron-premisesvmwarevsphereormicrosofthyper-v_scvmmvirtualmachinestotheawscloud.-policy-keys)

## Actions Defined by AWS Server Migration Service automates the migration of your on\-premises VMware vSphere or Microsoft Hyper\-V/SCVMM virtual machines to the AWS Cloud\.<a name="awsservermigrationserviceautomatesthemigrationofyouron-premisesvmwarevsphereormicrosofthyper-v_scvmmvirtualmachinestotheawscloud.-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateApp ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_CreateApp.html)  | Create an application configuration to migrate on\-premise application onto AWS\.\. | Write |  |  |  | 
|   [ CreateReplicationJob ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_CreateReplicationJob.html)  | Create a job to migrate on\-premise server onto AWS\. | Write |  |  |  | 
|   [ DeleteApp ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_DeleteApp.html)  | Delete an existing application configuration\. | Write |  |  |  | 
|   [ DeleteAppLaunchConfiguration ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_DeleteAppLaunchConfiguration.html)  | Delete launch configuration for an existing application\. | Write |  |  |  | 
|   [ DeleteAppReplicationConfiguration ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_DeleteAppReplicationConfiguration.html)  | Delete replication configuration for an existing application\.\. | Write |  |  |  | 
|   [ DeleteReplicationJob ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_DeleteReplicationJob.html)  | Delete an existing job to migrate on\-premise server onto AWS\. | Write |  |  |  | 
|   [ DeleteServerCatalog ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_DeleteServerCatalog.html)  | Delete the complete list of on\-premise servers gathered into AWS\. | Write |  |  |  | 
|   [ DisassociateConnectors ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_DisassociateConnectors.html)  | Disassociate a connector that has been associated\. | Write |  |  |  | 
|   [ GenerateChangeSet ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GenerateChangeSet.html)  | Generate a changeSet for the CloudFormation stack of an application\. | Write |  |  |  | 
|   [ GenerateTemplate ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GenerateTemplate.html)  | Generate a CloudFormation template for an existing application\. | Write |  |  |  | 
|   [ GetApp ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GetApp.html)  | Get the configuration and statuses for an existing application\. | Read |  |  |  | 
|   [ GetAppLaunchConfiguration ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GetAppLaunchConfiguration.html)  | Get launch configuration for an existing application\. | Read |  |  |  | 
|   [ GetAppReplicationConfiguration ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GetAppReplicationConfiguration.html)  | Get replication configuration for an existing application\. | Read |  |  |  | 
|   [ GetConnectors ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GetConnectors.html)  | Get all connectors that have been associated\. | Read |  |  |  | 
|   [ GetReplicationJobs ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GetReplicationJobs.html)  | Get all existing jobs to migrate on\-premise servers onto AWS\. | Read |  |  |  | 
|   [ GetReplicationRuns ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GetReplicationRuns.html)  | Get all runs for an existing job\. | Read |  |  |  | 
|   [ GetServers ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_GetServers.html)  | Get all servers that have been imported\. | Read |  |  |  | 
|   [ ImportServerCatalog ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_ImportServerCatalog.html)  | Gathers a complete list of on\-premise servers\. | Write |  |  |  | 
|   [ LaunchApp ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_LaunchApp.html)  | Create and launch a CloudFormation stack for an existing application\. | Write |  |  |  | 
|   [ ListApps ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_ListAppss.html)  | Get a list of summaries for existing applications\. | List |  |  |  | 
|   [ PutAppLaunchConfiguration ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_PutAppLaunchConfiguration.html)  | Create or update launch configuration for an existing application\. | Write |  |  |  | 
|   [ PutAppReplicationConfiguration ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_PutAppReplicationConfiguration.html)  | Create or update replication configuration for an existing application\. | Write |  |  |  | 
|   [ StartAppReplication ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_StartAppReplication.html)  | Create and start replication jobs for an existing application\. | Write |  |  |  | 
|   [ StartOnDemandReplicationRun ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_StartOnDemandReplicationRun.html)  | Start a replication run for an existing replication job\. | Write |  |  |  | 
|   [ StopAppReplication ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_StopAppReplication.html)  | Stop and delete replication jobs for an existing application\. | Write |  |  |  | 
|   [ TerminateApp ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_TerminateApp.html)  | Terminate the CloudFormation stack for an existing application\. | Write |  |  |  | 
|   [ UpdateApp ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_UpdateApp.html)  | Update an existing application configuration | Write |  |  |  | 
|   [ UpdateReplicationJob ](https://docs.aws.amazon.com/ServerMigration/latest/APIReference/API_UpdateReplicationJob.html)  | Update an existing job to migrate on\-premise server onto AWS\. | Write |  |  |  | 

## Resources Defined by ServerMigrationService<a name="awsservermigrationserviceautomatesthemigrationofyouron-premisesvmwarevsphereormicrosofthyper-v_scvmmvirtualmachinestotheawscloud.-resources-for-iam-policies"></a>

AWS Server Migration Service automates the migration of your on\-premises VMware vSphere or Microsoft Hyper\-V/SCVMM virtual machines to the AWS Cloud\. has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Server Migration Service automates the migration of your on\-premises VMware vSphere or Microsoft Hyper\-V/SCVMM virtual machines to the AWS Cloud\.<a name="awsservermigrationserviceautomatesthemigrationofyouron-premisesvmwarevsphereormicrosofthyper-v_scvmmvirtualmachinestotheawscloud.-policy-keys"></a>

ServerMigrationService has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.