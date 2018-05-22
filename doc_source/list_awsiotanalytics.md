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
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_BatchPutMessage.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_BatchPutMessage.html) | Puts a batch of messages into the specified channel\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CancelPipelineReprocessing.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CancelPipelineReprocessing.html) | Cancels reprocessing for the specified pipeline\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateChannel.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateChannel.html) | Creates a channel\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDataset.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDataset.html) | Creates a dataset\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDatasetContent.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDatasetContent.html) | Generates content of the specified dataset \(by executing the dataset actions\)\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDatastore.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreateDatastore.html) | Creates a datastore\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreatePipeline.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_CreatePipeline.html) | Creates a pipeline\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteChannel.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteChannel.html) | Deletes the specified channel\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDataset.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDataset.html) | Deletes the specified dataset\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDatasetContent.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDatasetContent.html) | Deletes the content of the specified dataset\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDatastore.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeleteDatastore.html) | Deletes the specified datastore\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeletePipeline.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DeletePipeline.html) | Deletes the specified pipeline\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeChannel.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeChannel.html) | Describes the specified channel\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeDataset.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeDataset.html) | Describes the specified dataset\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeDatastore.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeDatastore.html) | Describes the specified datastore\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeLoggingOptions.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribeLoggingOptions.html) | Describes logging options for the the account\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribePipeline.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_DescribePipeline.html) | Describes the specified pipeline\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_GetDatasetContent.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_GetDatasetContent.html) | Gets the content of the specified dataset\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListChannels.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListChannels.html) | Lists the channels for the account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListDatasets.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListDatasets.html) | Lists the datasets for the account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListDatastores.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListDatastores.html) | Lists the datastores for the account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListPipelines.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_ListPipelines.html) | Lists the pipelines for the account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_PutLoggingOptions.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_PutLoggingOptions.html) | Puts logging options for the the account\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_RunPipelineActivity.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_RunPipelineActivity.html) | Runs the specified pipeline activity\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_SampleChannelData.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_SampleChannelData.html) | Samples the specified channel's data\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_StartPipelineReprocessing.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_StartPipelineReprocessing.html) | Starts reprocessing for the specified pipeline\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateChannel.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateChannel.html) | Updates the specified channel\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateDataset.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateDataset.html) | Updates the specified dataset\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateDatastore.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdateDatastore.html) | Updates the specified datastore\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdatePipeline.html](http://docs.aws.amazon.com/iotanalytics/latest/APIReference/API_UpdatePipeline.html) | Updates the specified pipeline\. | Write |  |  |  | 

## Resources Defined by IoT Analytics<a name="awsiotanalytics-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiotanalytics-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/iotanalytics/latest/developerguide/channel.html](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/channel.html) | arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:channel/$\{ChannelName\} |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/developerguide/dataset.html](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/dataset.html) | arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:dataset/$\{DatasetName\} |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/developerguide/datastore.html](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/datastore.html) | arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:datastore/$\{DatastoreName\} |  | 
| [http://docs.aws.amazon.com/iotanalytics/latest/developerguide/pipeline.html](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/pipeline.html) | arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:pipeline/$\{PipelineName\} |  | 

## Condition Keys for AWS IoT Analytics<a name="awsiotanalytics-policy-keys"></a>

IoT Analytics has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.