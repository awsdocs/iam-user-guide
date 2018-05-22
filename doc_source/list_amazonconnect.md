# Actions, Resources, and Condition Keys for Amazon Connect<a name="list_amazonconnect"></a>

Amazon Connect \(service prefix: `connect`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/connect/latest/adminguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/connect/latest/adminguide/)\.
+ Learn how to protect this service and its resources by [using IAM]() permission policies\.

**Topics**
+ [Actions Defined by Amazon Connect](#amazonconnect-actions-as-permissions)
+ [Resources Defined by Connect](#amazonconnect-resources-for-iam-policies)
+ [Condition Keys for Amazon Connect](#amazonconnect-policy-keys)

## Actions Defined by Amazon Connect<a name="amazonconnect-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| CreateInstance | Grants permissions to create a new Amazon Connect instance\. The associated required actions grant permissions to configure instance settings\. | Write |  |  |  | 
| DescribeInstance | Grants permissions to view details of an Amazon Connect instance\. This is required to create an instance\. | Read | [instance\*](#amazonconnect-instance)  |  | firehose:DescribeDeliveryStream firehose:ListDeliveryStreams kinesis:DescribeStream kinesis:ListStreams kms:DescribeKey kms:ListAliases s3:ListAllMyBuckets  | 
| DestroyInstance | Grants permissions to delete an Amazon Connect instance\. When you remove an instance, the link to an existing AWS directory is also removed\. | Write | [instance\*](#amazonconnect-instance)  |  |  | 
| GetFederationToken | Allows federation into an instance when using SAML\-based authentication for identity management\. | Read | [instance\*](#amazonconnect-instance)  |  |  | 
| GetFederationTokens | Grants permissions to federate in to an Amazon Connect instance \(Log in as administrator functionality in the AWS console\)\. | Read | [instance\*](#amazonconnect-instance)  |  | connect:DescribeInstance connect:DestroyInstance connect:ListInstances ds:DeleteDirectory ds:DescribeDirectories ds:UnauthorizeApplication kms:RetireGrant  | 
| ListInstances | Grants permissions to view the Amazon Connect instances associated with an AWS account\. | List |  |  |  | 
| ModifyInstance | Grants permissions to modify configuration settings for an existing Amazon Connect instance\. The associated required actions grant permission modify the settings for the instance\.  | Write | [instance\*](#amazonconnect-instance)  |  | firehose:DescribeDeliveryStream firehose:ListDeliveryStreams kinesis:DescribeStream kinesis:ListStreams kms:CreateGrant kms:DescribeKey kms:ListAliases kms:RetireGrant s3:CreateBucket s3:ListAllMyBuckets  | 
| StartOutboundVoiceContact | Grants permissions to initiate outbound calls using the Amazon Connect API\. | Write | [contact\*](#amazonconnect-contact)  |  |  | 
| StopContact | Grants permissions to stop contacts that were initiated using the Amazon Connect API\. If you use this operation on an active contact the contact ends, even if an agent is active on a call with a customer\. | Write | [contact\*](#amazonconnect-contact)  |  |  | 

## Resources Defined by Connect<a name="amazonconnect-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonconnect-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| contact | arn:$\{Partition\}:connect::$\{Account\}:instance/$\{InstanceId\}/contact/$\{ContactId\} |  | 
| instance | arn:$\{Partition\}:connect::$\{Account\}:instance/$\{InstanceId\} |  | 

## Condition Keys for Amazon Connect<a name="amazonconnect-policy-keys"></a>

Connect has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.