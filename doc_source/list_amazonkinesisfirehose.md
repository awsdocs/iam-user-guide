# Actions, Resources, and Condition Keys for Amazon Kinesis Firehose<a name="list_amazonkinesisfirehose"></a>

Amazon Kinesis Firehose \(service prefix: `firehose`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/firehose/latest/dev/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/firehose/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/firehose/latest/dev/controlling-access.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Kinesis Firehose](#amazonkinesisfirehose-actions-as-permissions)
+ [Resources Defined by Firehose](#amazonkinesisfirehose-resources-for-iam-policies)
+ [Condition Keys for Amazon Kinesis Firehose](#amazonkinesisfirehose-policy-keys)

## Actions Defined by Amazon Kinesis Firehose<a name="amazonkinesisfirehose-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/firehose/latest/APIReference/API_CreateDeliveryStream.html](http://docs.aws.amazon.com/firehose/latest/APIReference/API_CreateDeliveryStream.html) | Creates a delivery stream\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/firehose/latest/APIReference/API_DeleteDeliveryStream.html](http://docs.aws.amazon.com/firehose/latest/APIReference/API_DeleteDeliveryStream.html) | Deletes a delivery stream and its data\. | Write | [deliverystream\*](#amazonkinesisfirehose-deliverystream)  |  |  | 
| [http://docs.aws.amazon.com/firehose/latest/APIReference/API_DescribeDeliveryStream.html](http://docs.aws.amazon.com/firehose/latest/APIReference/API_DescribeDeliveryStream.html) | Describes the specified delivery stream and gets the status\. | List |  |  |  | 
| [http://docs.aws.amazon.com/firehose/latest/APIReference/API_ListDeliveryStreams.html](http://docs.aws.amazon.com/firehose/latest/APIReference/API_ListDeliveryStreams.html) | Lists your delivery streams\. | List |  |  |  | 
| [http://docs.aws.amazon.com/firehose/latest/APIReference/API_PutRecord.html](http://docs.aws.amazon.com/firehose/latest/APIReference/API_PutRecord.html) | Writes a single data record into an Amazon Kinesis Firehose delivery stream\. | Write | [deliverystream\*](#amazonkinesisfirehose-deliverystream)  |  |  | 
| [http://docs.aws.amazon.com/firehose/latest/APIReference/API_PutRecordBatch.html](http://docs.aws.amazon.com/firehose/latest/APIReference/API_PutRecordBatch.html) | Writes multiple data records into a delivery stream in a single call, which can achieve higher throughput per producer than when writing single records\. | Write | [deliverystream\*](#amazonkinesisfirehose-deliverystream)  |  |  | 
| [http://docs.aws.amazon.com/firehose/latest/APIReference/API_UpdateDestination.html](http://docs.aws.amazon.com/firehose/latest/APIReference/API_UpdateDestination.html) | Updates the specified destination of the specified delivery stream\. | Write | [deliverystream\*](#amazonkinesisfirehose-deliverystream)  |  |  | 

## Resources Defined by Firehose<a name="amazonkinesisfirehose-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonkinesisfirehose-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/firehose/latest/dev/basic-create.html](http://docs.aws.amazon.com/firehose/latest/dev/basic-create.html) | arn:$\{Partition\}:firehose:$\{Region\}:$\{Account\}:deliverystream/$\{DeliveryStreamName\} |  | 

## Condition Keys for Amazon Kinesis Firehose<a name="amazonkinesisfirehose-policy-keys"></a>

Firehose has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.