# Actions, Resources, and Condition Keys for AWS Marketplace Metering Service<a name="list_awsmarketplacemeteringservice"></a>

AWS Marketplace Metering Service \(service prefix: `aws-marketplace`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/marketplace/latest/controlling-access/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions) permission policies\.

**Topics**
+ [Actions Defined by AWS Marketplace Metering Service](#awsmarketplacemeteringservice-actions-as-permissions)
+ [Resources Defined by Marketplace Metering](#awsmarketplacemeteringservice-resources-for-iam-policies)
+ [Condition Keys for AWS Marketplace Metering Service](#awsmarketplacemeteringservice-policy-keys)

## Actions Defined by AWS Marketplace Metering Service<a name="awsmarketplacemeteringservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_BatchMeterUsage.html](http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_BatchMeterUsage.html) | Called from a SaaS application listed on the AWS Marketplace to post metering records for a set of customers\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html](http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_MeterUsage.html) | Emits metering records\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html](http://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html) | Resolves a registration token to obtain a CustomerIdentifier and product code\. | Write |  |  |  | 

## Resources Defined by Marketplace Metering<a name="awsmarketplacemeteringservice-resources-for-iam-policies"></a>

Marketplace Metering has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Marketplace Metering Service<a name="awsmarketplacemeteringservice-policy-keys"></a>

Marketplace Metering has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.