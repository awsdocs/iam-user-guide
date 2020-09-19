# Actions, resources, and condition keys for Amazon ElastiCache<a name="list_amazonelasticache"></a>

Amazon ElastiCache \(service prefix: `elasticache`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/IAM.html) permission policies\.

**Topics**
+ [Actions defined by Amazon ElastiCache](#amazonelasticache-actions-as-permissions)
+ [Resource types defined by Amazon ElastiCache](#amazonelasticache-resources-for-iam-policies)
+ [Condition keys for Amazon ElastiCache](#amazonelasticache-policy-keys)

## Actions defined by Amazon ElastiCache<a name="amazonelasticache-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.

**Note**  
When you create an ElastiCache policy in IAM you must use the "\*" wildcard character for the Resource block\. For information about using the following ElastiCache API actions in an IAM policy, see [ElastiCache Actions and IAM](https://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/UsingIAM.html#UsingIAM.ElastiCacheActions) in the *Amazon ElastiCache User Guide*\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonelasticache.html)

## Resource types defined by Amazon ElastiCache<a name="amazonelasticache-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonelasticache-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ parametergroup ](AmazonElastiCache/latest/red-ug/WhatIs.Components.html)  |  arn:$\{Partition\}:elasticache:$\{Region\}:$\{Account\}:parametergroup:$\{CacheParameterGroupName\}  |  | 
|   [ securitygroup ](AmazonElastiCache/latest/red-ug/WhatIs.Components.html)  |  arn:$\{Partition\}:elasticache:$\{Region\}:$\{Account\}:securitygroup:$\{CacheSecurityGroupName\}  |  | 
|   [ subnetgroup ](AmazonElastiCache/latest/red-ug/WhatIs.Components.html)  |  arn:$\{Partition\}:elasticache:$\{Region\}:$\{Account\}:subnetgroup:$\{CacheSubnetGroupName\}  |  | 
|   [ replicationgroup ](AmazonElastiCache/latest/red-ug/Replication.html)  |  arn:$\{Partition\}:elasticache:$\{Region\}:$\{Account\}:replicationgroup:$\{ReplicationGroupId\}  |  | 
|   [ cluster ](AmazonElastiCache/latest/red-ug/WhatIs.Components.html)  |  arn:$\{Partition\}:elasticache:$\{Region\}:$\{Account\}:cluster:$\{CacheClusterId\}  |  | 
|   [ reserved\-instance ](AmazonElastiCache/latest/red-ug/reserved-nodes.html)  |  arn:$\{Partition\}:elasticache:$\{Region\}:$\{Account\}:reserved\-instance:$\{ReservedCacheNodeId\}  |  | 
|   [ snapshot ](AmazonElastiCache/latest/red-ug/backups.html)  |  arn:$\{Partition\}:elasticache:$\{Region\}:$\{Account\}:snapshot:$\{SnapshotName\}  |  | 
|   [ globalreplicationgroup ](AmazonElastiCache/latest/red-ug/Redis-Global-Datastore.html)  |  arn:$\{Partition\}:elasticache::$\{Account\}:globalreplicationgroup:$\{GlobalReplicationGroupId\}  |  | 

## Condition keys for Amazon ElastiCache<a name="amazonelasticache-policy-keys"></a>

ElastiCache has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.

**Note**  
For information about conditions in an IAM policy to control access to ElastiCache, see [ElastiCache Keys](https://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/UsingIAM.html#UsingIAM.Keys) in the *Amazon ElastiCache User Guide*\.