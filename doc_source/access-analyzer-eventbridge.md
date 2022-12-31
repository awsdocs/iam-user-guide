# Monitoring AWS Identity and Access Management Access Analyzer with Amazon EventBridge<a name="access-analyzer-eventbridge"></a>

Use the information in this topic to learn how to monitor IAM Access Analyzer findings and access previews with Amazon EventBridge\. EventBridge is the new version of Amazon CloudWatch Events\.

## Findings events<a name="access-analyzer-events-findings"></a>

IAM Access Analyzer sends an event to EventBridge for each generated finding, for a change to the status of an existing finding, and when a finding is deleted\. To receive findings and notifications about findings, you must create an event rule in Amazon EventBridge\. When you create an event rule, you can also specify a target action to trigger based on the rule\. For example, you could create an event rule that triggers an Amazon SNS topic when an event for a new finding is received from IAM Access Analyzer\.

## Access preview events<a name="access-analyzer-access-preview-events"></a>

IAM Access Analyzer sends an event to EventBridge for each access preview and change to its status\. This includes an event when the access preview is first created \(status Creating\), when the access preview is complete \(status Completed\), or when the access preview creation failed \(status Failed\)\. To receive notifications about access previews, you must create an event rule in EventBridge\. When you create an event rule, you can specify a target action to trigger based on the rule\. For example, you could create an event rule that triggers an Amazon SNS topic when an event for a completed access preview is received from IAM Access Analyzer\. 

## Event notification frequency<a name="access-analyzer-event-frequency"></a>

IAM Access Analyzer sends events for new findings and findings with status updates to EventBridge within about an hour from when the event occurs in your account\. IAM Access Analyzer also sends events to EventBridge when a resolved finding is deleted because the retention period has expired\. For findings that are deleted because the analyzer that generated them is deleted, the event is sent to EventBridge approximately 24 hours after the analyzer was deleted\. When a finding is deleted, the finding status is not changed\. Instead, the `isDeleted` attribute is set to `true`\. IAM Access Analyzer also sends events for newly created access previews and access preview status changes to EventBridge\.



## Example findings events<a name="access-analyzer-event-example"></a>

The following is an example IAM Access Analyzer event sent to EventBridge\. The `id` listed is the ID for the event in EventBridge\. To learn more, see [Events and Event Patterns in EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eventbridge-and-event-patterns.html)\.

In the `detail` object, the values for the `accountId` and `region` attributes refer to the account and region reported in the finding\. The `isDeleted` attribute indicates whether the event was from the finding being deleted\. The `id` is the finding ID\. The `resources` array is a singleton with the ARN of the analyzer that generated the finding\.

```
{
    "account": "111122223333",
    "detail": {
        "accountId": "111122223333",
        "action": [
            "s3:GetObject"
        ],
        "analyzedAt": "2019-11-21T01:22:22Z",
        "condition": {},
        "createdAt": "2019-11-20T04:58:50Z",
        "id": "22222222-dcba-4444-dcba-333333333333",
        "isDeleted": false,
        "isPublic": false,
        "principal": {
            "AWS": "999988887777"
        },
        "region": "us-west-2",
        "resource": "arn:aws:s3:::my-bucket",
        "resourceType": "AWS::S3::Bucket",
        "status": "ACTIVE",
        "updatedAt": "2019-11-21T01:14:07Z",
        "version": "1.0"
    },
    "detail-type": "Access Analyzer Finding",
    "id": "11111111-2222-4444-aaaa-333333333333",
    "region": "us-west-2",
    "resources": [
        "arn:aws:access-analyzer:us-west-2:111122223333:analyzer/MyAnalyzer"
    ],
    "source": "aws.access-analyzer",
    "time": "2019-11-21T01:22:33Z",
    "version": "0"
}
```

IAM Access Analyzer also sends events to EventBridge for error findings\. An error finding is a finding generated when IAM Access Analyzer can't analyze the resource\. Events for error findings include an `error` attribute as shown in the following example\.

