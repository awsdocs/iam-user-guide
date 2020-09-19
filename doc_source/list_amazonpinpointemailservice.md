# Actions, resources, and condition keys for Amazon Pinpoint Email Service<a name="list_amazonpinpointemailservice"></a>

Amazon Pinpoint Email Service \(service prefix: `ses`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/pinpoint-email/latest/APIReference/)\.

**Topics**
+ [Actions defined by Amazon Pinpoint Email Service](#amazonpinpointemailservice-actions-as-permissions)
+ [Resource types defined by Amazon Pinpoint Email Service](#amazonpinpointemailservice-resources-for-iam-policies)
+ [Condition keys for Amazon Pinpoint Email Service](#amazonpinpointemailservice-policy-keys)

## Actions defined by Amazon Pinpoint Email Service<a name="amazonpinpointemailservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonpinpointemailservice.html)

## Resource types defined by Amazon Pinpoint Email Service<a name="amazonpinpointemailservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonpinpointemailservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   configuration\-set  |  arn:$\{Partition\}:ses:$\{Region\}:$\{Account\}:configuration\-set/$\{ConfigurationSetName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpointemailservice-aws_ResourceTag___TagKey_)   | 
|   [ dedicated\-ip\-pool ](https://docs.aws.amazon.com/pinpoint-email/latest/APIReference/API_DedicatedIp.html)  |  arn:$\{Partition\}:ses:$\{Region\}:$\{Account\}:dedicated\-ip\-pool/$\{CustomVerificationEmailTemplateName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpointemailservice-aws_ResourceTag___TagKey_)   | 
|   [ deliverability\-test\-report ](https://docs.aws.amazon.com/pinpoint-email/latest/APIReference/API_DeliverabilityTestReport.html)  |  arn:$\{Partition\}:ses:$\{Region\}:$\{Account\}:deliverability\-test\-report/$\{CustomVerificationEmailTemplateName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpointemailservice-aws_ResourceTag___TagKey_)   | 
|   [ event\-destination ](https://docs.aws.amazon.com/pinpoint-email/latest/APIReference/API_EventDestination.html)  |  arn:$\{Partition\}:ses:$\{Region\}:$\{Account\}:configuration\-set/$\{ConfigurationSetName\}:event\-destination/$\{EventDestinationName\}  |  | 
|   [ identity ](https://docs.aws.amazon.com/pinpoint-email/latest/APIReference/API_IdentityInfo.html)  |  arn:$\{Partition\}:ses:$\{Region\}:$\{Account\}:identity/$\{IdentityName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpointemailservice-aws_ResourceTag___TagKey_)   | 

## Condition keys for Amazon Pinpoint Email Service<a name="amazonpinpointemailservice-policy-keys"></a>

Amazon Pinpoint Email Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of tag keys in the request | String | 
|   ses:FeedbackAddress  | The "Return\-Path" address, which specifies where bounces and complaints are sent by email feedback forwarding\. | String | 
|   ses:FromAddress  | The "From" address of a message\. | String | 
|   ses:FromDisplayName  | The "From" address that is used as the display name of a message\. | String | 
|   ses:Recipients  | The recipient addresses of a message, which include the "To", "CC", and "BCC" addresses\. | String | 