# Actions and Condition Context Keys for Amazon DynamoDB<a name="list_dynamodb"></a>

Amazon DynamoDB \(service prefix: dynamodb\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon DynamoDB**

For information about using the following DynamoDB API actions in an IAM policy, see [DynamoDB Actions](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html#UsingWithActions) in the *Amazon DynamoDB Developer Guide*\.
+ `[dynamodb:BatchGetItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_BatchGetItem.html)`
+ `[dynamodb:BatchWriteItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_BatchWriteItem.html)`
+ `[dynamodb:CreateBackup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_CreateBackup.html)`
+ `[dynamodb:CreateTable](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_CreateTable.html)`
+ `[dynamodb:DeleteBackup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DeleteBackup.html)`
+ `[dynamodb:DeleteItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DeleteItem.html)`
+ `[dynamodb:DeleteTable](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DeleteTable.html)`
+ `[dynamodb:DescribeBackup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeBackup.html)`
+ `[dynamodb:DescribeContinuousBackups](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeContinuousBackups.html)`
+ `[dynamodb:DescribeLimits](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeLimits.html)`
+ `[dynamodb:DescribeReservedCapacity](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeReservedCapacity.html)`
+ `[dynamodb:DescribeReservedCapacityOfferings](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeReservedCapacityOfferings.html)`
+ `[dynamodb:DescribeStream](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeStream.html)`
+ `[dynamodb:DescribeTable](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeTable.html)`
+ `[dynamodb:DescribeTimeToLive](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_DescribeTimeToLive.html)`
+ `[dynamodb:GetItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_GetItem.html)`
+ `[dynamodb:GetRecords](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_GetRecords.html)`
+ `[dynamodb:GetShardIterator](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_GetShardIterator.html)`
+ `[dynamodb:ListBackups](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_ListBackups.html)`
+ `[dynamodb:ListStreams](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_ListStreams.html)`
+ `[dynamodb:ListTables](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_ListTables.html)`
+ `[dynamodb:ListTagsOfResource](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_ListTagsOfResource.html)`
+ `[dynamodb:PurchaseReservedCapacityOfferings](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_PurchaseReservedCapacityOfferings.html)`
+ `[dynamodb:PutItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_PutItem.html)`
+ `[dynamodb:Query](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Query.html)`
+ `[dynamodb:RestoreTableFromBackup](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_RestoreTableFromBackup.html)`
+ `[dynamodb:Scan](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Scan.html)`
+ `[dynamodb:TagResource](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_TagResource.html)`
+ `[dynamodb:UntagResource](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_UntagResource.html)`
+ `[dynamodb:UpdateItem](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_UpdateItem.html)`
+ `[dynamodb:UpdateTable](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_UpdateTable.html)`
+ `[dynamodb:UpdateTimeToLive](http://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_UpdateTimeToLive.html)`

**Condition context keys for Amazon DynamoDB**

For information about using the following DynamoDB condition keys in an IAM policy, see [IAM Policy Keys](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html#IAMPolicyKeys) in the *Amazon DynamoDB Developer Guide*\.

Amazon DynamoDB has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ `dynamodb:Attributes`
+ `dynamodb:LeadingKeys`
+ `dynamodb:ReturnConsumedCapacity`
+ `dynamodb:ReturnValues`
+ `dynamodb:Select`