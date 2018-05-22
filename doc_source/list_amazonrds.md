# Actions, Resources, and Condition Keys for Amazon RDS<a name="list_amazonrds"></a>

Amazon RDS \(service prefix: `rds`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon RDS](#amazonrds-actions-as-permissions)
+ [Resources Defined by RDS](#amazonrds-resources-for-iam-policies)
+ [Condition Keys for Amazon RDS](#amazonrds-policy-keys)

## Actions Defined by Amazon RDS<a name="amazonrds-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonrds.html)

## Resources Defined by RDS<a name="amazonrds-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonrds-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Aurora.Managing.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Aurora.Managing.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster:$\{DbClusteInstanceName\} | [rds:DatabaseEngine](#amazonrds-rds_DatabaseEngine) [rds:DatabaseName](#amazonrds-rds_DatabaseName) [rds:Vpc](#amazonrds-rds_Vpc) [rds:cluster\-tag](#amazonrds-rds_cluster-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster\-snapshot:$\{ClusterParameterGroupName\} | [rds:cluster\-pg\-tag](#amazonrds-rds_cluster-pg-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster\-snapshot:$\{ClusterSnapshotName\} | [rds:cluster\-snapshot\-tag](#amazonrds-rds_cluster-snapshot-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBInstance.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBInstance.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:db:$\{DbInstanceName\} | [rds:DatabaseClass](#amazonrds-rds_DatabaseClass) [rds:DatabaseEngine](#amazonrds-rds_DatabaseEngine) [rds:DatabaseName](#amazonrds-rds_DatabaseName) [rds:MultiAz](#amazonrds-rds_MultiAz) [rds:Piops](#amazonrds-rds_Piops) [rds:StorageSize](#amazonrds-rds_StorageSize) [rds:Vpc](#amazonrds-rds_Vpc) [rds:db\-tag](#amazonrds-rds_db-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Events.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Events.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:es:$\{SubscriptionName\} | [rds:es\-tag](#amazonrds-rds_es-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.html) | arn:$\{Partition\}:iam::$\{Account\}:role/$\{RoleNameWithPath\} |  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithOptionGroups.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithOptionGroups.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:og:$\{OptionGroupName\} | [rds:og\-tag](#amazonrds-rds_og-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:pg:$\{ParameterGroupName\} | [rds:pg\-tag](#amazonrds-rds_pg-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithReservedDBInstances.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithReservedDBInstances.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:ri:$\{ReservedDbInstanceName\} | [rds:DatabaseClass](#amazonrds-rds_DatabaseClass) [rds:MultiAz](#amazonrds-rds_MultiAz) [rds:ri\-tag](#amazonrds-rds_ri-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithSecurityGroups.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithSecurityGroups.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:secgrp:$\{SecurityGroupName\} | [rds:secgrp\-tag](#amazonrds-rds_secgrp-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:snapshot:$\{SnapshotName\} | [rds:snapshot\-tag](#amazonrds-rds_snapshot-tag)  | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.Scenarios.html#USER_VPC.Scenario1](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.Scenarios.html#USER_VPC.Scenario1) | arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:subgrp:$\{SubnetGroupName\} | [rds:subgrp\-tag](#amazonrds-rds_subgrp-tag)  | 

## Condition Keys for Amazon RDS<a name="amazonrds-policy-keys"></a>

Amazon RDS defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A value that contains the number of Provisioned IOPS \(PIOPS\) that the instance supports\. | Numeric | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A type of DB instance class\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A database engine, such as MySQL\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | The user\-defined name of the database on the DB instance\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A value that specifies whether the DB instance runs in multiple Availability Zones\. To indicate that the DB instance is using Multi\-AZ, specify true\. | Numeric | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A value that contains the number of Provisioned IOPS \(PIOPS\) that the instance supports\. To indicate a DB instance that does not have PIOPS enabled, specify 0\. | Numeric | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | The storage volume size \(in GB\)\. | Numeric | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A value that specifies whether the DB instance runs in an Amazon Virtual Private Cloud \(Amazon VPC\)\. To indicate that the DB instance runs in an Amazon VPC, specify true\. | Boolean | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB cluster parameter group\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB cluster snapshot\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB cluster\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB instance\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to an event subscription\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB option group\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB parameter group | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a reserved DB instance\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB security group\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB snapshot\. | String | 
| [http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.Conditions.html) | A tag attached to a DB subnet group\. | String | 