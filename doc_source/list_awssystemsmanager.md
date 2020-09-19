# Actions, resources, and condition keys for AWS Systems Manager<a name="list_awssystemsmanager"></a>

AWS Systems Manager \(service prefix: `ssm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/systems-manager/latest/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by AWS Systems Manager](#awssystemsmanager-actions-as-permissions)
+ [Resource types defined by AWS Systems Manager](#awssystemsmanager-resources-for-iam-policies)
+ [Condition keys for AWS Systems Manager](#awssystemsmanager-policy-keys)

## Actions defined by AWS Systems Manager<a name="awssystemsmanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awssystemsmanager.html)

## Resource types defined by AWS Systems Manager<a name="awssystemsmanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awssystemsmanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ association ](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-associations.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:association/$\{AssociationId\}  |  | 
|   [ automation\-execution ](https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-working.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:automation\-execution/$\{AutomationExecutionId\}  |  | 
|   [ automation\-definition ](https://docs.aws.amazon.com/systems-manager/latest/userguide/automation-documents.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:automation\-definition/$\{AutomationDefinitionName:VersionId\}  |  | 
|   [ document ](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-ssm-docs.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:document/$\{DocumentName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awssystemsmanager-aws_ResourceTag___TagKey_)   [ ssm:resourceTag/tag\-key ](#awssystemsmanager-ssm_resourceTag_tag-key)   | 
|   [ instance ](https://docs.aws.amazon.com/systems-manager/latest/userguide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awssystemsmanager-aws_ResourceTag___TagKey_)   [ ssm:resourceTag/tag\-key ](#awssystemsmanager-ssm_resourceTag_tag-key)   | 
|   [ maintenancewindow ](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-maintenance.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:maintenancewindow/$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awssystemsmanager-aws_ResourceTag___TagKey_)   [ ssm:resourceTag/tag\-key ](#awssystemsmanager-ssm_resourceTag_tag-key)   | 
|   [ managed\-instance ](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:managed\-instance/$\{ManagedInstanceName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awssystemsmanager-aws_ResourceTag___TagKey_)   [ ssm:resourceTag/tag\-key ](#awssystemsmanager-ssm_resourceTag_tag-key)   | 
|   [ managed\-instance\-inventory ](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-inventory-configuring.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:managed\-instance\-inventory/$\{InstanceId\}  |  | 
|   [ opsitem ](https://docs.aws.amazon.com/systems-manager/latest/userguide/OpsCenter-working-with-OpsItems.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:opsitem/$\{ResourceId\}  |  | 
|   [ parameter ](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:parameter/$\{FullyQualifiedParameterName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awssystemsmanager-aws_ResourceTag___TagKey_)   [ ssm:resourceTag/tag\-key ](#awssystemsmanager-ssm_resourceTag_tag-key)   | 
|   [ patchbaseline ](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-patch.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:patchbaseline/$\{PatchBaselineIdResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awssystemsmanager-aws_ResourceTag___TagKey_)   [ ssm:resourceTag/tag\-key ](#awssystemsmanager-ssm_resourceTag_tag-key)   | 
|   [ session ](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:session/$\{SessionId\}  |  | 
|   [ resourcedatasync ](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-inventory-datasync.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:resource\-data\-sync/$\{SyncName\}  |  | 
|   [ servicesetting ](https://docs.aws.amazon.com/systems-manager/latest/userguide/API_ServiceSetting.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:servicesetting/$\{ResourceId\}  |  | 
|   [ windowtarget ](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-maintenance-assign-targets.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:windowtarget/$\{WindowTargetId\}  |  | 
|   [ windowtask ](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-maintenance-assign-tasks.html)  |  arn:$\{Partition\}:ssm:$\{Region\}:$\{Account\}:windowtask/$\{WindowTaskId\}  |  | 

## Condition keys for AWS Systems Manager<a name="awssystemsmanager-policy-keys"></a>

AWS Systems Manager defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   aws:RequestTag/$\{TagKey\}  | Filters 'Create' requests based on the allowed set of values for a specified tags | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#policy-conditions)  | Filters access based on a tag key\-value pair assigned to the AWS resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#policy-conditions)  | Filters 'Create' requests based on whether mandatory tags are included in the request | String | 
|   [ ssm:Overwrite ](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#policy-conditions)  | Filters access by controlling whether the values for specified resources can be overwritten\. | String | 
|   [ ssm:Recursive ](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#policy-conditions)  | Filters access for resources created in a hierarchical structure\. | String | 
|   [ ssm:SessionDocumentAccessCheck ](https://docs.aws.amazon.com/systems-manager/latest/userguide/getting-started-sessiondocumentaccesscheck.html)  | Filters access by verifying that a user has permission to access either the default Session Manager configuration document or the custom configuration document specified in a request\. | Boolean | 
|   ssm:SyncType  | Filters access by verifying that a user also has access to the ResourceDataSync SyncType specified in the request | String | 
|   [ ssm:resourceTag/tag\-key ](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#policy-conditions)  | Filters access based on a tag key\-value pair assigned to the Systems Manager resource | String | 