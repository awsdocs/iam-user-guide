# Actions, Resources, and Condition Keys for AWS App Mesh<a name="list_awsappmesh"></a>

AWS App Mesh \(service prefix: `appmesh`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/app-mesh/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/app-mesh/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/app-mesh/latest/userguide/IAM_policies.html) permission policies\.

**Topics**
+ [Actions Defined by AWS App Mesh](#awsappmesh-actions-as-permissions)
+ [Resources Defined by App Mesh](#awsappmesh-resources-for-iam-policies)
+ [Condition Keys for AWS App Mesh](#awsappmesh-policy-keys)

## Actions Defined by AWS App Mesh<a name="awsappmesh-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsappmesh.html)

## Resources Defined by App Mesh<a name="awsappmesh-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsappmesh-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ mesh ](https://docs.aws.amazon.com/app-mesh/latest/userguide/meshes.html)  |  arn:$\{Partition\}:appmesh:$\{Region\}:$\{Account\}:mesh/$\{MeshName\}  |  | 
|   [ virtualservice ](https://docs.aws.amazon.com/app-mesh/latest/userguide/virtual_services.html)  |  arn:$\{Partition\}:appmesh:$\{Region\}:$\{Account\}:mesh/$\{MeshName\}/virtualService/$\{VirtualServiceName\}  |  | 
|   [ virtualnode ](https://docs.aws.amazon.com/app-mesh/latest/userguide/virtual_nodes.html)  |  arn:$\{Partition\}:appmesh:$\{Region\}:$\{Account\}:mesh/$\{MeshName\}/virtualNode/$\{VirtualNodeName\}  |  | 
|   [ virtualrouter ](https://docs.aws.amazon.com/app-mesh/latest/userguide/virtual_routers.html)  |  arn:$\{Partition\}:appmesh:$\{Region\}:$\{Account\}:mesh/$\{MeshName\}/virtualRouter/$\{VirtualRouterName\}  |  | 
|   [ route ](https://docs.aws.amazon.com/app-mesh/latest/userguide/routes.html)  |  arn:$\{Partition\}:appmesh:$\{Region\}:$\{Account\}:mesh/$\{MeshName\}/virtualRouter/$\{VirtualRouterName\}/route/$\{RouteName\}  |  | 

## Condition Keys for AWS App Mesh<a name="awsappmesh-policy-keys"></a>

App Mesh has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.