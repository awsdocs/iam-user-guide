# Amazon DynamoDB: Allows Access to Specific Columns<a name="reference_policies_examples_dynamodb_columns"></a>

This example shows how you might create a policy that allows access to the specific DynamoDB columns\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

The `dynamodb:Select` requirement prevents the API action from returning any attributes that aren't allowed, such as from an index projection\. To learn more about DynamoDB condition keys, see [Specifying Conditions: Using Condition Keys](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) in the* Amazon DynamoDB Developer Guide*\. To learn about using multiple conditions or multiple condition keys within the `Condition` block of an IAM policy, see [Multiple Values in a Condition](reference_policies_elements_condition.md#Condition-multiple-conditions)\.

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
             "Resource": [
                 "arn:aws:dynamodb:<REGION>:<ACCOUNTNUMBER>:table/<TABLE-NAME>"
             ],
             "
             "Condition": {
                 "ForAllValues:StringEquals": {
                     "dynamodb:Attributes": [
                         "<COLUMN-NAME-1>",
                         "<COLUMN-NAME-2>",
                         "<COLUMN-NAME-3>"
                     ]
                 },
                 "StringEqualsIfExists": {
                     "dynamodb:Select": "SPECIFIC_ATTRIBUTES"
                 } 
             }
         }
     ]
 }
```