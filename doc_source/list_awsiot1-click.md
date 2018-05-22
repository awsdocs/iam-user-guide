# Actions, Resources, and Condition Keys for AWS IoT 1\-Click<a name="list_awsiot1-click"></a>

AWS IoT 1\-Click \(service prefix: `iot1click`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/iot1click/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/iot1click/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/iot1click/latest/developerguide/authentication.html) permission policies\.

**Topics**
+ [Actions Defined by AWS IoT 1\-Click](#awsiot1-click-actions-as-permissions)
+ [Resources Defined by IoT 1\-Click](#awsiot1-click-resources-for-iam-policies)
+ [Condition Keys for AWS IoT 1\-Click](#awsiot1-click-policy-keys)

## Actions Defined by AWS IoT 1\-Click<a name="awsiot1-click-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_AssociateDeviceWithPlacement.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_AssociateDeviceWithPlacement.html) | Associate a device to a placement | Write | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ClaimDeviceByClaimCode.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ClaimDeviceByClaimCode.html) | Claim a batch of devices with a claim code\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_CreatePlacement.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_CreatePlacement.html) | Create a new placement in a project | Write | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_CreateProject.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_CreateProject.html) | Create a new project | Write | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DeletePlacement.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DeletePlacement.html) | Delete a placement from a project | Write | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DeleteProject.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DeleteProject.html) | Delete a project | Write | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DescribeDevice.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DescribeDevice.html) | Describe a device | Read | [device\*](#awsiot1-click-device)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DescribePlacement.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DescribePlacement.html) | Describe a placement | Read | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DescribeProject.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DescribeProject.html) | Describe a project | Read | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DissacociateDeviceFromPlacement.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_DissacociateDeviceFromPlacement.html) | Disassociate a device from a placement | Write | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_FinalizeDeviceClaim.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_FinalizeDeviceClaim.html) | Finalize a device claim | Read | [device\*](#awsiot1-click-device)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_GetDeviceMethods.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_GetDeviceMethods.html) | Get available methods of a device | Read | [device\*](#awsiot1-click-device)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_GetDevicesInPlacement.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_GetDevicesInPlacement.html) | Get devices associated to a placement | Read | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_InitializeDeviceClaim.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_InitializeDeviceClaim.html) | Initialize a device claim | Read | [device\*](#awsiot1-click-device)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_InvokeDeviceMethod.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_InvokeDeviceMethod.html) | Invoke a device method | Write | [device\*](#awsiot1-click-device)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ListDeviceEvents.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ListDeviceEvents.html) | List past events published by a device | Read | [device\*](#awsiot1-click-device)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ListDevices.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ListDevices.html) | List all devices | List |  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ListPlacements.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ListPlacements.html) | List placements in a project | Read | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ListProjects.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_ListProjects.html) | List all projects | List |  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_UnclaimDevice.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_UnclaimDevice.html) | Unclaim a device | Read | [device\*](#awsiot1-click-device)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_UpdateDeviceState.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_UpdateDeviceState.html) | Update device state | Write | [device\*](#awsiot1-click-device)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_UpdatePlacement.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_UpdatePlacement.html) | Update a placement | Write | [project\*](#awsiot1-click-project)  |  |  | 
| [http://docs.aws.amazon.com/iot1click/latest/APIReference/API_UpdateProject.html](http://docs.aws.amazon.com/iot1click/latest/APIReference/API_UpdateProject.html) | Update a project | Write | [project\*](#awsiot1-click-project)  |  |  | 

## Resources Defined by IoT 1\-Click<a name="awsiot1-click-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiot1-click-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| device | arn:$\{Partition\}:iot1click:$\{Region\}:$\{Account\}:devices/$\{DeviceId\} |  | 
| project | arn:$\{Partition\}:iot1click:$\{Region\}:$\{Account\}:projects/$\{ProjectName\} |  | 

## Condition Keys for AWS IoT 1\-Click<a name="awsiot1-click-policy-keys"></a>

IoT 1\-Click has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.