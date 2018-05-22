# Actions, Resources, and Condition Keys for AWS IoT<a name="list_awsiot"></a>

AWS IoT \(service prefix: `iot`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/iot/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/iot/latest/apireference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/iot/latest/developerguide/authorization.html) permission policies\.

**Topics**
+ [Actions Defined by AWS IoT](#awsiot-actions-as-permissions)
+ [Resources Defined by IoT](#awsiot-resources-for-iam-policies)
+ [Condition Keys for AWS IoT](#awsiot-policy-keys)

## Actions Defined by AWS IoT<a name="awsiot-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsiot.html)

## Resources Defined by IoT<a name="awsiot-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiot-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/custom-authorizer.html](http://docs.aws.amazon.com/iot/latest/developerguide/custom-authorizer.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:authorizer/$\{AuthorizerName\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/x509-certs.html](http://docs.aws.amazon.com/iot/latest/developerguide/x509-certs.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:cacert/$\{CACertificate\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/x509-certs.html](http://docs.aws.amazon.com/iot/latest/developerguide/x509-certs.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:cert/$\{Certificate\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/iot-message-broker.html](http://docs.aws.amazon.com/iot/latest/developerguide/iot-message-broker.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:client/$\{ClientId\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/iot-indexing.html](http://docs.aws.amazon.com/iot/latest/developerguide/iot-indexing.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:index/$\{IndexName\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/iot-jobs.html](http://docs.aws.amazon.com/iot/latest/developerguide/iot-jobs.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:job/$\{JobId\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/iot-policies.html](http://docs.aws.amazon.com/iot/latest/developerguide/iot-policies.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:policy/$\{PolicyName\} |  | 
| [https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) | arn:$\{Partition\}:iam::$\{Account\}:role/$\{Role\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/authorizing-direct-aws.html](http://docs.aws.amazon.com/iot/latest/developerguide/authorizing-direct-aws.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:rolealias/$\{RoleAlias\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/thing-registry.html](http://docs.aws.amazon.com/iot/latest/developerguide/thing-registry.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:thing/$\{ThingName\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/thing-groups.html](http://docs.aws.amazon.com/iot/latest/developerguide/thing-groups.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:thinggroup/$\{ThingGroupName\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/thing-types.html](http://docs.aws.amazon.com/iot/latest/developerguide/thing-types.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:thingtype/$\{ThingTypeName\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/iot-message-broker.html](http://docs.aws.amazon.com/iot/latest/developerguide/iot-message-broker.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:topic/$\{TopicName\} |  | 
| [http://docs.aws.amazon.com/iot/latest/developerguide/topics.html](http://docs.aws.amazon.com/iot/latest/developerguide/topics.html) | arn:$\{Partition\}:iot:$\{Region\}:$\{Account\}:topicfilter/$\{TopicFilter\} |  | 

## Condition Keys for AWS IoT<a name="awsiot-policy-keys"></a>

IoT has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.