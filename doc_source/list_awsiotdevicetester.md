# Actions, resources, and condition keys for AWS IoT Device Tester<a name="list_awsiotdevicetester"></a>

AWS IoT Device Tester \(service prefix: `iot-device-tester`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/freertos/latest/userguide/device-tester-for-freertos-ug.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/freertos/latest/userguide/dev-tester-prereqs.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/freertos/latest/userguide/dev-tester-prereqs.html) permission policies\.

**Topics**
+ [Actions defined by AWS IoT Device Tester](#awsiotdevicetester-actions-as-permissions)
+ [Resource types defined by AWS IoT Device Tester](#awsiotdevicetester-resources-for-iam-policies)
+ [Condition keys for AWS IoT Device Tester](#awsiotdevicetester-policy-keys)

## Actions defined by AWS IoT Device Tester<a name="awsiotdevicetester-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CheckVersion ](https://docs.aws.amazon.com/freertos/latest/userguide/dev-tester-prereqs.html)  | Grants permission for IoT Device Tester to check if a given set of product, test suite and device tester version are compatible | Read |  |  |  | 
|   [ DownloadTestSuite ](https://docs.aws.amazon.com/freertos/latest/userguide/dev-tester-prereqs.html)  | Grants permission for IoT Device Tester to download compatible test suite versions | Read |  |  |  | 
|   [ LatestIdt ](https://docs.aws.amazon.com/freertos/latest/userguide/dev-tester-prereqs.html)  | Grants permission for IoT Device Tester to get information on latest version of device tester available | Read |  |  |  | 
|   [ SendMetrics ](https://docs.aws.amazon.com/freertos/latest/userguide/dev-tester-prereqs.html)  | Grants permissions for IoT Device Tester to send usage metrics on your behalf | Write |  |  |  | 
|   [ SupportedVersion ](https://docs.aws.amazon.com/freertos/latest/userguide/dev-tester-prereqs.html)  | Grants permission for IoT Device Tester to get list of supported products and test suite versions | Read |  |  |  | 

## Resource types defined by AWS IoT Device Tester<a name="awsiotdevicetester-resources-for-iam-policies"></a>

AWS IoT Device Tester does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS IoT Device Tester, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS IoT Device Tester<a name="awsiotdevicetester-policy-keys"></a>

IoT Device Tester has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.