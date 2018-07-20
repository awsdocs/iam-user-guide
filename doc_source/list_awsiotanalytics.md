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
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsiotanalytics.html)

## Resources Defined by IoT Analytics<a name="awsiotanalytics-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiotanalytics-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ channel ](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/channel.html)  |  arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:channel/$\{ChannelName\}  |  | 
|   [ dataset ](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/dataset.html)  |  arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:dataset/$\{DatasetName\}  |  | 
|   [ datastore ](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/datastore.html)  |  arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:datastore/$\{DatastoreName\}  |  | 
|   [ pipeline ](http://docs.aws.amazon.com/iotanalytics/latest/developerguide/pipeline.html)  |  arn:$\{Partition\}:iotanalytics:$\{Region\}:$\{Account\}:pipeline/$\{PipelineName\}  |  | 

## Condition Keys for AWS IoT Analytics<a name="awsiotanalytics-policy-keys"></a>

IoT Analytics has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.