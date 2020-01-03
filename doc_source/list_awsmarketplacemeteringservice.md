# Actions, Resources, and Condition Keys for AWS Marketplace Metering Service<a name="list_awsmarketplacemeteringservice"></a>

AWS Marketplace Metering Service \(service prefix: `aws-marketplace`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/marketplace/latest/controlling-access/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions) permission policies\.

**Topics**
+ [Actions Defined by AWS Marketplace Metering Service](#awsmarketplacemeteringservice-actions-as-permissions)
+ [Resource Types Defined by AWS Marketplace Metering Service](#awsmarketplacemeteringservice-resources-for-iam-policies)
+ [Condition Keys for AWS Marketplace Metering Service](#awsmarketplacemeteringservice-policy-keys)

## Actions Defined by AWS Marketplace Metering Service<a name="awsmarketplacemeteringservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchMeterUsage ](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_BatchMeterUsage.html)  | Called from a SaaS application listed on the AWS Marketplace to post metering records for a set of customers\. | Write |  |  |  | 
|   [ MeterUsage ](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html)  | Emits metering records\. | Write |  |  |  | 
|   [ RegisterUsage ](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_RegisterUsage.html)  | Allows you to verify that the customer running your paid software is subscribed to your product on AWS Marketplace, enabling you to guard against unauthorized use\. Meters software use per ECS task, per hour, with usage prorated to the second\. | Write |  |  |  | 
|   [ ResolveCustomer ](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html)  | Resolves a registration token to obtain a CustomerIdentifier and product code\. | Write |  |  |  | 

## Resource Types Defined by AWS Marketplace Metering Service<a name="awsmarketplacemeteringservice-resources-for-iam-policies"></a>

AWS Marketplace Metering Service does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Marketplace Metering Service, specify `“Resource”: “*”` in your policy\.

## Condition Keys for AWS Marketplace Metering Service<a name="awsmarketplacemeteringservice-policy-keys"></a>

Marketplace Metering has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.