```
{
    "account": "111122223333",
    "detail": {
        "accountId": "111122223333",
        "analyzedAt": "2019-11-21T01:22:22Z",
        "createdAt": "2019-11-20T04:58:50Z",
        "error": "ACCESS_DENIED",
        "id": "22222222-dcba-4444-dcba-333333333333",
        "isDeleted": false,
        "region": "us-west-2",
        "resource": "arn:aws:s3:::my-bucket",
        "resourceType": "AWS::S3::Bucket",
        "status": "ACTIVE",
        "updatedAt": "2019-11-21T01:14:07Z",
        "version": "1.0"
    },
    "detail-type": "Access Analyzer Finding",
    "id": "11111111-2222-4444-aaaa-333333333333",
    "region": "us-west-2",
    "resources": [
        "arn:aws:access-analyzer:us-west-2:111122223333:analyzer/MyAnalyzer"
    ],
    "source": "aws.access-analyzer",
    "time": "2019-11-21T01:22:33Z",
    "version": "0"
}
```

## Example access preview events<a name="access-analyzer-example-access-preview-events"></a>

The following example shows data for the first event that is sent to EventBridge when you create an access preview\. The `resources` array is a singleton with the ARN of the analyzer that the access preview is associated with\. In the `detail` object, the `id` refers to the access preview ID and `configuredResources` refers to the resource for which the access preview was created\. The `status` is `Creating` and refers to the access preview status\. The `previousStatus` is not specified because the access preview was just created\. 

```
{
    "account": "111122223333",
    "detail": {
        "accessPreviewId": "aaaabbbb-cccc-dddd-eeee-ffffaaaabbbb",
        "configuredResources": [
            "arn:aws:s3:::example-bucket"
        ],
        "createdAt": "2020-02-20T00:00:00.00Z",
        "region": "us-west-2",
        "status": "CREATING",
        "version": "1.0"
    },
    "detail-type": "Access Preview State Change",
    "id": "aaaabbbb-2222-3333-4444-555566667777",
    "region": "us-west-2",
    "resources": [
        "arn:aws:access-analyzer:us-west-2:111122223333:analyzer/MyAnalyzer"
    ],
    "source": "aws.access-analyzer",
    "time": "2020-02-20T00:00:00.00Z",
    "version": "0"
}
```

The following example shows data for an event that is sent to EventBridge for an access preview with a status change from `Creating` to `Completed`\. In the detail object, the `id` refers to the access preview ID\. The `status` and `previousStatus` refer to the access preview status, where the previous status was `Creating` and the current status is `Completed`\. 

```
{
    "account": "111122223333",
    "detail": {
        "accessPreviewId": "aaaabbbb-cccc-dddd-eeee-ffffaaaabbbb",
        "configuredResources": [
            "arn:aws:s3:::example-bucket"
        ],
        "createdAt": "2020-02-20T00:00:00.000Z",
        "previousStatus": "CREATING",
        "region": "us-west-2",
        "status": "COMPLETED",
        "version": "1.0"
    },
    "detail-type": "Access Preview State Change",
    "id": "11112222-3333-4444-5555-666677778888",
    "region": "us-west-2",
    "resources": [
        "arn:aws:access-analyzer:us-west-2:111122223333:analyzer/MyAnalyzer"
    ],
    "source": "aws.access-analyzer",
    "time": "2020-02-20T00:00:00.00Z",
    "version": "0"
}
```

The following example shows data for an event that is sent to EventBridge for an access preview with a status change from `Creating` to `Failed`\. In the `detail` object, the `id` refers to the access preview ID\. The `status` and `previousStatus` refer to the access preview status, where the previous status was `Creating` and the current status is `Failed`\. The `statusReason` field provides the reason code indicating that the access preview failed due to an invalid resource configuration\.

