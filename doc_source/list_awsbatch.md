# Actions, resources, and condition keys for AWS Batch<a name="list_awsbatch"></a>

AWS Batch \(service prefix: `batch`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/batch/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/batch/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/batch/latest/userguide/IAM_policies.html) permission policies\.

**Topics**
+ [Actions defined by AWS Batch](#awsbatch-actions-as-permissions)
+ [Resource types defined by AWS Batch](#awsbatch-resources-for-iam-policies)
+ [Condition keys for AWS Batch](#awsbatch-policy-keys)

## Actions defined by AWS Batch<a name="awsbatch-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsbatch.html)

## Resource types defined by AWS Batch<a name="awsbatch-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsbatch-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ compute\-environment ](${AuthZDocPage}compute_environments.html)  |  arn:$\{Partition\}:batch:$\{Region\}:$\{Account\}:compute\-environment/$\{ComputeEnvironmentName\}  |  | 
|   [ job\-queue ](${AuthZDocPage}job_queues.html)  |  arn:$\{Partition\}:batch:$\{Region\}:$\{Account\}:job\-queue/$\{JobQueueName\}  |  | 
|   [ job\-definition ](${AuthZDocPage}job_definitions.html)  |  arn:$\{Partition\}:batch:$\{Region\}:$\{Account\}:job\-definition/$\{JobDefinitionName\}:$\{Revision\}  |  | 

## Condition keys for AWS Batch<a name="awsbatch-policy-keys"></a>

AWS Batch defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ batch:Image ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsbatch.html#awsbatch-policy-keys)  | The image used to start a container\. | String | 
|   [ batch:Privileged ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsbatch.html#awsbatch-policy-keys)  | When this parameter is true, the container is given elevated privileges on the host container instance \(similar to the root user\)\. | Boolean | 
|   [ batch:User ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsbatch.html#awsbatch-policy-keys)  | The user name or numeric uid to use inside the container\. | String | 