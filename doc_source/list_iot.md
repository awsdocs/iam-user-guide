# Actions and Condition Context Keys for AWS IoT<a name="list_iot"></a>

AWS IoT \(service prefix: iot\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS IoT**

For information about using IAM policies to grant permissions to run AWS IoT actions and access AWS IoT resources, see [Security and Identity for AWS IoT](http://docs.aws.amazon.com/iot/latest/developerguide/iot-security-identity.html) in the *AWS IoT User Guide*\.
+ `[iot:AcceptCertificateTransfer](http://docs.aws.amazon.com/iot/latest/apireference/API_AcceptCertificateTransfer.html)`
+ `[iot:AssociateTargetsWithJob](http://docs.aws.amazon.com/iot/latest/apireference/API_AssociateTargetsWithJob.html)`
+ `[iot:AttachPolicy](http://docs.aws.amazon.com/iot/latest/apireference/API_AttachPolicy.html)`
+ `[iot:AttachPrincipalPolicy](http://docs.aws.amazon.com/iot/latest/apireference/API_AttachPrincipalPolicy.html)`
+ `[iot:AttachThingPrincipal](http://docs.aws.amazon.com/iot/latest/apireference/API_AttachThingPrincipal.html)`
+ `[iot:CancelCertificateTransfer](http://docs.aws.amazon.com/iot/latest/apireference/API_CancelCertificateTransfer.html)`
+ `[iot:CancelJob](http://docs.aws.amazon.com/iot/latest/apireference/API_CancelJob.html)`
+ `[iot:ClearDefaultAuthorizer](http://docs.aws.amazon.com/iot/latest/apireference/API_ClearDefaultAuthorizer.html)`
+ `[iot:Connect](http://docs.aws.amazon.com/iot/latest/developerguide/authorization.html)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[iot:CreateAuthorizer](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateAuthorizer.html)`
+ `[iot:CreateCertificateFromCsr](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateCertificateFromCsr.html)`
+ `[iot:CreateJob](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateJob.html)`
+ `[iot:CreateKeysAndCertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateKeysAndCertificate.html)`
+ `[iot:CreateOTAUpdateJob](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateOTAUpdateJob.html)`
+ `[iot:CreatePolicy](http://docs.aws.amazon.com/iot/latest/apireference/API_CreatePolicy.html)`
+ `[iot:CreatePolicyVersion](http://docs.aws.amazon.com/iot/latest/apireference/API_CreatePolicyVersion.html)`
+ `[iot:CreateRoleAlias](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateRoleAlias.html)`
+ `[iot:CreateStream](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateStream.html)`
+ `[iot:CreateThing](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateThing.html)`
+ `[iot:CreateThingType](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateThingType.html)`
+ `[iot:CreateTopicRule](http://docs.aws.amazon.com/iot/latest/apireference/API_CreateTopicRule.html)`
+ `[iot:DeleteAuthorizer](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteAuthorizer.html)`
+ `[iot:DeleteCACertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteCACertificate.html)`
+ `[iot:DeleteCertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteCertificate.html)`
+ `[iot:DeleteOTAUpdateJob](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteOTAUpdateJob.html)`
+ `[iot:DeletePolicy](http://docs.aws.amazon.com/iot/latest/apireference/API_DeletePolicy.html)`
+ `[iot:DeletePolicyVersion](http://docs.aws.amazon.com/iot/latest/apireference/API_DeletePolicyVersion.html)`
+ `[iot:DeleteRegistrationCode](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteRegistrationCode.html)`
+ `[iot:DeleteRoleAlias](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteRoleAlias.html)`
+ `[iot:DeleteStream](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteStream.html)`
+ `[iot:DeleteThing](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteThing.html)`
+ `[iot:DeleteThingShadow](http://docs.aws.amazon.com/iot/latest/developerguide/authorization.html)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[iot:DeleteThingType](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteThingType.html)`
+ `[iot:DeleteTopicRule](http://docs.aws.amazon.com/iot/latest/apireference/API_DeleteTopicRule.html)`
+ `[iot:DeprecateThingType](http://docs.aws.amazon.com/iot/latest/apireference/API_DeprecateThingType.html)`
+ `[iot:DescribeAuthorizer](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeAuthorizer.html)`
+ `[iot:DescribeCACertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeCACertificate.html)`
+ `[iot:DescribeCertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeCertificate.html)`
+ `[iot:DescribeDefaultAuthorizer](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeDefaultAuthorizer.html)`
+ `[iot:DescribeEndpoint](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeEndpoint.html)`
+ `[iot:DescribeIndex](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeIndex.html)`
+ `[iot:DescribeJob](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeJob.html)`
+ `[iot:DescribeJobExecution](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeJobExecution.html)`
+ `[iot:DescribeRoleAlias](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeRoleAlias.html)`
+ `[iot:DescribeStream](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeStream.html)`
+ `[iot:DescribeThing](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeThing.html)`
+ `[iot:DescribeThingType](http://docs.aws.amazon.com/iot/latest/apireference/API_DescribeThingType.html)`
+ `[iot:DetachPolicy](http://docs.aws.amazon.com/iot/latest/apireference/API_DetachPolicy.html)`
+ `[iot:DetachPrincipalPolicy](http://docs.aws.amazon.com/iot/latest/apireference/API_DetachPrincipalPolicy.html)`
+ `[iot:DetachThingPrincipal](http://docs.aws.amazon.com/iot/latest/apireference/API_DetachThingPrincipal.html)`
+ `[iot:DisableTopicRule](http://docs.aws.amazon.com/iot/latest/apireference/API_DisableTopicRule.html)`
+ `[iot:EnableTopicRule](http://docs.aws.amazon.com/iot/latest/apireference/API_EnableTopicRule.html)`
+ `[iot:GetEffectivePolicies](http://docs.aws.amazon.com/iot/latest/apireference/API_GetEffectivePolicies.html)`
+ `[iot:GetIndexingConfiguration](http://docs.aws.amazon.com/iot/latest/apireference/API_GetIndexingConfiguration.html)`
+ `[iot:GetJobDocument](http://docs.aws.amazon.com/iot/latest/apireference/API_GetJobDocument.html)`
+ `[iot:GetLoggingOptions](http://docs.aws.amazon.com/iot/latest/apireference/API_GetLoggingOptions.html)`
+ `[iot:GetOTAUpdateJob](http://docs.aws.amazon.com/iot/latest/apireference/API_GetOTAUpdateJob.html)`
+ `[iot:GetPolicy](http://docs.aws.amazon.com/iot/latest/apireference/API_GetPolicy.html)`
+ `[iot:GetPolicyVersion](http://docs.aws.amazon.com/iot/latest/apireference/API_GetPolicyVersion.html)`
+ `[iot:GetRegistrationCode](http://docs.aws.amazon.com/iot/latest/apireference/API_GetRegistrationCode.html)`
+ `[iot:GetThingShadow](http://docs.aws.amazon.com/iot/latest/developerguide/authorization.html)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[iot:GetTopicRule](http://docs.aws.amazon.com/iot/latest/apireference/API_GetTopicRule.html)`
+ `[iot:ListAttachedPolicies](http://docs.aws.amazon.com/iot/latest/apireference/API_ListAttachedPolicies.html)`
+ `[iot:ListAuthorizers](http://docs.aws.amazon.com/iot/latest/apireference/API_ListAuthorizers.html)`
+ `[iot:ListCACertificates](http://docs.aws.amazon.com/iot/latest/apireference/API_ListCACertificates.html)`
+ `[iot:ListCertificates](http://docs.aws.amazon.com/iot/latest/apireference/API_ListCertificates.html)`
+ `[iot:ListCertificatesByCA](http://docs.aws.amazon.com/iot/latest/apireference/API_ListCertificatesByCA.html)`
+ `[iot:ListIndices](http://docs.aws.amazon.com/iot/latest/apireference/API_ListIndices.html)`
+ `[iot:ListJobExecutionsForJob](http://docs.aws.amazon.com/iot/latest/apireference/API_ListJobExecutionsForJob.html)`
+ `[iot:ListJobExecutionsForThing](http://docs.aws.amazon.com/iot/latest/apireference/API_ListJobExecutionsForThing.html)`
+ `[iot:ListJobs](http://docs.aws.amazon.com/iot/latest/apireference/API_ListJobs.html)`
+ `[iot:ListOTAUpdateJobs](http://docs.aws.amazon.com/iot/latest/apireference/API_ListOTAUpdateJobs.html)`
+ `[iot:ListOutgoingCertificates](http://docs.aws.amazon.com/iot/latest/apireference/API_ListOutgoingCertificates.html)`
+ `[iot:ListPolicies](http://docs.aws.amazon.com/iot/latest/apireference/API_ListPolicies.html)`
+ `[iot:ListPolicyPrincipals](http://docs.aws.amazon.com/iot/latest/apireference/API_ListPolicyPrincipals.html)`
+ `[iot:ListPolicyVersions](http://docs.aws.amazon.com/iot/latest/apireference/API_ListPolicyVersions.html)`
+ `[iot:ListPrincipalPolicies](http://docs.aws.amazon.com/iot/latest/apireference/API_ListPrincipalPolicies.html)`
+ `[iot:ListPrincipalThings](http://docs.aws.amazon.com/iot/latest/apireference/API_ListPrincipalThings.html)`
+ `[iot:ListRoleAliases](http://docs.aws.amazon.com/iot/latest/apireference/API_ListRoleAliases.html)`
+ `[iot:ListStreams](http://docs.aws.amazon.com/iot/latest/apireference/API_ListStreams.html)`
+ `[iot:ListTargetsForPolicy](http://docs.aws.amazon.com/iot/latest/apireference/API_ListTargetsForPolicy.html)`
+ `[iot:ListThingPrincipals](http://docs.aws.amazon.com/iot/latest/apireference/API_ListThingPrincipals.html)`
+ `[iot:ListThingTypes](http://docs.aws.amazon.com/iot/latest/apireference/API_ListThingTypes.html)`
+ `[iot:ListThings](http://docs.aws.amazon.com/iot/latest/apireference/API_ListThings.html)`
+ `[iot:ListTopicRules](http://docs.aws.amazon.com/iot/latest/apireference/API_ListTopicRules.html)`
+ `[iot:Publish](http://docs.aws.amazon.com/iot/latest/developerguide/authorization.html)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[iot:Receive](http://docs.aws.amazon.com/iot/latest/developerguide/authorization.html)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[iot:RegisterCACertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_RegisterCACertificate.html)`
+ `[iot:RegisterCertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_RegisterCertificate.html)`
+ `[iot:RejectCertificateTransfer](http://docs.aws.amazon.com/iot/latest/apireference/API_RejectCertificateTransfer.html)`
+ `[iot:ReplaceTopicRule](http://docs.aws.amazon.com/iot/latest/apireference/API_ReplaceTopicRule.html)`
+ `[iot:SearchIndex](http://docs.aws.amazon.com/iot/latest/apireference/API_SearchIndex.html)`
+ `[iot:SetDefaultAuthorizer](http://docs.aws.amazon.com/iot/latest/apireference/API_SetDefaultAuthorizer.html)`
+ `[iot:SetDefaultPolicyVersion](http://docs.aws.amazon.com/iot/latest/apireference/API_SetDefaultPolicyVersion.html)`
+ `[iot:SetLoggingOptions](http://docs.aws.amazon.com/iot/latest/apireference/API_SetLoggingOptions.html)`
+ `[iot:Subscribe](http://docs.aws.amazon.com/iot/latest/developerguide/authorization.html)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[iot:TestAuthorization](http://docs.aws.amazon.com/iot/latest/apireference/API_TestAuthorization.html)`
+ `[iot:TestInvokeAuthorizer](http://docs.aws.amazon.com/iot/latest/apireference/API_TestInvokeAuthorizer.html)`
+ `[iot:TransferCertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_TransferCertificate.html)`
+ `[iot:UpdateAuthorizer](http://docs.aws.amazon.com/iot/latest/apireference/API_UpdateAuthorizer.html)`
+ `[iot:UpdateCACertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_UpdateCACertificate.html)`
+ `[iot:UpdateCertificate](http://docs.aws.amazon.com/iot/latest/apireference/API_UpdateCertificate.html)`
+ `[iot:UpdateIndexingConfiguration](http://docs.aws.amazon.com/iot/latest/apireference/API_UpdateIndexingConfiguration.html)`
+ `[iot:UpdateRoleAlias](http://docs.aws.amazon.com/iot/latest/apireference/API_UpdateRoleAlias.html)`
+ `[iot:UpdateStream](http://docs.aws.amazon.com/iot/latest/apireference/API_UpdateStream.html)`
+ `[iot:UpdateThing](http://docs.aws.amazon.com/iot/latest/apireference/API_UpdateThing.html)`
+ `[iot:UpdateThingShadow](http://docs.aws.amazon.com/iot/latest/developerguide/authorization.html)` \- this is an IAM policy permission only, not an API action that can be called\.

**Condition context keys for AWS IoT**

AWS IoT has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.