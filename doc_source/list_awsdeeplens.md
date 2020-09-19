# Actions, resources, and condition keys for AWS DeepLens<a name="list_awsdeeplens"></a>

AWS DeepLens \(service prefix: `deeplens`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions defined by AWS DeepLens](#awsdeeplens-actions-as-permissions)
+ [Resource types defined by AWS DeepLens](#awsdeeplens-resources-for-iam-policies)
+ [Condition keys for AWS DeepLens](#awsdeeplens-policy-keys)

## Actions defined by AWS DeepLens<a name="awsdeeplens-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsdeeplens.html)

## Resource types defined by AWS DeepLens<a name="awsdeeplens-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsdeeplens-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   device  |  arn:$\{Partition\}:deeplens:$\{Region\}:$\{Account\}:device/$\{DeviceName\}  |  | 
|   project  |  arn:$\{Partition\}:deeplens:$\{Region\}:$\{Account\}:project/$\{ProjectName\}  |  | 
|   model  |  arn:$\{Partition\}:deeplens:$\{Region\}:$\{Account\}:model/$\{ModelName\}  |  | 

## Condition keys for AWS DeepLens<a name="awsdeeplens-policy-keys"></a>

DeepLens has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.