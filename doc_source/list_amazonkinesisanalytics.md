# Actions, Resources, and Condition Keys for Amazon Kinesis Analytics<a name="list_amazonkinesisanalytics"></a>

Amazon Kinesis Analytics \(service prefix: `kinesisanalytics`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Kinesis Analytics](#amazonkinesisanalytics-actions-as-permissions)
+ [Resources Defined by Kinesis Analytics](#amazonkinesisanalytics-resources-for-iam-policies)
+ [Condition Keys for Amazon Kinesis Analytics](#amazonkinesisanalytics-policy-keys)

## Actions Defined by Amazon Kinesis Analytics<a name="amazonkinesisanalytics-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_AddApplicationInput.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_AddApplicationInput.html) | Adds input to the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_AddApplicationOutput.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_AddApplicationOutput.html) | Adds output to the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_AddApplicationReferenceDataSource.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_AddApplicationReferenceDataSource.html) | Adds reference data source to the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_CreateApplication.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_CreateApplication.html) | Creates an application\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DeleteApplication.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DeleteApplication.html) | Deletes the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DeleteApplicationOutput.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DeleteApplicationOutput.html) | Deletes the specified output of the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DeleteApplicationReferenceDataSource.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DeleteApplicationReferenceDataSource.html) | Deletes the specified reference data source of the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DescribeApplication.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DescribeApplication.html) | Describes the specified application\. | Read | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DiscoverInputSchema.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_DiscoverInputSchema.html) | Discovers the input schema for the application\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_ListApplications.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_ListApplications.html) | List applications for the account | List |  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_StartsApplication.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_StartsApplication.html) | Starts the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_StopApplication.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_StopApplication.html) | Stops the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_UpdateApplication.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/API_UpdateApplication.html) | Updates the application\. | Write | [application\*](#amazonkinesisanalytics-application)  |  |  | 

## Resources Defined by Kinesis Analytics<a name="amazonkinesisanalytics-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonkinesisanalytics-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/kinesisanalytics/latest/dev/how-it-works.html](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/how-it-works.html) | arn:$\{Partition\}:kinesisanalytics:$\{Region\}:$\{Account\}:application/$\{ApplicationName\} |  | 

## Condition Keys for Amazon Kinesis Analytics<a name="amazonkinesisanalytics-policy-keys"></a>

Kinesis Analytics has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.