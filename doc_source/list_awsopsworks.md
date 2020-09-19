# Actions, resources, and condition keys for AWS OpsWorks<a name="list_awsopsworks"></a>

AWS OpsWorks \(service prefix: `opsworks`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/opsworks/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/opsworks/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/opsworks/latest/userguide/workingsecurity.html) permission policies\.

**Topics**
+ [Actions defined by AWS OpsWorks](#awsopsworks-actions-as-permissions)
+ [Resource types defined by AWS OpsWorks](#awsopsworks-resources-for-iam-policies)
+ [Condition keys for AWS OpsWorks](#awsopsworks-policy-keys)

## Actions defined by AWS OpsWorks<a name="awsopsworks-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssignInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignInstance.html)  | Assign a registered instance to a layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ AssignVolume ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignVolume.html)  | Assigns one of the stack's registered Amazon EBS volumes to a specified instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ AssociateElasticIp ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssociateElasticIp.html)  | Associates one of the stack's registered Elastic IP addresses with a specified instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ AttachElasticLoadBalancer ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_AttachElasticLoadBalancer.html)  | Attaches an Elastic Load Balancing load balancer to a specified layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ CloneStack ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_CloneStack.html)  | Creates a clone of a specified stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ CreateApp ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateApp.html)  | Creates an app for a specified stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ CreateDeployment ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateDeployment.html)  | Runs deployment or stack commands | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ CreateInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateInstance.html)  | Creates an instance in a specified stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ CreateLayer ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateLayer.html)  | Creates a layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ CreateStack ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateStack.html)  | Creates a new stack | Write |  |  |  | 
|   [ CreateUserProfile ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateUserProfile.html)  | Creates a new user profile | Write |  |  |  | 
|   [ DeleteApp ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteApp.html)  | Deletes a specified app | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DeleteInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteInstance.html)  | Deletes a specified instance, which terminates the associated Amazon EC2 instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DeleteLayer ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteLayer.html)  | Deletes a specified layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DeleteStack ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteStack.html)  | Deletes a specified stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DeleteUserProfile ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteUserProfile.html)  | Deletes a user profile | Write |  |  |  | 
|   [ DeregisterEcsCluster ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterEcsCluster.html)  | Deletes a user profile | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DeregisterElasticIp ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterElasticIp.html)  | Deregisters a specified Elastic IP address | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DeregisterInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterInstance.html)  | Deregister a registered Amazon EC2 or on\-premises instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DeregisterRdsDbInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterRdsDbInstance.html)  | Deregisters an Amazon RDS instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DeregisterVolume ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterVolume.html)  | Deregisters an Amazon EBS volume | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeAgentVersions ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeAgentVersions.html)  | Describes the available AWS OpsWorks agent versions | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeApps ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeApps.html)  | Requests a description of a specified set of apps | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeCommands ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeCommands.html)  | Describes the results of specified commands | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeDeployments ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeDeployments.html)  | Requests a description of a specified set of deployments | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeEcsClusters ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeEcsClusters.html)  | Describes Amazon ECS clusters that are registered with a stack | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeElasticIps ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticIps.html)  | Describes Elastic IP addresses | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeElasticLoadBalancers ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticLoadBalancers.html)  | Describes a stack's Elastic Load Balancing instances | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeInstances ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeInstances.html)  | Requests a description of a set of instances | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeLayers ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLayers.html)  | Requests a description of one or more layers in a specified stack | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeLoadBasedAutoScaling ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLoadBasedAutoScaling.html)  | Describes load\-based auto scaling configurations for specified layers | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeMyUserProfile ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeMyUserProfile.html)  | Describes a user's SSH information | List |  |  |  | 
|   [ DescribePermissions ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribePermissions.html)  | Describes the permissions for a specified stack | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeRaidArrays ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRaidArrays.html)  | Describe an instance's RAID arrays | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeRdsDbInstances ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRdsDbInstances.html)  | Describes Amazon RDS instances | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeServiceErrors ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeServiceErrors.html)  | Describes AWS OpsWorks service errors | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeStackProvisioningParameters ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackProvisioningParameters.html)  | Requests a description of a stack's provisioning parameters | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeStackSummary ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackSummary.html)  | Describes the number of layers and apps in a specified stack, and the number of instances in each state, such as running\_setup or online | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeStacks ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStacks.html)  | Requests a description of one or more stacks | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeTimeBasedAutoScaling ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeTimeBasedAutoScaling.html)  | Describes time\-based auto scaling configurations for specified instances | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DescribeUserProfiles ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeUserProfiles.html)  | Describe specified users | List |  |  |  | 
|   [ DescribeVolumes ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeVolumes.html)  | Describes an instance's Amazon EBS volumes | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DetachElasticLoadBalancer ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DetachElasticLoadBalancer.html)  | Detaches a specified Elastic Load Balancing instance from its layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ DisassociateElasticIp ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_DisassociateElasticIp.html)  | Disassociates an Elastic IP address from its instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ GetHostnameSuggestion ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_GetHostnameSuggestion.html)  | Gets a generated host name for the specified layer, based on the current host name theme | Read |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ GrantAccess ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html)  | Grants RDP access to a Windows instance for a specified time period | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ ListTags ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_ListTags.html)  | Returns a list of tags that are applied to the specified stack or layer | List |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ RebootInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html)  | Reboots a specified instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ RegisterEcsCluster ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterEcsCluster.html)  | Registers a specified Amazon ECS cluster with a stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ RegisterElasticIp ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterElasticIp.html)  | Registers an Elastic IP address with a specified stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ RegisterInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterInstance.html)  | Registers instances with a specified stack that were created outside of AWS OpsWorks | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ RegisterRdsDbInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterRdsDbInstance.html)  | Registers an Amazon RDS instance with a stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ RegisterVolume ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterVolume.html)  | Registers an Amazon EBS volume with a specified stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ SetLoadBasedAutoScaling ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetLoadBasedAutoScaling.html)  | Specify the load\-based auto scaling configuration for a specified layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ SetPermission ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetPermission.html)  | Specifies a user's permissions | Permissions management |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ SetTimeBasedAutoScaling ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetTimeBasedAutoScaling.html)  | Specify the time\-based auto scaling configuration for a specified instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ StartInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartInstance.html)  | Starts a specified instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ StartStack ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartStack.html)  | Starts a stack's instances | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ StopInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopInstance.html)  | Stops a specified instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ StopStack ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopStack.html)  | Stops a specified stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_TagResource.html)  | Apply tags to a specified stack or layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UnassignInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignInstance.html)  | Unassigns a registered instance from all of it's layers | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UnassignVolume ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignVolume.html)  | Unassigns an assigned Amazon EBS volume | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UntagResource.html)  | Removes tags from a specified stack or layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UpdateApp ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateApp.html)  | Updates a specified app | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UpdateElasticIp ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateElasticIp.html)  | Updates a registered Elastic IP address's name | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UpdateInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateInstance.html)  | Updates a specified instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UpdateLayer ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateLayer.html)  | Updates a specified layer | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UpdateMyUserProfile ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateMyUserProfile.html)  | Updates a user's SSH public key | Write |  |  |  | 
|   [ UpdateRdsDbInstance ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateRdsDbInstance.html)  | Updates an Amazon RDS instance | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UpdateStack ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateStack.html)  | Updates a specified stack | Write |   [ stack ](#awsopsworks-stack)   |  |  | 
|   [ UpdateUserProfile ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateUserProfile.html)  | Updates a specified user profile | Permissions management |  |  |  | 
|   [ UpdateVolume ](https://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateVolume.html)  | Updates an Amazon EBS volume's name or mount point | Write |   [ stack ](#awsopsworks-stack)   |  |  | 

## Resource types defined by AWS OpsWorks<a name="awsopsworks-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsopsworks-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ stack ](https://docs.aws.amazon.com/opsworks/latest/userguide/workingstacks.html)  |  arn:$\{Partition\}:opsworks:$\{Region\}:$\{Account\}:stack/$\{StackId\}/  |  | 

## Condition keys for AWS OpsWorks<a name="awsopsworks-policy-keys"></a>

OpsWorks has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.