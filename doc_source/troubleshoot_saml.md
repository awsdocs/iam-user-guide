# Troubleshooting SAML 2\.0 federation with AWS<a name="troubleshoot_saml"></a>

Use the information here to help you diagnose and fix issues that you might encounter when working with SAML 2\.0 and federation with IAM\.

**Topics**
+ [Error: Your request included an invalid SAML response\. to logout, click here\.](#troubleshoot_saml_invalid-response)
+ [Error: RoleSessionName is required in AuthnResponse \(service: AWSSecurityTokenService; status code: 400; error code: InvalidIdentityToken\)](#troubleshoot_saml_missing-rolesessionname)
+ [Error: Not authorized to perform sts:AssumeRoleWithSAML \(service: AWSSecurityTokenService; status code: 403; error code: AccessDenied\)](#troubleshoot_saml_missing-role)
+ [Error: RoleSessionName in AuthnResponse must match \[a\-zA\-Z\_0\-9\+=,\.@\-\]\{2,64\} \(service: AWSSecurityTokenService; status code: 400; error code: InvalidIdentityToken\)](#troubleshoot_saml_invalid-rolesessionname)
+ [Error: Response signature invalid \(service: AWSSecurityTokenService; status code: 400; error code: InvalidIdentityToken\)](#troubleshoot_saml_invalid-metadata)
+ [Error: Failed to assume role: Issuer not present in specified provider \(service: AWSOpenIdDiscoveryService; status code: 400; error code: AuthSamlInvalidSamlResponseException\)](#troubleshoot_saml_issuer-mismatch)
+ [Error: Could not parse metadata\.](#troubleshoot_saml_issuer-metadata)
+ [Error: Specified provider doesn't exist\.](#troubleshoot_saml_provider-doesnotexist)
+ [Error: Requested DurationSeconds exceeds MaxSessionDuration set for this role\.](#troubleshoot_saml_duration-exceeds)
+ [How to view a SAML response in your browser for troubleshooting](troubleshoot_saml_view-saml-response.md)

## Error: Your request included an invalid SAML response\. to logout, click here\.<a name="troubleshoot_saml_invalid-response"></a>

This error can occur when the SAML response from the identity provider does not include an attribute with the `Name` set to `https://aws.amazon.com/SAML/Attributes/Role`\. The attribute must contain one or more `AttributeValue` elements, each containing a comma\-separated pair of strings:
+ The ARN of a role that the user can be mapped to
+ The ARN of the SAML provider

For more information, see [Configuring SAML assertions for the authentication response](id_roles_providers_create_saml_assertions.md)\. To view the SAML response in your browser, follow the steps listed in [How to view a SAML response in your browser for troubleshooting](troubleshoot_saml_view-saml-response.md)\.

## Error: RoleSessionName is required in AuthnResponse \(service: AWSSecurityTokenService; status code: 400; error code: InvalidIdentityToken\)<a name="troubleshoot_saml_missing-rolesessionname"></a>

This error can occur when the SAML response from the identity provider does not include an attribute with the `Name` set to `https://aws.amazon.com/SAML/Attributes/RoleSessionName`\. The attribute value is an identifier for the user and is typically a user ID or an email address\.

For more information, see [Configuring SAML assertions for the authentication response](id_roles_providers_create_saml_assertions.md)\. To view the SAML response in your browser, follow the steps listed in [How to view a SAML response in your browser for troubleshooting](troubleshoot_saml_view-saml-response.md)\.

## Error: Not authorized to perform sts:AssumeRoleWithSAML \(service: AWSSecurityTokenService; status code: 403; error code: AccessDenied\)<a name="troubleshoot_saml_missing-role"></a>

This error can occur if the IAM role specified in the SAML response is misspelled or does not exist\. Make sure to use the exact name of your role, because role names are case sensitive\. Correct the name of the role in the SAML service provider configuration\.

You are allowed access only if your role trust policy includes the `sts:AssumeRoleWithSAML` action\. If your SAML assertion is configured to use the [`PrincipalTag` attribute](id_roles_providers_create_saml_assertions.md#saml_role-session-tags), your trust policy must also include the `sts:TagSession` action\. For more information about session tags, see [Passing session tags in AWS STS](id_session-tags.md)\.

This error can also occur if the federated users do not have permissions to assume the role\. The role must have a trust policy that specifies the ARN of the IAM SAML identity provider as the `Principal`\. The role also contains conditions that control which users can assume the role\. Ensure that your users meet the requirements of the conditions\.

This error can also occur if the SAML response does not include a `Subject` containing a `NameID`\.

For more information, see [Establish Permissions in AWS for Federated Users](https://docs.aws.amazon.com/STS/latest/UsingSTS/STSMgmtConsole-SAML.html#configuring-role) and [Configuring SAML assertions for the authentication response](id_roles_providers_create_saml_assertions.md)\. To view the SAML response in your browser, follow the steps listed in [How to view a SAML response in your browser for troubleshooting](troubleshoot_saml_view-saml-response.md)\.

## Error: RoleSessionName in AuthnResponse must match \[a\-zA\-Z\_0\-9\+=,\.@\-\]\{2,64\} \(service: AWSSecurityTokenService; status code: 400; error code: InvalidIdentityToken\)<a name="troubleshoot_saml_invalid-rolesessionname"></a>

This error can occur if the `RoleSessionName` attribute value is too long or contains invalid characters\. The maximum valid length is 64 characters\.

For more information, see [Configuring SAML assertions for the authentication response](id_roles_providers_create_saml_assertions.md)\. To view the SAML response in your browser, follow the steps listed in [How to view a SAML response in your browser for troubleshooting](troubleshoot_saml_view-saml-response.md)\.

## Error: Response signature invalid \(service: AWSSecurityTokenService; status code: 400; error code: InvalidIdentityToken\)<a name="troubleshoot_saml_invalid-metadata"></a>

This error can occur when federation metadata of the identity provider does not match the metadata of the IAM identity provider\. For example, the metadata file for the identity service provider might have changed to update an expired certificate\. Download the updated SAML metadata file from your identity service provider\. Then update it in the AWS identity provider entity that you define in IAM with the `aws iam update-saml-provider` cross\-platform CLI command or the `Update-IAMSAMLProvider` PowerShell cmdlet\.

## Error: Failed to assume role: Issuer not present in specified provider \(service: AWSOpenIdDiscoveryService; status code: 400; error code: AuthSamlInvalidSamlResponseException\)<a name="troubleshoot_saml_issuer-mismatch"></a>

This error can occur if the issuer in the SAML response does not match the issuer declared in the federation metadata file\. The metadata file was uploaded to AWS when you created the identity provider in IAM\.

## Error: Could not parse metadata\.<a name="troubleshoot_saml_issuer-metadata"></a>

This error can occur if your metadata file is not formatted properly\. 

When you [create or manage a SAML identity provider](id_roles_providers_create_saml.md#idp-manage-identityprovider-console) in the AWS Management Console, you must retrieve the SAML metadata document from your identity provider\. This metadata file includes the issuer's name, expiration information, and keys that can be used to validate the SAML authentication response \(assertions\) that are received from the IdP\. The metadata file must be encoded in UTF\-8 format without a byte order mark \(BOM\)\. Also, the x\.509 certificate that is included as part of the SAML metadata document must use a key size of at least 1024 bits\. If the key size is smaller, the IdP creation fails with an "Unable to parse metadata" error\. To remove the BOM, you can encode the file as UTF\-8 using a text editing tool, such as Notepad\+\+\.

## Error: Specified provider doesn't exist\.<a name="troubleshoot_saml_provider-doesnotexist"></a>

This error can occur if the name of the provider that you specify in the SAML assertion does not match the name of the provider configured in IAM\. For more information about viewing the provider name, see [Creating IAM SAML identity providers](id_roles_providers_create_saml.md)\.

## Error: Requested DurationSeconds exceeds MaxSessionDuration set for this role\.<a name="troubleshoot_saml_duration-exceeds"></a>

This error can occur if you assume a role from the AWS CLI or API\. 

When you use the [assume\-role\-with\-saml](https://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-saml.html) CLI or [AssumeRoleWithSAML](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html) API operations to assume a role, you can specify a value for the `DurationSeconds` parameter\. You can specify a value from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. If you specify a value higher than this setting, the operation fails\. For example, if you specify a session duration of 12 hours, but your administrator set the maximum session duration to 6 hours, your operation fails\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\. 