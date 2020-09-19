# Actions, resources, and condition keys for Amazon Elastic Container Service<a name="list_amazonelasticcontainerservice"></a>

Amazon Elastic Container Service \(service prefix: `ecs`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/IAM_policies.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Elastic Container Service](#amazonelasticcontainerservice-actions-as-permissions)
+ [Resource types defined by Amazon Elastic Container Service](#amazonelasticcontainerservice-resources-for-iam-policies)
+ [Condition keys for Amazon Elastic Container Service](#amazonelasticcontainerservice-policy-keys)

## Actions defined by Amazon Elastic Container Service<a name="amazonelasticcontainerservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonelasticcontainerservice.html)

## Resource types defined by Amazon Elastic Container Service<a name="amazonelasticcontainerservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonelasticcontainerservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ cluster ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_clusters.html)  |  arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:cluster/$\{ClusterName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-aws_ResourceTag___TagKey_)   [ ecs:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-ecs_ResourceTag___TagKey_)   | 
|   [ container\-instance ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html)  |  arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:container\-instance/$\{ContainerInstanceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-aws_ResourceTag___TagKey_)   [ ecs:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-ecs_ResourceTag___TagKey_)   | 
|   [ service ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html)  |  arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:service/$\{ServiceName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-aws_ResourceTag___TagKey_)   [ ecs:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-ecs_ResourceTag___TagKey_)   | 
|   [ task ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/scheduling_tasks.html)  |  arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:task/$\{TaskId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-aws_ResourceTag___TagKey_)   [ ecs:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-ecs_ResourceTag___TagKey_)   | 
|   [ task\-definition ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html)  |  arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:task\-definition/$\{TaskDefinitionFamilyName\}:$\{TaskDefinitionRevisionNumber\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-aws_ResourceTag___TagKey_)   [ ecs:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-ecs_ResourceTag___TagKey_)   | 
|   [ capacity\-provider ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/capacity_provider_definitions.html)  |  arn:$\{Partition\}:ecs:$\{Region\}:$\{Account\}:capacity\-provider/$\{CapacityProviderName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-aws_ResourceTag___TagKey_)   [ ecs:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-ecs_ResourceTag___TagKey_)   | 
|   [ task\-set ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_sets.html)  |  arn:$\{Partition\}:ecs:$\{region\}:$\{Account\}:task\-set/$\{ClusterName\}/$\{ServiceName\}/$\{TaskSetId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-aws_ResourceTag___TagKey_)   [ ecs:ResourceTag/$\{TagKey\} ](#amazonelasticcontainerservice-ecs_ResourceTag___TagKey_)   | 

## Condition keys for Amazon Elastic Container Service<a name="amazonelasticcontainerservice-policy-keys"></a>

Amazon Elastic Container Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   aws:RequestTag/$\{TagKey\}  | Filters actions based on the presence of tag key\-value pairs in the request\. | String | 
|   aws:ResourceTag/$\{TagKey\}  | Filters actions based on tag key\-value pairs attached to the resource\. | String | 
|   aws:TagKeys  | Filters actions based on the presence of tag keys in the request\. | String | 
|   ecs:ResourceTag/$\{TagKey\}  | Filters actions based on tag key\-value pairs attached to the resource\. | String | 
|   [ ecs:capacity\-provider ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys)  | The ARN of an Amazon ECS capacity provider\. | ARN | 
|   [ ecs:cluster ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys)  | The ARN of an Amazon ECS cluster\. | ARN | 
|   [ ecs:container\-instances ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys)  | The ARN of an Amazon ECS container instance\. | ARN | 
|   [ ecs:service ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys)  | The ARN of an Amazon ECS service\. | ARN | 
|   [ ecs:task\-definition ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/iam-policy-structure.html#amazon-ecs-keys)  | The ARN of an Amazon ECS task definition\. | ARN | 