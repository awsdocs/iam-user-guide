# Actions and Condition Context Keys for Amazon ElastiCache<a name="list_elasticache"></a>

Amazon ElastiCache \(service prefix: elasticache\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon ElastiCache**

When you create an ElastiCache policy in IAM you must use the "\*" wildcard character for the Resource block\. For information about using the following ElastiCache API actions in an IAM policy, see [ElastiCache Actions and IAM](http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/UsingIAM.html#UsingIAM.ElastiCacheActions) in the *Amazon ElastiCache User Guide*\.
+ `[elasticache:AddTagsToResource](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_AddTagsToResource.html)`
+ `[elasticache:AuthorizeCacheSecurityGroupIngress](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_AuthorizeCacheSecurityGroupIngress.html)`
+ `[elasticache:CopySnapshot](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CopySnapshot.html)`
+ `[elasticache:CreateCacheCluster](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateCacheCluster.html)`
+ `[elasticache:CreateCacheParameterGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateCacheParameterGroup.html)`
+ `[elasticache:CreateCacheSecurityGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateCacheSecurityGroup.html)`
+ `[elasticache:CreateCacheSubnetGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateCacheSubnetGroup.html)`
+ `[elasticache:CreateReplicationGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateReplicationGroup.html)`
+ `[elasticache:CreateSnapshot](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_CreateSnapshot.html)`
+ `[elasticache:DeleteCacheCluster](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteCacheCluster.html)`
+ `[elasticache:DeleteCacheParameterGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteCacheParameterGroup.html)`
+ `[elasticache:DeleteCacheSecurityGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteCacheSecurityGroup.html)`
+ `[elasticache:DeleteCacheSubnetGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteCacheSubnetGroup.html)`
+ `[elasticache:DeleteReplicationGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteReplicationGroup.html)`
+ `[elasticache:DeleteSnapshot](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DeleteSnapshot.html)`
+ `[elasticache:DescribeCacheClusters](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheClusters.html)`
+ `[elasticache:DescribeCacheEngineVersions](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheEngineVersions.html)`
+ `[elasticache:DescribeCacheParameterGroups](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheParameterGroups.html)`
+ `[elasticache:DescribeCacheParameters](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheParameters.html)`
+ `[elasticache:DescribeCacheSecurityGroups](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheSecurityGroups.html)`
+ `[elasticache:DescribeCacheSubnetGroups](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeCacheSubnetGroups.html)`
+ `[elasticache:DescribeEngineDefaultParameters](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeEngineDefaultParameters.html)`
+ `[elasticache:DescribeEvents](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeEvents.html)`
+ `[elasticache:DescribeReplicationGroups](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeReplicationGroups.html)`
+ `[elasticache:DescribeReservedCacheNodes](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeReservedCacheNodes.html)`
+ `[elasticache:DescribeReservedCacheNodesOfferings](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeReservedCacheNodesOfferings.html)`
+ `[elasticache:DescribeSnapshots](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_DescribeSnapshots.html)`
+ `[elasticache:ListAllowedNodeTypeModifications](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ListAllowedNodeTypeModifications.html)`
+ `[elasticache:ListTagsForResource](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ListTagsForResource.html)`
+ `[elasticache:ModifyCacheCluster](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ModifyCacheCluster.html)`
+ `[elasticache:ModifyCacheParameterGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ModifyCacheParameterGroup.html)`
+ `[elasticache:ModifyCacheSubnetGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ModifyCacheSubnetGroup.html)`
+ `[elasticache:ModifyReplicationGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ModifyReplicationGroup.html)`
+ `[elasticache:PurchaseReservedCacheNodesOffering](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_PurchaseReservedCacheNodesOffering.html)`
+ `[elasticache:RebootCacheCluster](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_RebootCacheCluster.html)`
+ `[elasticache:RemoveTagsFromResource](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_RemoveTagsFromResource.html)`
+ `[elasticache:ResetCacheParameterGroup](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_ResetCacheParameterGroup.html)`
+ `[elasticache:RevokeCacheSecurityGroupIngress](http://docs.aws.amazon.com/AmazonElastiCache/latest/APIReference/API_RevokeCacheSecurityGroupIngress.html)`

**Condition context keys for Amazon ElastiCache**

For information about conditions in an IAM policy to control access to ElastiCache, see [ElastiCache Keys](http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/UsingIAM.html#UsingIAM.Keys) in the *Amazon ElastiCache User Guide*\.

Amazon ElastiCache has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.