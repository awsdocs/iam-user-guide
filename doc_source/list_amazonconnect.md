# Actions, resources, and condition keys for Amazon Connect<a name="list_amazonconnect"></a>

Amazon Connect \(service prefix: `connect`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/connect/latest/adminguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/connect/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/console/connect/security/access-control/) permission policies\.

**Topics**
+ [Actions defined by Amazon Connect](#amazonconnect-actions-as-permissions)
+ [Resource types defined by Amazon Connect](#amazonconnect-resources-for-iam-policies)
+ [Condition keys for Amazon Connect](#amazonconnect-policy-keys)

## Actions defined by Amazon Connect<a name="amazonconnect-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonconnect.html)

## Resource types defined by Amazon Connect<a name="amazonconnect-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonconnect-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ instance ](https://docs.aws.amazon.com/connect/latest/adminguide/amazon-connect-instances.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}  |  | 
|   [ contact ](https://docs.aws.amazon.com/connect/latest/adminguide/connect-contact-attributes.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/contact/$\{ContactId\}  |  | 
|   [ user ](https://docs.aws.amazon.com/connect/latest/adminguide/connect-agents.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/agent/$\{UserId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonconnect-aws_ResourceTag___TagKey_)   | 
|   [ routing\-profile ](https://docs.aws.amazon.com/connect/latest/adminguide/routing-profiles.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/routing\-profile/$\{RoutingProfileId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonconnect-aws_ResourceTag___TagKey_)   | 
|   [ security\-profile ](https://docs.aws.amazon.com/connect/latest/adminguide/connect-security-profiles.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/security\-profile/$\{SecurityProfileId\}  |  | 
|   [ hierarchy\-group ](https://docs.aws.amazon.com/connect/latest/adminguide/agent-hierarchy.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/agent\-group/$\{HierarchyGroupId\}  |  | 
|   [ queue ](https://docs.aws.amazon.com/connect/latest/adminguide/create-queue.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/queue/$\{QueueId\}  |  | 
|   [ contact\-flow ](https://docs.aws.amazon.com/connect/latest/adminguide/connect-contact-flows.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/contact\-flow/$\{ContactFlowId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonconnect-aws_ResourceTag___TagKey_)   | 
|   [ hours\-of\-operation ](https://docs.aws.amazon.com/connect/latest/adminguide/set-hours-operation.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/operating\-hours/$\{HoursOfOperationId\}  |  | 
|   [ phone\-number ](https://docs.aws.amazon.com/connect/latest/adminguide/contact-center-phone-number.html)  |  arn:$\{Partition\}:connect:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}/phone\-numbers/$\{PhoneNumberId\}  |  | 

## Condition keys for Amazon Connect<a name="amazonconnect-policy-keys"></a>

Amazon Connect defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the presence of tag key\-value pairs in the request\. | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource\. | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of tag keys in the request\. | String | 