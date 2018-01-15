# Actions and Condition Context Keys for AWS Key Management Service<a name="list_kms"></a>

AWS Key Management Service \(service prefix: kms\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS Key Management Service**

For information about using the following AWS KMS API actions in an IAM resource policy attached to a AWS KMS key, see [Key Policies](http://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html) in the *AWS Key Management Service Developer Guide*\.

+ `[kms:ListGrants](http://docs.aws.amazon.com/kms/latest/APIReference/API_ListGrants.html)`

+ `[kms:GenerateDataKey](http://docs.aws.amazon.com/kms/latest/APIReference/API_GenerateDataKey.html)`

+ `[kms:Decrypt](http://docs.aws.amazon.com/kms/latest/APIReference/API_Decrypt.html)`

+ `[kms:GenerateRandom](http://docs.aws.amazon.com/kms/latest/APIReference/API_GenerateRandom.html)`

+ `[kms:TagResource](http://docs.aws.amazon.com/kms/latest/APIReference/API_TagResource.html)`

+ `[kms:CreateAlias](http://docs.aws.amazon.com/kms/latest/APIReference/API_CreateAlias.html)`

+ `[kms:ListKeyPolicies](http://docs.aws.amazon.com/kms/latest/APIReference/API_ListKeyPolicies.html)`

+ `[kms:ListResourceTags](http://docs.aws.amazon.com/kms/latest/APIReference/API_ListResourceTags.html)`

+ `[kms:CreateGrant](http://docs.aws.amazon.com/kms/latest/APIReference/API_CreateGrant.html)`

+ `[kms:RevokeGrant](http://docs.aws.amazon.com/kms/latest/APIReference/API_RevokeGrant.html)`

+ `[kms:GetKeyPolicy](http://docs.aws.amazon.com/kms/latest/APIReference/API_GetKeyPolicy.html)`

+ `[kms:ListKeys](http://docs.aws.amazon.com/kms/latest/APIReference/API_ListKeys.html)`

+ `[kms:ListRetirableGrants](http://docs.aws.amazon.com/kms/latest/APIReference/API_ListRetirableGrants.html)`

+ `[kms:PutKeyPolicy](http://docs.aws.amazon.com/kms/latest/APIReference/API_PutKeyPolicy.html)`

+ `[kms:ListAliases](http://docs.aws.amazon.com/kms/latest/APIReference/API_ListAliases.html)`

+ `[kms:CancelKeyDeletion](http://docs.aws.amazon.com/kms/latest/APIReference/API_CancelKeyDeletion.html)`

+ `[kms:DisableKey](http://docs.aws.amazon.com/kms/latest/APIReference/API_DisableKey.html)`

+ `[kms:DeleteAlias](http://docs.aws.amazon.com/kms/latest/APIReference/API_DeleteAlias.html)`

+ `[kms:DescribeKey](http://docs.aws.amazon.com/kms/latest/APIReference/API_DescribeKey.html)`

+ `[kms:ImportKeyMaterial](http://docs.aws.amazon.com/kms/latest/APIReference/API_ImportKeyMaterial.html)`

+ `[kms:UpdateKeyDescription](http://docs.aws.amazon.com/kms/latest/APIReference/API_UpdateKeyDescription.html)`

+ `[kms:Encrypt](http://docs.aws.amazon.com/kms/latest/APIReference/API_Encrypt.html)`

+ `[kms:GetKeyRotationStatus](http://docs.aws.amazon.com/kms/latest/APIReference/API_GetKeyRotationStatus.html)`

+ `kms:ReEncryptFrom` \- this is an IAM policy permission only, not an API action that can be called\.

+ `[kms:DeleteImportedKeyMaterial](http://docs.aws.amazon.com/kms/latest/APIReference/API_DeleteImportedKeyMaterial.html)`

+ `kms:ReEncryptTo` \- this is an IAM policy permission only, not an API action that can be called\.

+ `[kms:DisableKeyRotation](http://docs.aws.amazon.com/kms/latest/APIReference/API_DisableKeyRotation.html)`

+ `[kms:UpdateAlias](http://docs.aws.amazon.com/kms/latest/APIReference/API_UpdateAlias.html)`

+ `[kms:UntagResource](http://docs.aws.amazon.com/kms/latest/APIReference/API_UntagResource.html)`

+ `[kms:RetireGrant](http://docs.aws.amazon.com/kms/latest/APIReference/API_RetireGrant.html)`

+ `[kms:EnableKey](http://docs.aws.amazon.com/kms/latest/APIReference/API_EnableKey.html)`

+ `[kms:GenerateDataKeyWithoutPlaintext](http://docs.aws.amazon.com/kms/latest/APIReference/API_GenerateDataKeyWithoutPlaintext.html)`

+ `[kms:EnableKeyRotation](http://docs.aws.amazon.com/kms/latest/APIReference/API_EnableKeyRotation.html)`

+ `[kms:ScheduleKeyDeletion](http://docs.aws.amazon.com/kms/latest/APIReference/API_ScheduleKeyDeletion.html)`

+ `[kms:GetParametersForImport](http://docs.aws.amazon.com/kms/latest/APIReference/API_GetParametersForImport.html)`

+ `[kms:CreateKey](http://docs.aws.amazon.com/kms/latest/APIReference/API_CreateKey.html)`

**Condition context keys for AWS Key Management Service**

For more information about using AWS KMS condition keys, see [Using Policy Conditions with AWS KMS](http://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html)\.

AWS Key Management Service has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.