# Actions and Condition Context Keys for Amazon Storage Gateway<a name="list_storagegateway"></a>

Amazon Storage Gateway \(service prefix: storagegateway\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon Storage Gateway**

For information about using the following AWS Storage Gateway API actions in an IAM policy, see [Access Control Using AWS Identity and Access Management \(IAM\)](http://docs.aws.amazon.com/storagegateway/latest/userguide/UsingIAMWithStorageGateway.html) in the *AWS Storage Gateway User Guide*\.

**Note**  
For the latest information about permissions in this service, see [AWS Storage Gateway API Permissions: Actions, Resources, and Conditions Reference](http://docs.aws.amazon.com/storagegateway/latest/userguide/sg-api-permissions-ref.html)
+ `[storagegateway:ActivateGateway](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ActivateGateway.html)`
+ `[storagegateway:AddCache](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_AddCache.html)`
+ `[storagegateway:AddTagsToResource](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_AddTagsToResource.html)`
+ `[storagegateway:AddUploadBuffer](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_AddUploadBuffer.html)`
+ `[storagegateway:AddWorkingStorage](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_AddWorkingStorage.html)`
+ `[storagegateway:CancelArchival](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CancelArchival.html)`
+ `[storagegateway:CancelRetrieval](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CancelRetrieval.html)`
+ `[storagegateway:CreateCachediSCSIVolume](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CreateCachediSCSIVolume.html)`
+ `[storagegateway:CreateNFSFileShare](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CreateNFSFileShare.html)`
+ `[storagegateway:CreateSnapshot](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CreateSnapshot.html)`
+ `[storagegateway:CreateSnapshotFromVolumeRecoveryPoint](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CreateSnapshotFromVolumeRecoveryPoint.html)`
+ `[storagegateway:CreateStorediSCSIVolume](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CreateStorediSCSIVolume.html)`
+ `[storagegateway:CreateTapeWithBarcode](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CreateTapeWithBarcode.html)`
+ `[storagegateway:CreateTapes](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_CreateTapes.html)`
+ `[storagegateway:DeleteBandwidthRateLimit](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DeleteBandwidthRateLimit.html)`
+ `[storagegateway:DeleteChapCredentials](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DeleteChapCredentials.html)`
+ `[storagegateway:DeleteFileShare](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DeleteFileShare.html)`
+ `[storagegateway:DeleteGateway](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DeleteGateway.html)`
+ `[storagegateway:DeleteSnapshotSchedule](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DeleteSnapshotSchedule.html)`
+ `[storagegateway:DeleteTape](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DeleteTape.html)`
+ `[storagegateway:DeleteTapeArchive](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DeleteTapeArchive.html)`
+ `[storagegateway:DeleteVolume](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DeleteVolume.html)`
+ `[storagegateway:DescribeBandwidthRateLimit](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeBandwidthRateLimit.html)`
+ `[storagegateway:DescribeCache](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeCache.html)`
+ `[storagegateway:DescribeCachediSCSIVolumes](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeCachediSCSIVolumes.html)`
+ `[storagegateway:DescribeChapCredentials](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeChapCredentials.html)`
+ `[storagegateway:DescribeGatewayInformation](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeGatewayInformation.html)`
+ `[storagegateway:DescribeMaintenanceStartTime](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeMaintenanceStartTime.html)`
+ `[storagegateway:DescribeNFSFileShares](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeNFSFileShares.html)`
+ `[storagegateway:DescribeSnapshotSchedule](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeSnapshotSchedule.html)`
+ `[storagegateway:DescribeStorediSCSIVolumes](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeStorediSCSIVolumes.html)`
+ `[storagegateway:DescribeTapeArchives](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeTapeArchives.html)`
+ `[storagegateway:DescribeTapeRecoveryPoints](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeTapeRecoveryPoints.html)`
+ `[storagegateway:DescribeTapes](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeTapes.html)`
+ `[storagegateway:DescribeUploadBuffer](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeUploadBuffer.html)`
+ `[storagegateway:DescribeVTLDevices](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeVTLDevices.html)`
+ `[storagegateway:DescribeWorkingStorage](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DescribeWorkingStorage.html)`
+ `[storagegateway:DisableGateway](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_DisableGateway.html)`
+ `[storagegateway:ListFileShares](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ListFileShares.html)`
+ `[storagegateway:ListGateways](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ListGateways.html)`
+ `[storagegateway:ListLocalDisks](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ListLocalDisks.html)`
+ `[storagegateway:ListTagsForResource](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ListTagsForResource.html)`
+ `[storagegateway:ListTapes](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ListTapes.html)`
+ `[storagegateway:ListVolumeInitiators](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ListVolumeInitiators.html)`
+ `[storagegateway:ListVolumeRecoveryPoints](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ListVolumeRecoveryPoints.html)`
+ `[storagegateway:ListVolumes](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ListVolumes.html)`
+ `[storagegateway:RefreshCache](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_RefreshCache.html)`
+ `[storagegateway:RemoveTagsFromResource](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_RemoveTagsFromResource.html)`
+ `[storagegateway:ResetCache](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ResetCache.html)`
+ `[storagegateway:RetrieveTapeArchive](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_RetrieveTapeArchive.html)`
+ `[storagegateway:RetrieveTapeRecoveryPoint](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_RetrieveTapeRecoveryPoint.html)`
+ `[storagegateway:SetLocalConsolePassword](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_SetLocalConsolePassword.html)`
+ `[storagegateway:ShutdownGateway](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_ShutdownGateway.html)`
+ `[storagegateway:StartGateway](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_StartGateway.html)`
+ `[storagegateway:UpdateBandwidthRateLimit](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_UpdateBandwidthRateLimit.html)`
+ `[storagegateway:UpdateChapCredentials](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_UpdateChapCredentials.html)`
+ `[storagegateway:UpdateGatewayInformation](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_UpdateGatewayInformation.html)`
+ `[storagegateway:UpdateGatewaySoftwareNow](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_UpdateGatewaySoftwareNow.html)`
+ `[storagegateway:UpdateMaintenanceStartTime](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_UpdateMaintenanceStartTime.html)`
+ `[storagegateway:UpdateNFSFileShare](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_UpdateNFSFileShare.html)`
+ `[storagegateway:UpdateSnapshotSchedule](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_UpdateSnapshotSchedule.html)`
+ `[storagegateway:UpdateVTLDeviceType](http://docs.aws.amazon.com/storagegateway/latest/APIReference/API_UpdateVTLDeviceType.html)`

**Condition context keys for Amazon Storage Gateway**

Amazon Storage Gateway has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.