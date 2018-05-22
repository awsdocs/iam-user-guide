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
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2containerservice.html)

## Resources Defined by EC2 Container Service<a name="amazonec2containerservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonec2containerservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_clusters.html](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_clusters.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:cluster/$\{ClusterName\} |  | 
| [http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#ECS_ARN_Format](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#ECS_ARN_Format) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:container/$\{ContainerId\} |  | 
| [http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:container\-instance/$\{ContainerInstanceId\} |  | 
| [http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:service/$\{ServiceName\} |  | 
| [http://docs.aws.amazon.com/AmazonECS/latest/developerguide/scheduling_tasks.html](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/scheduling_tasks.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:task/$\{TaskId\} |  | 
| [http://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html) | arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:task\-definition/$\{TaskDefinitionFamilyName:$\{TaskDefinitionRevisionNumber\} |  | 

## Condition Keys for Amazon EC2 Container Service<a name="amazonec2containerservice-policy-keys"></a>

Amazon EC2 Container Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys) | The ARN of an ECS cluster\. | ARN | 
| [http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys) | The ARN of an ECS container instance\. | ARN | 