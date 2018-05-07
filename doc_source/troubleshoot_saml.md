# Troubleshooting SAML 2\.0 Federation with AWS<a name="troubleshoot_saml"></a>

Use the information here to help you diagnose and fix issues that you might encounter when working with SAML 2\.0 and federation with IAM\.

**Topics**
+ [Error: Your request included an invalid SAML response\. To logout, click here\.](#troubleshoot_saml_invalid-response)
+ [Error: RoleSessionName is required in AuthnResponse \(Service: AWSSecurityTokenService; Status Code: 400; Error Code: InvalidIdentityToken\)](#troubleshoot_saml_missing-rolesessionname)
+ [Error: Not authorized to perform sts:AssumeRoleWithSAML \(Service: AWSSecurityTokenService; Status Code: 403; Error Code: AccessDenied\)](#troubleshoot_saml_missing-role)
+ [Error: RoleSessionName in AuthnResponse must match \[a\-zA\-Z\_0\-9\+=,\.@\-\]\{2,64\} \(Service: AWSSecurityTokenService; Status Code: 400; Error Code: InvalidIdentityToken\)](#troubleshoot_saml_invalid-rolesessionname)
+ [Error: Response signature invalid \(Service: AWSSecurityTokenService; Status Code: 400; Error Code: InvalidIdentityToken\)](#troubleshoot_saml_invalid-metadata)
+ [Error: Failed to assume role: Issuer not present in specified provider \(Service: AWSOpenIdDiscoveryService; Status Code: 400; Error Code: AuthSamlInvalidSamlResponseException\)](#troubleshoot_saml_issuer-mismatch)
+ [Error: Could not parse metadata\.](#troubleshoot_saml_issuer-metadata)
+ [Error: Requested DurationSeconds Exceeds MaxSessionDuration Set for this Role\.](#troubleshoot_saml_duration-exceeds)
+ [How to View a SAML Response in Your Browser for Troubleshooting](troubleshoot_saml_view-saml-response.md)

## Error: Your request included an invalid SAML response\. To logout, click here\.<a name="troubleshoot_saml_invalid-response"></a>

This error can occur when the SAML response from the identity provider does not include an attribute with the `Name` set to `https://aws.amazon.com/SAML/Attributes/Role`\. The attribute must contain one or more `AttributeValue` elements, each containing a comma\-separated pair of strings:
+ The ARN of a role that the user can be mapped to
+ The ARN of the SAML provider

For more information, see [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\. To view the SAML response in your browser, follow the steps listed in [How to View a SAML Response in Your Browser for Troubleshooting](troubleshoot_saml_view-saml-response.md)\.

## Error: RoleSessionName is required in AuthnResponse \(Service: AWSSecurityTokenService; Status Code: 400; Error Code: InvalidIdentityToken\)<a name="troubleshoot_saml_missing-rolesessionname"></a>

This error can occur when the SAML response from the identity provider does not include an attribute with the `Name` set to `https://aws.amazon.com/SAML/Attributes/RoleSessionName`\. The attribute value is an identifier for the user and is typically a user ID or an email address\.

For more information, see [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\. To view the SAML response in your browser, follow the steps listed in [How to View a SAML Response in Your Browser for Troubleshooting](troubleshoot_saml_view-saml-response.md)\.

## Error: Not authorized to perform sts:AssumeRoleWithSAML \(Service: AWSSecurityTokenService; Status Code: 403; Error Code: AccessDenied\)<a name="troubleshoot_saml_missing-role"></a>

This error can occur if the IAM role specified in the SAML response is misspelled or does not exist\. Correct the name of the role in the SAML service provider configuration\.

This error can also occur if the federated users do not have permissions to assume the role\. The role must have a trust policy that specifies the ARN of the IAM SAML identity provider as the `Principal`\. The role also contains conditions that control which users can assume the role\. Ensure that your users meet the requirements of the conditions\.

This error can also occur if the SAML response does not include a `Subject` containing a `NameID`\.

For more information see [Establish Permissions in AWS for Federated Users](http://docs.aws.amazon.com/STS/latest/UsingSTS/STSMgmtConsole-SAML.html#configuring-role) and [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\. To view the SAML response in your browser, follow the steps listed in [How to View a SAML Response in Your Browser for Troubleshooting](troubleshoot_saml_view-saml-response.md)\.

## Error: RoleSessionName in AuthnResponse must match \[a\-zA\-Z\_0\-9\+=,\.@\-\]\{2,64\} \(Service: AWSSecurityTokenService; Status Code: 400; Error Code: InvalidIdentityToken\)<a name="troubleshoot_saml_invalid-rolesessionname"></a>

This error can occur if the `RoleSessionName` attribute value is too long or contains invalid characters\. The maximum valid length is 64 characters\.

For more information, see [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\. To view the SAML response in your browser, follow the steps listed in [How to View a SAML Response in Your Browser for Troubleshooting](troubleshoot_saml_view-saml-response.md)\.

## Error: Response signature invalid \(Service: AWSSecurityTokenService; Status Code: 400; Error Code: InvalidIdentityToken\)<a name="troubleshoot_saml_invalid-metadata"></a>

This error can occur when federation metadata of the identity provider does not match the metadata of the IAM identity provider\. For example, the metadata file for the identity service provider might have changed to update an expired certificate\. Download the updated SAML metadata file from your identity service provider\. Then update it in the AWS identity provider entity that you define in IAM with the `aws iam update-saml-provider` cross\-platform CLI command or the `Update-IAMSAMLProvider` PowerShell cmdlet\.

## Error: Failed to assume role: Issuer not present in specified provider \(Service: AWSOpenIdDiscoveryService; Status Code: 400; Error Code: AuthSamlInvalidSamlResponseException\)<a name="troubleshoot_saml_issuer-mismatch"></a>

This error can occur if the issuer in the SAML response does not match the issuer declared in the federation metadata file uploaded to AWS when you created the identity provider in IAM\.

## Error: Could not parse metadata\.<a name="troubleshoot_saml_issuer-metadata"></a>

This error can occur if your metadata file is not formatted properly\. 

When you [create or manage a SAML identity provider](id_roles_providers_create_saml.md#idp-manage-identityprovider-console) in the AWS Management Console, you must retrieve the SAML metadata document from your identity provider\. This metadata file includes the issuer's name, expiration information, and keys that can be used to validate the SAML authentication response \(assertions\) that are received from the IdP\. The metadata file must be encoded in UTF\-8 format without a byte order mark \(BOM\)\. Also, the x\.509 certificate that is included as part of the SAML metadata document must use a key size of at least 1024 bits\. If the key size is smaller, the IdP creation fails with an "Unable to parse metadata" error\. To remove the BOM, you can encode the file as UTF\-8 using a text editing tool, such as Notepad\+\+\.

## Error: Requested DurationSeconds Exceeds MaxSessionDuration Set for this Role\.<a name="troubleshoot_saml_duration-exceeds"></a>

This error can occur if you assume a role from the AWS CLI or API\. 

When you use the [assume\-role\-with\-saml](http://docs.aws.amazon.com/cli/latest/reference/sts/assume-role-with-saml.html) CLI or [AssumeRoleWithSAML](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html) API operations to assume a role, you can specify a value for the `DurationSeconds` parameter\. You can specify a value from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. If you specify a value higher than this setting, the operation fails\. For example, if you specify a session duration of 12 hours, but your administrator set the maximum session duration to 6 hours, your operation fails\. To learn how to view the maximum value for your role, see [View the Maximum Session Duration Setting for a Role](id_roles_use.md#id_roles_use_view-role-max-session)\. 