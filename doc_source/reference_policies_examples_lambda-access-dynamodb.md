# AWS Lambda: Allows a Lambda function to access an Amazon DynamoDB table<a name="reference_policies_examples_lambda-access-dynamodb"></a>

This example shows how you might create a policy that allows read and write access to a specific Amazon DynamoDB table\. The policy also allows writing log files to CloudWatch Logs\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

To use this policy, attach the policy to a Lambda [service role](id_roles_create_for-service.md)\. A service role is a role that you create in your account to allow a service to perform actions on your behalf\. That service role must include AWS Lambda as the principal in the trust policy\. For details about how to use this policy, see [How to Create an AWS IAM Policy to Grant AWS Lambda Access to an Amazon DynamoDB Table](http://aws.amazon.com/blogs/security/how-to-create-an-aws-iam-policy-to-grant-aws-lambda-access-to-an-amazon-dynamodb-table/) in the *AWS Security Blog*\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ReadWriteTable",
            "Effect": "Allow",
            "Action": [
                "dynamodb:BatchGetItem",
                "dynamodb:GetItem",
                "dynamodb:Query",
                "dynamodb:Scan",
                "dynamodb:BatchWriteItem",
                "dynamodb:PutItem",
                "dynamodb:UpdateItem"
            ],
            "Resource": "arn:aws:dynamodb:*:*:table/SampleTable"
        },
        {
            "Sid": "GetStreamRecords",
            "Effect": "Allow",
            "Action": "dynamodb:GetRecords",
            "Resource": "arn:aws:dynamodb:*:*:table/SampleTable/stream/* "
        },
        {
            "Sid": "WriteLogStreamsAndGroups",
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Resource": "*"
        },
        {
            "Sid": "CreateLogGroup",
            "Effect": "Allow",
            "Action": "logs:CreateLogGroup",
            "Resource": "*"
        }
    ]
}
```