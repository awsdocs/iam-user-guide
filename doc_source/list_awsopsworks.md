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
| [AssignInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignInstance.html) | Assign a registered instance to a layer |   |  |  |  | 
| [AssignVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignVolume.html) | Assigns one of the stack's registered Amazon EBS volumes to a specified instance |   |  |  |  | 
| [AssociateElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssociateElasticIp.html) | Associates one of the stack's registered Elastic IP addresses with a specified instance |   |  |  |  | 
| [AttachElasticLoadBalancer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AttachElasticLoadBalancer.html) | Attaches an Elastic Load Balancing load balancer to a specified layer |   |  |  |  | 
| [CloneStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CloneStack.html) | Creates a clone of a specified stack |   |  |  |  | 
| [CreateApp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateApp.html) | Creates an app for a specified stack |   |  |  |  | 
| [CreateDeployment](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateDeployment.html) | Runs deployment or stack commands |   |  |  |  | 
| [CreateInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateInstance.html) | Creates an instance in a specified stack |   |  |  |  | 
| [CreateLayer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateLayer.html) | Creates a layer |   |  |  |  | 
| [CreateStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateStack.html) | Creates a new stack |   |  |  |  | 
| [CreateUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateUserProfile.html) | Creates a new user profile |   |  |  |  | 
| [DeleteApp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteApp.html) | Deletes a specified app |   |  |  |  | 
| [DeleteInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteInstance.html) | Deletes a specified instance, which terminates the associated Amazon EC2 instance |   |  |  |  | 
| [DeleteLayer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteLayer.html) | Deletes a specified layer |   |  |  |  | 
| [DeleteStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteStack.html) | Deletes a specified stack |   |  |  |  | 
| [DeleteUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteUserProfile.html) | Deletes a user profile |   |  |  |  | 
| [DeregisterEcsCluster](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterEcsCluster.html) | Deletes a user profile |   |  |  |  | 
| [DeregisterElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterElasticIp.html) | Deregisters a specified Elastic IP address |   |  |  |  | 
| [DeregisterInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterInstance.html) | Deregister a registered Amazon EC2 or on\-premises instance |   |  |  |  | 
| [DeregisterRdsDbInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterRdsDbInstance.html) | Deregisters an Amazon RDS instance |   |  |  |  | 
| [DeregisterVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterVolume.html) | Deregisters an Amazon EBS volume |   |  |  |  | 
| [DescribeAgentVersions](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeAgentVersions.html) | Describes the available AWS OpsWorks agent versions |   |  |  |  | 
| [DescribeApps](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeApps.html) | Requests a description of a specified set of apps |   |  |  |  | 
| [DescribeCommands](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeCommands.html) | Describes the results of specified commands |   |  |  |  | 
| [DescribeDeployments](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeDeployments.html) | Requests a description of a specified set of deployments |   |  |  |  | 
| [DescribeEcsClusters](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeEcsClusters.html) | Describes Amazon ECS clusters that are registered with a stack |   |  |  |  | 
| [DescribeElasticIps](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticIps.html) | Describes Elastic IP addresses |   |  |  |  | 
| [DescribeElasticLoadBalancers](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticLoadBalancers.html) | Describes a stack's Elastic Load Balancing instances |   |  |  |  | 
| [DescribeInstances](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeInstances.html) | Requests a description of a set of instances |   |  |  |  | 
| [DescribeLayers](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLayers.html) | Requests a description of one or more layers in a specified stack |   |  |  |  | 
| [DescribeLoadBasedAutoScaling](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLoadBasedAutoScaling.html) | Describes load\-based auto scaling configurations for specified layers |   |  |  |  | 
| [DescribeMyUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeMyUserProfile.html) | Describes a user's SSH information |   |  |  |  | 
| [DescribePermissions](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribePermissions.html) | Describes the permissions for a specified stack |   |  |  |  | 
| [DescribeRaidArrays](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRaidArrays.html) | Describe an instance's RAID arrays |   |  |  |  | 
| [DescribeRdsDbInstances](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRdsDbInstances.html) | Describes Amazon RDS instances |   |  |  |  | 
| [DescribeServiceErrors](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeServiceErrors.html) | Describes AWS OpsWorks service errors |   |  |  |  | 
| [DescribeStackProvisioningParameters](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackProvisioningParameters.html) | Requests a description of a stack's provisioning parameters |   |  |  |  | 
| [DescribeStackSummary](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackSummary.html) | Describes the number of layers and apps in a specified stack, and the number of instances in each state, such as running\_setup or online |   |  |  |  | 
| [DescribeStacks](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStacks.html) | Requests a description of one or more stacks |   |  |  |  | 
| [DescribeTimeBasedAutoScaling](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeTimeBasedAutoScaling.html) | Describes time\-based auto scaling configurations for specified instances |   |  |  |  | 
| [DescribeUserProfiles](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeUserProfiles.html) | Describe specified users |   |  |  |  | 
| [DescribeVolumes](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeVolumes.html) | Describes an instance's Amazon EBS volumes |   |  |  |  | 
| [DetachElasticLoadBalancer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DetachElasticLoadBalancer.html) | Detaches a specified Elastic Load Balancing instance from its layer |   |  |  |  | 
| [DisassociateElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DisassociateElasticIp.html) | Disassociates an Elastic IP address from its instance |   |  |  |  | 
| [GetHostnameSuggestion](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_GetHostnameSuggestion.html) | Gets a generated host name for the specified layer, based on the current host name theme |   |  |  |  | 
| [GrantAccess](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html) | Grants RDP access to a Windows instance for a specified time period |   |  |  |  | 
| [ListTags](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_ListTags.html) | Returns a list of tags that are applied to the specified stack or layer |   |  |  |  | 
| [RebootInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html) | Reboots a specified instance |   |  |  |  | 
| [RegisterEcsCluster](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterEcsCluster.html) | Registers a specified Amazon ECS cluster with a stack |   |  |  |  | 
| [RegisterElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterElasticIp.html) | Registers an Elastic IP address with a specified stack |   |  |  |  | 
| [RegisterInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterInstance.html) | Registers instances with a specified stack that were created outside of AWS OpsWorks |   |  |  |  | 
| [RegisterRdsDbInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterRdsDbInstance.html) | Registers an Amazon RDS instance with a stack |   |  |  |  | 
| [RegisterVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterVolume.html) | Registers an Amazon EBS volume with a specified stack |   |  |  |  | 
| [SetLoadBasedAutoScaling](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetLoadBasedAutoScaling.html) | Specify the load\-based auto scaling configuration for a specified layer |   |  |  |  | 
| [SetPermission](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetPermission.html) | Specifies a user's permissions |   |  |  |  | 
| [SetTimeBasedAutoScaling](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetTimeBasedAutoScaling.html) | Specify the time\-based auto scaling configuration for a specified instance |   |  |  |  | 
| [StartInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartInstance.html) | Starts a specified instance |   |  |  |  | 
| [StartStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartStack.html) | Starts a stack's instances |   |  |  |  | 
| [StopInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopInstance.html) | Stops a specified instance |   |  |  |  | 
| [StopStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopStack.html) | Stops a specified stack |   |  |  |  | 
| [TagResource](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_TagResource.html) | Apply tags to a specified stack or layer |   |  |  |  | 
| [UnassignInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignInstance.html) | Unassigns a registered instance from all of it's layers |   |  |  |  | 
| [UnassignVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignVolume.html) | Unassigns an assigned Amazon EBS volume |   |  |  |  | 
| [UntagResource](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UntagResource.html) | Removes tags from a specified stack or layer |   |  |  |  | 
| [UpdateApp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateApp.html) | Updates a specified app |   |  |  |  | 
| [UpdateElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateElasticIp.html) | Updates a registered Elastic IP address's name |   |  |  |  | 
| [UpdateInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateInstance.html) | Updates a specified instance |   |  |  |  | 
| [UpdateLayer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateLayer.html) | Updates a specified layer |   |  |  |  | 
| [UpdateMyUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateMyUserProfile.html) | Updates a user's SSH public key |   |  |  |  | 
| [UpdateRdsDbInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateRdsDbInstance.html) | Updates an Amazon RDS instance |   |  |  |  | 
| [UpdateStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateStack.html) | Updates a specified stack |   |  |  |  | 
| [UpdateUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateUserProfile.html) | Updates a specified user profile |   |  |  |  | 
| [UpdateVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateVolume.html) | Updates an Amazon EBS volume's name or mount point |   |  |  |  | 

## Resources Defined by OpsWorks<a name="awsopsworks-resources-for-iam-policies"></a>

OpsWorks has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS OpsWorks<a name="awsopsworks-policy-keys"></a>

OpsWorks has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.