# Actions, resources, and condition keys for CloudWatch Application Insights<a name="list_cloudwatchapplicationinsights"></a>

CloudWatch Application Insights \(service prefix: `applicationinsights`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/appinsights/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-application-insights.html) permission policies\.

**Topics**
+ [Actions defined by CloudWatch Application Insights](#cloudwatchapplicationinsights-actions-as-permissions)
+ [Resource types defined by CloudWatch Application Insights](#cloudwatchapplicationinsights-resources-for-iam-policies)
+ [Condition keys for CloudWatch Application Insights](#cloudwatchapplicationinsights-policy-keys)

## Actions defined by CloudWatch Application Insights<a name="cloudwatchapplicationinsights-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateApplication ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_CreateApplication.html)  | Creates an application from a resource group | Write |  |  |  | 
|   [ CreateComponent ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_CreateComponent.html)  | Creates a component from a group of resources | Write |  |  |  | 
|   [ DeleteApplication ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DeleteApplication.html)  | Deletes an application | Write |  |  |  | 
|   [ DeleteComponent ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DeleteComponent.html)  | Deletes a component | Write |  |  |  | 
|   [ DescribeApplication ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DescribeApplication.html)  | Describes an application | Read |  |  |  | 
|   [ DescribeComponent ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DescribeComponent.html)  | Describes a component | Read |  |  |  | 
|   [ DescribeComponentConfiguration ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DescribeComponentConfiguration.html)  | Describes a component configuration | Read |  |  |  | 
|   [ DescribeComponentConfigurationRecommendation ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DescribeComponentConfigurationRecommendation.html)  | Describe the recommended application component configuration | Read |  |  |  | 
|   [ DescribeObservation ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DescribeObservation.html)  | Describes an observation | Read |  |  |  | 
|   [ DescribeProblem ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DescribeProblem.html)  | Describes a problem | Read |  |  |  | 
|   [ DescribeProblemObservations ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_DescribeProblemObservations.html)  | Describes the observation in a problem | Read |  |  |  | 
|   [ ListApplications ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_ListApplications.html)  | Lists all applications | List |  |  |  | 
|   [ ListComponents ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_ListComponents.html)  | List an application's components | List |  |  |  | 
|   [ ListProblems ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_ListProblems.html)  | Lists the problems in an application | List |  |  |  | 
|   [ UpdateApplication ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_UpdateApplication.html)  | Updates an application | Write |  |  |  | 
|   [ UpdateComponent ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_UpdateComponent.html)  | Updates a component | Write |  |  |  | 
|   [ UpdateComponentConfiguration ](https://docs.aws.amazon.com/appinsights/latest/APIReference/API_UpdateComponentConfiguration.html)  | Updates a component configuration | Write |  |  |  | 

## Resource types defined by CloudWatch Application Insights<a name="cloudwatchapplicationinsights-resources-for-iam-policies"></a>

CloudWatch Application Insights does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to CloudWatch Application Insights, specify `“Resource”: “*”` in your policy\.

## Condition keys for CloudWatch Application Insights<a name="cloudwatchapplicationinsights-policy-keys"></a>

CloudWatch Application Insights has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.