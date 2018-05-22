# Actions, Resources, and Condition Keys for AWS OpsWorks<a name="list_awsopsworks"></a>

AWS OpsWorks \(service prefix: `opsworks`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/opsworks/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/opsworks/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/opsworks/latest/userguide/workingsecurity.html) permission policies\.

**Topics**
+ [Actions Defined by AWS OpsWorks](#awsopsworks-actions-as-permissions)
+ [Resources Defined by OpsWorks](#awsopsworks-resources-for-iam-policies)
+ [Condition Keys for AWS OpsWorks](#awsopsworks-policy-keys)

## Actions Defined by AWS OpsWorks<a name="awsopsworks-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignInstance.html) | Assign a registered instance to a layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignVolume.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignVolume.html) | Assigns one of the stack's registered Amazon EBS volumes to a specified instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssociateElasticIp.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssociateElasticIp.html) | Associates one of the stack's registered Elastic IP addresses with a specified instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AttachElasticLoadBalancer.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AttachElasticLoadBalancer.html) | Attaches an Elastic Load Balancing load balancer to a specified layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CloneStack.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CloneStack.html) | Creates a clone of a specified stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateApp.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateApp.html) | Creates an app for a specified stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateDeployment.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateDeployment.html) | Runs deployment or stack commands | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateInstance.html) | Creates an instance in a specified stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateLayer.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateLayer.html) | Creates a layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateStack.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateStack.html) | Creates a new stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateUserProfile.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateUserProfile.html) | Creates a new user profile | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteApp.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteApp.html) | Deletes a specified app | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteInstance.html) | Deletes a specified instance, which terminates the associated Amazon EC2 instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteLayer.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteLayer.html) | Deletes a specified layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteStack.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteStack.html) | Deletes a specified stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteUserProfile.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteUserProfile.html) | Deletes a user profile | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterEcsCluster.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterEcsCluster.html) | Deletes a user profile | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterElasticIp.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterElasticIp.html) | Deregisters a specified Elastic IP address | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterInstance.html) | Deregister a registered Amazon EC2 or on\-premises instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterRdsDbInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterRdsDbInstance.html) | Deregisters an Amazon RDS instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterVolume.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterVolume.html) | Deregisters an Amazon EBS volume | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeAgentVersions.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeAgentVersions.html) | Describes the available AWS OpsWorks agent versions | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeApps.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeApps.html) | Requests a description of a specified set of apps | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeCommands.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeCommands.html) | Describes the results of specified commands | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeDeployments.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeDeployments.html) | Requests a description of a specified set of deployments | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeEcsClusters.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeEcsClusters.html) | Describes Amazon ECS clusters that are registered with a stack | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticIps.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticIps.html) | Describes Elastic IP addresses | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticLoadBalancers.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticLoadBalancers.html) | Describes a stack's Elastic Load Balancing instances | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeInstances.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeInstances.html) | Requests a description of a set of instances | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLayers.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLayers.html) | Requests a description of one or more layers in a specified stack | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLoadBasedAutoScaling.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLoadBasedAutoScaling.html) | Describes load\-based auto scaling configurations for specified layers | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeMyUserProfile.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeMyUserProfile.html) | Describes a user's SSH information | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribePermissions.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribePermissions.html) | Describes the permissions for a specified stack | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRaidArrays.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRaidArrays.html) | Describe an instance's RAID arrays | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRdsDbInstances.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRdsDbInstances.html) | Describes Amazon RDS instances | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeServiceErrors.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeServiceErrors.html) | Describes AWS OpsWorks service errors | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackProvisioningParameters.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackProvisioningParameters.html) | Requests a description of a stack's provisioning parameters | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackSummary.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackSummary.html) | Describes the number of layers and apps in a specified stack, and the number of instances in each state, such as running\_setup or online | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStacks.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStacks.html) | Requests a description of one or more stacks | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeTimeBasedAutoScaling.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeTimeBasedAutoScaling.html) | Describes time\-based auto scaling configurations for specified instances | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeUserProfiles.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeUserProfiles.html) | Describe specified users | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeVolumes.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeVolumes.html) | Describes an instance's Amazon EBS volumes | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DetachElasticLoadBalancer.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DetachElasticLoadBalancer.html) | Detaches a specified Elastic Load Balancing instance from its layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DisassociateElasticIp.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DisassociateElasticIp.html) | Disassociates an Elastic IP address from its instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_GetHostnameSuggestion.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_GetHostnameSuggestion.html) | Gets a generated host name for the specified layer, based on the current host name theme | Read |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html) | Grants RDP access to a Windows instance for a specified time period | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_ListTags.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_ListTags.html) | Returns a list of tags that are applied to the specified stack or layer | List |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html) | Reboots a specified instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterEcsCluster.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterEcsCluster.html) | Registers a specified Amazon ECS cluster with a stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterElasticIp.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterElasticIp.html) | Registers an Elastic IP address with a specified stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterInstance.html) | Registers instances with a specified stack that were created outside of AWS OpsWorks | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterRdsDbInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterRdsDbInstance.html) | Registers an Amazon RDS instance with a stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterVolume.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterVolume.html) | Registers an Amazon EBS volume with a specified stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetLoadBasedAutoScaling.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetLoadBasedAutoScaling.html) | Specify the load\-based auto scaling configuration for a specified layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetPermission.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetPermission.html) | Specifies a user's permissions | Permissions management |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetTimeBasedAutoScaling.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetTimeBasedAutoScaling.html) | Specify the time\-based auto scaling configuration for a specified instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartInstance.html) | Starts a specified instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartStack.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartStack.html) | Starts a stack's instances | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopInstance.html) | Stops a specified instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopStack.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopStack.html) | Stops a specified stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_TagResource.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_TagResource.html) | Apply tags to a specified stack or layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignInstance.html) | Unassigns a registered instance from all of it's layers | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignVolume.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignVolume.html) | Unassigns an assigned Amazon EBS volume | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UntagResource.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UntagResource.html) | Removes tags from a specified stack or layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateApp.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateApp.html) | Updates a specified app | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateElasticIp.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateElasticIp.html) | Updates a registered Elastic IP address's name | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateInstance.html) | Updates a specified instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateLayer.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateLayer.html) | Updates a specified layer | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateMyUserProfile.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateMyUserProfile.html) | Updates a user's SSH public key | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateRdsDbInstance.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateRdsDbInstance.html) | Updates an Amazon RDS instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateStack.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateStack.html) | Updates a specified stack | Write |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateUserProfile.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateUserProfile.html) | Updates a specified user profile | Permissions management |  |  |  | 
| [http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateVolume.html](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateVolume.html) | Updates an Amazon EBS volume's name or mount point | Write |  |  |  | 

## Resources Defined by OpsWorks<a name="awsopsworks-resources-for-iam-policies"></a>

OpsWorks has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS OpsWorks<a name="awsopsworks-policy-keys"></a>

OpsWorks has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.