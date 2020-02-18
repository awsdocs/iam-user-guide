# Actions, Resources, and Condition Keys for Amazon CloudWatch Logs<a name="list_amazoncloudwatchlogs"></a>

Amazon CloudWatch Logs \(service prefix: `logs`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/auth-and-access-control-cw.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon CloudWatch Logs](#amazoncloudwatchlogs-actions-as-permissions)
+ [Resource Types Defined by Amazon CloudWatch Logs](#amazoncloudwatchlogs-resources-for-iam-policies)
+ [Condition Keys for Amazon CloudWatch Logs](#amazoncloudwatchlogs-policy-keys)

## Actions Defined by Amazon CloudWatch Logs<a name="amazoncloudwatchlogs-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateKmsKey ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_AssociateKmsKey.html)  | Associates the specified AWS Key Management Service \(AWS KMS\) customer master key \(CMK\) with the specified log group\. | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ CancelExportTask ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_CancelExportTask.html)  | Cancels an export task if it is in PENDING or RUNNING state | Write |  |  |  | 
|   [ CreateExportTask ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_CreateExportTask.html)  | Creates an ExportTask which allows you to efficiently export data from a Log Group to your Amazon S3 bucket | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   CreateLogDelivery \[permission only\] | Creates the log delivery | Write |  |  |  | 
|   [ CreateLogGroup ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_CreateLogGroup.html)  | Creates a new log group with the specified name | Write |  |  |  | 
|   [ CreateLogStream ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_CreateLogStream.html)  | Creates a new log stream with the specified name | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DeleteDestination ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DeleteDestination.html)  | Deletes the destination with the specified name and eventually disables all the subscription filters that publish to it | Write |  |  |  | 
|   DeleteLogDelivery \[permission only\] | Deletes the log delivery information for specified log delivery | Write |  |  |  | 
|   [ DeleteLogGroup ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DeleteLogGroup.html)  | Deletes the log group with the specified name and permanently deletes all the archived log events associated with it | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DeleteLogStream ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DeleteLogStream.html)  | Deletes a log stream and permanently deletes all the archived log events associated with it | Write |   [ log\-stream\* ](#amazoncloudwatchlogs-log-stream)   |  |  | 
|   [ DeleteMetricFilter ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DeleteMetricFilter.html)  | Deletes a metric filter associated with the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DeleteResourcePolicy ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DeleteResourcePolicy.html)  | Deletes a resource policy from this account | Write |  |  |  | 
|   [ DeleteRetentionPolicy ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DeleteRetentionPolicy.html)  | Deletes the retention policy of the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DeleteSubscriptionFilter ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DeleteSubscriptionFilter.html)  | Deletes a subscription filter associated with the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DescribeDestinations ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DescribeDestinations.html)  | Returns all the destinations that are associated with the AWS account making the request | List |  |  |  | 
|   [ DescribeExportTasks ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DescribeExportTasks.html)  | Returns all the export tasks that are associated with the AWS account making the request | List |  |  |  | 
|   [ DescribeLogGroups ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DescribeLogGroups.html)  | Returns all the log groups that are associated with the AWS account making the request | List |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DescribeLogStreams ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DescribeLogStreams.html)  | Returns all the log streams that are associated with the specified log group | List |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DescribeMetricFilters ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DescribeMetricFilters.html)  | Returns all the metrics filters associated with the specified log group | List |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DescribeQueries ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DescribeQueries.html)  | Returns a list of CloudWatch Logs Insights queries that are scheduled, executing, or have been executed recently in this account\. You can request all queries, or limit it to queries of a specific log group or queries with a certain status\. | List |  |  |  | 
|   [ DescribeResourcePolicies ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DescribeResourcePolicies.html)  | Return all the resource policies in this account\. | List |  |  |  | 
|   [ DescribeSubscriptionFilters ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DescribeSubscriptionFilters.html)  | Returns all the subscription filters associated with the specified log group | List |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ DisassociateKmsKey ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_DisassociateKmsKey.html)  | Disassociates the associated AWS Key Management Service \(AWS KMS\) customer master key \(CMK\) from the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ FilterLogEvents ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_FilterLogEvents.html)  | Retrieves log events, optionally filtered by a filter pattern from the specified log group | Read |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   GetLogDelivery \[permission only\] | Gets the log delivery information for specified log delivery | Read |  |  |  | 
|   [ GetLogEvents ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_GetLogEvents.html)  | Retrieves log events from the specified log stream | Read |   [ log\-stream\* ](#amazoncloudwatchlogs-log-stream)   |  |  | 
|   [ GetLogGroupFields ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_GetLogGroupFields.html)  | Returns a list of the fields that are included in log events in the specified log group, along with the percentage of log events that contain each field\. The search is limited to a time period that you specify\. | Read |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ GetLogRecord ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_GetLogRecord.html)  | Retrieves all the fields and values of a single log event\. All fields are retrieved, even if the original query that produced the logRecordPointer retrieved only a subset of fields\. Fields are returned as field name/field value pairs\. | Read |  |  |  | 
|   [ GetQueryResults ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_GetQueryResults.html)  | Returns the results from the specified query\. If the query is in progress, partial results of that current execution are returned\. Only the fields requested in the query are returned\. | Read |  |  |  | 
|   ListLogDeliveries \[permission only\] | Lists all the log deliveries for specified account and/or log source | List |  |  |  | 
|   [ ListTagsLogGroup ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_ListTagsLogGroup.html)  | Lists the tags for the specified log group | List |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ PutDestination ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutDestination.html)  | Creates or updates a Destination | Write |  |  |  | 
|   [ PutDestinationPolicy ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutDestinationPolicy.html)  | Creates or updates an access policy associated with an existing Destination | Write |  |  |  | 
|   [ PutLogEvents ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutLogEvents.html)  | Uploads a batch of log events to the specified log stream | Write |   [ log\-stream\* ](#amazoncloudwatchlogs-log-stream)   |  |  | 
|   [ PutMetricFilter ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutMetricFilter.html)  | Creates or updates a metric filter and associates it with the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ PutResourcePolicy ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutResourcePolicy.html)  | Creates or updates a resource policy allowing other AWS services to put log events to this account | Write |  |  |  | 
|   [ PutRetentionPolicy ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutRetentionPolicy.html)  | Sets the retention of the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ PutSubscriptionFilter ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_PutSubscriptionFilter.html)  | Creates or updates a subscription filter and associates it with the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ StartQuery ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_StartQuery.html)  | Schedules a query of a log group using CloudWatch Logs Insights\. You specify the log group and time range to query, and the query string to use\. | Read |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ StopQuery ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_StopQuery.html)  | Stops a CloudWatch Logs Insights query that is in progress\. If the query has already ended, the operation returns an error indicating that the specified query is not running\. | Read |  |  |  | 
|   [ TagLogGroup ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_TagLogGroup.html)  | Adds or updates the specified tags for the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   [ TestMetricFilter ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_TestMetricFilter.html)  | Tests the filter pattern of a metric filter against a sample of log event messages | Read |  |  |  | 
|   [ UntagLogGroup ](https://docs.aws.amazon.com/AmazonCloudWatchLogs/latest/APIReference/API_UntagLogGroup.html)  | Removes the specified tags from the specified log group | Write |   [ log\-group\* ](#amazoncloudwatchlogs-log-group)   |  |  | 
|   UpdateLogDelivery \[permission only\] | Updates the log delivery information for specified log delivery | Write |  |  |  | 

## Resource Types Defined by Amazon CloudWatch Logs<a name="amazoncloudwatchlogs-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncloudwatchlogs-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   log\-group  |  arn:$\{Partition\}:logs:$\{Region\}:$\{Account\}:log\-group:$\{LogGroupName\}  |  | 
|   log\-stream  |  arn:$\{Partition\}:logs:$\{Region\}:$\{Account\}:log\-group:$\{LogGroupName\}:log\-stream:$\{LogStreamName\}  |  | 

### Restricting Permissions to Specific Log-Streams

When restricting action permissions to a specific set of log-streams, you must **also** specify a similar log-group in your resource constraints. For example, assume you have the following log-group:

```
arn:aws:logs:us-east-1:1234567890:log-group:MyApplicationLogGroup
```

If portions of your application generated log-streams within that log group, their ARNs might look something like this:

```
arn:aws:logs:us-east-1:1234567890:log-group:MyApplicationLogGroup:log-stream:MyApplicationLogStream1
arn:aws:logs:us-east-1:1234567890:log-group:MyApplicationLogGroup:log-stream:MyApplicationLogStream2
arn:aws:logs:us-east-1:1234567890:log-group:MyApplicationLogGroup:log-stream:MyApplicationLogStream3
```

If you had a separate resource whose only job was to read log data, you would need to specify **both** the log-group and the log-stream resources within your policy statement when granting the GetLogEvents permission:

```
{
  "Version" : "2012-10-17",
  "Statement" : [
    {
      "Sid" : "GrantLimitedLogAccess",
      "Effect" : "Allow",
      "Action": [
        "logs:GetLogEvents"
      "Resource": [
        "arn:aws:logs:us-east-1:1234567890:log-group:MyApplicationLog",
        "arn:aws:logs:us-east-1:1234567890:log-group:MyApplicationLog:log-stream:*
      ]
    }
  ]
}
```

This same logic applies to all actions requiring a log-stream resource identifier. If the log-group resource identifier is already included for use by some other action such as logs:CreateLogStream in the same statement, then any log-stream permissions would receive log-group permissions from that resource identifier. Therefore, the following policy would allow the policy holder to create new log-groups and log-streams for your application, as well as write to them:

```
{
  "Version" : "2012-10-17",
  "Statement" : [
    {
      "Sid" : "GrantLimitedLogAccess",
      "Effect" : "Allow",
      "Action": [
        "logs:CreateLogGroup"
        "logs:CreateLogStream,
        "logs:PutLogEvents"
      "Resource": [
        "arn:aws:logs:us-east-1:1234567890:log-group:MyApplicationLog",
        "arn:aws:logs:us-east-1:1234567890:log-group:MyApplicationLog:log-stream:*
      ]
    }
  ]
}
```

## Condition Keys for Amazon CloudWatch Logs<a name="amazoncloudwatchlogs-policy-keys"></a>

CloudWatch Logs has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.
