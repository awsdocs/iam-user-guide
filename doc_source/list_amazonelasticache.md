# Actions, Resources, and Condition Keys for Amazon ElastiCache<a name="list_amazonelasticache"></a>

Amazon ElastiCache \(service prefix: `elasticache`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/IAM.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon ElastiCache](#amazonelasticache-actions-as-permissions)
+ [Resources Defined by ElastiCache](#amazonelasticache-resources-for-iam-policies)
+ [Condition Keys for Amazon ElastiCache](#amazonelasticache-policy-keys)

## Actions Defined by Amazon ElastiCache<a name="amazonelasticache-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.

When you create an ElastiCache policy in IAM you must use the "\*" wildcard character for the Resource block\. For information about using the following ElastiCache API actions in an IAM policy, see [ElastiCache Actions and IAM](http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/UsingIAM.html#UsingIAM.ElastiCacheActions) in the *Amazon ElastiCache User Guide*\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddTagsToResource ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_AddTagsToResource.html)  | The AddTagsToResource action adds up to 10 cost allocation tags to the named resource\. | Tagging |  |  |  | 
|   [ AuthorizeCacheSecurityGroupIngress ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_AuthorizeCacheSecurityGroupIngress.html)  | The AuthorizeCacheSecurityGroupIngress action allows network ingress to a cache security group\. | Write |  |  |   ec2:AuthorizeSecurityGroupIngress   | 
|   [ CopySnapshot ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CopySnapshot.html)  | The CopySnapshot action makes a copy of an existing snapshot\. | Write |  |  |   s3:DeleteObject   s3:GetBucketAcl   s3:PutObject   | 
|   [ CreateCacheCluster ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateCacheCluster.html)  | The CreateCacheCluster action creates a cache cluster\. | Write |  |  |   ec2:CreateNetworkInterface   ec2:DeleteNetworkInterface   ec2:DescribeNetworkInterfaces   ec2:DescribeSubnets   ec2:DescribeVpcs   s3:GetObject   | 
|   [ CreateCacheParameterGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateCacheParameterGroup.html)  | The CreateCacheParameterGroup action creates a new cache parameter group\. | Write |  |  |  | 
|   [ CreateCacheSecurityGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateCacheSecurityGroup.html)  | The CreateCacheSecurityGroup action creates a new cache security group\.  | Write |  |  |  | 
|   [ CreateCacheSubnetGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateCacheSubnetGroup.html)  | The CreateCacheSubnetGroup action creates a new cache subnet group\. | Write |  |  |  | 
|   [ CreateReplicationGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateReplicationGroup.html)  | The CreateReplicationGroup action creates a replication group\. | Write |  |  |   ec2:CreateNetworkInterface   ec2:DeleteNetworkInterface   ec2:DescribeNetworkInterfaces   ec2:DescribeSubnets   ec2:DescribeVpcs   s3:GetObject   | 
|   [ CreateSnapshot ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateSnapshot.html)  | The CreateSnapshot action creates a copy of an entire cache cluster at a specific moment in time\. | Write |  |  |  | 
|   [ DeleteCacheCluster ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteCacheCluster.html)  | The DeleteCacheCluster action deletes a previously provisioned cache cluster\. | Write |  |  |  | 
|   [ DeleteCacheParameterGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteCacheParameterGroup.html)  | The DeleteCacheParameterGroup action deletes the specified cache parameter group\. | Write |  |  |  | 
|   [ DeleteCacheSecurityGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteCacheSecurityGroup.html)  | The DeleteCacheSecurityGroup action deletes a cache security group\. | Write |  |  |  | 
|   [ DeleteCacheSubnetGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteCacheSubnetGroup.html)  | The DeleteCacheSubnetGroup action deletes a cache subnet group\. | Write |  |  |  | 
|   [ DeleteReplicationGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteReplicationGroup.html)  | The DeleteReplicationGroup action deletes an existing replication group\. | Write |  |  |  | 
|   [ DeleteSnapshot ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteSnapshot.html)  | The DeleteSnapshot action deletes an existing snapshot\. | Write |  |  |  | 
|   [ DescribeCacheClusters ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheClusters.html)  | The DescribeCacheClusters action returns information about all provisioned cache clusters if no cache cluster identifier is specified, or about a specific cache cluster if a cache cluster identifier is supplied\. | List |  |  |  | 
|   [ DescribeCacheEngineVersions ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheEngineVersions.html)  | The DescribeCacheEngineVersions action returns a list of the available cache engines and their versions\. | List |  |  |  | 
|   [ DescribeCacheParameterGroups ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheParameterGroups.html)  | The DescribeCacheParameterGroups action returns a list of cache parameter group descriptions\. | List |  |  |  | 
|   [ DescribeCacheParameters ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheParameters.html)  | The DescribeCacheParameters action returns the detailed parameter list for a particular cache parameter group\. | List |  |  |  | 
|   [ DescribeCacheSecurityGroups ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheSecurityGroups.html)  | The DescribeCacheSecurityGroups action returns a list of cache security group descriptions\. | List |  |  |  | 
|   [ DescribeCacheSubnetGroups ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheSubnetGroups.html)  | The DescribeCacheSubnetGroups action returns a list of cache subnet group descriptions\. | List |  |  |  | 
|   [ DescribeEngineDefaultParameters ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeEngineDefaultParameters.html)  | The DescribeEngineDefaultParameters action returns the default engine and system parameter information for the specified cache engine\. | List |  |  |  | 
|   [ DescribeEvents ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeEvents.html)  | The DescribeEvents action returns events related to cache clusters, cache security groups, and cache parameter groups\. | List |  |  |  | 
|   [ DescribeReplicationGroups ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeReplicationGroups.html)  | The DescribeReplicationGroups action returns information about a particular replication group\. | List |  |  |  | 
|   [ DescribeReservedCacheNodes ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeReservedCacheNodes.html)  | The DescribeReservedCacheNodes action returns information about reserved cache nodes for this account, or about a specified reserved cache node\. | List |  |  |  | 
|   [ DescribeReservedCacheNodesOfferings ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeReservedCacheNodesOfferings.html)  | The DescribeReservedCacheNodesOfferings action lists available reserved cache node offerings\. | List |  |  |  | 
|   [ DescribeSnapshots ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeSnapshots.html)  | The DescribeSnapshots action returns information about cache cluster snapshots\. | List |  |  |  | 
|   [ ListAllowedNodeTypeModifications ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ListAllowedNodeTypeModifications.html)  | List Allowed Node Type Modifications | List |  |  |  | 
|   [ ListTagsForResource ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ListTagsForResource.html)  | The ListTagsForResource action lists all cost allocation tags currently on the named resource\. | Read |  |  |  | 
|   [ ModifyCacheCluster ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ModifyCacheCluster.html)  | The ModifyCacheCluster action modifies the settings for a cache cluster\. | Write |  |  |  | 
|   [ ModifyCacheParameterGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ModifyCacheParameterGroup.html)  | The ModifyCacheParameterGroup action modifies the parameters of a cache parameter group\. | Write |  |  |  | 
|   [ ModifyCacheSubnetGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ModifyCacheSubnetGroup.html)  | The ModifyCacheSubnetGroup action modifies an existing cache subnet group\. | Write |  |  |  | 
|   [ ModifyReplicationGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ModifyReplicationGroup.html)  | The ModifyReplicationGroup action modifies the settings for a replication group\. | Write |  |  |  | 
|   [ PurchaseReservedCacheNodesOffering ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_PurchaseReservedCacheNodesOffering.html)  | The PurchaseReservedCacheNodesOffering action allows you to purchase a reserved cache node offering\. | Write |  |  |  | 
|   [ RebootCacheCluster ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_RebootCacheCluster.html)  | The RebootCacheCluster action reboots some, or all, of the cache nodes within a provisioned cache cluster\. | Write |  |  |  | 
|   [ RemoveTagsFromResource ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_RemoveTagsFromResource.html)  | The RemoveTagsFromResource action removes the tags identified by the TagKeys list from the named resource\. | Tagging |  |  |  | 
|   [ ResetCacheParameterGroup ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ResetCacheParameterGroup.html)  | The ResetCacheParameterGroup action modifies the parameters of a cache parameter group to the engine or system default value\. | Write |  |  |  | 
|   [ RevokeCacheSecurityGroupIngress ](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_RevokeCacheSecurityGroupIngress.html)  | The RevokeCacheSecurityGroupIngress action revokes ingress from a cache security group\. | Write |  |  |  | 

## Resources Defined by ElastiCache<a name="amazonelasticache-resources-for-iam-policies"></a>

Amazon ElastiCache has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon ElastiCache<a name="amazonelasticache-policy-keys"></a>

ElastiCache has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.

For information about conditions in an IAM policy to control access to ElastiCache, see [ElastiCache Keys](http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/UsingIAM.html#UsingIAM.Keys) in the *Amazon ElastiCache User Guide*\.