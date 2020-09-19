# Actions, resources, and condition keys for AWS Cost Explorer Service<a name="list_awscostexplorerservice"></a>

AWS Cost Explorer Service \(service prefix: `ce`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-explorer-what-is.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_Operations_AWS_Cost_Explorer_Service.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-explorer-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS Cost Explorer Service](#awscostexplorerservice-actions-as-permissions)
+ [Resource types defined by AWS Cost Explorer Service](#awscostexplorerservice-resources-for-iam-policies)
+ [Condition keys for AWS Cost Explorer Service](#awscostexplorerservice-policy-keys)

## Actions defined by AWS Cost Explorer Service<a name="awscostexplorerservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateCostCategoryDefinition ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_CreateCostCategoryDefinition.html)  | Grants permission to create a new Cost Category with the requested name and rules\. | Write |  |  |  | 
|   [ DeleteCostCategoryDefinition ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_DeleteCostCategoryDefinition.html)  | Grants permission to delete a Cost Category\. | Write |  |  |  | 
|   [ DescribeCostCategoryDefinition ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_DescribeCostCategoryDefinition.html)  | Grants permission to retrieve descriptions such as the name, ARN, rules, definition, and effective dates of a Cost Category\. | Read |  |  |  | 
|   [ GetCostAndUsage ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetCostAndUsage.html)  | Grants permission to retrieve the cost and usage metrics for your account\. | Read |  |  |  | 
|   [ GetCostAndUsageWithResources ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetCostAndUsageWithResources.html)  | Grants permission to retrieve the cost and usage metrics with resources for your account\. | Read |  |  |  | 
|   [ GetCostForecast ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetCostForecast.html)  | Grants permission to retrieve a cost forecast for a forecast time period\. | Read |  |  |  | 
|   [ GetDimensionValues ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetDimensionValues.html)  | Grants permission to retrieve all available filter values for a filter for a period of time\. | Read |  |  |  | 
|   [ GetReservationCoverage ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetReservationCoverage.html)  | Grants permission to retrieve the reservation coverage for your account\. | Read |  |  |  | 
|   [ GetReservationPurchaseRecommendation ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetReservationPurchaseRecommendation.html)  | Grants permission to retrieve the reservation recommendations for your account\. | Read |  |  |  | 
|   [ GetReservationUtilization ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetReservationUtilization.html)  | Grants permission to retrieve the reservation utilization for your account\. | Read |  |  |  | 
|   [ GetRightsizingRecommendation ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetRightsizingRecommendation.html)  | Grants permission to retrieve the rightsizing recommendations for your account\. | Read |  |  |  | 
|   [ GetSavingsPlansCoverage ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetSavingsPlansCoverage.html)  | Grants permission to retrieve the Savings Plans coverage for your account\. | Read |  |  |  | 
|   [ GetSavingsPlansPurchaseRecommendation ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetSavingsPlansPurchaseRecommendation.html)  | Grants permission to retrieve the Savings Plans recommendations for your account\. | Read |  |  |  | 
|   [ GetSavingsPlansUtilization ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetSavingsPlansUtilization.html)  | Grants permission to retrieve the Savings Plans utilization for your account\. | Read |  |  |  | 
|   [ GetSavingsPlansUtilizationDetails ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetSavingsPlansUtilizationDetails.html)  | Grants permission to retrieve the Savings Plans utilization details for your account\. | Read |  |  |  | 
|   [ GetTags ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetTags.html)  | Grants permission to query tags for a specified time period\. | Read |  |  |  | 
|   [ GetUsageForecast ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetUsageForecast.html)  | Grants permission to retrieve a usage forecast for a forecast time period\. | Read |  |  |  | 
|   [ ListCostCategoryDefinitions ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_ListCostCategoryDefinitions.html)  | Grants permission to retrieve names, ARN, and effective dates for all Cost Categories\. | List |  |  |  | 
|   [ UpdateCostCategoryDefinition ](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_UpdateCostCategoryDefinition.html)  | Grants permission to update an existing Cost Category\. | Write |  |  |  | 

## Resource types defined by AWS Cost Explorer Service<a name="awscostexplorerservice-resources-for-iam-policies"></a>

AWS Cost Explorer Service does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Cost Explorer Service, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS Cost Explorer Service<a name="awscostexplorerservice-policy-keys"></a>

Cost Explorer Service has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.