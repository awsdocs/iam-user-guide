# Actions, Resources, and Condition Keys for Global Accelerator<a name="list_globalaccelerator"></a>

Global Accelerator \(service prefix: `globalaccelerator`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/global-accelerator/latest/dg/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/global-accelerator/latest/dg/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Global Accelerator](#globalaccelerator-actions-as-permissions)
+ [Resources Defined by GlobalAccelerator](#globalaccelerator-resources-for-iam-policies)
+ [Condition Keys for Global Accelerator](#globalaccelerator-policy-keys)

## Actions Defined by Global Accelerator<a name="globalaccelerator-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateAccelerator ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_CreateAccelerator.html)  | Create an accelerator\. | Write |  |  |  | 
|   [ CreateEndpointGroup ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_CreateEndpointGroup.html)  | Add an endpoint group\. | Write |   [ listener\* ](#globalaccelerator-listener)   |  |  | 
|   [ CreateListener ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_CreateListener.html)  | Add a listener\. | Write |   [ accelerator\* ](#globalaccelerator-accelerator)   |  |  | 
|   [ DeleteAccelerator ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_DeleteAccelerator.html)  | Delete the accelerator\. | Write |   [ accelerator\* ](#globalaccelerator-accelerator)   |  |  | 
|   [ DeleteEndpointGroup ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_DeleteEndpointGroup.html)  | Delete the endpoint group\. | Write |   [ endpointgroup\* ](#globalaccelerator-endpointgroup)   |  |  | 
|   [ DeleteListener ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_DeleteListener.html)  | Delete the listener\. | Write |   [ listener\* ](#globalaccelerator-listener)   |  |  | 
|   [ DescribeAccelerator ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_DescribeAccelerator.html)  | Describe the accelerator\. | Read |   [ accelerator\* ](#globalaccelerator-accelerator)   |  |  | 
|   [ DescribeAcceleratorAttributes ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_DescribeAcceleratorAttributes.html)  | Describe the accelerator Attributes\. | Read |   [ accelerator\* ](#globalaccelerator-accelerator)   |  |  | 
|   [ DescribeEndpointGroup ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_DescribeEndpointGroup.html)  | Describe the endpoint group\. | Read |   [ endpointgroup\* ](#globalaccelerator-endpointgroup)   |  |  | 
|   [ DescribeListener ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_DescribeListener.html)  | Describe the listener\. | Read |   [ listener\* ](#globalaccelerator-listener)   |  |  | 
|   [ ListAccelerators ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_ListAccelerators.html)  | List the accelerators\. | List |  |  |  | 
|   [ ListEndpointGroups ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_ListEndpointGroups.html)  | List the endpoint groups\. | List |   [ listener\* ](#globalaccelerator-listener)   |  |  | 
|   [ ListListeners ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_ListListeners.html)  | List the listeners\. | List |   [ accelerator\* ](#globalaccelerator-accelerator)   |  |  | 
|   [ UpdateAccelerator ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_UpdateAccelerator.html)  | Update the accelerator\. | Write |   [ accelerator\* ](#globalaccelerator-accelerator)   |  |  | 
|   [ UpdateAcceleratorAttributes ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_UpdateAcceleratorAttributes.html)  | Update the accelerator attributes\. | Write |   [ accelerator\* ](#globalaccelerator-accelerator)   |  |  | 
|   [ UpdateEndpointGroup ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_UpdateEndpointGroup.html)  | Update the endpoint group\. | Write |   [ endpointgroup\* ](#globalaccelerator-endpointgroup)   |  |  | 
|   [ UpdateListener ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_UpdateListener.html)  | Update the listener\. | Write |   [ listener\* ](#globalaccelerator-listener)   |  |  | 

## Resources Defined by GlobalAccelerator<a name="globalaccelerator-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#globalaccelerator-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ accelerator ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_Accelerator.html)  |  arn:$\{Partition\}:globalaccelerator::$\{Account\}:accelerator/$\{AcceleratorId\}  |  | 
|   [ listener ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_Listener.html)  |  arn:$\{Partition\}:globalaccelerator::$\{Account\}:accelerator/$\{AcceleratorId\}/listener/$\{ListenerId\}  |  | 
|   [ endpointgroup ](https://docs.aws.amazon.com/global-accelerator/latest/APIReference/API_EndpointGroup.html)  |  arn:$\{Partition\}:globalaccelerator::$\{Account\}:accelerator/$\{AcceleratorId\}/listener/$\{ListenerId\}/endpoint\-group/$\{EndpointGroupId\}  |  | 

## Condition Keys for Global Accelerator<a name="globalaccelerator-policy-keys"></a>

GlobalAccelerator has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.