# Actions, resources, and condition keys for Compute Optimizer<a name="list_computeoptimizer"></a>

Compute Optimizer \(service prefix: `compute-optimizer`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/compute-optimizer/latest/ug/what-is.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/compute-optimizer/latest/ug/security-iam.html) permission policies\.

**Topics**
+ [Actions defined by Compute Optimizer](#computeoptimizer-actions-as-permissions)
+ [Resource types defined by Compute Optimizer](#computeoptimizer-resources-for-iam-policies)
+ [Condition keys for Compute Optimizer](#computeoptimizer-policy-keys)

## Actions defined by Compute Optimizer<a name="computeoptimizer-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DescribeRecommendationExportJobs ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_DescribeRecommendationExportJobs.html)  | Grants permission to view the status of recommendation export jobs\. | List |  |  |  | 
|   [ ExportAutoScalingGroupRecommendations ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_ExportAutoScalingGroupRecommendations.html)  | Grants permission to export autoscaling group recommendations to S3 for the provided accounts\. | Write |  |  |  | 
|   [ ExportEC2InstanceRecommendations ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_ExportEC2InstanceRecommendations.html)  | Grants permission to export EC2 instance recommendations to S3 for the provided accounts\. | Write |  |  |  | 
|   [ GetAutoScalingGroupRecommendations ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_GetAutoScalingGroupRecommendations.html)  | Grants permission to get recommendations for the provided autoscaling groups\. | List |  |  |  | 
|   [ GetEC2InstanceRecommendations ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_GetEC2InstanceRecommendations.html)  | Grants permission to get recommendations for the provided EC2 instances\. | List |  |  |  | 
|   [ GetEC2RecommendationProjectedMetrics ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_GetEC2RecommendationProjectedMetrics.html)  | Grants permission to get the recommendation projected metrics of the specified instance\. | List |  |  |  | 
|   [ GetEnrollmentStatus ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_GetEnrollmentStatus.html)  | Grants permission to get the enrollment status for the specified account\. | List |  |  |  | 
|   [ GetRecommendationSummaries ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_GetRecommendationSummaries.html)  | Grants permission to get the recommendation summaries for the specified account\(s\)\. | List |  |  |  | 
|   [ UpdateEnrollmentStatus ](https://docs.aws.amazon.com/compute-optimizer/latest/APIReference/API_UpdateEnrollmentStatus.html)  | Grants permission to update the enrollment status\. | Write |  |  |  | 

## Resource types defined by Compute Optimizer<a name="computeoptimizer-resources-for-iam-policies"></a>

Compute Optimizer does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Compute Optimizer, specify `“Resource”: “*”` in your policy\.

## Condition keys for Compute Optimizer<a name="computeoptimizer-policy-keys"></a>

Compute Optimizer has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.