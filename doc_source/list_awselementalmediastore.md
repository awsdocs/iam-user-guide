# Actions, Resources, and Condition Keys for AWS Elemental MediaStore<a name="list_awselementalmediastore"></a>

AWS Elemental MediaStore \(service prefix: `mediastore`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/mediastore/latest/ug/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/mediastore/latest/ug/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/mediastore/latest/ug/IAM-user-create.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Elemental MediaStore](#awselementalmediastore-actions-as-permissions)
+ [Resources Defined by MediaStore](#awselementalmediastore-resources-for-iam-policies)
+ [Condition Keys for AWS Elemental MediaStore](#awselementalmediastore-policy-keys)

## Actions Defined by AWS Elemental MediaStore<a name="awselementalmediastore-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateContainer ](http://docs.aws.amazon.com/mediastore/latest/ug/containers-create.html)  | Creates a storage container | Write |  |  |  | 
|   [ DeleteContainer ](http://docs.aws.amazon.com/mediastore/latest/ug/containers-delete.html)  | Deletes a storage container | Write |  |  |  | 
|   [ DeleteContainerPolicy ](http://docs.aws.amazon.com/mediastore/latest/ug/policies-edit.html)  | Deletes a container storage policy\. | Permissions management |  |  |  | 
|   [ DeleteObject ](http://docs.aws.amazon.com/mediastore/latest/ug/objects-delete.html)  | Deletes an object\. | Write |  |  |  | 
|   [ DescribeContainer ](http://docs.aws.amazon.com/mediastore/latest/ug/containers-view-details.html)  | Retrieves details of a specific container | List |  |  |  | 
|   [ DescribeObject ](http://docs.aws.amazon.com/mediastore/latest/ug/objects-view-details.html)  | Retrieves an objects metadata\. | Read |  |  |  | 
|   [ GetContainerPolicy ](http://docs.aws.amazon.com/mediastore/latest/ug/policies-view.html)  | Retrieves a container resource policy\. | Read |  |  |  | 
|   [ GetObject ](http://docs.aws.amazon.com/mediastore/latest/ug/objects-download.html)  | Retrieves an object\. | Read |  |  |  | 
|   [ ListContainers ](http://docs.aws.amazon.com/mediastore/latest/ug/ccontainers-view-list.html)  | Retrieves a list of storage containers\. | List |  |  |  | 
|   [ ListItems ](http://docs.aws.amazon.com/mediastore/latest/ug/objects-view-list.html)  | Retrieves a list of items like objects or folders\. | List |  |  |  | 
|   [ PutContainerPolicy ](http://docs.aws.amazon.com/mediastore/latest/ug/policies-edit.html)  | Adds or modifies a container resource policy\. | Permissions management |  |  |  | 
|   [ PutObject ](http://docs.aws.amazon.com/mediastore/latest/ug/objects-upload.html)  | Uploads an object\. | Write |  |  |  | 

## Resources Defined by MediaStore<a name="awselementalmediastore-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awselementalmediastore-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ container ](http://docs.aws.amazon.com/mediastore/latest/ug/containers.html)  |  arn:$\{Partition\}:mediastore:$\{Region\}:$\{Account\}:container/$\{ContainerName\}  |  | 

## Condition Keys for AWS Elemental MediaStore<a name="awselementalmediastore-policy-keys"></a>

MediaStore has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.