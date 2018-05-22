# Actions, Resources, and Condition Keys for Amazon Simple Systems Manager<a name="list_amazonsimplesystemsmanager"></a>

Amazon Simple Systems Manager \(service prefix: `ssm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/systems-manager/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/systems-manager/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-configuring-access-iam-create.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Simple Systems Manager](#amazonsimplesystemsmanager-actions-as-permissions)
+ [Resources Defined by SSM](#amazonsimplesystemsmanager-resources-for-iam-policies)
+ [Condition Keys for Amazon Simple Systems Manager](#amazonsimplesystemsmanager-policy-keys)

## Actions Defined by Amazon Simple Systems Manager<a name="amazonsimplesystemsmanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsimplesystemsmanager.html)

## Resources Defined by SSM<a name="amazonsimplesystemsmanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsimplesystemsmanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-ssm-docs.html](http://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-ssm-docs.html) | arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:document/$\{DocumentName\} |  | 
| maintenancewindow | arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:maintenancewindow/$\{ResourceId\} |  | 
| [http://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html](http://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html) | arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:managed\-instance/$\{ManagedInstanceName\} |  | 
| parameter | arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:parameter/$\{FullyQualifiedParameterName\} |  | 
| patchbaseline | arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:patchbaseline/$\{ResourceId\} |  | 
| windowtarget | arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:windowtarget/$\{ResourceId\} |  | 
| windowtask | arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:windowtask/$\{ResourceId\} |  | 

## Condition Keys for Amazon Simple Systems Manager<a name="amazonsimplesystemsmanager-policy-keys"></a>

SSM has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.