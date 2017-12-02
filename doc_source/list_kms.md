# Actions and Condition Context Keys for AWS Key Management Service<a name="list_kms"></a>

AWS Key Management Service \(service prefix: kms\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS Key Management Service**

For information about using the following AWS KMS API actions in an IAM resource policy attached to a AWS KMS key, see [Key Policies](http://alpha-docs-aws.amazon.com/kms/latest/developerguide/key-policies.html) in the *AWS Key Management Service Developer Guide*\.

+ `[kms:ListGrants](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_ListGrants.html)`

+ `[kms:GenerateDataKey](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_GenerateDataKey.html)`

+ `[kms:GenerateRandom](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_GenerateRandom.html)`

+ `[kms:Decrypt](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_Decrypt.html)`

+ `[kms:TagResource](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_TagResource.html)`

+ `[kms:CreateAlias](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_CreateAlias.html)`

+ `[kms:ListKeyPolicies](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_ListKeyPolicies.html)`

+ `[kms:ListResourceTags](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_ListResourceTags.html)`

+ `[kms:CreateGrant](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_CreateGrant.html)`

+ `[kms:RevokeGrant](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_RevokeGrant.html)`

+ `[kms:GetKeyPolicy](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_GetKeyPolicy.html)`

+ `[kms:ListRetirableGrants](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_ListRetirableGrants.html)`

+ `[kms:ListKeys](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_ListKeys.html)`

+ `[kms:PutKeyPolicy](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_PutKeyPolicy.html)`

+ `[kms:ListAliases](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_ListAliases.html)`

+ `[kms:CancelKeyDeletion](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_CancelKeyDeletion.html)`

+ `[kms:DeleteAlias](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_DeleteAlias.html)`

+ `[kms:DisableKey](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_DisableKey.html)`

+ `[kms:DescribeKey](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_DescribeKey.html)`

+ `[kms:ImportKeyMaterial](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_ImportKeyMaterial.html)`

+ `[kms:UpdateKeyDescription](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_UpdateKeyDescription.html)`

+ `[kms:Encrypt](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_Encrypt.html)`

+ `[kms:GetKeyRotationStatus](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_GetKeyRotationStatus.html)`

+ `kms:ReEncryptFrom` \- this is an IAM policy permission only, not an API action that can be called\.

+ `[kms:DeleteImportedKeyMaterial](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_DeleteImportedKeyMaterial.html)`

+ `kms:ReEncryptTo` \- this is an IAM policy permission only, not an API action that can be called\.

+ `[kms:DisableKeyRotation](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_DisableKeyRotation.html)`

+ `[kms:UpdateAlias](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_UpdateAlias.html)`

+ `[kms:UntagResource](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_UntagResource.html)`

+ `[kms:RetireGrant](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_RetireGrant.html)`

+ `[kms:EnableKey](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_EnableKey.html)`

+ `[kms:GenerateDataKeyWithoutPlaintext](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_GenerateDataKeyWithoutPlaintext.html)`

+ `[kms:EnableKeyRotation](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_EnableKeyRotation.html)`

+ `[kms:ScheduleKeyDeletion](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_ScheduleKeyDeletion.html)`

+ `[kms:GetParametersForImport](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_GetParametersForImport.html)`

+ `[kms:CreateKey](http://alpha-docs-aws.amazon.com/kms/latest/APIReference/API_CreateKey.html)`

**Condition context keys for AWS Key Management Service**

For more information about using AWS KMS condition keys, see [Using Policy Conditions with AWS KMS](http://alpha-docs-aws.amazon.com/kms/latest/developerguide/policy-conditions.html)\.

AWS Key Management Service has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.