# Actions, Resources, and Condition Keys for Amazon EC2 Container Service<a name="list_amazonec2containerservice"></a>

Amazon EC2 Container Service \(service prefix: `ecs`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/IAM_policies.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon EC2 Container Service](#amazonec2containerservice-actions-as-permissions)
+ [Resources Defined by EC2 Container Service](#amazonec2containerservice-resources-for-iam-policies)
+ [Condition Keys for Amazon EC2 Container Service](#amazonec2containerservice-policy-keys)

## Actions Defined by Amazon EC2 Container Service<a name="amazonec2containerservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [CreateCluster](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_CreateCluster.html) | Creates a new Amazon ECS cluster\. |   |  |  |  | 
| [CreateService](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_CreateService.html) | Runs and maintains a desired number of tasks from a specified task definition\. |   |  |  |  | 
| [DeleteCluster](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DeleteCluster.html) | Deletes the specified cluster\. |   | [cluster\*](#amazonec2containerservice-cluster)  |  |  | 
| [DeleteService](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DeleteService.html) | Deletes a specified service within a cluster\. |   |  |  |  | 
| [DeregisterContainerInstance](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DeregisterContainerInstance.html) | Deregisters an Amazon ECS container instance from the specified cluster\. |   | [cluster\*](#amazonec2containerservice-cluster)  |  |  | 
| [DeregisterTaskDefinition](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DeregisterTaskDefinition.html) | Deregisters the specified task definition by family and revision\. |   |  |  |  | 
| [DescribeClusters](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeClusters.html) | Describes one or more of your clusters\. |   | [cluster\*](#amazonec2containerservice-cluster)  |  |  | 
| [DescribeContainerInstances](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeContainerInstances.html) | Describes Amazon EC2 Container Service container instances\. |   | [container\-instance\*](#amazonec2containerservice-container-instance)  |  |  | 
| [DescribeServices](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeServices.html) | Describes the specified services running in your cluster\. |   |  |  |  | 
| [DescribeTaskDefinition](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeTaskDefinition.html) | Describes a task definition\. You can specify a family and revision to find information about a specific task definition, or you can simply specify the family to find the latest ACTIVE revision in that family\. |   |  |  |  | 
| [DescribeTasks](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeTasks.html) | Describes a specified task or tasks\. |   | [task\*](#amazonec2containerservice-task)  |  |  | 
| [DiscoverPollEndpoint](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DiscoverPollEndpoint.html) | Returns an endpoint for the Amazon EC2 Container Service agent to poll for updates\. |   |  |  |  | 
| [ListClusters](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListClusters.html) | Returns a list of existing clusters\. |   |  |  |  | 
| [ListContainerInstances](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListContainerInstances.html) | Returns a list of container instances in a specified cluster\. |   | [container\-instance\*](#amazonec2containerservice-container-instance)  |  |  | 
| [ListServices](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListServices.html) | Lists the services that are running in a specified cluster\. |   |  |  |  | 
| [ListTaskDefinitionFamilies](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListServices.html) | Returns a list of task definition families that are registered to your account \(which may include task definition families that no longer have any ACTIVE task definitions\)\. |   |  |  |  | 
| [ListTaskDefinitions](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListTaskDefinitions.html) | Returns a list of task definitions that are registered to your account\. |   |  |  |  | 
| [ListTasks](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListTasks.html) | Returns a list of tasks for a specified cluster\. |   | [container\-instance\*](#amazonec2containerservice-container-instance)  |  |  | 
| Poll \[permission only\] | Grants permission to an agent to connect with the Amazon ECS service to report status and get commands\. |   |  |  |  | 
| [RegisterContainerInstance](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_RegisterContainerInstance.html) | Registers an EC2 instance into the specified cluster\. |   | [cluster\*](#amazonec2containerservice-cluster)  |  |  | 
| [RegisterTaskDefinition](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_RegisterTaskDefinition.html) | Registers a new task definition from the supplied family and containerDefinitions\. |   |  |  |  | 
| [RunTask](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_RunTask.html) | Start a task using random placement and the default Amazon ECS scheduler\. |   | [task\*](#amazonec2containerservice-task)  |  |  | 
| [StartTask](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_StartTask.html) | Starts a new task from the specified task definition on the specified container instance or instances\. |   | [task\-definition\*](#amazonec2containerservice-task-definition)  |  |  | 
| [StopTask](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_StopTask.html) | Stops a running task\. |   | [task\*](#amazonec2containerservice-task)  |  |  | 
| [SubmitContainerStateChange](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_SubmitContainerStateChange.html) | Sent to acknowledge that a container changed states\. |   | [cluster\*](#amazonec2containerservice-cluster)  |  |  | 
| [SubmitTaskStateChange](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_SubmitTaskStateChange.html) | Sent to acknowledge that a task changed states\. |   | [cluster\*](#amazonec2containerservice-cluster)  |  |  | 
| [UpdateContainerAgent](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_UpdateContainerAgent.html) | Updates the Amazon ECS container agent on a specified container instance\. |   | [container\-instance\*](#amazonec2containerservice-container-instance)  |  |  | 
| [UpdateContainerInstancesState](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_UpdateContainerInstancesState.html) | Enables the user to modify the status of an Amazon ECS container instance\. |   | [container\-instance\*](#amazonec2containerservice-container-instance)  |  |  | 
| [UpdateService](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_UpdateService.html) | Modifies the desired count, deployment configuration, or task definition used in a service\. |   |  |  |  | 

## Resources Defined by EC2 Container Service<a name="amazonec2containerservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonec2containerservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [cluster](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_clusters.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:cluster/$\{ClusterName\} |  | 
| [container](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#ECS_ARN_Format) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:container/$\{ContainerId\} |  | 
| [container\-instance](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:container\-instance/$\{ContainerInstanceId\} |  | 
| [service](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:service/$\{ServiceName\} |  | 
| [task](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/scheduling_tasks.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:task/$\{TaskId\} |  | 
| [task\-definition](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:task\-definition/$\{TaskDefinitionFamilyName:$\{TaskDefinitionRevisionNumber\} |  | 

## Condition Keys for Amazon EC2 Container Service<a name="amazonec2containerservice-policy-keys"></a>

Amazon EC2 Container Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [ecs:cluster](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys) | The ARN of an ECS cluster\. | ARN | 
| [ecs:container\-instances](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys) | The ARN of an ECS container instance\. | ARN | 