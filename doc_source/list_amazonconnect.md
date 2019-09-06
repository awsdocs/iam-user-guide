# Actions, Resources, and Condition Keys for Amazon Connect<a name="list_amazonconnect"></a>

Amazon Connect \(service prefix: `connect`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/connect/latest/adminguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/connect/latest/adminguide/)\.

**Topics**
+ [Actions Defined by Amazon Connect](#amazonconnect-actions-as-permissions)
+ [Resources Defined by Amazon Connect](#amazonconnect-resources-for-iam-policies)
+ [Condition Keys for Amazon Connect](#amazonconnect-policy-keys)

## Actions Defined by Amazon Connect<a name="amazonconnect-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   CreateInstance  | Grants permissions to create a new Amazon Connect instance\. The associated required actions grant permissions to configure instance settings\. | Write |  |  |   ds:CreateAlias   ds:DeleteDirectory   ds:DescribeDirectories   firehose:DescribeDeliveryStream   firehose:ListDeliveryStreams   iam:CreateServiceLinkedRole   kinesis:DescribeStream   kinesis:ListStreams   kms:CreateGrant   kms:DescribeKey   kms:ListAliases   kms:RetireGrant   s3:CreateBucket   s3:ListAllMyBuckets   | 
|   DescribeInstance  | Grants permissions to view details of an Amazon Connect instance\. This is required to create an instance\. | Read |   [ instance\* ](#amazonconnect-instance)   |  |   firehose:DescribeDeliveryStream   firehose:ListDeliveryStreams   kinesis:DescribeStream   kinesis:ListStreams   kms:DescribeKey   kms:ListAliases   s3:ListAllMyBuckets   | 
|   DestroyInstance  | Grants permissions to delete an Amazon Connect instance\. When you remove an instance, the link to an existing AWS directory is also removed\. | Write |   [ instance\* ](#amazonconnect-instance)   |  |  | 
|   GetCurrentMetricData  | Grants permissions to retrieve current metric data for the queues in an Amazon Connect instance | Read |   [ queue\* ](#amazonconnect-queue)   |  |  | 
|   GetFederationToken  | Allows federation into an instance when using SAML\-based authentication for identity management\. | Read |   [ instance\* ](#amazonconnect-instance)   |  |  | 
|   GetFederationTokens  | Grants permissions to federate in to an Amazon Connect instance \(Log in as administrator functionality in the AWS console\)\. | Write |   [ instance\* ](#amazonconnect-instance)   |  |   connect:DescribeInstance   connect:ListInstances   ds:DescribeDirectories   | 
|   GetMetricData  | Grants permissions to retrieve historical metric data for queues in an Amazon Connect instance | Read |   [ queue\* ](#amazonconnect-queue)   |  |  | 
|   ListInstances  | Grants permissions to view the Amazon Connect instances associated with an AWS account\. | List |  |  |  | 
|   ModifyInstance  | Grants permissions to modify configuration settings for an existing Amazon Connect instance\. The associated required actions grant permission modify the settings for the instance\.  | Write |   [ instance\* ](#amazonconnect-instance)   |  |   firehose:DescribeDeliveryStream   firehose:ListDeliveryStreams   kinesis:DescribeStream   kinesis:ListStreams   kms:CreateGrant   kms:DescribeKey   kms:ListAliases   kms:RetireGrant   s3:CreateBucket   s3:ListAllMyBuckets   | 
|   StartOutboundVoiceContact  | Grants permissions to initiate outbound calls using the Amazon Connect API\. | Write |   [ contact\* ](#amazonconnect-contact)   |  |  | 
|   StopContact  | Grants permissions to stop contacts that were initiated using the Amazon Connect API\. If you use this operation on an active contact the contact ends, even if an agent is active on a call with a customer\. | Write |   [ contact\* ](#amazonconnect-contact)   |  |  | 

## Resources Defined by Amazon Connect<a name="amazonconnect-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonconnect-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   instance  |  arn:$\{Partition\}:connect::$\{Account\}:instance/$\{InstanceId\}  |  | 
|   contact  |  arn:$\{Partition\}:connect::$\{Account\}:instance/$\{InstanceId\}/contact/$\{ContactId\}  |  | 
|   queue  |  arn:$\{Partition\}:connect::$\{Account\}:instance/$\{InstanceId\}/queue/$\{QueueId\}  |  | 

## Condition Keys for Amazon Connect<a name="amazonconnect-policy-keys"></a>

Connect has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.