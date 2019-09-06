# Actions, Resources, and Condition Keys for AWS Cost Explorer Service<a name="list_awscostexplorerservice"></a>

AWS Cost Explorer Service \(service prefix: `ce`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-explorer-access.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Cost Explorer Service](#awscostexplorerservice-actions-as-permissions)
+ [Resources Defined by AWS Cost Explorer Service](#awscostexplorerservice-resources-for-iam-policies)
+ [Condition Keys for AWS Cost Explorer Service](#awscostexplorerservice-policy-keys)

## Actions Defined by AWS Cost Explorer Service<a name="awscostexplorerservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ GetCostAndUsage ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetCostAndUsage.html)  | Grants permission to retrieve the cost and usage metrics for your account\. | Read |  |  |  | 
|   [ GetCostForecast ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetCostForecast.html)  | Grants permission to retrieve a cost forecast for a forecast time period\. | Read |  |  |  | 
|   [ GetDimensionValues ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetDimensionValues.html)  | Grants permission to retrieve all available filter values for a filter for a period of time\. | Read |  |  |  | 
|   [ GetReservationCoverage ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetReservationCoverage.html)  | Grants permission to retrieve the reservation coverage for your account\. | Read |  |  |  | 
|   [ GetReservationPurchaseRecommendation ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetReservationPurchaseRecommendation.html)  | Grants permission to retrieve the reservation recommendations for your account\. | Read |  |  |  | 
|   [ GetReservationUtilization ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetReservationUtilization.html)  | Grants permission to retrieve the reservation utilization for your account\. | Read |  |  |  | 
|   [ GetRightsizingRecommendation ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetRightsizingRecommendation.html)  | Grants permission to retrieve the rightsizing recommendations for your account\. | Read |  |  |  | 
|   [ GetTags ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetTags.html)  | Grants permission to query tags for a specified time period\. | Read |  |  |  | 
|   [ GetUsageForecast ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetUsageForecast.html)  | Grants permission to retrieve a usage forecast for a forecast time period\. | Read |  |  |  | 

## Resources Defined by AWS Cost Explorer Service<a name="awscostexplorerservice-resources-for-iam-policies"></a>

AWS Cost Explorer Service has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Cost Explorer Service<a name="awscostexplorerservice-policy-keys"></a>

Cost Explorer Service has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.