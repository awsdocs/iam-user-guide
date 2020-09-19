# Actions, resources, and condition keys for Amazon Pinpoint<a name="list_amazonpinpoint"></a>

Amazon Pinpoint \(service prefix: `mobiletargeting`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/pinpoint/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/pinpoint/latest/apireference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/pinpoint/latest/developerguide/permissions-actions.html#permissions-actions-apiactions) permission policies\.

**Topics**
+ [Actions defined by Amazon Pinpoint](#amazonpinpoint-actions-as-permissions)
+ [Resource types defined by Amazon Pinpoint](#amazonpinpoint-resources-for-iam-policies)
+ [Condition keys for Amazon Pinpoint](#amazonpinpoint-policy-keys)

## Actions defined by Amazon Pinpoint<a name="amazonpinpoint-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonpinpoint.html)

## Resource types defined by Amazon Pinpoint<a name="amazonpinpoint-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonpinpoint-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ apps ](https://docs.aws.amazon.com/pinpoint/latest/developerguide/gettingstarted.html#gettingstarted-addapp)  |  arn:$\{Partition\}:mobiletargeting:$\{Region\}:$\{Account\}:apps/$\{AppId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpoint-aws_ResourceTag___TagKey_)   | 
|   [ campaigns ](https://docs.aws.amazon.com/pinpoint/latest/apireference/rest-api-campaigns.html)  |  arn:$\{Partition\}:mobiletargeting:$\{Region\}:$\{Account\}:apps/$\{AppId\}/campaigns/$\{CampaignId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpoint-aws_ResourceTag___TagKey_)   | 
|   [ journeys ](https://docs.aws.amazon.com/pinpoint/latest/apireference/apps-application-id-journeys.html)  |  arn:$\{Partition\}:mobiletargeting:$\{Region\}:$\{Account\}:apps/$\{AppId\}/journeys/$\{JourneyId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpoint-aws_ResourceTag___TagKey_)   | 
|   [ segments ](https://docs.aws.amazon.com/pinpoint/latest/apireference/rest-api-segments.html)  |  arn:$\{Partition\}:mobiletargeting:$\{Region\}:$\{Account\}:apps/$\{AppId\}/segments/$\{SegmentId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpoint-aws_ResourceTag___TagKey_)   | 
|   [ templates ](https://docs.aws.amazon.com/pinpoint/latest/apireference/templates.html)  |  arn:$\{Partition\}:mobiletargeting:$\{Region\}:$\{Account\}:templates/$\{TemplateName\}/$\{ChannelType\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonpinpoint-aws_ResourceTag___TagKey_)   | 
|   [ recommenders ](https://docs.aws.amazon.com/pinpoint/latest/apireference/recommenders.html)  |  arn:$\{Partition\}:mobiletargeting:$\{Region\}:$\{Account\}:recommenders/$\{RecommenderId\}  |  | 

## Condition keys for Amazon Pinpoint<a name="amazonpinpoint-policy-keys"></a>

Amazon Pinpoint defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-permissions.html#iam-contextkeys)  | Filters access by a key that is present in the request the user makes to the pinpoint service\. | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-permissions.html#iam-contextkeys)  | Filters access by a tag key and value pair\. | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-permissions.html#iam-contextkeys)  | Filters access by the list of all the tag key names present in the request the user makes to the pinpoint service\. | String | 