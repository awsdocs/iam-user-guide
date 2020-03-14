# Actions, Resources, and Condition Keys for Amazon CloudWatch Synthetics<a name="list_amazoncloudwatchsynthetics"></a>

Amazon CloudWatch Synthetics \(service prefix: `synthetics`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AmazonSynthetics/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Synthetics_Canaries.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon CloudWatch Synthetics](#amazoncloudwatchsynthetics-actions-as-permissions)
+ [Resource Types Defined by Amazon CloudWatch Synthetics](#amazoncloudwatchsynthetics-resources-for-iam-policies)
+ [Condition Keys for Amazon CloudWatch Synthetics](#amazoncloudwatchsynthetics-policy-keys)

## Actions Defined by Amazon CloudWatch Synthetics<a name="amazoncloudwatchsynthetics-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateCanary ](${APIReferenceDocPage}API_CreateCanary.html)  | Create a canary\. | Write |  |  |  | 
|   [ DeleteCanary ](${APIReferenceDocPage}API_DeleteCanary.html)  | Deletes a canary\. Amazon Synthetics deletes all the resources except for the Lambda function and the CloudWatch Alarms if you created one\. | Write |   [ canary\* ](#amazoncloudwatchsynthetics-canary)   |  |  | 
|   [ DescribeCanaries ](${APIReferenceDocPage}API_DescribeCanaries.html)  | Returns information of all canaries or a canary\. | Read |   [ canary ](#amazoncloudwatchsynthetics-canary)   |  |  | 
|   [ DescribeTestRuns ](${APIReferenceDocPage}API_DescribeTestRuns.html)  | Returns information about all the test runs associated with a canary\. | Read |   [ canary ](#amazoncloudwatchsynthetics-canary)   |  |  | 
|   [ ListTagsForResource ](${APIReferenceDocPage}API_ListTagsForResource.html)  | Returns a list of all tags and values associated with a canary\. | Read |   [ canary ](#amazoncloudwatchsynthetics-canary)   |  |  | 
|   [ StartCanary ](${APIReferenceDocPage}API_StartCanary.html)  | Starts a canary, so that Amazon Synthetics starts monitoring a website\. | Write |   [ canary\* ](#amazoncloudwatchsynthetics-canary)   |  |  | 
|   [ StopCanary ](${APIReferenceDocPage}API_StopCanary.html)  | Stops a canary\. | Write |   [ canary\* ](#amazoncloudwatchsynthetics-canary)   |  |  | 
|   [ TagResource ](${APIReferenceDocPage}API_TagResource.html)  | Adds one or more tags to a canary\. | Write |   [ canary ](#amazoncloudwatchsynthetics-canary)   |  |  | 
|   [ UntagResource ](${APIReferenceDocPage}API_UntagResource.html)  | Removes one or more tags from a canary\. | Write |   [ canary ](#amazoncloudwatchsynthetics-canary)   |  |  | 
|   [ UpdateCanary ](${APIReferenceDocPage}API_UpdateCanary.html)  | Updates a canary\. | Write |   [ canary\* ](#amazoncloudwatchsynthetics-canary)   |  |  | 

## Resource Types Defined by Amazon CloudWatch Synthetics<a name="amazoncloudwatchsynthetics-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncloudwatchsynthetics-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ canary ](${APIReferenceDocPage}CloudWatch_Synthetics_Canaries.html#CloudWatch_Synthetics_Canaries_Create)  |  arn:$\{Partition\}:synthetics::$\{Account\}:canary:$\{CanaryName\}  |  | 

## Condition Keys for Amazon CloudWatch Synthetics<a name="amazoncloudwatchsynthetics-policy-keys"></a>

CloudWatch Synthetics has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.