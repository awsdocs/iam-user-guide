# Amazon DynamoDB: Allows row\-level access to DynamoDB based on an Amazon Cognito ID<a name="reference_policies_examples_dynamodb_rows"></a>

This example shows how you might create a policy that allows row\-level access to the `MyTable` DynamoDB table based on an Amazon Cognito ID\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

To use this policy, you must structure your DynamoDB table so the Cognito user ID is the partition key\. For more information, see [Creating a Table](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithTables.Basics.html#WorkingWithTables.Basics.CreateTable) in the *Amazon DynamoDB Developer Guide*\.

To learn more about DynamoDB condition keys, see [Specifying Conditions: Using Condition Keys](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) in the* Amazon DynamoDB Developer Guide*\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:DeleteItem",
                "dynamodb:GetItem",
                "dynamodb:PutItem",
                "dynamodb:Query",
                "dynamodb:UpdateItem"
            ],
            "Resource": ["arn:aws:dynamodb:*:*:table/MyTable"],
            "Condition": {
                "ForAllValues:StringEquals": {
                    "dynamodb:LeadingKeys": ["${cognito-identity.amazonaws.com:sub}"]
                }
            }
        }
    ]
}
```