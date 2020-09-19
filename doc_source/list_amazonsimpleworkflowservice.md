# Actions, resources, and condition keys for Amazon Simple Workflow Service<a name="list_amazonsimpleworkflowservice"></a>

Amazon Simple Workflow Service \(service prefix: `swf`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/amazonswf/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/amazonswf/latest/apireference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Simple Workflow Service](#amazonsimpleworkflowservice-actions-as-permissions)
+ [Resource types defined by Amazon Simple Workflow Service](#amazonsimpleworkflowservice-resources-for-iam-policies)
+ [Condition keys for Amazon Simple Workflow Service](#amazonsimpleworkflowservice-policy-keys)

## Actions defined by Amazon Simple Workflow Service<a name="amazonsimpleworkflowservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsimpleworkflowservice.html)

## Resource types defined by Amazon Simple Workflow Service<a name="amazonsimpleworkflowservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsimpleworkflowservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ domain ](https://docs.aws.amazon.com/swf/latest/developerguide/swf-dev-domains.html)  |  arn:$\{Partition\}:swf::$\{Account\}:domain/$\{DomainName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsimpleworkflowservice-aws_ResourceTag___TagKey_)   | 

## Condition keys for Amazon Simple Workflow Service<a name="amazonsimpleworkflowservice-policy-keys"></a>

Amazon Simple Workflow Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Tag for request\. | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Tag for resource\. | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Tag for key\. | String | 
|   [ swf:activityType\.name ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only an activity type of the specified name\. | String | 
|   [ swf:activityType\.version ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Contstrains the policy statement to only an activity type of the specified version\. | String | 
|   [ swf:defaultTaskList\.name ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that specify a matching defaultTaskList name\. | String | 
|   [ swf:name ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only activities or workflows with the specified name\. | String | 
|   [ swf:tagFilter\.tag ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that specify a matching tagFilter\.tag value\. | String | 
|   [ swf:tagList\.member\.0 ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that contain the specified tag\. | String | 
|   [ swf:tagList\.member\.1 ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that contain the specified tag\. | String | 
|   [ swf:tagList\.member\.2 ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that contain the specified tag\. | String | 
|   [ swf:tagList\.member\.3 ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that contain the specified tag\. | String | 
|   [ swf:tagList\.member\.4 ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that contain the specified tag\. | String | 
|   [ swf:taskList\.name ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that specify a tasklist with the specified name\. | String | 
|   [ swf:typeFilter\.name ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that specify a type filter with the specified name\. | String | 
|   [ swf:typeFilter\.version ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that specify a type filter with the specified version\. | String | 
|   [ swf:version ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only activities or workflows with the specified version\. | String | 
|   [  swf:workflowType\.name ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only a workflow of the specified type\. | String | 
|   [ swf:workflowType\.name ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that specify a workflow type of the specified name\. | String | 
|   [ swf:workflowType\.version ](https://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html##swf-dev-iam.api)  | Constrains the policy statement to only requests that specify a workflow type of the specified version\. | String | 