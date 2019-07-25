# Actions, Resources, and Condition Keys for AWS Cloud Map<a name="list_awscloudmap"></a>

AWS Cloud Map \(service prefix: `servicediscovery`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com//cloud-map/latest/dg/)\.

**Topics**
+ [Actions Defined by AWS Cloud Map](#awscloudmap-actions-as-permissions)
+ [Resources Defined by AWS Cloud Map](#awscloudmap-resources-for-iam-policies)
+ [Condition Keys for AWS Cloud Map](#awscloudmap-policy-keys)

## Actions Defined by AWS Cloud Map<a name="awscloudmap-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   CreateHttpNamespace  | Creates an HTTP namespace\. | Write |  |  |  | 
|   CreatePrivateDnsNamespace  | Creates a private namespace based on DNS, which will be visible only inside a specified Amazon VPC\. | Write |  |  |  | 
|   CreatePublicDnsNamespace  | Creates a public namespace based on DNS, which will be visible on the internet\. | Write |  |  |  | 
|   CreateService  | Creates a service\. | Write |  |   [ servicediscovery:NamespaceArn ](#awscloudmap-servicediscovery_NamespaceArn)   |  | 
|   DeleteNamespace  | Deletes a specified namespace\. | Write |   [ namespace\* ](#awscloudmap-namespace)   |  |  | 
|   DeleteService  | Deletes a specified service\. | Write |   [ service\* ](#awscloudmap-service)   |  |  | 
|   DeregisterInstance  | Deletes the records and the health check, if any, that Amazon Route 53 created for the specified instance\. | Write |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   DiscoverInstances  | Discovers registered instances for a specified namespace and service\. | Read |  |   [ servicediscovery:NamespaceName ](#awscloudmap-servicediscovery_NamespaceName)   [ servicediscovery:ServiceName ](#awscloudmap-servicediscovery_ServiceName)   |  | 
|   GetInstance  | Gets information about a specified instance\. | Read |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   GetInstancesHealthStatus  | Gets the current health status \(Healthy, Unhealthy, or Unknown\) of one or more instances\. | Read |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   GetNamespace  | Gets information about a namespace\. | Read |   [ namespace\* ](#awscloudmap-namespace)   |  |  | 
|   GetOperation  | Gets information about a specific operation\. | Read |  |  |  | 
|   GetService  | Gets the settings for a specified service\. | Read |   [ service\* ](#awscloudmap-service)   |  |  | 
|   ListInstances  | Gets summary information about the instances that were registered with a specified service\. | List |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   ListNamespaces  | Gets information about the namespaces\. | List |  |  |  | 
|   ListOperations  | Lists operations that match the criteria that you specify\. | List |  |  |  | 
|   ListServices  | Gets settings for all the services that match specified filters\. | List |  |  |  | 
|   RegisterInstance  | Registers an instance based on the settings in a specified service\. | Write |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   UpdateInstanceCustomHealthStatus  | Updates the current health status for an instance that has a custom health check\. | Write |  |   [ servicediscovery:ServiceArn ](#awscloudmap-servicediscovery_ServiceArn)   |  | 
|   UpdateService  | Updates the settings in a specified service\. | Write |   [ service\* ](#awscloudmap-service)   |  |  | 

## Resources Defined by AWS Cloud Map<a name="awscloudmap-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloudmap-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   namespace  |  arn:$\{Partition\}:servicediscovery:$\{Region\}:$\{Account\}:namespace/$\{NamespaceId\}  |  | 
|   service  |  arn:$\{Partition\}:servicediscovery:$\{Region\}:$\{Account\}:service/$\{ServiceId\}  |  | 

## Condition Keys for AWS Cloud Map<a name="awscloudmap-policy-keys"></a>

AWS Cloud Map defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ servicediscovery:NamespaceArn ](https://docs.aws.amazon.com//cloud-map/latest/dg/access-control-overview.html#specifying-conditions)  | A filter that lets you get objects by specifying the Amazon Resource Name \(ARN\) for the related namespace\. | String | 
|   [ servicediscovery:NamespaceName ](https://docs.aws.amazon.com//cloud-map/latest/dg/access-control-overview.html#specifying-conditions)  | A filter that lets you get objects by specifying the name of the related namespace\. | String | 
|   [ servicediscovery:ServiceArn ](https://docs.aws.amazon.com//cloud-map/latest/dg/access-control-overview.html#specifying-conditions)  | A filter that lets you get objects by specifying the Amazon Resource Name \(ARN\) for the related service\. | String | 
|   [ servicediscovery:ServiceName ](https://docs.aws.amazon.com//cloud-map/latest/dg/access-control-overview.html#specifying-conditions)  | A filter that lets you get objects by specifying the name of the related service\. | String | 