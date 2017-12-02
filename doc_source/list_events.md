# Actions and Condition Context Keys for Amazon CloudWatch Events<a name="list_events"></a>

Amazon CloudWatch Events \(service prefix: events\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon CloudWatch Events**

For information about controlling access to CloudWatch Events by using an IAM policy, see [Controlling User Access to Rules and Events](http://alpha-docs-aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsPoliciesRolesAccessControl.html) in the *Amazon CloudWatch User Guide*\.

+ `[events:PutEvents](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutEvents.html)`

+ `[events:DescribeRule](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DescribeRule.html)`

+ `[events:EnableRule](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_EnableRule.html)`

+ `[events:DisableRule](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DisableRule.html)`

+ `[events:PutRule](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutRule.html)`

+ `[events:PutTargets](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_PutTargets.html)`

+ `[events:DeleteRule](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_DeleteRule.html)`

+ `[events:ListRules](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListRules.html)`

+ `[events:TestEventPattern](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_TestEventPattern.html)`

+ `[events:RemoveTargets](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_RemoveTargets.html)`

+ `[events:ListRuleNamesByTarget](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListRuleNamesByTarget.html)`

+ `[events:ListTargetsByRule](http://alpha-docs-aws.amazon.com/AmazonCloudWatchEvents/latest/APIReference/API_ListTargetsByRule.html)`

**Condition context keys for Amazon CloudWatch Events**

For information about using condition keys to provide more granular control over CloudWatch Events with IAM policies, see [Condition Keys for CloudWatch Events](http://alpha-docs-aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsConditionKeys.html) in the *Amazon CloudWatch User Guide*\.

Amazon CloudWatch Events has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `[events: detail\.userIdentity\.principalId](http://alpha-docs-aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsConditionKeys.html)`

+ `[events:TargetArn](http://alpha-docs-aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsConditionKeys.html)`

+ `[events:detail\-type](http://alpha-docs-aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsConditionKeys.html)`

+ `[events:detail\.userIdentity\.principalId](http://alpha-docs-aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsConditionKeys.html)`

+ `[events:source](http://alpha-docs-aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsConditionKeys.html)`