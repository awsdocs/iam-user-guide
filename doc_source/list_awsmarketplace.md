# Actions, Resources, and Condition Keys for AWS Marketplace<a name="list_awsmarketplace"></a>

AWS Marketplace \(service prefix: `aws-marketplace`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/marketplace/latest/controlling-access/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/marketplace/latest/controlling-access/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Marketplace](#awsmarketplace-actions-as-permissions)
+ [Resource Types Defined by AWS Marketplace](#awsmarketplace-resources-for-iam-policies)
+ [Condition Keys for AWS Marketplace](#awsmarketplace-policy-keys)

## Actions Defined by AWS Marketplace<a name="awsmarketplace-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AcceptAgreementApprovalRequest ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to approve an incoming subscription request \(for providers who provide products that require subscription verification\)\. | Write |  |  |  | 
|   [ CancelAgreementRequest ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to cancel pending subscription requests for products that require subscription verification\. | Write |  |  |  | 
|   [ GetAgreementApprovalRequest ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to view the details of their incoming subscription requests \(for providers who provide products that require subscription verification\)\. | Read |  |  |  | 
|   [ GetAgreementRequest ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to view the details of their subscription requests for data products that require subscription verification\. | Read |  |  |  | 
|   [ ListAgreementApprovalRequests ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to list their incoming subscription requests \(for providers who provide products that require subscription verification\)\. | List |  |  |  | 
|   [ ListAgreementRequests ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to list their subscription requests for products that require subscription verification\. | List |  |  |  | 
|   [ RejectAgreementApprovalRequest ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to decline an incoming subscription requests \(for providers who provide products that require subscription verification\)\. | Write |  |  |  | 
|   [ Subscribe ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to subscribe to AWS Marketplace products\. Includes the ability to send a subscription request for products that require subscription verification\. Includes the ability to enable auto\-renewal for an existing subscription\. | Write |  |  |  | 
|   [ Unsubscribe ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to remove subscriptions to AWS Marketplace products\. Includes the ability to disable auto\-renewal for an existing subscription\. | Write |  |  |  | 
|   [ UpdateAgreementApprovalRequest ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to make changes to an incoming subscription request, including the ability to delete the prospective subscriber's information \(for providers who provide products that require subscription verification\)\. | Write |  |  |  | 
|   [ ViewSubscriptions ](https://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html#SummaryOfAWSMarketplaceSubscriptionsPermissions)  | Allows users to see their account's subscriptions\. | List |  |  |  | 

## Resource Types Defined by AWS Marketplace<a name="awsmarketplace-resources-for-iam-policies"></a>

AWS Marketplace does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Marketplace, specify `“Resource”: “*”` in your policy\.

## Condition Keys for AWS Marketplace<a name="awsmarketplace-policy-keys"></a>

Marketplace has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.