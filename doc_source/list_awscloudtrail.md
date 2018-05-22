# Actions, Resources, and Condition Keys for AWS CloudTrail<a name="list_awscloudtrail"></a>

AWS CloudTrail \(service prefix: `cloudtrail`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/grant-custom-permissions-for-cloudtrail-users.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CloudTrail](#awscloudtrail-actions-as-permissions)
+ [Resources Defined by CloudTrail](#awscloudtrail-resources-for-iam-policies)
+ [Condition Keys for AWS CloudTrail](#awscloudtrail-policy-keys)

## Actions Defined by AWS CloudTrail<a name="awscloudtrail-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_AddTags.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_AddTags.html) | Adds one or more tags to a trail, up to a limit of 10 | Tagging | [trail\*](#awscloudtrail-trail)  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_CreateTrail.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_CreateTrail.html) | Creates a trail that specifies the settings for delivery of log data to an Amazon S3 bucket | Write | [trail\*](#awscloudtrail-trail)  |  | s3:PutObject  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_DeleteTrail.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_DeleteTrail.html) | Deletes a trail | Write | [trail\*](#awscloudtrail-trail)  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_DescribeTrails.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_DescribeTrails.html) | Retrieves settings for the trail associated with the current region for your account | List |  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_GetTrailStatus.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_GetTrailStatus.html) | Returns a JSON\-formatted list of information about the specified trail | Read | [trail\*](#awscloudtrail-trail)  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_ListPublicKeys.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_ListPublicKeys.html) | Returns all public keys whose private keys were used to sign the digest files within the specified time range | Read |  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_ListTags.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_ListTags.html) | Lists the tags for the trail in the current region | Read | [trail\*](#awscloudtrail-trail)  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_LookupEvents.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_LookupEvents.html) | Looks up API activity events captured by CloudTrail that create, update, or delete resources in your account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_RemoveTags.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_RemoveTags.html) | Removes the specified tags from a trail | Tagging | [trail\*](#awscloudtrail-trail)  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_StartLogging.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_StartLogging.html) | Starts the recording of AWS API calls and log file delivery for a trail | Write | [trail\*](#awscloudtrail-trail)  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_StopLogging.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_StopLogging.html) | Suspends the recording of AWS API calls and log file delivery for the specified trail | Write | [trail\*](#awscloudtrail-trail)  |  |  | 
| [http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_UpdateTrail.html](http://docs.aws.amazon.com/awscloudtrail/latest/APIReference/API_UpdateTrail.html) | Updates the settings that specify delivery of log files | Write | [trail\*](#awscloudtrail-trail)  |  |  | 

## Resources Defined by CloudTrail<a name="awscloudtrail-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloudtrail-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.

For policies that control access to CloudTrail actions, the Resource element is always set to "\*"\. For information about using resource ARNs in an IAM policy, see [Granting Custom Permissions](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/controlling_access_granting_custom_permissions.html) in the *AWS CloudTrail User Guide*\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/how-cloudtrail-works.html](http://docs.aws.amazon.com/how-cloudtrail-works.html) | arn:$\{Partition\}:cloudtrail:$\{Region\}:$\{Account\}:trail/$\{TrailName\} |  | 

## Condition Keys for AWS CloudTrail<a name="awscloudtrail-policy-keys"></a>

CloudTrail has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.