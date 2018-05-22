# Amazon DynamoDB: Allows Row\-Level Access to DynamoDB Based on an Amazon Cognito ID<a name="reference_policies_examples_dynamodb_rows"></a>

This example shows how you might create a policy that allows row\-level access to a specific DynamoDB table based on an Amazon Cognito ID\.  This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

To use this policy, you must structure your DynamoDB table so the Cognito user ID is the partition key\. For more information, see [Creating a Table](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithTables.Basics.html#WorkingWithTables.Basics.CreateTable) in the *Amazon DynamoDB Developer Guide*\.

To learn more about DynamoDB condition keys, see [Specifying Conditions: Using Condition Keys](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html#FGAC_DDB.ConditionKeys) in the* Amazon DynamoDB Developer Guide*\.

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
             "Resource": [
                 "arn:aws:dynamodb:<REGION>:<ACCOUNTNUMBER>:table/<TABLE-NAME>"
             ],
             "Condition": {
                 "ForAllValues:StringEquals": {
                     "dynamodb:LeadingKeys": [
                         "${cognito-identity.amazonaws.com:sub}"
                     ]
                 }
             }
         }
     ]
 }
```