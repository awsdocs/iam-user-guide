# Actions, Resources, and Condition Keys for AWS IoT Events<a name="list_awsiotevents"></a>

AWS IoT Events \(service prefix: `iotevents`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/iotevents/latest/developerguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/iotevents/latest/developerguide/authorization) permission policies\.

**Topics**
+ [Actions Defined by AWS IoT Events](#awsiotevents-actions-as-permissions)
+ [Resources Defined by IoT Events](#awsiotevents-resources-for-iam-policies)
+ [Condition Keys for AWS IoT Events](#awsiotevents-policy-keys)

## Actions Defined by AWS IoT Events<a name="awsiotevents-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchPutMessage ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_BatchPutMessage.html)  | Sends a set of messages to the AWS IoT Events system\. | Write |   [ input\* ](#awsiotevents-input)   |  |  | 
|   [ CreateDetectorModel ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_CreateDetectorModel.html)  | Creates a detector model\. | Write |  |  |  | 
|   [ CreateInput ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_CreateInput.html)  | Creates an input\. | Write |  |  |  | 
|   [ DeleteDetectorModel ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_DeleteDetectorModel.html)  | Deletes a detector model\. | Write |   [ detectorModel\* ](#awsiotevents-detectorModel)   |  |  | 
|   [ DeleteInput ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_DeleteInput.html)  | Deletes an input\. | Write |   [ input\* ](#awsiotevents-input)   |  |  | 
|   [ DescribeDetector ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_DescribeDetector.html)  | Returns information about the specified detector \(instance\)\. | Read |   [ detectorModel\* ](#awsiotevents-detectorModel)   |  |  | 
|   [ DescribeDetectorModel ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_DescribeDetectorModel.html)  | Describes a detector model\. | Read |   [ detectorModel\* ](#awsiotevents-detectorModel)   |  |  | 
|   [ DescribeInput ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_DescribeInput.html)  | Describes an input\. | Read |   [ input\* ](#awsiotevents-input)   |  |  | 
|   [ DescribeLoggingOptions ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_DescribeLoggingOptions.html)  | Retrieves the current settings of the AWS IoT Events logging options\. | Read |  |  |  | 
|   [ ListDetectorModelVersions ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_ListDetectorModelVersions.html)  | Lists all the versions of a detector model\. Only the metadata associated with each detector model version is returned\. | List |   [ detectorModel\* ](#awsiotevents-detectorModel)   |  |  | 
|   [ ListDetectorModels ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_ListDetectorModels.html)  | Lists the detector models you have created\. Only the metadata associated with each detector model is returned\. | List |  |  |  | 
|   [ ListDetectors ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_ListDetectors.html)  | Lists detectors \(the instances of a detector model\)\. | List |   [ detectorModel\* ](#awsiotevents-detectorModel)   |  |  | 
|   ListInputs  | Lists the inputs you have created\. | List |  |  |  | 
|   [ PutLoggingOptions ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_PutLoggingOptions.html)  | Sets or updates the AWS IoT Events logging options\. | Write |  |  |  | 
|   [ UpdateDetectorModel ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_UpdateDetectorModel.html)  | Updates a detector model\. | Write |   [ detectorModel\* ](#awsiotevents-detectorModel)   |  |  | 
|   [ UpdateInput ](https://docs.aws.amazon.com/iotevents/latest/developerguide/iotevents/latest/APIReference/API_UpdateInput.html)  | Updates an input\. | Write |   [ input\* ](#awsiotevents-input)   |  |  | 

## Resources Defined by IoT Events<a name="awsiotevents-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiotevents-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ detectorModel ](https://docs.aws.amazon.com/iotevents/latest/developerguide/detectormodel.html)  |  arn:$\{Partition\}:iotevents:$\{Region\}:$\{Account\}:detectorModel/$\{DetectorModelName\}  |  | 
|   [ input ](https://docs.aws.amazon.com/iotevents/latest/developerguide/input.html)  |  arn:$\{Partition\}:iotevents:$\{Region\}:$\{Account\}:input/$\{inputName\}  |  | 

## Condition Keys for AWS IoT Events<a name="awsiotevents-policy-keys"></a>

AWS IoT Events defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ iotevents:KeyValue ](${DocumentationLink}keyvalue.html)  | The value of the key \(identifying the device or system\) which caused the creation of this detector \(instance\)\. | String | 