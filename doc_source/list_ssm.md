# Actions and Condition Context Keys for Amazon Simple Systems Manager<a name="list_ssm"></a>

Amazon Simple Systems Manager \(service prefix: ssm\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon Simple Systems Manager**

For information about using the following Amazon EC2 Systems Manager API actions in an IAM policy, see [Managing Windows Instance Configuration](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-configuration-manage.html) in the *Amazon EC2 User Guide for Windows Instances*\.
+ `[ssm:AddTagsToResource](http://docs.aws.amazon.com/ssm/latest/APIReference/API_AddTagsToResource.html)`
+ `[ssm:CancelCommand](http://docs.aws.amazon.com/ssm/latest/APIReference/API_CancelCommand.html)`
+ `[ssm:CreateActivation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_CreateActivation.html)`
+ `[ssm:CreateAssociation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_CreateAssociation.html)`
+ `[ssm:CreateAssociationBatch](http://docs.aws.amazon.com/ssm/latest/APIReference/API_CreateAssociationBatch.html)`
+ `[ssm:CreateDocument](http://docs.aws.amazon.com/ssm/latest/APIReference/API_CreateDocument.html)`
+ `[ssm:CreateMaintenanceWindow](http://docs.aws.amazon.com/ssm/latest/APIReference/API_CreateMaintenanceWindow.html)`
+ `[ssm:CreatePatchBaseline](http://docs.aws.amazon.com/ssm/latest/APIReference/API_CreatePatchBaseline.html)`
+ `[ssm:CreateResourceDataSync](http://docs.aws.amazon.com/ssm/latest/APIReference/API_CreateResourceDataSync.html)`
+ `[ssm:DeleteActivation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeleteActivation.html)`
+ `[ssm:DeleteAssociation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeleteAssociation.html)`
+ `[ssm:DeleteDocument](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeleteDocument.html)`
+ `[ssm:DeleteMaintenanceWindow](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeleteMaintenanceWindow.html)`
+ `[ssm:DeleteParameter](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeleteParameter.html)`
+ `[ssm:DeleteParameters](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeleteParameters.html)`
+ `[ssm:DeletePatchBaseline](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeletePatchBaseline.html)`
+ `[ssm:DeleteResourceDataSync](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeleteResourceDataSync.html)`
+ `[ssm:DeregisterManagedInstance](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeregisterManagedInstance.html)`
+ `[ssm:DeregisterPatchBaselineForPatchGroup](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeregisterPatchBaselineForPatchGroup.html)`
+ `[ssm:DeregisterTargetFromMaintenanceWindow](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeregisterTargetFromMaintenanceWindow.html)`
+ `[ssm:DeregisterTaskFromMaintenanceWindow](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DeregisterTaskFromMaintenanceWindow.html)`
+ `[ssm:DescribeActivations](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeActivations.html)`
+ `[ssm:DescribeAssociation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeAssociation.html)`
+ `[ssm:DescribeAutomationExecutions](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeAutomationExecutions.html)`
+ `[ssm:DescribeAutomationStepExecutions](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeAutomationStepExecutions.html)`
+ `[ssm:DescribeAvailablePatches](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeAvailablePatches.html)`
+ `[ssm:DescribeDocument](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeDocument.html)`
+ `[ssm:DescribeDocumentParameters](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeDocumentParameters.html)`
+ `[ssm:DescribeDocumentPermission](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeDocumentPermission.html)`
+ `[ssm:DescribeEffectiveInstanceAssociations](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeEffectiveInstanceAssociations.html)`
+ `[ssm:DescribeEffectivePatchesForPatchBaseline](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeEffectivePatchesForPatchBaseline.html)`
+ `[ssm:DescribeInstanceAssociationsStatus](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeInstanceAssociationsStatus.html)`
+ `[ssm:DescribeInstanceInformation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeInstanceInformation.html)`
+ `[ssm:DescribeInstancePatchStates](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeInstancePatchStates.html)`
+ `[ssm:DescribeInstancePatchStatesForPatchGroup](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeInstancePatchStatesForPatchGroup.html)`
+ `[ssm:DescribeInstancePatches](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeInstancePatches.html)`
+ `[ssm:DescribeInstanceProperties](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeInstanceProperties.html)`
+ `[ssm:DescribeMaintenanceWindowExecutionTaskInvocations](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeMaintenanceWindowExecutionTaskInvocations.html)`
+ `[ssm:DescribeMaintenanceWindowExecutionTasks](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeMaintenanceWindowExecutionTasks.html)`
+ `[ssm:DescribeMaintenanceWindowExecutions](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeMaintenanceWindowExecutions.html)`
+ `[ssm:DescribeMaintenanceWindowTargets](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeMaintenanceWindowTargets.html)`
+ `[ssm:DescribeMaintenanceWindowTasks](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeMaintenanceWindowTasks.html)`
+ `[ssm:DescribeMaintenanceWindows](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeMaintenanceWindows.html)`
+ `[ssm:DescribeParameters](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribeParameters.html)`
+ `[ssm:DescribePatchBaselines](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribePatchBaselines.html)`
+ `[ssm:DescribePatchGroupState](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribePatchGroupState.html)`
+ `[ssm:DescribePatchGroups](http://docs.aws.amazon.com/ssm/latest/APIReference/API_DescribePatchGroups.html)`
+ `[ssm:GetAutomationExecution](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetAutomationExecution.html)`
+ `[ssm:GetCommandInvocation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetCommandInvocation.html)`
+ `[ssm:GetDefaultPatchBaseline](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetDefaultPatchBaseline.html)`
+ `[ssm:GetDeployablePatchSnapshotForInstance](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetDeployablePatchSnapshotForInstance.html)`
+ `[ssm:GetDocument](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetDocument.html)`
+ `[ssm:GetInventory](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetInventory.html)`
+ `[ssm:GetInventorySchema](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetInventorySchema.html)`
+ `[ssm:GetMaintenanceWindow](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetMaintenanceWindow.html)`
+ `[ssm:GetMaintenanceWindowExecution](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetMaintenanceWindowExecution.html)`
+ `[ssm:GetMaintenanceWindowExecutionTask](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetMaintenanceWindowExecutionTask.html)`
+ `[ssm:GetMaintenanceWindowExecutionTaskInvocation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetMaintenanceWindowExecutionTaskInvocation.html)`
+ `[ssm:GetMaintenanceWindowTask](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetMaintenanceWindowTask.html)`
+ `[ssm:GetManifest](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetManifest.html)`
+ `[ssm:GetParameter](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetParameter.html)`
+ `[ssm:GetParameterHistory](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetParameterHistory.html)`
+ `[ssm:GetParameters](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetParameters.html)`
+ `[ssm:GetParametersByPath](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetParametersByPath.html)`
+ `[ssm:GetPatchBaseline](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetPatchBaseline.html)`
+ `[ssm:GetPatchBaselineForPatchGroup](http://docs.aws.amazon.com/ssm/latest/APIReference/API_GetPatchBaselineForPatchGroup.html)`
+ `[ssm:ListAssociationVersions](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListAssociationVersions.html)`
+ `[ssm:ListAssociations](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListAssociations.html)`
+ `[ssm:ListCommandInvocations](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListCommandInvocations.html)`
+ `[ssm:ListCommands](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListCommands.html)`
+ `[ssm:ListDocumentVersions](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListDocumentVersions.html)`
+ `[ssm:ListDocuments](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListDocuments.html)`
+ `ssm:ListInstanceAssociations` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[ssm:ListInventoryEntries](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListInventoryEntries.html)`
+ `[ssm:ListResourceDataSync](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListResourceDataSync.html)`
+ `[ssm:ListTagsForResource](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ListTagsForResource.html)`
+ `[ssm:ModifyDocumentPermission](http://docs.aws.amazon.com/ssm/latest/APIReference/API_ModifyDocumentPermission.html)`
+ `[ssm:PutComplianceItems](http://docs.aws.amazon.com/ssm/latest/APIReference/API_PutComplianceItems.html)`
+ `[ssm:PutConfigurePackageResult](http://docs.aws.amazon.com/ssm/latest/APIReference/API_PutConfigurePackageResult.html)`
+ `[ssm:PutInventory](http://docs.aws.amazon.com/ssm/latest/APIReference/API_PutInventory.html)`
+ `[ssm:PutParameter](http://docs.aws.amazon.com/ssm/latest/APIReference/API_PutParameter.html)`
+ `[ssm:RegisterDefaultPatchBaseline](http://docs.aws.amazon.com/ssm/latest/APIReference/API_RegisterDefaultPatchBaseline.html)`
+ `[ssm:RegisterPatchBaselineForPatchGroup](http://docs.aws.amazon.com/ssm/latest/APIReference/API_RegisterPatchBaselineForPatchGroup.html)`
+ `[ssm:RegisterTargetWithMaintenanceWindow](http://docs.aws.amazon.com/ssm/latest/APIReference/API_RegisterTargetWithMaintenanceWindow.html)`
+ `[ssm:RegisterTaskWithMaintenanceWindow](http://docs.aws.amazon.com/ssm/latest/APIReference/API_RegisterTaskWithMaintenanceWindow.html)`
+ `[ssm:RemoveTagsFromResource](http://docs.aws.amazon.com/ssm/latest/APIReference/API_RemoveTagsFromResource.html)`
+ `[ssm:SendAutomationSignal](http://docs.aws.amazon.com/ssm/latest/APIReference/API_SendAutomationSignal.html)`
+ `[ssm:SendCommand](http://docs.aws.amazon.com/ssm/latest/APIReference/API_SendCommand.html)`
+ `ssm:StartAssociationsOnce` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[ssm:StartAutomationExecution](http://docs.aws.amazon.com/ssm/latest/APIReference/API_StartAutomationExecution.html)`
+ `[ssm:StopAutomationExecution](http://docs.aws.amazon.com/ssm/latest/APIReference/API_StopAutomationExecution.html)`
+ `[ssm:UpdateAssociation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateAssociation.html)`
+ `[ssm:UpdateAssociationStatus](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateAssociationStatus.html)`
+ `[ssm:UpdateDocument](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateDocument.html)`
+ `[ssm:UpdateDocumentDefaultVersion](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateDocumentDefaultVersion.html)`
+ `ssm:UpdateInstanceAssociationStatus` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[ssm:UpdateInstanceInformation](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateInstanceInformation.html)`
+ `[ssm:UpdateMaintenanceWindow](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateMaintenanceWindow.html)`
+ `[ssm:UpdateMaintenanceWindowTarget](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateMaintenanceWindowTarget.html)`
+ `[ssm:UpdateMaintenanceWindowTask](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateMaintenanceWindowTask.html)`
+ `[ssm:UpdateManagedInstanceRole](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdateManagedInstanceRole.html)`
+ `[ssm:UpdatePatchBaseline](http://docs.aws.amazon.com/ssm/latest/APIReference/API_UpdatePatchBaseline.html)`

**Condition context keys for Amazon Simple Systems Manager**

Amazon Simple Systems Manager has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.