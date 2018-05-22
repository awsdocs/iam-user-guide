# Amazon DynamoDB: Allows Access to a Specific Table<a name="reference_policies_examples_dynamodb_specific-table"></a>

This example shows how you might create a policy that allows full access to a DynamoDB table with the specified name\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

**Important**  
This policy allows all actions that can be performed on a DynamoDB table\. To review these actions, see [DynamoDB API Permissions: Actions, Resources, and Conditions Reference](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/api-permissions-reference.html) in the* Amazon DynamoDB Developer Guide*\. You could provide the same permissions by listing each individual action\. However, if you use the `"Action":"dynamodb:*"` element, then you will not need to update your policy if DynamoDB adds a new action for DynamoDB tables\. 

This policy allows actions only on DynamoDB tables that exist with the specified name\. To allow your users `Read` access to everything in DynamoDB, you can also attach the [AmazonDynamoDBReadOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AmazonDynamoDBReadOnlyAccess) AWS managed policy\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "dynamodb:*",
      "Resource": "arn:aws:dynamodb:<REGION>:<ACCOUNTNUMBER>:table/<TABLE-NAME>"
    }
  ]
}
```