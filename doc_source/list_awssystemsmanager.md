# Actions, Resources, and Condition Keys for AWS Systems Manager<a name="list_awssystemsmanager"></a>

AWS Systems Manager \(service prefix: `ssm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/systems-manager/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/systems-manager/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Systems Manager](#awssystemsmanager-actions-as-permissions)
+ [Resources Defined by Systems Manager](#awssystemsmanager-resources-for-iam-policies)
+ [Condition Keys for AWS Systems Manager](#awssystemsmanager-policy-keys)

## Actions Defined by AWS Systems Manager<a name="awssystemsmanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awssystemsmanager.html)

## Resources Defined by Systems Manager<a name="awssystemsmanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awssystemsmanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ document ](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-ssm-docs.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:document/$\{DocumentName\}  |  | 
|   maintenancewindow  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:maintenancewindow/$\{ResourceId\}  |  | 
|   [ managed\-instance ](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:managed\-instance/$\{ManagedInstanceName\}  |  | 
|   [ instance ](https://docs.aws.amazon.com/systems-manager/latest/userguide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}  |   [ ssm:resourceTag/tag\-key ](#awssystemsmanager-ssm_resourceTag_tag-key)   | 
|   parameter  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:parameter/$\{FullyQualifiedParameterName\}  |   [ ssm:resourceTag/tag\-key ](#awssystemsmanager-ssm_resourceTag_tag-key)   | 
|   patchbaseline  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:patchbaseline/$\{ResourceId\}  |  | 
|   session  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:session/$\{ResourceId\}  |  | 
|   windowtarget  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:windowtarget/$\{ResourceId\}  |  | 
|   windowtask  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:windowtask/$\{ResourceId\}  |  | 

## Condition Keys for AWS Systems Manager<a name="awssystemsmanager-policy-keys"></a>

AWS Systems Manager defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ ssm:resourceTag/tag\-key ](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-rc-setting-up-cmdsec.html)  | A tag key and value pair\. | String | 