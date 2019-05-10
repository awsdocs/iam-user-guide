# Actions, Resources, and Condition Keys for Amazon Kinesis Analytics V2<a name="list_amazonkinesisanalyticsv2"></a>

Amazon Kinesis Analytics V2 \(service prefix: `kinesisanalytics`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Kinesis Analytics V2](#amazonkinesisanalyticsv2-actions-as-permissions)
+ [Resources Defined by Kinesis Analytics V2](#amazonkinesisanalyticsv2-resources-for-iam-policies)
+ [Condition Keys for Amazon Kinesis Analytics V2](#amazonkinesisanalyticsv2-policy-keys)

## Actions Defined by Amazon Kinesis Analytics V2<a name="amazonkinesisanalyticsv2-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddApplicationCloudWatchLoggingOption ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_AddApplicationCloudWatchLoggingOption.html)  | Adds cloudwatch logging option to the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ AddApplicationInput ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_AddApplicationInput.html)  | Adds input to the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ AddApplicationInputProcessingConfiguration ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_AddApplicationInputProcessingConfiguration.html)  | Adds input processing configuration to the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ AddApplicationOutput ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_AddApplicationOutput.html)  | Adds output to the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ AddApplicationReferenceDataSource ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_AddApplicationReferenceDataSource.html)  | Adds reference data source to the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ CreateApplication ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_CreateApplication.html)  | Creates an application\. | Write |  |  |  | 
|   [ CreateApplicationSnapshot ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_CreateApplicationSnapshot.html)  | Creates a snapshot for an application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DeleteApplication ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DeleteApplication.html)  | Deletes the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DeleteApplicationCloudWatchLoggingOption ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DeleteApplicationCloudWatchLoggingOption.html)  | Deletes the specified cloudwatch logging option of the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DeleteApplicationInputProcessingConfiguration ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DeleteApplicationInputProcessingConfiguration.html)  | Deletes the specified input processing configuration of the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DeleteApplicationOutput ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DeleteApplicationOutput.html)  | Deletes the specified output of the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DeleteApplicationReferenceDataSource ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DeleteApplicationReferenceDataSource.html)  | Deletes the specified reference data source of the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DeleteApplicationSnapshot ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DeleteApplicationSnapshot.html)  | Deletes a snapshot for an application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DescribeApplication ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DescribeApplication.html)  | Describes the specified application\. | Read |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DescribeApplicationSnapshot ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DescribeApplicationSnapshot.html)  | Describes an application snapshot\. | Read |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ DiscoverInputSchema ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_DiscoverInputSchema.html)  | Discovers the input schema for the application\. | Read |  |  |  | 
|   [ ListApplicationSnapshots ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_ListApplicationSnapshots.html)  | Lists the snapshots for an application\. | Read |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ ListApplications ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_ListApplications.html)  | List applications for the account | List |  |  |  | 
|   [ StartApplication ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_StartsApplication.html)  | Starts the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ StopApplication ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_StopApplication.html)  | Stops the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 
|   [ UpdateApplication ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/API_UpdateApplication.html)  | Updates the application\. | Write |   [ application\* ](#amazonkinesisanalyticsv2-application)   |  |  | 

## Resources Defined by Kinesis Analytics V2<a name="amazonkinesisanalyticsv2-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonkinesisanalyticsv2-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ application ](https://docs.aws.amazon.com/kinesisanalytics/latest/apiv2/how-it-works.html)  |  arn:$\{Partition\}:kinesisanalytics:$\{Region\}:$\{Account\}:application/$\{ApplicationName\}  |  | 

## Condition Keys for Amazon Kinesis Analytics V2<a name="amazonkinesisanalyticsv2-policy-keys"></a>

Kinesis Analytics V2 has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.