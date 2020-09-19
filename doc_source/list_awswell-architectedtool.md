# Actions, resources, and condition keys for AWS Well\-Architected Tool<a name="list_awswell-architectedtool"></a>

AWS Well\-Architected Tool \(service prefix: `wellarchitected`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/wellarchitected/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/wellarchitected/latest/userguide/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/wellarchitected/latest/userguide/iam-auth-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS Well\-Architected Tool](#awswell-architectedtool-actions-as-permissions)
+ [Resource types defined by AWS Well\-Architected Tool](#awswell-architectedtool-resources-for-iam-policies)
+ [Condition keys for AWS Well\-Architected Tool](#awswell-architectedtool-policy-keys)

## Actions defined by AWS Well\-Architected Tool<a name="awswell-architectedtool-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateWorkload ](https://docs.aws.amazon.com/wellarchitected/latest/userguide/define-workload.html)  | Creates a new workload\. | Write |  |  |  | 
|   [ CreateWorkloadShare ](https://docs.aws.amazon.com/wellarchitected/latest/userguide/workloads-sharing.html)  | Shares a workload with another account\. | Write |   [ workload\* ](#awswell-architectedtool-workload)   |  |  | 
|   [ DeleteWorkload ](https://docs.aws.amazon.com/wellarchitected/latest/userguide/workloads-delete.html)  | Deletes an existing workload\. | Write |   [ workload\* ](#awswell-architectedtool-workload)   |  |  | 
|   [ GetWorkload ](https://docs.aws.amazon.com/wellarchitected/latest/userguide/workload-details.html)  | Retrieves the specified workload\. | Read |   [ workload\* ](#awswell-architectedtool-workload)   |  |  | 
|   [ ListWorkloads ](https://docs.aws.amazon.com/wellarchitected/latest/userguide/workloads-page.html)  | Lists the workloads in this account\. | List |  |  |  | 

## Resource types defined by AWS Well\-Architected Tool<a name="awswell-architectedtool-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awswell-architectedtool-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ workload ](https://docs.aws.amazon.com/wellarchitected/latest/userguide/iam-auth-access.html)  |  arn:$\{Partition\}:wellarchitected:$\{Region\}:$\{Account\}:workload/$\{ResourceId\}  |  | 

## Condition keys for AWS Well\-Architected Tool<a name="awswell-architectedtool-policy-keys"></a>

Well\-Architected Tool has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.