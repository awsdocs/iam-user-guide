# Actions, Resources, and Condition Keys for Amazon Storage Gateway<a name="list_amazonstoragegateway"></a>

Amazon Storage Gateway \(service prefix: `storagegateway`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/storagegateway/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/storagegateway/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/storagegateway/latest/userguide/UsingIAMWithStorageGateway.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Storage Gateway](#amazonstoragegateway-actions-as-permissions)
+ [Resources Defined by Storage Gateway](#amazonstoragegateway-resources-for-iam-policies)
+ [Condition Keys for Amazon Storage Gateway](#amazonstoragegateway-policy-keys)

## Actions Defined by Amazon Storage Gateway<a name="amazonstoragegateway-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonstoragegateway.html)

## Resources Defined by Storage Gateway<a name="amazonstoragegateway-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonstoragegateway-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/storagegateway/latest/userguide/resource_vtl-devices.html](http://docs.aws.amazon.com/storagegateway/latest/userguide/resource_vtl-devices.html) | arn:$\{Partition\}:storagegateway:$\{Region\}:$\{Account\}:gateway/$\{GatewayId\}/device/$\{Vtldevice\} |  | 
| [http://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html](http://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html) | arn:$\{Partition\}:storagegateway:$\{Region\}:$\{Account\}:gateway/$\{GatewayId\} |  | 
| [http://docs.aws.amazon.com/storagegateway/latest/userguide/GettingStartedCreateFileShare.html](http://docs.aws.amazon.com/storagegateway/latest/userguide/GettingStartedCreateFileShare.html) | arn:$\{Partition\}:storagegateway:$\{Region\}:$\{Account\}:share/$\{ShareId\} |  | 
| [http://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html#storage-gateway-vtl-concepts](http://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html#storage-gateway-vtl-concepts) | arn:$\{Partition\}:storagegateway:$\{Region\}:$\{Account\}:gateway/$\{TapeBarcode\} |  | 
| [http://docs.aws.amazon.com/storagegateway/latest/userguide/GettingStartedCreateVolumes.html](http://docs.aws.amazon.com/storagegateway/latest/userguide/GettingStartedCreateVolumes.html) | arn:$\{Partition\}:storagegateway:$\{Region\}:$\{Account\}:gateway/$\{GatewayId\}/target/$\{IscsiTarget\} |  | 
| [http://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html#volume-gateway-concepts](http://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html#volume-gateway-concepts) | arn:$\{Partition\}:storagegateway:$\{Region\}:$\{Account\}:gateway/$\{GatewayId\}/volume/$\{VolumeId\} |  | 

## Condition Keys for Amazon Storage Gateway<a name="amazonstoragegateway-policy-keys"></a>

Storage Gateway has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.