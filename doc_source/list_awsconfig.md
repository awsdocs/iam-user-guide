# Actions, Resources, and Condition Keys for AWS Config<a name="list_awsconfig"></a>

AWS Config \(service prefix: `config`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/config/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/config/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/config/latest/developerguide/example-policies.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Config](#awsconfig-actions-as-permissions)
+ [Resources Defined by Config](#awsconfig-resources-for-iam-policies)
+ [Condition Keys for AWS Config](#awsconfig-policy-keys)

## Actions Defined by AWS Config<a name="awsconfig-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteConfigRule.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteConfigRule.html) | Deletes the specified AWS Config rule and all of its evaluation results | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteConfigurationRecorder.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteConfigurationRecorder.html) | Deletes the configuration recorder | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteDeliveryChannel.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteDeliveryChannel.html) | Deletes the delivery channel | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteEvaluationResults.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteEvaluationResults.html) | Deletes the evaluation results for the specified Config rule | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DeliverConfigSnapshot.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DeliverConfigSnapshot.html) | Schedules delivery of a configuration snapshot to the Amazon S3 bucket in the specified delivery channel | Read |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeComplianceByConfigRule.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeComplianceByConfigRule.html) | Indicates whether the specified AWS Config rules are compliant | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeComplianceByResource.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeComplianceByResource.html) | Indicates whether the specified AWS resources are compliant | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigRuleEvaluationStatus.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigRuleEvaluationStatus.html) | Returns status information for each of your AWS managed Config rules | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigRules.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigRules.html) | Returns details about your AWS Config rules | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigurationRecorderStatus.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigurationRecorderStatus.html) | Returns the current status of the specified configuration recorder | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigurationRecorders.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigurationRecorders.html) | Returns the name of one or more specified configuration recorders | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeDeliveryChannelStatus.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeDeliveryChannelStatus.html) | Returns the current status of the specified delivery channel | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeDeliveryChannels.html](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeDeliveryChannels.html) | Returns details about the specified delivery channel | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceDetailsByConfigRule.html](http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceDetailsByConfigRule.html) | Returns the evaluation results for the specified AWS Config rule | Read |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceDetailsByResource.html](http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceDetailsByResource.html) | Returns the evaluation results for the specified AWS resource | Read |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceSummaryByConfigRule.html](http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceSummaryByConfigRule.html) | Returns the number of AWS Config rules that are compliant and noncompliant, up to a maximum of 25 for each | Read |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceSummaryByResourceType.html](http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceSummaryByResourceType.html) | Returns the number of resources that are compliant and the number that are noncompliant | Read |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_GetResourceConfigHistory.html](http://docs.aws.amazon.com/config/latest/APIReference/API_GetResourceConfigHistory.html) | Returns a list of configuration items for the specified resource | Read |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_ListDiscoveredResources.html](http://docs.aws.amazon.com/config/latest/APIReference/API_ListDiscoveredResources.html) | Accepts a resource type and returns a list of resource identifiers for the resources of that type | List |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_PutConfigRule.html](http://docs.aws.amazon.com/config/latest/APIReference/API_PutConfigRule.html) | Adds or updates an AWS Config rule for evaluating whether your AWS resources comply with your desired configurations | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_PutConfigurationRecorder.html](http://docs.aws.amazon.com/config/latest/APIReference/API_PutConfigurationRecorder.html) | Creates a new configuration recorder to record the selected resource configurations | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_PutDeliveryChannel.html](http://docs.aws.amazon.com/config/latest/APIReference/API_PutDeliveryChannel.html) | Creates a delivery channel object to deliver configuration information to an Amazon S3 bucket and Amazon SNS topic | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_PutEvaluations.html](http://docs.aws.amazon.com/config/latest/APIReference/API_PutEvaluations.html) | Used by an AWS Lambda function to deliver evaluation results to AWS Config | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_StartConfigRulesEvaluation.html](http://docs.aws.amazon.com/config/latest/APIReference/API_StartConfigRulesEvaluation.html) | Evaluates your resources against the specified Config rules | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_StartConfigurationRecorder.html](http://docs.aws.amazon.com/config/latest/APIReference/API_StartConfigurationRecorder.html) | Starts recording configurations of the AWS resources you have selected to record in your AWS account | Write |  |  |  | 
| [http://docs.aws.amazon.com/config/latest/APIReference/API_StopConfigurationRecorder.html](http://docs.aws.amazon.com/config/latest/APIReference/API_StopConfigurationRecorder.html) | Stops recording configurations of the AWS resources you have selected to record in your AWS account | Write |  |  |  | 

## Resources Defined by Config<a name="awsconfig-resources-for-iam-policies"></a>

Config has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Config<a name="awsconfig-policy-keys"></a>

Config has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.