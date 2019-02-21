# Actions, Resources, and Condition Keys for AWS DeepLens<a name="list_awsdeeplens"></a>

AWS DeepLens \(service prefix: `deeplens`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by AWS DeepLens](#awsdeeplens-actions-as-permissions)
+ [Resources Defined by DeepLens](#awsdeeplens-resources-for-iam-policies)
+ [Condition Keys for AWS DeepLens](#awsdeeplens-policy-keys)

## Actions Defined by AWS DeepLens<a name="awsdeeplens-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsdeeplens.html)

## Resources Defined by DeepLens<a name="awsdeeplens-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsdeeplens-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   device  |  arn:$\{Partition\}:deeplens:$\{Region\}:$\{Account\}:device/$\{DeviceName\}  |  | 
|   project  |  arn:$\{Partition\}:deeplens:$\{Region\}:$\{Account\}:project/$\{ProjectName\}  |  | 
|   model  |  arn:$\{Partition\}:deeplens:$\{Region\}:$\{Account\}:model/$\{ModelName\}  |  | 

## Condition Keys for AWS DeepLens<a name="awsdeeplens-policy-keys"></a>

DeepLens has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.