```
{
    "account": "111122223333",
    "detail": {
        "accessPreviewId": "aaaabbbb-cccc-dddd-eeee-ffffaaaabbbb",
        "configuredResources": [
            "arn:aws:s3:::example-bucket"
        ],
        "createdAt": "2020-02-20T00:00:00.00Z",
        "previousStatus": "CREATING",
        "region": "us-west-2",
        "status": "FAILED",
        "statusReason": {
            "code": "INVALID_CONFIGURATION"
        },
        "version": "1.0"
    },
    "detail-type": "Access Preview State Change",
    "id": "99998888-7777-6666-5555-444433332222",
    "region": "us-west-2",
    "resources": [
        "arn:aws:access-analyzer:us-west-2:111122223333:analyzer/MyAnalyzer"
    ],
    "source": "aws.access-analyzer",
    "time": "2020-02-20T00:00:00.00Z",
    "version": "0"
}
```

## Creating an event rule using the console<a name="access-analyzer-create-rule"></a>

The following procedure describes how to create an event rule using the console\.

1. Open the Amazon EventBridge console at [https://console\.aws\.amazon\.com/events/](https://console.aws.amazon.com/events/)\.

1. Using the following values, create an EventBridge rule that monitors finding events or access preview events:
   + For **Rule type**, choose **Rule with an event pattern**\.
   + For **Event source**, choose **Other**\.
   + For **Event pattern**, choose **Custom patterns \(JSON editor\)**, and paste one of the following event pattern examples into the text area:
     + To create a rule based on a findings event, use the following pattern example:

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
     + To create a rule based on an access preview event, use the following pattern example:

       ```
       {
         "source": [
           "aws.access-analyzer"
         ],
         "detail-type": [
           "Access Preview State Change"
         ]
       }
       ```
   + For **Target types**, choose **AWS service**, and for **Select a target**, choose a target such as an Amazon SNS topic or AWS Lambda function\. The target is triggered when an event is received that matches the event pattern defined in the rule\.

   To learn more about creating rules, see [Creating Amazon EventBridge rules that react to events](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-create-rule.html) in the *Amazon EventBridge User Guide*\.

### Creating an event rule using the CLI<a name="access-analyzer-create-rule-cli"></a>

1. Use the following to create a rule for Amazon EventBridge using the AWS CLI\. Replace the rule name *TestRule* with the name for your rule\.

   ```
   aws events put-rule --name TestRule --event-pattern "{\"source\":[\"aws.access-analyzer\"]}"
   ```

1. You can customize the rule to trigger target actions only for a subset of generated findings, such as findings with specific attributes\. The following example demonstrates how to create a rule that triggers a target action only for findings with a status of Active\.

   ```
   aws events put-rule --name TestRule --event-pattern "{\"source\":[\"aws.access-analyzer\"],\"detail-type\":[\"Access Analyzer Finding\"],\"detail\":{\"status\":[\"ACTIVE\"]}}"
   ```

   The following example demonstrates how to create a rule that triggers a target action only for access previews with a status from `Creating` to `Completed`\.

   ```
   aws events put-rule --name TestRule --event-pattern "{\"source\":[\"aws.access-analyzer\"],\"detail-type\":[\"Access Preview State Change\"],\"detail\":{\"status\":[\"COMPLETED\"]}}"
   ```

1. To define a Lambda function as a target for the rule you created, use the following example command\. Replace the Region and the function name in the ARN as appropriate for your environment\.

   ```
   aws events put-targets --rule TestRule --targets Id=1,Arn=arn:aws:lambda:us-east-1:111122223333:function:MyFunction
   ```

1. Add the permissions required to invoke the rule target\. The following example demonstrates how to grant permissions to a Lambda function, following the preceding examples\.

   ```
   aws lambda add-permission --function-name MyFunction --statement-id 1 --action 'lambda:InvokeFunction' --principal events.amazonaws.com
   ```