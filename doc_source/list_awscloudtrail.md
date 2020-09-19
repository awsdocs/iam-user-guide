# Actions, resources, and condition keys for AWS CloudTrail<a name="list_awscloudtrail"></a>

AWS CloudTrail \(service prefix: `cloudtrail`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/grant-custom-permissions-for-cloudtrail-users.html) permission policies\.

**Topics**
+ [Actions defined by AWS CloudTrail](#awscloudtrail-actions-as-permissions)
+ [Resource types defined by AWS CloudTrail](#awscloudtrail-resources-for-iam-policies)
+ [Condition keys for AWS CloudTrail](#awscloudtrail-policy-keys)

## Actions defined by AWS CloudTrail<a name="awscloudtrail-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddTags ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_AddTags.html)  | Grants permission to add one or more tags to a trail, up to a limit of 10 | Tagging |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ CreateTrail ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_CreateTrail.html)  | Grants permission to create a trail that specifies the settings for delivery of log data to an Amazon S3 bucket | Write |   [ trail\* ](#awscloudtrail-trail)   |  |   s3:PutObject   | 
|   [ DeleteTrail ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_DeleteTrail.html)  | Grants permission to delete a trail | Write |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ DescribeTrails ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_DescribeTrails.html)  | Grants permission to list settings for the trails associated with the current region for your account | Read |  |  |  | 
|   [ GetEventSelectors ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_GetEventSelectors.html)  | Grants permission to list settings for event selectors configured for a trail | Read |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ GetInsightSelectors ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_GetInsightSelectors.html)  | Grants permission to list CloudTrail Insights selectors that are configured for a trail | Read |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ GetTrail ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_GetTrail.html)  | Grants permission to list settings for the trail | Read |  |  |  | 
|   [ GetTrailStatus ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_GetTrailStatus.html)  | Grants permission to retrieve a JSON\-formatted list of information about the specified trail | Read |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ ListPublicKeys ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_ListPublicKeys.html)  | Grants permission to list the public keys whose private keys were used to sign trail digest files within a specified time range | Read |  |  |  | 
|   [ ListTags ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_ListTags.html)  | Grants permission to list the tags for trails in the current region | Read |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ ListTrails ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_ListTrails.html)  | Grants permission to list trails associated with the current region for your account | List |  |  |  | 
|   [ LookupEvents ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_LookupEvents.html)  | Grants permission to look up API activity events captured by CloudTrail that create, update, or delete resources in your account | Read |  |  |  | 
|   [ PutEventSelectors ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_PutEventSelectors.html)  | Grants permission to create and update event selectors for a trail | Write |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ PutInsightSelectors ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_PutInsightSelectors.html)  | Grants permission to create and update CloudTrail Insights selectors for a trail | Write |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ RemoveTags ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_RemoveTags.html)  | Grants permission to remove tags from a trail | Tagging |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ StartLogging ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_StartLogging.html)  | Grants permission to start the recording of AWS API calls and log file delivery for a trail | Write |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ StopLogging ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_StopLogging.html)  | Grants permission to stop the recording of AWS API calls and log file delivery for a trail | Write |   [ trail\* ](#awscloudtrail-trail)   |  |  | 
|   [ UpdateTrail ](https://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_UpdateTrail.html)  | Grants permission to update the settings that specify delivery of log files | Write |   [ trail\* ](#awscloudtrail-trail)   |  |  | 

## Resource types defined by AWS CloudTrail<a name="awscloudtrail-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloudtrail-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.

**Note**  
For policies that control access to CloudTrail actions, the Resource element is always set to "\*"\. For information about using resource ARNs in an IAM policy, see [Granting Custom Permissions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/controlling_access_granting_custom_permissions.html) in the *AWS CloudTrail User Guide*\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ trail ](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/how-cloudtrail-works.html)  |  arn:$\{Partition\}:cloudtrail:$\{Region\}:$\{Account\}:trail/$\{TrailName\}  |  | 

## Condition keys for AWS CloudTrail<a name="awscloudtrail-policy-keys"></a>

CloudTrail has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.