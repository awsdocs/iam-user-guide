# Actions, Resources, and Condition Keys for CloudWatch Application Insights<a name="list_cloudwatchapplicationinsights"></a>

CloudWatch Application Insights \(service prefix: `applicationinsights`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)\.
+ View a [list of the API operations available for this service]({DocHomeURL}appinsights/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-application-insights.html) permission policies\.

**Topics**
+ [Actions Defined by CloudWatch Application Insights](#cloudwatchapplicationinsights-actions-as-permissions)
+ [Resources Defined by CloudWatch Application Insights](#cloudwatchapplicationinsights-resources-for-iam-policies)
+ [Condition Keys for CloudWatch Application Insights](#cloudwatchapplicationinsights-policy-keys)

## Actions Defined by CloudWatch Application Insights<a name="cloudwatchapplicationinsights-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateApplication ]({DocHomeURL}appinsights/latest/APIReference/API_CreateApplication.html)  | Creates an application from a resource group | Write |  |  |  | 
|   [ CreateComponent ]({DocHomeURL}appinsights/latest/APIReference/API_CreateComponent.html)  | Creates a component from a group of resources | Write |  |  |  | 
|   [ DeleteApplication ]({DocHomeURL}appinsights/latest/APIReference/API_DeleteApplication.html)  | Deletes an application | Write |  |  |  | 
|   [ DeleteComponent ]({DocHomeURL}appinsights/latest/APIReference/API_DeleteComponent.html)  | Deletes a component | Write |  |  |  | 
|   [ DescribeApplication ]({DocHomeURL}appinsights/latest/APIReference/API_DescribeApplication.html)  | Describes an application | Read |  |  |  | 
|   [ DescribeComponent ]({DocHomeURL}appinsights/latest/APIReference/API_DescribeComponent.html)  | Describes a component | Read |  |  |  | 
|   [ DescribeComponentConfiguration ]({DocHomeURL}appinsights/latest/APIReference/API_DescribeComponentConfiguration.html)  | Describes a component configuration | Read |  |  |  | 
|   [ DescribeComponentConfigurationRecommendation ]({DocHomeURL}appinsights/latest/APIReference/API_DescribeComponentConfigurationRecommendation.html)  | Describe the recommended application component configuration | Read |  |  |  | 
|   [ DescribeObservation ]({DocHomeURL}appinsights/latest/APIReference/API_DescribeObservation.html)  | Describes an observation | Read |  |  |  | 
|   [ DescribeProblem ]({DocHomeURL}appinsights/latest/APIReference/API_DescribeProblem.html)  | Describes a problem | Read |  |  |  | 
|   [ DescribeProblemDashboard ]({DocHomeURL}appinsights/latest/APIReference/API_DescribeProblemDashboard.html)  | Describes a problem dashboard | Read |  |  |  | 
|   [ DescribeProblemObservations ]({DocHomeURL}appinsights/latest/APIReference/API_DescribeProblemObservations.html)  | Describes the observation in a problem | Read |  |  |  | 
|   [ ListApplications ]({DocHomeURL}appinsights/latest/APIReference/API_ListApplications.html)  | Lists all applications | List |  |  |  | 
|   [ ListComponents ]({DocHomeURL}appinsights/latest/APIReference/API_ListComponents.html)  | List an application's components | List |  |  |  | 
|   [ ListProblems ]({DocHomeURL}appinsights/latest/APIReference/API_ListProblems.html)  | Lists the problems in an application | List |  |  |  | 
|   [ UpdateApplication ]({DocHomeURL}appinsights/latest/APIReference/API_UpdateApplication.html)  | Updates an application | Write |  |  |  | 
|   [ UpdateComponent ]({DocHomeURL}appinsights/latest/APIReference/API_UpdateComponent.html)  | Updates a component | Write |  |  |  | 
|   [ UpdateComponentConfiguration ]({DocHomeURL}appinsights/latest/APIReference/API_UpdateComponentConfiguration.html)  | Updates a component configuration | Write |  |  |  | 
|   [ UpdateProblem ]({DocHomeURL}appinsights/latest/APIReference/API_UpdateProblem.html)  | Updates a problem | Write |  |  |  | 

## Resources Defined by CloudWatch Application Insights<a name="cloudwatchapplicationinsights-resources-for-iam-policies"></a>

CloudWatch Application Insights has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for CloudWatch Application Insights<a name="cloudwatchapplicationinsights-policy-keys"></a>

CloudWatch Application Insights has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.