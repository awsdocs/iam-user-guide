# Actions, Resources, and Condition Keys for Amazon Kinesis Video Streams<a name="list_amazonkinesisvideostreams"></a>

Amazon Kinesis Video Streams \(service prefix: `kinesisvideo`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by Amazon Kinesis Video Streams](#amazonkinesisvideostreams-actions-as-permissions)
+ [Resources Defined by Kinesis Video Streams](#amazonkinesisvideostreams-resources-for-iam-policies)
+ [Condition Keys for Amazon Kinesis Video Streams](#amazonkinesisvideostreams-policy-keys)

## Actions Defined by Amazon Kinesis Video Streams<a name="amazonkinesisvideostreams-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| CreateStream | Create a Kinesis video stream\. | Write |  |  |  | 
| DeleteStream | Delete an existing Kinesis video stream\. | Write | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| DescribeStream | Describe the specified Kinesis video stream\. | List |  |  |  | 
| GetDataEndpoint | Gets an endpoint for a specified stream for either reading or writing media data to Kinesis Video Streams\. | Read | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| GetMedia | Returns media content of a Kinesis video stream\. | Read | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| GetMediaForFragmentList | Read and return media data only from persisted storage\. | Read | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| ListFragments | List the fragments from archival storage based on the pagination token or selector type with range specified\. | List | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| ListStreams | List your Kinesis video streams\. | List |  |  |  | 
| ListTagsForStream | Fetch the tags associated with Kinesis video stream\. | Read | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| PutMedia | Send media data to a Kinesis video stream\. | Write | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| TagStream | Attach set of tags to your Kinesis video streams\. | Tagging | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| UntagStream | Remove one or more tags from your Kinesis video streams\. | Tagging | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| UpdateDataRetention | Update the data retention period of your Kinesis video stream\. | Write | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 
| UpdateStream | Update an existing Kinesis video stream\. | Write | [stream\*](#amazonkinesisvideostreams-stream)  |  |  | 

## Resources Defined by Kinesis Video Streams<a name="amazonkinesisvideostreams-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonkinesisvideostreams-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| stream | arn:$\{Partition\}:kinesisvideo:$\{Region\}:$\{Account\}:stream/$\{StreamName\}/$\{CreationTime\} |  | 

## Condition Keys for Amazon Kinesis Video Streams<a name="amazonkinesisvideostreams-policy-keys"></a>

Kinesis Video Streams has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.