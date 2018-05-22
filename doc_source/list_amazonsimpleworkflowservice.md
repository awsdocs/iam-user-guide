# Actions, Resources, and Condition Keys for Amazon Simple Workflow Service<a name="list_amazonsimpleworkflowservice"></a>

Amazon Simple Workflow Service \(service prefix: `swf`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/amazonswf/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/amazonswf/latest/apireference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/swf-dev-iam.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Simple Workflow Service](#amazonsimpleworkflowservice-actions-as-permissions)
+ [Resources Defined by SWF](#amazonsimpleworkflowservice-resources-for-iam-policies)
+ [Condition Keys for Amazon Simple Workflow Service](#amazonsimpleworkflowservice-policy-keys)

## Actions Defined by Amazon Simple Workflow Service<a name="amazonsimpleworkflowservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsimpleworkflowservice.html)

## Resources Defined by SWF<a name="amazonsimpleworkflowservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsimpleworkflowservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/swf/latest/developerguide/swf-dev-domains.html](http://docs.aws.amazon.com/swf/latest/developerguide/swf-dev-domains.html) | arn:$\{Partition\}:swf::$\{Account\}:domain/$\{DomainName\} |  | 

## Condition Keys for Amazon Simple Workflow Service<a name="amazonsimpleworkflowservice-policy-keys"></a>

Amazon Simple Workflow Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only a workflow of the specified type\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only an activity type of the specified name\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Contstrains the policy statement to only an activity type of the specified version\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a matching defaultTaskList name\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only activities or workflows with the specified name\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a matching tagFilter\.tag value\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that contain the specified tag\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a tasklist with the specified name\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a type filter with the specified name\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a type filter with the specified version\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only activities or workflows with the specified version\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a workflow type of the specified name\. | String | 
| [http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api](http://docs.aws.amazon.com/amazonswf/latest/APIReference/swf-dev-iam.html#swf-dev-iam.api) | Constrains the policy statement to only requests that specify a workflow type of the specified version\. | String | 