# Actions, Resources, and Condition Keys for Amazon Kinesis Video Streams<a name="list_amazonkinesisvideostreams"></a>

Amazon Kinesis Video Streams \(service prefix: `kinesisvideo`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/how-iam.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Kinesis Video Streams](#amazonkinesisvideostreams-actions-as-permissions)
+ [Resources Defined by Kinesis Video Streams](#amazonkinesisvideostreams-resources-for-iam-policies)
+ [Condition Keys for Amazon Kinesis Video Streams](#amazonkinesisvideostreams-policy-keys)

## Actions Defined by Amazon Kinesis Video Streams<a name="amazonkinesisvideostreams-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateStream ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_CreateStream.html)  | Create a Kinesis video stream\. | Write |  |  |  | 
|   [ DeleteStream ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_DeleteStream.html)  | Delete an existing Kinesis video stream\. | Write |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ DescribeStream ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_DescribeStream.html)  | Describe the specified Kinesis video stream\. | List |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ GetDataEndpoint ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_GetDataEndpoint.html)  | Gets an endpoint for a specified stream for either reading or writing media data to Kinesis Video Streams\. | Read |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ GetHLSStreamingSessionURL ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_GetHLSStreamingSessionURL.html)  | Creates a URL for HLS video streaming\. | Read |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ GetMedia ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_GetMedia.html)  | Returns media content of a Kinesis video stream\. | Read |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ GetMediaForFragmentList ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_GetMediaForFragmentList.html)  | Read and return media data only from persisted storage\. | Read |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ ListFragments ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_ListFragments.html)  | List the fragments from archival storage based on the pagination token or selector type with range specified\. | List |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ ListStreams ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_ListStreams.html)  | List your Kinesis video streams\. | List |  |  |  | 
|   [ ListTagsForStream ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_ListTagsForStream.html)  | Fetch the tags associated with Kinesis video stream\. | Read |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ PutMedia ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_PutMedia.html)  | Send media data to a Kinesis video stream\. | Write |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ TagStream ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_TagStream.html)  | Attach set of tags to your Kinesis video streams\. | Tagging |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ UntagStream ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_UntagStream.html)  | Remove one or more tags from your Kinesis video streams\. | Tagging |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ UpdateDataRetention ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_UpdateDataRetention.html)  | Update the data retention period of your Kinesis video stream\. | Write |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 
|   [ UpdateStream ](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/API_UpdateStream.html)  | Update an existing Kinesis video stream\. | Write |   [ stream\* ](#amazonkinesisvideostreams-stream)   |  |  | 

## Resources Defined by Kinesis Video Streams<a name="amazonkinesisvideostreams-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonkinesisvideostreams-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   stream  |  arn:$\{Partition\}:kinesisvideo:$\{Region\}:$\{Account\}:stream/$\{StreamName\}/$\{CreationTime\}  |  | 

## Condition Keys for Amazon Kinesis Video Streams<a name="amazonkinesisvideostreams-policy-keys"></a>

Kinesis Video Streams has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.