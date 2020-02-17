# Monitoring AWS IAM Access Analyzer with Amazon EventBridge<a name="access-analyzer-eventbridge"></a>

Use the information in this topic to learn how to monitor Access Analyzer findings with Amazon EventBridge\. EventBridge is the new version of Amazon CloudWatch Events\.

## Findings Events<a name="access-analyzer-events-findings"></a>

Access Analyzer sends an event to EventBridge for each generated finding, for a change to the status of an existing finding, and when a finding is deleted\. To receive findings and notifications about findings, you must create an event rule in Amazon EventBridge\. When you create an event rule, you can also specify a target action to trigger based on the rule\. For example, you could create an event rule that triggers an Amazon SNS topic when an event for a new finding is received from Access Analyzer\.

## Event Notification Frequency<a name="access-analyzer-event-frequency"></a>

Access Analyzer sends events for new findings and findings with status updates to EventBridge within about an hour from when the event occurs in your account\. Access Analyzer also sends events to EventBridge when a resolved finding is deleted because the retention period has expired\. For findings that are deleted because the analyzer that generated them is deleted, the event is sent to EventBridge approximately 24 hours after the analyzer was deleted\. When a finding is deleted, the finding status is not changed\. Instead, the `isDeleted` attribute is set to `true`\.

## Example Event<a name="access-analyzer-event-example"></a>

The following is an example Access Analyzer event sent to EventBridge\. The `id` listed is the ID for the event in EventBridge\. To learn more, see [Events and Event Patterns in EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eventbridge-and-event-patterns.html)\.

In the `detail` object, the values for the `accountId` and `region` attributes refer to the account and Region reported in the finding\. The `isDeleted` attribute indicates whether the event was from the finding being deleted\.

```
{
  "id": "22222222-dcba-4444-dcba-333333333333",
  "detail-type": "Access Analyzer Finding",
  "source": "aws.access-analyzer",
  "account": "111122223333",
  "time": "2019-11-21T01:22:33Z",
  "region": "us-west-2",
  "resources": [
    "arn:aws:access-analyzer:us-west-2:111122223333:analyzer/MyAnalyzer"
  ],
  "detail": {
      "version": "1.0",
      "accountId": "111122223333",
      "region": "us-west-2",
      "isDeleted": false,
      COMPLETE_ACCESS_ANALYZER_GET_FINDING_RESPONSE
    }
}
```

The `"id"` is the finding ID\. The `"resources"` array is a singleton with the ARN of the analyzer that generated the finding\.

The following example shows data for an event that is sent to EventBridge from the `GetFinding` operation of the Access Analyzer API\.

```
"version": "0",
  "id": "22222222-dcba-4444-dcba-333333333333",
  "status": "ACTIVE",
  "resourceType": "AWS::S3::Bucket",
  "resource": "arn:aws:s3:::my-bucket",
  "createdAt": "2019-11-20T04:58:50Z",
  "analyzedAt": "2019-11-21T01:22:22Z",
  "updatedAt": "2019-11-21T01:14:07Z",
  "principal": {"AWS": "999988887777"},
  "action": ["s3:GetObject"],
  "condition": {},
  "isPublic": false
```

Access Analyzer also sends events to EventBridge for error findings\. An error finding is a finding generated when Access Analyzer can't access a resource it tries to analyze\. Events for error findings include an `error` attribute as shown in the following example\.

```
"id": "22222222-dcba-4444-dcba-333333333333",
"status": "ACTIVE",
"resourceType": "AWS::S3::Bucket",
"resource": "arn:aws:s3:::my-bucket",
"error": "ACCESS_DENIED",
"createdAt": "2019-10-16T19:21:44.244Z",
"analyzedAt": "2019-10-16T19:21:44.244Z",
"updatedAt": "2019-10-16T19:21:44.244Z"
```

## Creating an Event Rule with a Target<a name="access-analyzer-create-rule"></a>

The following procedure describes how to create an event rule using the console\.

Open the Amazon EventBridge console at [https://console\.aws\.amazon\.com/events/](https://console.aws.amazon.com/events/)\.

1. Choose **Create rule**\.

1. Enter a **Name** and, optionally, a **Description**\.

1. Under **Define pattern** choose **Event pattern**, then choose **Custom pattern**\.

1. Copy the following example and then paste it into the **Event pattern** box\.

   ```
   {
     "source": [
       "aws.access-analyzer"
     ],
     "detail-type": [
       "Access Analyzer Finding"
     ]
   }
   ```

1. Choose **Save**\.

1. Under **Select targets**, choose a **Target** action for the rule, such as an Amazon SNS topic or AWS Lambda function\. 

1. Choose the specific SNS topic or Lambda function to use when the target is triggered\.

   The target is triggered when an event is received that matches the event pattern defined in the rule\.

1. Choose **Save** to create the rule\.

To learn more about creating rules, see [Creating an EventBridge Rule That Triggers on an Event from an AWS Resource](https://docs.aws.amazon.com/eventbridge/latest/userguide/create-eventbridge-rule.html)\.

### Create a Rule Using the CLI<a name="access-analyzer-create-rule-cli"></a>

1. Use the following to create a rule for Amazon EventBridge using the AWS CLI\. Replace the rule name *TestRule* with the name for your rule\.

   ```
   aws events put-rule --name TestRule --event-pattern "{\"source\":[\"aws.access-analyzer\"]}"
   ```

1. You can customize the rule to trigger target actions only for a subset of generated findings, such as findings with specific attributes\. The following example demonstrates how to create a rule that triggers a target action only for findings with a status of Active\.

   ```
   aws events put-rule --name TestRule --event-pattern "{\"source\":[\"aws.access-analyzer\"],\"detail-type\":[\"Access Analyzer Finding\"],\"detail\":{\"status\":[\"ACTIVE\"]}}"
   ```

1. To define a Lambda function as a target for the rule you created, use the following example command\. Replace the Region and the function name in the ARN as appropriate for your environment\.

   ```
   aws events put-targets --rule TestRule --targets Id=1,Arn=arn:aws:lambda:us-east-1:111122223333:function:MyFunction
   ```

1. Add the permissions required to invoke the rule target\. The following example demonstrates how to grant permissions to a Lambda function, following the preceding examples\.

   ```
   aws lambda add-permission --function-name MyFunction --statement-id 1 --action 'lambda:InvokeFunction' --principal events.amazonaws.com
   ```