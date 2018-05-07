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
| [DeleteConfigRule](http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteConfigRule.html) | Deletes the specified AWS Config rule and all of its evaluation results | Write |  |  |  | 
| [DeleteConfigurationRecorder](http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteConfigurationRecorder.html) | Deletes the configuration recorder | Write |  |  |  | 
| [DeleteDeliveryChannel](http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteDeliveryChannel.html) | Deletes the delivery channel | Write |  |  |  | 
| [DeleteEvaluationResults](http://docs.aws.amazon.com/config/latest/APIReference/API_DeleteEvaluationResults.html) | Deletes the evaluation results for the specified Config rule | Write |  |  |  | 
| [DeliverConfigSnapshot](http://docs.aws.amazon.com/config/latest/APIReference/API_DeliverConfigSnapshot.html) | Schedules delivery of a configuration snapshot to the Amazon S3 bucket in the specified delivery channel | Read |  |  |  | 
| [DescribeComplianceByConfigRule](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeComplianceByConfigRule.html) | Indicates whether the specified AWS Config rules are compliant | List |  |  |  | 
| [DescribeComplianceByResource](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeComplianceByResource.html) | Indicates whether the specified AWS resources are compliant | List |  |  |  | 
| [DescribeConfigRuleEvaluationStatus](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigRuleEvaluationStatus.html) | Returns status information for each of your AWS managed Config rules | List |  |  |  | 
| [DescribeConfigRules](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigRules.html) | Returns details about your AWS Config rules | List |  |  |  | 
| [DescribeConfigurationRecorderStatus](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigurationRecorderStatus.html) | Returns the current status of the specified configuration recorder | List |  |  |  | 
| [DescribeConfigurationRecorders](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeConfigurationRecorders.html) | Returns the name of one or more specified configuration recorders | List |  |  |  | 
| [DescribeDeliveryChannelStatus](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeDeliveryChannelStatus.html) | Returns the current status of the specified delivery channel | List |  |  |  | 
| [DescribeDeliveryChannels](http://docs.aws.amazon.com/config/latest/APIReference/API_DescribeDeliveryChannels.html) | Returns details about the specified delivery channel | List |  |  |  | 
| [GetComplianceDetailsByConfigRule](http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceDetailsByConfigRule.html) | Returns the evaluation results for the specified AWS Config rule | Read |  |  |  | 
| [GetComplianceDetailsByResource](http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceDetailsByResource.html) | Returns the evaluation results for the specified AWS resource | Read |  |  |  | 
| [GetComplianceSummaryByConfigRule](http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceSummaryByConfigRule.html) | Returns the number of AWS Config rules that are compliant and noncompliant, up to a maximum of 25 for each | Read |  |  |  | 
| [GetComplianceSummaryByResourceType](http://docs.aws.amazon.com/config/latest/APIReference/API_GetComplianceSummaryByResourceType.html) | Returns the number of resources that are compliant and the number that are noncompliant | Read |  |  |  | 
| [GetResourceConfigHistory](http://docs.aws.amazon.com/config/latest/APIReference/API_GetResourceConfigHistory.html) | Returns a list of configuration items for the specified resource | Read |  |  |  | 
| [ListDiscoveredResources](http://docs.aws.amazon.com/config/latest/APIReference/API_ListDiscoveredResources.html) | Accepts a resource type and returns a list of resource identifiers for the resources of that type | List |  |  |  | 
| [PutConfigRule](http://docs.aws.amazon.com/config/latest/APIReference/API_PutConfigRule.html) | Adds or updates an AWS Config rule for evaluating whether your AWS resources comply with your desired configurations | Write |  |  |  | 
| [PutConfigurationRecorder](http://docs.aws.amazon.com/config/latest/APIReference/API_PutConfigurationRecorder.html) | Creates a new configuration recorder to record the selected resource configurations | Write |  |  |  | 
| [PutDeliveryChannel](http://docs.aws.amazon.com/config/latest/APIReference/API_PutDeliveryChannel.html) | Creates a delivery channel object to deliver configuration information to an Amazon S3 bucket and Amazon SNS topic | Write |  |  |  | 
| [PutEvaluations](http://docs.aws.amazon.com/config/latest/APIReference/API_PutEvaluations.html) | Used by an AWS Lambda function to deliver evaluation results to AWS Config | Write |  |  |  | 
| [StartConfigRulesEvaluation](http://docs.aws.amazon.com/config/latest/APIReference/API_StartConfigRulesEvaluation.html) | Evaluates your resources against the specified Config rules | Write |  |  |  | 
| [StartConfigurationRecorder](http://docs.aws.amazon.com/config/latest/APIReference/API_StartConfigurationRecorder.html) | Starts recording configurations of the AWS resources you have selected to record in your AWS account | Write |  |  |  | 
| [StopConfigurationRecorder](http://docs.aws.amazon.com/config/latest/APIReference/API_StopConfigurationRecorder.html) | Stops recording configurations of the AWS resources you have selected to record in your AWS account | Write |  |  |  | 

## Resources Defined by Config<a name="awsconfig-resources-for-iam-policies"></a>

Config has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Config<a name="awsconfig-policy-keys"></a>

Config has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.