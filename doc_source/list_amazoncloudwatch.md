# Actions, Resources, and Condition Keys for Amazon CloudWatch<a name="list_amazoncloudwatch"></a>

Amazon CloudWatch \(service prefix: `cloudwatch`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/auth-and-access-control-cw.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon CloudWatch](#amazoncloudwatch-actions-as-permissions)
+ [Resources Defined by CloudWatch](#amazoncloudwatch-resources-for-iam-policies)
+ [Condition Keys for Amazon CloudWatch](#amazoncloudwatch-policy-keys)

## Actions Defined by Amazon CloudWatch<a name="amazoncloudwatch-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DeleteAlarms.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DeleteAlarms.html) | Deletes all specified alarms\. In the event of an error, no alarms are deleted | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DeleteDashboards.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DeleteDashboards.html) | Deletes all CloudWatch dashboards that you specify | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarmHistory.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarmHistory.html) | Retrieves history for the specified alarm | Read |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarms.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarms.html) | Retrieves alarms with the specified names | Read |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarmsForMetric.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarmsForMetric.html) | Retrieves all alarms for a single metric | Read |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DisableAlarmActions.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DisableAlarmActions.html) | Disables actions for the specified alarms | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_EnableAlarmActions.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_EnableAlarmActions.html) | Enables actions for the specified alarms | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_GetDashboard.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_GetDashboard.html) | Displays the details of the CloudWatch dashboard you specify | Read |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_GetMetricData.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_GetMetricData.html) | Required to retrieve batch amounts of CloudWatch metric data and perform metric math on retrieved data | Read |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_GetMetricStatistics.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_GetMetricStatistics.html) | Gets statistics for the specified metric | Read |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_ListDashboards.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_ListDashboards.html) | Returns a list of all CloudWatch dashboards in your account | List |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_ListMetrics.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_ListMetrics.html) | Returns a list of valid metrics stored for the AWS account owner | List |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_PutDashboard.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_PutDashboard.html) | Creates a CloudWatch dashboard, or updates an existing dashboard if it already exists | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_PutMetricAlarm.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_PutMetricAlarm.html) | Creates or updates an alarm and associates it with the specified Amazon CloudWatch metric | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_PutMetricData.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_PutMetricData.html) | Publishes metric data points to Amazon CloudWatch | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_SetAlarmState.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_SetAlarmState.html) | Temporarily sets the state of an alarm for testing purposes | Write |  |  |  | 

## Resources Defined by CloudWatch<a name="amazoncloudwatch-resources-for-iam-policies"></a>

CloudWatch has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon CloudWatch<a name="amazoncloudwatch-policy-keys"></a>

CloudWatch has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.