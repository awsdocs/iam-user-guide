# Amazon DynamoDB: Allows access to specific columns<a name="reference_policies_examples_dynamodb_columns"></a>

This example shows how you might create a policy that allows access to the specific DynamoDB columns\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

The `dynamodb:Select` requirement prevents the API action from returning any attributes that aren't allowed, such as from an index projection\. To learn more about DynamoDB condition keys, see [Specifying Conditions: Using Condition Keys](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) in the* Amazon DynamoDB Developer Guide*\. To learn about using multiple conditions or multiple condition keys within the `Condition` block of an IAM policy, see [Multiple values in a condition](reference_policies_elements_condition.md#Condition-multiple-conditions)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:GetItem",
                "dynamodb:BatchGetItem",
                "dynamodb:Query",
                "dynamodb:PutItem",
                "dynamodb:UpdateItem",
                "dynamodb:DeleteItem",
                "dynamodb:BatchWriteItem"
            ],
            "Resource": ["arn:aws:dynamodb:*:*:table/table-name"],
            "Condition": {
                "ForAllValues:StringEquals": {
                    "dynamodb:Attributes": [
                        "column-name-1",
                        "column-name-2",
                        "column-name-3"
                    ]
                },
                "StringEqualsIfExists": {"dynamodb:Select": "SPECIFIC_ATTRIBUTES"}
            }
        }
    ]
}
```