# Actions, Resources, and Condition Keys for AWS Cloud Map<a name="list_awscloudmap"></a>

AWS Cloud Map \(service prefix: `servicediscovery`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/cloud-map/latest/dg/what-is-cloud-map.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/cloud-map/latest/api/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/cloud-map/latest/dg/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Cloud Map](#awscloudmap-actions-as-permissions)
+ [Resource Types Defined by AWS Cloud Map](#awscloudmap-resources-for-iam-policies)
+ [Condition Keys for AWS Cloud Map](#awscloudmap-policy-keys)

## Actions Defined by AWS Cloud Map<a name="awscloudmap-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateHttpNamespace ](https://docs.aws.amazon.com/cloud-map/latest/api/API_CreateHttpNamespace.html)  | Creates an HTTP namespace\. | Write |  |  |  | 
|   [ CreatePrivateDnsNamespace ](https://docs.aws.amazon.com/cloud-map/latest/api/API_CreatePrivateDnsNamespace.html)  | Creates a private namespace based on DNS, which will be visible only inside a specified Amazon VPC\. | Write |  |  |  | 
|   [ CreatePublicDnsNamespace ](https://docs.aws.amazon.com/cloud-map/latest/api/API_CreatePublicDnsNamespace.html)  | Creates a public namespace based on DNS, which will be visible on the internet\. | Write |  |  |  | 
|   [ CreateService ](https://docs.aws.amazon.com/cloud-map/latest/api/API_CreateService.html)  | Creates a service\. | Write |  |   [ servicediscovery:NamespaceArn ](#awscloudmap-servicediscovery_NamespaceArn)   |  | 
|   [ DeleteNamespace ](https://docs.aws.amazon.com/cloud-map/latest/api/API_DeleteNamespace.html)  | Deletes a specified namespace\. | Write |   [ namespace\* ](#awscloudmap-namespace)   |  |  | 
|   [ DeleteService ](https://docs.aws.amazon.com/cloud-map/latest/api/API_DeleteService.html)  | Deletes a specified service\. | Write |   [ service\* ](#awscloudmap-service)   |  |  | 
|   [ DeregisterInstance ](https://docs.aws.amazon.com/cloud-map/latest/api/API_DeregisterInstance.html)  | Deletes the records and the health check, if any, that Amazon Route 53 created for the specified instance\. | Write |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   [ DiscoverInstances ](https://docs.aws.amazon.com/cloud-map/latest/api/API_DiscoverInstances.html)  | Discovers registered instances for a specified namespace and service\. | Read |  |   [ servicediscovery:NamespaceName ](#awscloudmap-servicediscovery_NamespaceName)   [ servicediscovery:ServiceName ](#awscloudmap-servicediscovery_ServiceName)   |  | 
|   [ GetInstance ](https://docs.aws.amazon.com/cloud-map/latest/api/API_GetInstance.html)  | Gets information about a specified instance\. | Read |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   [ GetInstancesHealthStatus ](https://docs.aws.amazon.com/cloud-map/latest/api/API_GetInstancesHealthStatus.html)  | Gets the current health status \(Healthy, Unhealthy, or Unknown\) of one or more instances\. | Read |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   [ GetNamespace ](https://docs.aws.amazon.com/cloud-map/latest/api/API_GetNamespace.html)  | Gets information about a namespace\. | Read |   [ namespace\* ](#awscloudmap-namespace)   |  |  | 
|   [ GetOperation ](https://docs.aws.amazon.com/cloud-map/latest/api/API_GetOperation.html)  | Gets information about a specific operation\. | Read |  |  |  | 
|   [ GetService ](https://docs.aws.amazon.com/cloud-map/latest/api/API_GetService.html)  | Gets the settings for a specified service\. | Read |   [ service\* ](#awscloudmap-service)   |  |  | 
|   [ ListInstances ](https://docs.aws.amazon.com/cloud-map/latest/api/API_ListInstances.html)  | Gets summary information about the instances that were registered with a specified service\. | List |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   [ ListNamespaces ](https://docs.aws.amazon.com/cloud-map/latest/api/API_ListNamespaces.html)  | Gets information about the namespaces\. | List |  |  |  | 
|   [ ListOperations ](https://docs.aws.amazon.com/cloud-map/latest/api/API_ListOperations.html)  | Lists operations that match the criteria that you specify\. | List |  |  |  | 
|   [ ListServices ](https://docs.aws.amazon.com/cloud-map/latest/api/API_ListServices.html)  | Gets settings for all the services that match specified filters\. | List |  |  |  | 
|   [ RegisterInstance ](https://docs.aws.amazon.com/cloud-map/latest/api/API_RegisterInstance.html)  | Registers an instance based on the settings in a specified service\. | Write |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   [ UpdateInstanceCustomHealthStatus ](https://docs.aws.amazon.com/cloud-map/latest/api/API_UpdateInstanceCustomHealthStatus.html)  | Updates the current health status for an instance that has a custom health check\. | Write |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   [ UpdateService ](https://docs.aws.amazon.com/cloud-map/latest/api/API_UpdateService.html)  | Updates the settings in a specified service\. | Write |   [ service\* ](#awscloudmap-service)   |  |  | 

## Resource Types Defined by AWS Cloud Map<a name="awscloudmap-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloudmap-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ namespace ](https://docs.aws.amazon.com/cloud-map/latest/dg/API_Namespace.html)  |  arn:$\{Partition\}:servicediscovery:$\{Region\}:$\{Account\}:namespace/$\{NamespaceId\}  |  | 
|   [ service ](https://docs.aws.amazon.com/cloud-map/latest/dg/API_Service.html)  |  arn:$\{Partition\}:servicediscovery:$\{Region\}:$\{Account\}:service/$\{ServiceId\}  |  | 

## Condition Keys for AWS Cloud Map<a name="awscloudmap-policy-keys"></a>

AWS Cloud Map defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ servicediscovery:NamespaceArn ](https://docs.aws.amazon.com/cloud-map/latest/dg/access-control-overview.html#specifying-conditions)  | A filter that lets you get objects by specifying the Amazon Resource Name \(ARN\) for the related namespace\. | String | 
|   [ servicediscovery:NamespaceName ](https://docs.aws.amazon.com/cloud-map/latest/dg/access-control-overview.html#specifying-conditions)  | A filter that lets you get objects by specifying the name of the related namespace\. | String | 
|   [ servicediscovery:ServiceArn ](https://docs.aws.amazon.com/cloud-map/latest/dg/access-control-overview.html#specifying-conditions)  | A filter that lets you get objects by specifying the Amazon Resource Name \(ARN\) for the related service\. | String | 
|   [ servicediscovery:ServiceName ](https://docs.aws.amazon.com/cloud-map/latest/dg/access-control-overview.html#specifying-conditions)  | A filter that lets you get objects by specifying the name of the related service\. | String | 