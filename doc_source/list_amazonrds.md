# Actions, Resources, and Condition Keys for Amazon RDS<a name="list_amazonrds"></a>

Amazon RDS \(service prefix: `rds`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/AmazonRDS/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon RDS](#amazonrds-actions-as-permissions)
+ [Resources Defined by Amazon RDS](#amazonrds-resources-for-iam-policies)
+ [Condition Keys for Amazon RDS](#amazonrds-policy-keys)

## Actions Defined by Amazon RDS<a name="amazonrds-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonrds.html)

## Resources Defined by Amazon RDS<a name="amazonrds-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonrds-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ cluster ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Aurora.Managing.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster:$\{DbClusterInstanceName\}  |   [ rds:DatabaseEngine ](#amazonrds-rds_DatabaseEngine)   [ rds:DatabaseName ](#amazonrds-rds_DatabaseName)   [ rds:Vpc ](#amazonrds-rds_Vpc)   [ rds:cluster\-tag ](#amazonrds-rds_cluster-tag)   | 
|   [ cluster\-endpoint ]({ActionsDocRoot}API_DBClusterEndpoint.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster\-endpoint:$\{DbClusterEndpoint\}  |   [ rds:EndpointType ](#amazonrds-rds_EndpointType)   | 
|   [ cluster\-pg ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster\-pg:$\{ClusterParameterGroupName\}  |   [ rds:cluster\-pg\-tag ](#amazonrds-rds_cluster-pg-tag)   | 
|   [ cluster\-snapshot ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster\-snapshot:$\{ClusterSnapshotName\}  |   [ rds:cluster\-snapshot\-tag ](#amazonrds-rds_cluster-snapshot-tag)   | 
|   [ db ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBInstance.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:db:$\{DbInstanceName\}  |   [ rds:DatabaseClass ](#amazonrds-rds_DatabaseClass)   [ rds:DatabaseEngine ](#amazonrds-rds_DatabaseEngine)   [ rds:DatabaseName ](#amazonrds-rds_DatabaseName)   [ rds:MultiAz ](#amazonrds-rds_MultiAz)   [ rds:Piops ](#amazonrds-rds_Piops)   [ rds:StorageSize ](#amazonrds-rds_StorageSize)   [ rds:Vpc ](#amazonrds-rds_Vpc)   [ rds:db\-tag ](#amazonrds-rds_db-tag)   | 
|   [ es ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Events.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:es:$\{SubscriptionName\}  |   [ rds:es\-tag ](#amazonrds-rds_es-tag)   | 
|   [ global\-cluster ](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database.html)  |  arn:$\{Partition\}:rds:$\{Account\}:global\-cluster:$\{GlobalCluster\}  |  | 
|   [ iam\-role ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.html)  |  arn:$\{Partition\}:iam::$\{Account\}:role/$\{RoleNameWithPath\}  |  | 
|   [ og ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithOptionGroups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:og:$\{OptionGroupName\}  |   [ rds:og\-tag ](#amazonrds-rds_og-tag)   | 
|   [ pg ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:pg:$\{ParameterGroupName\}  |   [ rds:pg\-tag ](#amazonrds-rds_pg-tag)   | 
|   [ ri ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithReservedDBInstances.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:ri:$\{ReservedDbInstanceName\}  |   [ rds:DatabaseClass ](#amazonrds-rds_DatabaseClass)   [ rds:MultiAz ](#amazonrds-rds_MultiAz)   [ rds:ri\-tag ](#amazonrds-rds_ri-tag)   | 
|   [ secgrp ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithSecurityGroups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:secgrp:$\{SecurityGroupName\}  |   [ rds:secgrp\-tag ](#amazonrds-rds_secgrp-tag)   | 
|   [ snapshot ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:snapshot:$\{SnapshotName\}  |   [ rds:snapshot\-tag ](#amazonrds-rds_snapshot-tag)   | 
|   [ subgrp ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.Scenarios.html#USER_VPC.Scenario1)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:subgrp:$\{SubnetGroupName\}  |   [ rds:subgrp\-tag ](#amazonrds-rds_subgrp-tag)   | 

## Condition Keys for Amazon RDS<a name="amazonrds-policy-keys"></a>

Amazon RDS defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ Piops ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A value that contains the number of Provisioned IOPS \(PIOPS\) that the instance supports\. | Numeric | 
|   [ rds:DatabaseClass ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A type of DB instance class\. | String | 
|   [ rds:DatabaseEngine ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A database engine, such as MySQL\. | String | 
|   [ rds:DatabaseName ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | The user\-defined name of the database on the DB instance\. | String | 
|   [ rds:EndpointType ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | The type of the endpoint\. One of: READER, WRITER, CUSTOM\. | String | 
|   [ rds:MultiAz ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A value that specifies whether the DB instance runs in multiple Availability Zones\. To indicate that the DB instance is using Multi\-AZ, specify true\. | Numeric | 
|   [ rds:Piops ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A value that contains the number of Provisioned IOPS \(PIOPS\) that the instance supports\. To indicate a DB instance that does not have PIOPS enabled, specify 0\. | Numeric | 
|   [ rds:StorageEncrypted ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A value that specifies whether the DB instance storage should be encrypted\. To enforce storage encryption, specify true\. | Boolean | 
|   [ rds:StorageSize ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | The storage volume size \(in GB\)\. | Numeric | 
|   [ rds:Vpc ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A value that specifies whether the DB instance runs in an Amazon Virtual Private Cloud \(Amazon VPC\)\. To indicate that the DB instance runs in an Amazon VPC, specify true\. | Boolean | 
|   [ rds:cluster\-pg\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB cluster parameter group\. | String | 
|   [ rds:cluster\-snapshot\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB cluster snapshot\. | String | 
|   [ rds:cluster\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB cluster\. | String | 
|   [ rds:db\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB instance\. | String | 
|   [ rds:es\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to an event subscription\. | String | 
|   [ rds:og\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB option group\. | String | 
|   [ rds:pg\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB parameter group\. | String | 
|   [ rds:req\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | Limits the set of tag keys and values that can be used to tag a resource\. | String | 
|   [ rds:ri\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a reserved DB instance\. | String | 
|   [ rds:secgrp\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB security group\. | String | 
|   [ rds:snapshot\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB snapshot\. | String | 
|   [ rds:subgrp\-tag ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html)  | A tag attached to a DB subnet group\. | String | 