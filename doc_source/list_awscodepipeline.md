# Actions, resources, and condition keys for AWS CodePipeline<a name="list_awscodepipeline"></a>

AWS CodePipeline \(service prefix: `codepipeline`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/codepipeline/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/codepipeline/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/codepipeline/latest/userguide/security-iam.html) permission policies\.

**Topics**
+ [Actions defined by AWS CodePipeline](#awscodepipeline-actions-as-permissions)
+ [Resource types defined by AWS CodePipeline](#awscodepipeline-resources-for-iam-policies)
+ [Condition keys for AWS CodePipeline](#awscodepipeline-policy-keys)

## Actions defined by AWS CodePipeline<a name="awscodepipeline-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodepipeline.html)

## Resource types defined by AWS CodePipeline<a name="awscodepipeline-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodepipeline-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ action ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:$\{PipelineName\}/$\{StageName\}/$\{ActionName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awscodepipeline-aws_ResourceTag___TagKey_)   | 
|   [ actiontype ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:actiontype:$\{Owner\}/$\{Category\}/$\{Provider\}/$\{Version\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awscodepipeline-aws_ResourceTag___TagKey_)   | 
|   [ pipeline ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:$\{PipelineName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awscodepipeline-aws_ResourceTag___TagKey_)   | 
|   [ stage ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:$\{PipelineName\}/$\{StageName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awscodepipeline-aws_ResourceTag___TagKey_)   | 
|   [ webhook ](https://docs.aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format)  |  arn:$\{Partition\}:codepipeline:$\{Region\}:$\{Account\}:webhook:$\{WebhookName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awscodepipeline-aws_ResourceTag___TagKey_)   | 

## Condition keys for AWS CodePipeline<a name="awscodepipeline-policy-keys"></a>

AWS CodePipeline defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of tag keys in the request | String | 