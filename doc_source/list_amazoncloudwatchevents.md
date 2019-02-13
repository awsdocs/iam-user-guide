# Actions, Resources, and Condition Keys for Amazon CloudWatch Events<a name="list_amazoncloudwatchevents"></a>

Amazon CloudWatch Events \(service prefix: `events`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/auth-and-access-control-cwe.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon CloudWatch Events](#amazoncloudwatchevents-actions-as-permissions)
+ [Resources Defined by CloudWatch Events](#amazoncloudwatchevents-resources-for-iam-policies)
+ [Condition Keys for Amazon CloudWatch Events](#amazoncloudwatchevents-policy-keys)

## Actions Defined by Amazon CloudWatch Events<a name="amazoncloudwatchevents-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazoncloudwatchevents.html)

## Resources Defined by CloudWatch Events<a name="amazoncloudwatchevents-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncloudwatchevents-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ rule ](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/iam-access-control-identity-based-cwe.html#CWE_ARN_Format)  |  arn:$\{Partition\}:events:$\{Region\}:$\{Account\}:rule/$\{RuleName\}  |  | 

## Condition Keys for Amazon CloudWatch Events<a name="amazoncloudwatchevents-policy-keys"></a>

Amazon CloudWatch Events defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.

For information about using condition keys to provide more granular control over CloudWatch Events with IAM policies, see [Condition Keys for CloudWatch Events](https://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsConditionKeys.html) in the *Amazon CloudWatch User Guide*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ events:TargetArn ](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#LimitingAccessToTargets)  | The ARN of a target that can be put to a rule\. | ARN | 
|   [ events:detail\-type ](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#EventsPatternDetailType)  | Matches the literal string of the detail\-type filed of the event\. | String | 
|   [ events:detail\.eventTypeCode ](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#LimitRuleByTypeCode)  | Matches the literal string for the detail\.eventTypeCode field of the event\. | String | 
|   [ events:detail\.service ](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#LimitRuleByService)  | Matches the literal string for the detail\.service field of the event\. | String | 
|   [ events:detail\.userIdentity\.principalId ](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#ConsumeSpecificEvents)  | Matches the literal string for the detail\.useridentity\.principalid field of the event\. | String | 
|   [ events:source ](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#EventsLimitAccessControl)  | The AWS service that generated the event\. Matches the literal string of the source field of the event\. | String | 