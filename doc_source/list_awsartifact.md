# Actions, resources, and condition keys for AWS Artifact<a name="list_awsartifact"></a>

AWS Artifact \(service prefix: `artifact`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/artifact/latest/ug/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/artifact/latest/ug/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/artifact/latest/ug/getting-started.html#create-iam-policy) permission policies\.

**Topics**
+ [Actions defined by AWS Artifact](#awsartifact-actions-as-permissions)
+ [Resource types defined by AWS Artifact](#awsartifact-resources-for-iam-policies)
+ [Condition keys for AWS Artifact](#awsartifact-policy-keys)

## Actions defined by AWS Artifact<a name="awsartifact-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsartifact.html)

## Resource types defined by AWS Artifact<a name="awsartifact-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsartifact-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ report\-package ](https://docs.aws.amazon.com/artifact/latest/ug/what-is-aws-artifact.html)  |  arn:$\{Partition\}:artifact:::report\-package/\*  |  | 
|   [ customer\-agreement ](https://docs.aws.amazon.com/artifact/latest/ug/$managingagreements.html)  |  arn:$\{Partition\}:artifact::$\{Account\}:customer\-agreement/\*  |  | 
|   [ agreement ](https://docs.aws.amazon.com/artifact/latest/ug/managingagreements.html)  |  arn:$\{Partition\}:artifact:::agreement/\*  |  | 

## Condition keys for AWS Artifact<a name="awsartifact-policy-keys"></a>

Artifact has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.