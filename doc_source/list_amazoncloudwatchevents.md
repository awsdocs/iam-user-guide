# Actions, Resources, and Condition Keys for Amazon CloudWatch Events<a name="list_amazoncloudwatchevents"></a>

Amazon CloudWatch Events \(service prefix: `events`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/auth-and-access-control-cwe.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon CloudWatch Events](#amazoncloudwatchevents-actions-as-permissions)
+ [Resources Defined by CloudWatch Events](#amazoncloudwatchevents-resources-for-iam-policies)
+ [Condition Keys for Amazon CloudWatch Events](#amazoncloudwatchevents-policy-keys)

## Actions Defined by Amazon CloudWatch Events<a name="amazoncloudwatchevents-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DeleteRule.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DeleteRule.html) | Deletes a rule\. You must remove all targets from a rule using RemoveTargets before you can delete the rule\. | Write | [rule\*](#amazoncloudwatchevents-rule)  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DescribeEventBus.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DescribeEventBus.html) | Displays the external AWS accounts that are permitted to write events to your account using your account's event bus, and the associated policy\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DescribeRule.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DescribeRule.html) | Describes the details of the specified rule | Read | [rule\*](#amazoncloudwatchevents-rule)  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DisableRule.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DisableRule.html) | Disables a rule\. A disabled rule won't match any events, and won't self\-trigger if it has a schedule expression\. | Write | [rule\*](#amazoncloudwatchevents-rule)  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_EnableRule.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_EnableRule.html) | Enables a rule\. If the rule does not exist, the operation fails | Write | [rule\*](#amazoncloudwatchevents-rule)  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListRuleNamesByTarget.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListRuleNamesByTarget.html) | Lists the names of the rules that the given target is put to | List | [rule\*](#amazoncloudwatchevents-rule)  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListRules.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListRules.html) | Lists the Amazon CloudWatch Events rules in your account | List | [rule\*](#amazoncloudwatchevents-rule)  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListTargetsByRule.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListTargetsByRule.html) | Lists of targets assigned to the rule | List | [rule\*](#amazoncloudwatchevents-rule)  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutEvents.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutEvents.html) | Sends custom events to Amazon CloudWatch Events so that they can be matched to rules | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutPermission.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutPermission.html) | Running PutPermission permits the specified AWS account to put events to your account's default event bus\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutRule.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutRule.html) | Creates or updates a rule\. Rules are enabled by default, or based on value of the State parameter | Write |  | [events:detail\.userIdentity\.principalId](#amazoncloudwatchevents-events_detail.userIdentity.principalId) [events:detail\-type](#amazoncloudwatchevents-events_detail-type) [events:source](#amazoncloudwatchevents-events_source)  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutTargets.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutTargets.html) | Adds target\(s\) to a rule\. Targets are the resources that can be invoked when a rule is triggered | Write |  | [events:TargetArn](#amazoncloudwatchevents-events_TargetArn)  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_RemovePermission.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_RemovePermission.html) | Revokes the permission of another AWS account to be able to put events to your default event bus\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_RemoveTargets.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_RemoveTargets.html) | Removes target\(s\) from a rule so that when the rule is triggered, those targets will no longer be invoked | Write | [rule\*](#amazoncloudwatchevents-rule)  |  |  | 
| [http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_TestEventPattern.html](http://docs.aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_TestEventPattern.html) | Tests whether an event pattern matches the provided event | Read |  |  |  | 

## Resources Defined by CloudWatch Events<a name="amazoncloudwatchevents-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncloudwatchevents-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/iam-access-control-identity-based-cwe.html#CWE_ARN_Format](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/iam-access-control-identity-based-cwe.html#CWE_ARN_Format) | arn:$\{Partition\}:events:$\{Region\}:$\{Account\}:rule/$\{RuleName\} |  | 

## Condition Keys for Amazon CloudWatch Events<a name="amazoncloudwatchevents-policy-keys"></a>

Amazon CloudWatch Events defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.

For information about using condition keys to provide more granular control over CloudWatch Events with IAM policies, see [Condition Keys for CloudWatch Events](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsConditionKeys.html) in the *Amazon CloudWatch User Guide*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#LimitingAccessToTargets](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#LimitingAccessToTargets) | The ARN of a target that can be put to a rule\. | ARN | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#EventsPatternDetailType](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#EventsPatternDetailType) | Matches the literal string of the detail\-type filed of the event\. | String | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#ConsumeSpecificEvents](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#ConsumeSpecificEvents) | Matches the literal string for the detail\.useridentity\.principalid field of the event\. | String | 
| [http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#EventsLimitAccessControl](http://docs.aws.amazon.com/AmazonCloudWatch/latest/events/policy-keys-cwe.html#EventsLimitAccessControl) | The AWS service that generated the event\. Matches the literal string of the source field of the event\. | String | 