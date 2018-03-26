# Actions and Condition Context Keys for Amazon EC2 Container Service<a name="list_ecs"></a>

Amazon EC2 Container Service \(service prefix: ecs\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon EC2 Container Service**

For information about using the following Amazon ECS API actions in an IAM policy, see [Amazon ECS IAM Policies](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/;IAM_policies.html) in the *Amazon ECS Developer Guide*\.
+ `[ecs:CreateCluster](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_CreateCluster.html)`
+ `[ecs:CreateService](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_CreateService.html)`
+ `[ecs:DeleteCluster](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DeleteCluster.html)`
+ `[ecs:DeleteService](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DeleteService.html)`
+ `[ecs:DeregisterContainerInstance](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DeregisterContainerInstance.html)`
+ `[ecs:DeregisterTaskDefinition](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DeregisterTaskDefinition.html)`
+ `[ecs:DescribeClusters](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeClusters.html)`
+ `[ecs:DescribeContainerInstances](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeContainerInstances.html)`
+ `[ecs:DescribeServices](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeServices.html)`
+ `[ecs:DescribeTaskDefinition](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeTaskDefinition.html)`
+ `[ecs:DescribeTasks](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DescribeTasks.html)`
+ `[ecs:DiscoverPollEndpoint](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_DiscoverPollEndpoint.html)`
+ `[ecs:ListClusters](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListClusters.html)`
+ `[ecs:ListContainerInstances](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListContainerInstances.html)`
+ `[ecs:ListServices](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListServices.html)`
+ `[ecs:ListTaskDefinitionFamilies](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListTaskDefinitionFamilies.html)`
+ `[ecs:ListTaskDefinitions](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListTaskDefinitions.html)`
+ `[ecs:ListTasks](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_ListTasks.html)`
+ `[ecs:Poll](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_Poll.html)`
+ `[ecs:RegisterContainerInstance](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_RegisterContainerInstance.html)`
+ `[ecs:RegisterTaskDefinition](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_RegisterTaskDefinition.html)`
+ `[ecs:RunTask](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_RunTask.html)`
+ `[ecs:StartTask](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_StartTask.html)`
+ `[ecs:StartTelemetrySession](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_StartTelemetrySession.html)`
+ `[ecs:StopTask](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_StopTask.html)`
+ `[ecs:SubmitContainerStateChange](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_SubmitContainerStateChange.html)`
+ `[ecs:SubmitTaskStateChange](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_SubmitTaskStateChange.html)`
+ `[ecs:UpdateContainerAgent](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_UpdateContainerAgent.html)`
+ `[ecs:UpdateContainerInstancesState](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_UpdateContainerInstancesState.html)`
+ `[ecs:UpdateService](http://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_UpdateService.html)`

**Condition context keys for Amazon EC2 Container Service**

For information about using the following Amazon ECS conditions in an IAM policy, see [Amazon ECS IAM Policies](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/IAM_policies.html) in the *Amazon ECS Developer Guide*\.

Amazon EC2 Container Service has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ `ecs:cluster`
+ `ecs:container-instances`