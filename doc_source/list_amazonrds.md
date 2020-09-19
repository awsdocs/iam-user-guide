# Actions, resources, and condition keys for Amazon RDS<a name="list_amazonrds"></a>

Amazon RDS \(service prefix: `rds`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AmazonRDS/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html) permission policies\.

**Topics**
+ [Actions defined by Amazon RDS](#amazonrds-actions-as-permissions)
+ [Resource types defined by Amazon RDS](#amazonrds-resources-for-iam-policies)
+ [Condition keys for Amazon RDS](#amazonrds-policy-keys)

## Actions defined by Amazon RDS<a name="amazonrds-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonrds.html)

## Resource types defined by Amazon RDS<a name="amazonrds-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonrds-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ cluster ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Aurora.Managing.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster:$\{DbClusterInstanceName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:cluster\-tag/$\{TagKey\} ](#amazonrds-rds_cluster-tag___TagKey_)   | 
|   [ cluster\-endpoint ]({ActionsDocRoot}API_DBClusterEndpoint.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster\-endpoint:$\{DbClusterEndpoint\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   | 
|   [ cluster\-pg ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster\-pg:$\{ClusterParameterGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:cluster\-pg\-tag/$\{TagKey\} ](#amazonrds-rds_cluster-pg-tag___TagKey_)   | 
|   [ cluster\-snapshot ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:cluster\-snapshot:$\{ClusterSnapshotName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:cluster\-snapshot\-tag/$\{TagKey\} ](#amazonrds-rds_cluster-snapshot-tag___TagKey_)   | 
|   [ db ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBInstance.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:db:$\{DbInstanceName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:DatabaseClass ](#amazonrds-rds_DatabaseClass)   [ rds:DatabaseEngine ](#amazonrds-rds_DatabaseEngine)   [ rds:DatabaseName ](#amazonrds-rds_DatabaseName)   [ rds:MultiAz ](#amazonrds-rds_MultiAz)   [ rds:Piops ](#amazonrds-rds_Piops)   [ rds:StorageEncrypted ](#amazonrds-rds_StorageEncrypted)   [ rds:StorageSize ](#amazonrds-rds_StorageSize)   [ rds:Vpc ](#amazonrds-rds_Vpc)   [ rds:db\-tag/$\{TagKey\} ](#amazonrds-rds_db-tag___TagKey_)   | 
|   [ es ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Events.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:es:$\{SubscriptionName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:es\-tag/$\{TagKey\} ](#amazonrds-rds_es-tag___TagKey_)   | 
|   [ global\-cluster ](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database.html)  |  arn:$\{Partition\}:rds:$\{Account\}:global\-cluster:$\{GlobalCluster\}  |  | 
|   [ og ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithOptionGroups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:og:$\{OptionGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:og\-tag/$\{TagKey\} ](#amazonrds-rds_og-tag___TagKey_)   | 
|   [ pg ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithParamGroups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:pg:$\{ParameterGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:pg\-tag/$\{TagKey\} ](#amazonrds-rds_pg-tag___TagKey_)   | 
|   [ proxy ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBProxy.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:db\-proxy:$\{DbProxyId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   | 
|   [ ri ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithReservedDBInstances.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:ri:$\{ReservedDbInstanceName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:ri\-tag/$\{TagKey\} ](#amazonrds-rds_ri-tag___TagKey_)   | 
|   [ secgrp ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithSecurityGroups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:secgrp:$\{SecurityGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:secgrp\-tag/$\{TagKey\} ](#amazonrds-rds_secgrp-tag___TagKey_)   | 
|   [ snapshot ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:snapshot:$\{SnapshotName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:snapshot\-tag/$\{TagKey\} ](#amazonrds-rds_snapshot-tag___TagKey_)   | 
|   [ subgrp ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.Scenarios.html#USER_VPC.Scenario1)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:subgrp:$\{SubnetGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   [ rds:subgrp\-tag/$\{TagKey\} ](#amazonrds-rds_subgrp-tag___TagKey_)   | 
|   [ target ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBProxy.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:target:$\{TargetId\}  |  | 
|   [ target\-group ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBProxy.html)  |  arn:$\{Partition\}:rds:$\{Region\}:$\{Account\}:target\-group:$\{TargetGroupId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonrds-aws_ResourceTag___TagKey_)   | 

## Condition keys for Amazon RDS<a name="amazonrds-policy-keys"></a>

Amazon RDS defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters access based on the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters access based on tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters access based on the presence of tag keys in the request | String | 
|   [ rds:DatabaseClass ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the type of DB instance class | String | 
|   [ rds:DatabaseEngine ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the database engine\. For possible values refer to the engine parameter in CreateDBInstance API | String | 
|   [ rds:DatabaseName ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the user\-defined name of the database on the DB instance | String | 
|   [ rds:EndpointType ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the type of the endpoint\. One of: READER, WRITER, CUSTOM | String | 
|   [ rds:MultiAz ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the value that specifies whether the DB instance runs in multiple Availability Zones\. To indicate that the DB instance is using Multi\-AZ, specify true | Boolean | 
|   [ rds:Piops ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the value that contains the number of Provisioned IOPS \(PIOPS\) that the instance supports\. To indicate a DB instance that does not have PIOPS enabled, specify 0 | Numeric | 
|   [ rds:StorageEncrypted ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the value that specifies whether the DB instance storage should be encrypted\. To enforce storage encryption, specify true | Boolean | 
|   [ rds:StorageSize ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the storage volume size \(in GB\) | Numeric | 
|   [ rds:Vpc ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the value that specifies whether the DB instance runs in an Amazon Virtual Private Cloud \(Amazon VPC\)\. To indicate that the DB instance runs in an Amazon VPC, specify true | Boolean | 
|   [ rds:cluster\-pg\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB cluster parameter group | String | 
|   [ rds:cluster\-snapshot\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB cluster snapshot | String | 
|   [ rds:cluster\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB cluster | String | 
|   [ rds:db\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB instance | String | 
|   [ rds:es\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to an event subscription | String | 
|   [ rds:og\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB option group | String | 
|   [ rds:pg\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB parameter group | String | 
|   [ rds:req\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the set of tag keys and values that can be used to tag a resource | String | 
|   [ rds:ri\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a reserved DB instance | String | 
|   [ rds:secgrp\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB security group | String | 
|   [ rds:snapshot\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB snapshot | String | 
|   [ rds:subgrp\-tag/$\{TagKey\} ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/security_iam_service-with-iam.html#UsingWithRDS.IAM.Conditions)  | Filters access by the tag attached to a DB subnet group | String | 