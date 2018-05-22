# Creating SAML Identity Providers<a name="id_roles_providers_create_saml"></a>

A SAML 2\.0 identity provider is an entity in IAM that describes an identity provider \(IdP\) service that supports the [SAML 2\.0 \(Security Assertion Markup Language 2\.0\)](https://wiki.oasis-open.org/security) standard\. You use a SAML identity provider when you want to establish trust between a SAML\-compatible IdP such as Shibboleth or Active Directory Federation Services and AWS, so that users in your organization can access AWS resources\. SAML identity providers in IAM are used as principals in an IAM trust policy\. 

For more information about this scenario, see [About SAML 2\.0\-based Federation](id_roles_providers_saml.md)\.

You can create and manage a SAML identity provider in the AWS Management Console or with AWS CLI, Tools for Windows PowerShell, or AWS API calls\. 

After you create a SAML provider, you must create one or more IAM roles\. A role is an identity in AWS that doesn't have its own credentials \(as a user does\) but is, in this context, dynamically assigned to a federated user that is authenticated by your organization's identity provider \(IdP\)\. The role permits your organization's IdP to request temporary security credentials for access to AWS\. The policies assigned to the role determine what the federated users are allowed to do in AWS\. To create a role for SAML federation, see [Creating a Role for a Third\-Party Identity Provider \(Federation\)](id_roles_create_for-idp.md)\. 

Finally, after you create the role, you complete the SAML trust by configuring your IdP with information about AWS and the role\(s\) that you want your federated users to use\. This is referred to as configuring relying party trust between your IdP and AWS\. To configure relying party trust, see [Configuring your SAML 2\.0 IdP with Relying Party Trust and Adding Claims](id_roles_providers_create_saml_relying-party.md)\. 

**Topics**
+ [Creating and Managing a SAML Identity Provider \(AWS Management Console\)](#idp-manage-identityprovider-console)
+ [Managing a SAML Provider \(AWS CLI, Tools for Windows PowerShell and AWS API\)](#idp-create-identityprovider-CLIAPI)
+ [Configuring your SAML 2\.0 IdP with Relying Party Trust and Adding Claims](id_roles_providers_create_saml_relying-party.md)
+ [Integrating Third\-Party SAML Solution Providers with AWS](id_roles_providers_saml_3rd-party.md)
+ [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)

## Creating and Managing a SAML Identity Provider \(AWS Management Console\)<a name="idp-manage-identityprovider-console"></a>

You can use the AWS Management Console to create and delete SAML identity providers\.

**To create a SAML identity provider**

1. <a name="samlstep1"></a>Before you can create a SAML identity provider, you need the SAML metadata document that you get from the IdP that includes the issuer's name, expiration information, and keys that can be used to validate the SAML authentication response \(assertions\) that are received from the IdP\. To generate the metadata document, use the identity management software your organization uses as its IdP\. For instructions on how to configure many of the available IdPs to work with AWS, including how to generate the required SAML metadata document, see [Integrating Third\-Party SAML Solution Providers with AWS](id_roles_providers_saml_3rd-party.md)\.
**Important**  
The metadata file must be encoded in UTF\-8 format without a byte order mark \(BOM\)\. Also, the x\.509 certificate that is included as part of the SAML metadata document must use a key size of at least 1024 bits\. If the key size is smaller, the IdP creation fails with an "Unable to parse metadata" error\. To remove the BOM, you can encode the file as UTF\-8 using a text editing tool, such as Notepad\+\+\.

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Identity Providers** and then click **Create Provider**\. 

1. For **Provider Type**, click **Choose a provider type** and click **SAML**\. 

1. Type a name for the identity provider\.

1. For **Metadata Document**, click **Choose File**, specify the SAML metadata document that you downloaded in [Step 1](#samlstep1), and click **Open**\. Click **Next Step**\.

1. Verify the information you have provided, and click **Create**\. 

**To delete a SAML provider**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Identity Providers**\.

1. Select the check box next to the identity provider that you want to delete\.

1. Click **Delete Providers**\.

## Managing a SAML Provider \(AWS CLI, Tools for Windows PowerShell and AWS API\)<a name="idp-create-identityprovider-CLIAPI"></a>

Use the following commands to create and manage a SAML provider\.

**To create an identity provider and upload a metadata document**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/create-saml-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-saml-provider.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMSAMLProvider.html&tocid=New-IAMSAMLProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMSAMLProvider.html&tocid=New-IAMSAMLProvider)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateSAMLProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateSAMLProvider.html) 

**To upload a new metadata document for an IdP**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/update-saml-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/update-saml-provider.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMSAMLProvider.html&tocid=Update-IAMSAMLProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMSAMLProvider.html&tocid=Update-IAMSAMLProvider)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateSAMLProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateSAMLProvider.html)

**To get information about a specific provider, such as the ARN, creation date, and expiration**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/get-saml-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/get-saml-provider.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMSAMLProvider.html&tocid=Get-IAMSAMLProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMSAMLProvider.html&tocid=Get-IAMSAMLProvider)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetSAMLProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetSAMLProvider.html)

**To list information for all IdPs, such as the ARN, creation date, and expiration**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/list-saml-providers.html](http://docs.aws.amazon.com/cli/latest/reference/iam/list-saml-providers.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMSAMLProviders.html&tocid=Get-IAMSAMLProviders](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMSAMLProviders.html&tocid=Get-IAMSAMLProviders)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListSAMLProviders.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListSAMLProviders.html) 

**To delete an IdP**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/delete-saml-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-saml-provider.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMSAMLProvider.html&tocid=Remove-IAMSAMLProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMSAMLProvider.html&tocid=Remove-IAMSAMLProvider)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteSAMLProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteSAMLProvider.html)