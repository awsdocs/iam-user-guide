# Actions, Resources, and Condition Keys for AWS IoT Analytics<a name="list_awsiotanalytics"></a>

AWS IoT Analytics \(service prefix: `iotanalytics`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/authorization.html) permission policies\.

**Topics**
+ [Actions Defined by AWS IoT Analytics](#awsiotanalytics-actions-as-permissions)
+ [Resources Defined by IoT Analytics](#awsiotanalytics-resources-for-iam-policies)
+ [Condition Keys for AWS IoT Analytics](#awsiotanalytics-policy-keys)

## Actions Defined by AWS IoT Analytics<a name="awsiotanalytics-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [BatchPutMessage](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_BatchPutMessage.html) | Puts a batch of messages into the specified channel\. | Write |  |  |  | 
| [CancelPipelineReprocessing](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CancelPipelineReprocessing.html) | Cancels reprocessing for the specified pipeline\. | Write |  |  |  | 
| [CreateChannel](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateChannel.html) | Creates a channel\. | Write |  |  |  | 
| [CreateDataset](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDataset.html) | Creates a dataset\. | Write |  |  |  | 
| [CreateDatasetContent](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDatasetContent.html) | Generates content of the specified dataset \(by executing the dataset actions\)\. | Write |  |  |  | 
| [CreateDatastore](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDatastore.html) | Creates a datastore\. | Write |  |  |  | 
| [CreatePipeline](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreatePipeline.html) | Creates a pipeline\. | Write |  |  |  | 
| [DeleteChannel](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteChannel.html) | Deletes the specified channel\. | Write |  |  |  | 
| [DeleteDataset](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDataset.html) | Deletes the specified dataset\. | Write |  |  |  | 
| [DeleteDatasetContent](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDatasetContent.html) | Deletes the content of the specified dataset\. | Write |  |  |  | 
| [DeleteDatastore](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDatastore.html) | Deletes the specified datastore\. | Write |  |  |  | 
| [DeletePipeline](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeletePipeline.html) | Deletes the specified pipeline\. | Write |  |  |  | 
| [DescribeChannel](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeChannel.html) | Describes the specified channel\. | Read |  |  |  | 
| [DescribeDataset](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeDataset.html) | Describes the specified dataset\. | Read |  |  |  | 
| [DescribeDatastore](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeDatastore.html) | Describes the specified datastore\. | Read |  |  |  | 
| [DescribeLoggingOptions](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeLoggingOptions.html) | Describes logging options for the the account\. | Read |  |  |  | 
| [DescribePipeline](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribePipeline.html) | Describes the specified pipeline\. | Read |  |  |  | 
| [GetDatasetContent](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_GetDatasetContent.html) | Gets the content of the specified dataset\. | Read |  |  |  | 
| [ListChannels](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListChannels.html) | Lists the channels for the account\. | List |  |  |  | 
| [ListDatasets](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListDatasets.html) | Lists the datasets for the account\. | List |  |  |  | 
| [ListDatastores](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListDatastores.html) | Lists the datastores for the account\. | List |  |  |  | 
| [ListPipelines](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListPipelines.html) | Lists the pipelines for the account\. | List |  |  |  | 
| [PutLoggingOptions](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_PutLoggingOptions.html) | Puts logging options for the the account\. | Write |  |  |  | 
| [RunPipelineActivity](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_RunPipelineActivity.html) | Runs the specified pipeline activity\. | Read |  |  |  | 
| [SampleChannelData](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_SampleChannelData.html) | Samples the specified channel's data\. | Read |  |  |  | 
| [StartPipelineReprocessing](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_StartPipelineReprocessing.html) | Starts reprocessing for the specified pipeline\. | Write |  |  |  | 
| [UpdateChannel](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateChannel.html) | Updates the specified channel\. | Write |  |  |  | 
| [UpdateDataset](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateDataset.html) | Updates the specified dataset\. | Write |  |  |  | 
| [UpdateDatastore](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateDatastore.html) | Updates the specified datastore\. | Write |  |  |  | 
| [UpdatePipeline](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdatePipeline.html) | Updates the specified pipeline\. | Write |  |  |  | 

## Resources Defined by IoT Analytics<a name="awsiotanalytics-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiotanalytics-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [channel](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/channel.html) | arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:channel/$\{ChannelName\} |  | 
| [dataset](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/dataset.html) | arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:dataset/$\{DatasetName\} |  | 
| [datastore](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/datastore.html) | arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:datastore/$\{DatastoreName\} |  | 
| [pipeline](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/pipeline.html) | arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:pipeline/$\{PipelineName\} |  | 

## Condition Keys for AWS IoT Analytics<a name="awsiotanalytics-policy-keys"></a>

IoT Analytics has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.