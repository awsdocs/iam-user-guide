# Actions and Condition Context Keys for Amazon CloudWatch<a name="list_cloudwatch"></a>

Amazon CloudWatch \(service prefix: cloudwatch\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon CloudWatch**

For information about using the following CloudWatch API actions in an IAM policy, see [CloudWatch Actions](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/UsingIAM.html#UsingWithCloudWatch_Actions) in the *Amazon CloudWatch User Guide*\.
+ `[cloudwatch:DeleteAlarms](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DeleteAlarms.html)`
+ `[cloudwatch:DescribeAlarmHistory](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarmHistory.html)`
+ `[cloudwatch:DescribeAlarms](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarms.html)`
+ `[cloudwatch:DescribeAlarmsForMetric](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DescribeAlarmsForMetric.html)`
+ `[cloudwatch:DisableAlarmActions](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_DisableAlarmActions.html)`
+ `[cloudwatch:EnableAlarmActions](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_EnableAlarmActions.html)`
+ `[cloudwatch:GetMetricData](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/permissions-reference-cw.html#cw-permissions-table)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[cloudwatch:GetMetricStatistics](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_GetMetricStatistics.html)`
+ `[cloudwatch:ListMetrics](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_ListMetrics.html)`
+ `[cloudwatch:PutMetricAlarm](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_PutMetricAlarm.html)`
+ `[cloudwatch:PutMetricData](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_PutMetricData.html)`
+ `[cloudwatch:SetAlarmState](http://docs.aws.amazon.com/AmazonCloudWatch/latest/APIReference/API_SetAlarmState.html)`

**Condition context keys for Amazon CloudWatch**

For information about using conditions to control access to CloudWatch in an IAM policy, see [CloudWatch Keys](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/UsingIAM.html#CloudWatch_Keys) in the *Amazon CloudWatch User Guide*\.

Amazon CloudWatch has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.