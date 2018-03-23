# Actions and Condition Context Keys for AWS OpsWorks<a name="list_opsworks"></a>

AWS OpsWorks \(service prefix: opsworks\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS OpsWorks**

For information about using the following AWS OpsWorks API actions in an IAM policy, see the Action section in [Managing AWS OpsWorks Permissions by Attaching an IAM Policy](http://docs.aws.amazon.com/opsworks/latest/userguide/opsworks-security-users-policy.html) in the *AWS OpsWorks User Guide*\.
+ `[opsworks:AssignInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignInstance.html)`
+ `[opsworks:AssignVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssignVolume.html)`
+ `[opsworks:AssociateElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AssociateElasticIp.html)`
+ `[opsworks:AttachElasticLoadBalancer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_AttachElasticLoadBalancer.html)`
+ `[opsworks:CloneStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CloneStack.html)`
+ `[opsworks:CreateApp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateApp.html)`
+ `[opsworks:CreateDeployment](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateDeployment.html)`
+ `[opsworks:CreateInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateInstance.html)`
+ `[opsworks:CreateLayer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateLayer.html)`
+ `[opsworks:CreateStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateStack.html)`
+ `[opsworks:CreateUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_CreateUserProfile.html)`
+ `[opsworks:DeleteApp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteApp.html)`
+ `[opsworks:DeleteInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteInstance.html)`
+ `[opsworks:DeleteLayer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteLayer.html)`
+ `[opsworks:DeleteStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteStack.html)`
+ `[opsworks:DeleteUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeleteUserProfile.html)`
+ `[opsworks:DeregisterEcsCluster](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterEcsCluster.html)`
+ `[opsworks:DeregisterElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterElasticIp.html)`
+ `[opsworks:DeregisterInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterInstance.html)`
+ `[opsworks:DeregisterRdsDbInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterRdsDbInstance.html)`
+ `[opsworks:DeregisterVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DeregisterVolume.html)`
+ `[opsworks:DescribeAgentVersions](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeAgentVersions.html)`
+ `[opsworks:DescribeApps](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeApps.html)`
+ `[opsworks:DescribeCommands](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeCommands.html)`
+ `[opsworks:DescribeDeployments](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeDeployments.html)`
+ `[opsworks:DescribeEcsClusters](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeEcsClusters.html)`
+ `[opsworks:DescribeElasticIps](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticIps.html)`
+ `[opsworks:DescribeElasticLoadBalancers](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeElasticLoadBalancers.html)`
+ `[opsworks:DescribeInstances](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeInstances.html)`
+ `[opsworks:DescribeLayers](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLayers.html)`
+ `[opsworks:DescribeLoadBasedAutoScaling](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeLoadBasedAutoScaling.html)`
+ `[opsworks:DescribeMyUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeMyUserProfile.html)`
+ `[opsworks:DescribePermissions](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribePermissions.html)`
+ `[opsworks:DescribeRaidArrays](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRaidArrays.html)`
+ `[opsworks:DescribeRdsDbInstances](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeRdsDbInstances.html)`
+ `[opsworks:DescribeServiceErrors](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeServiceErrors.html)`
+ `[opsworks:DescribeStackProvisioningParameters](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackProvisioningParameters.html)`
+ `[opsworks:DescribeStackSummary](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStackSummary.html)`
+ `[opsworks:DescribeStacks](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeStacks.html)`
+ `[opsworks:DescribeTimeBasedAutoScaling](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeTimeBasedAutoScaling.html)`
+ `[opsworks:DescribeUserProfiles](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeUserProfiles.html)`
+ `[opsworks:DescribeVolumes](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DescribeVolumes.html)`
+ `[opsworks:DetachElasticLoadBalancer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DetachElasticLoadBalancer.html)`
+ `[opsworks:DisassociateElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_DisassociateElasticIp.html)`
+ `[opsworks:GetHostnameSuggestion](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_GetHostnameSuggestion.html)`
+ `[opsworks:GrantAccess](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_GrantAccess.html)`
+ `[opsworks:ListTags](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_ListTags.html)`
+ `[opsworks:RebootInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RebootInstance.html)`
+ `[opsworks:RegisterEcsCluster](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterEcsCluster.html)`
+ `[opsworks:RegisterElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterElasticIp.html)`
+ `[opsworks:RegisterInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterInstance.html)`
+ `[opsworks:RegisterRdsDbInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterRdsDbInstance.html)`
+ `[opsworks:RegisterVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_RegisterVolume.html)`
+ `[opsworks:SetLoadBasedAutoScaling](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetLoadBasedAutoScaling.html)`
+ `[opsworks:SetPermission](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetPermission.html)`
+ `[opsworks:SetTimeBasedAutoScaling](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_SetTimeBasedAutoScaling.html)`
+ `[opsworks:StartInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartInstance.html)`
+ `[opsworks:StartStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StartStack.html)`
+ `[opsworks:StopInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopInstance.html)`
+ `[opsworks:StopStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_StopStack.html)`
+ `[opsworks:TagResource](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_TagResource.html)`
+ `[opsworks:UnassignInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignInstance.html)`
+ `[opsworks:UnassignVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UnassignVolume.html)`
+ `[opsworks:UntagResource](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UntagResource.html)`
+ `[opsworks:UpdateApp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateApp.html)`
+ `[opsworks:UpdateElasticIp](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateElasticIp.html)`
+ `[opsworks:UpdateInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateInstance.html)`
+ `[opsworks:UpdateLayer](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateLayer.html)`
+ `[opsworks:UpdateMyUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateMyUserProfile.html)`
+ `[opsworks:UpdateRdsDbInstance](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateRdsDbInstance.html)`
+ `[opsworks:UpdateStack](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateStack.html)`
+ `[opsworks:UpdateUserProfile](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateUserProfile.html)`
+ `[opsworks:UpdateVolume](http://docs.aws.amazon.com/opsworks/latest/APIReference/API_UpdateVolume.html)`

**Condition context keys for AWS OpsWorks**

AWS OpsWorks has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.