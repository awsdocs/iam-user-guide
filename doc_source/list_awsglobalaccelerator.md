# Actions, Resources, and Condition Keys for AWS Global Accelerator<a name="list_awsglobalaccelerator"></a>

AWS Global Accelerator \(service prefix: `globalaccelerator`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/global-accelerator/latest/dg/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/global-accelerator/latest/api/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/global-accelerator/latest/dg/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Global Accelerator](#awsglobalaccelerator-actions-as-permissions)
+ [Resources Defined by AWS Global Accelerator](#awsglobalaccelerator-resources-for-iam-policies)
+ [Condition Keys for AWS Global Accelerator](#awsglobalaccelerator-policy-keys)

## Actions Defined by AWS Global Accelerator<a name="awsglobalaccelerator-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateAccelerator ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_CreateAccelerator.html)  | Create an accelerator\. | Write |  |  |  | 
|   [ CreateEndpointGroup ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_CreateEndpointGroup.html)  | Add an endpoint group\. | Write |   [ listener\* ](#awsglobalaccelerator-listener)   |  |  | 
|   [ CreateListener ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_CreateListener.html)  | Add a listener\. | Write |   [ accelerator\* ](#awsglobalaccelerator-accelerator)   |  |  | 
|   [ DeleteAccelerator ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_DeleteAccelerator.html)  | Delete the accelerator\. | Write |   [ accelerator\* ](#awsglobalaccelerator-accelerator)   |  |  | 
|   [ DeleteEndpointGroup ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_DeleteEndpointGroup.html)  | Delete the endpoint group\. | Write |   [ endpointgroup\* ](#awsglobalaccelerator-endpointgroup)   |  |  | 
|   [ DeleteListener ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_DeleteListener.html)  | Delete the listener\. | Write |   [ listener\* ](#awsglobalaccelerator-listener)   |  |  | 
|   [ DescribeAccelerator ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_DescribeAccelerator.html)  | Describe the accelerator\. | Read |   [ accelerator\* ](#awsglobalaccelerator-accelerator)   |  |  | 
|   [ DescribeAcceleratorAttributes ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_DescribeAcceleratorAttributes.html)  | Describe the accelerator Attributes\. | Read |   [ accelerator\* ](#awsglobalaccelerator-accelerator)   |  |  | 
|   [ DescribeEndpointGroup ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_DescribeEndpointGroup.html)  | Describe the endpoint group\. | Read |   [ endpointgroup\* ](#awsglobalaccelerator-endpointgroup)   |  |  | 
|   [ DescribeListener ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_DescribeListener.html)  | Describe the listener\. | Read |   [ listener\* ](#awsglobalaccelerator-listener)   |  |  | 
|   [ ListAccelerators ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_ListAccelerators.html)  | List the accelerators\. | List |  |  |  | 
|   [ ListEndpointGroups ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_ListEndpointGroups.html)  | List the endpoint groups\. | List |   [ listener\* ](#awsglobalaccelerator-listener)   |  |  | 
|   [ ListListeners ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_ListListeners.html)  | List the listeners\. | List |   [ accelerator\* ](#awsglobalaccelerator-accelerator)   |  |  | 
|   [ UpdateAccelerator ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_UpdateAccelerator.html)  | Update the accelerator\. | Write |   [ accelerator\* ](#awsglobalaccelerator-accelerator)   |  |  | 
|   [ UpdateAcceleratorAttributes ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_UpdateAcceleratorAttributes.html)  | Update the accelerator attributes\. | Write |   [ accelerator\* ](#awsglobalaccelerator-accelerator)   |  |  | 
|   [ UpdateEndpointGroup ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_UpdateEndpointGroup.html)  | Update the endpoint group\. | Write |   [ endpointgroup\* ](#awsglobalaccelerator-endpointgroup)   |  |  | 
|   [ UpdateListener ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_UpdateListener.html)  | Update the listener\. | Write |   [ listener\* ](#awsglobalaccelerator-listener)   |  |  | 

## Resources Defined by AWS Global Accelerator<a name="awsglobalaccelerator-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsglobalaccelerator-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ accelerator ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_Accelerator.html)  |  arn:$\{Partition\}:globalaccelerator::$\{Account\}:accelerator/$\{AcceleratorId\}  |  | 
|   [ listener ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_Listener.html)  |  arn:$\{Partition\}:globalaccelerator::$\{Account\}:accelerator/$\{AcceleratorId\}/listener/$\{ListenerId\}  |  | 
|   [ endpointgroup ](https://docs.aws.amazon.com/global-accelerator/latest/api/API_EndpointGroup.html)  |  arn:$\{Partition\}:globalaccelerator::$\{Account\}:accelerator/$\{AcceleratorId\}/listener/$\{ListenerId\}/endpoint\-group/$\{EndpointGroupId\}  |  | 

## Condition Keys for AWS Global Accelerator<a name="awsglobalaccelerator-policy-keys"></a>

GlobalAccelerator has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.