# Creating OpenID Connect \(OIDC\) Identity Providers<a name="id_roles_providers_create_oidc"></a>

*OIDC identity providers* are entities in IAM that describe an identity provider \(IdP\) service that supports the [OpenID Connect](http://openid.net/connect/) \(OIDC\) standard\. You use an OIDC identity provider when you want to establish trust between an OIDC\-compatible IdP—such as Google, Salesforce, and many others—and your AWS account\. This is useful if you are creating a mobile app or web application that requires access to AWS resources, but you don't want to create custom sign\-in code or manage your own user identities\. For more information about this scenario, see [About Web Identity Federation](id_roles_providers_oidc.md)\.

You can create and manage an OIDC identity provider using the AWS Management Console, the AWS Command Line Interface, the Tools for Windows PowerShell, or the IAM API\. 

**Topics**
+ [Creating and Managing an OIDC Provider \(AWS Management Console\)](#manage-oidc-provider-console)
+ [Creating and Managing an OIDC Identity Provider \(AWS CLI, Tools for Windows PowerShell, and IAM API\)](#manage-oidc-provider-cli)
+ [Obtaining the Thumbprint for an OpenID Connect Identity Provider](id_roles_providers_create_oidc_verify-thumbprint.md)

## Creating and Managing an OIDC Provider \(AWS Management Console\)<a name="manage-oidc-provider-console"></a>

Follow these instructions to create and manage an OIDC provider in the AWS Management Console\.

**To create an OIDC identity provider**

1. <a name="idpoidcstep1"></a>Before you create an OIDC identity provider in IAM, you must register your application with the IdP to receive a *client ID*\. The client ID \(also known as *audience*\) is a unique identifier for your app that is issued to you when you register your app with the IdP\. For more information about obtaining a client ID, see the documentation for your IdP\. 

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Identity Providers**, and then click **Create Provider**\.

1. For **Provider Type**, click **Choose a provider type**, and then choose **OpenID Connect**\. 

1. For **Provider URL**, type the URL of the IdP\. The URL must comply with these restrictions:
   + The URL is case\-sensitive\.
   + The URL must begin with **https://**
   + The URL cannot include a colon \(:\) character, and therefore cannot specify a port number\. This means that the server must be listening on the default port 443\.
   + Within your AWS account, each OIDC identity provider must use a unique URL\.

1. For **Audience**, type the client ID of the application that you registered with the IdP and received in [Step 1](#idpoidcstep1), and that will make requests to AWS\. If you have additional client IDs \(also known as *audiences*\) for this IdP, you can add them later on the provider detail page\. Click **Next Step**\. 

1. Use the **Thumbprint** to verify the server certificate of your IdP\. To learn how, see [Obtaining the Thumbprint for an OpenID Connect Identity Provider](id_roles_providers_create_oidc_verify-thumbprint.md)\. Click **Create**\.

1. In the confirmation message at the top of the screen, click **Do this now** to go to the **Roles** tab to create a role for this identity provider\. For more information about creating a role for an OIDC identity provider, see [Creating a Role for a Third\-Party Identity Provider \(Federation\)](id_roles_create_for-idp.md)\. OIDC identity providers must have a role in order to access your AWS account\. To skip this step and create the role later, click **Close**\. 

**To add or remove a thumbprint or client ID \(also known as audience\) for an OIDC identity provider**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Identity Providers**, then click the name of the identity provider that you want to update\.

1. To add a thumbprint or audience, click **Add a Thumbprint** or **Add an Audience**\. To remove a thumbprint or audience, click **Remove** next to the item that you want to remove\. 
**Note**  
An OIDC identity provider must have at least 1 and can have a maximum of 5 thumbprints\. An OIDC identity provider must have at least 1 and can have a maximum of 100 audiences\.

    When you are done, click **Save Changes**\.

**To delete an OIDC identity provider**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Identity Providers**\. 

1. Select the check box next to the identity provider that you want to delete\.

1. Click **Delete Providers**\.

## Creating and Managing an OIDC Identity Provider \(AWS CLI, Tools for Windows PowerShell, and IAM API\)<a name="manage-oidc-provider-cli"></a>

Use the following commands to create and manage an OIDC provider\.

To create a new OIDC provider
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/create-open-id-connect-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-open-id-connect-provider.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMOpenIDConnectProvider.html&tocid=New-IAMOpenIDConnectProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMOpenIDConnectProvider.html&tocid=New-IAMOpenIDConnectProvider)
+ IAM API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateOpenIDConnectProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateOpenIDConnectProvider.html)

To add a new client ID to an existing OIDC provider
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/add-client-id-to-open-id-connect-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/add-client-id-to-open-id-connect-provider.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Add-IAMClientIDToOpenIDConnectProvider.html&tocid=Add-IAMClientIDToOpenIDConnectProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Add-IAMClientIDToOpenIDConnectProvider.html&tocid=Add-IAMClientIDToOpenIDConnectProvider)
+ IAM API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_AddClientIDToOpenIDConnectProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AddClientIDToOpenIDConnectProvider.html)

To remove a client ID from an existing OIDC provider
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/remove-client-id-from-open-id-connect-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/remove-client-id-from-open-id-connect-provider.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMClientIDFromOpenIDConnectProvider.html&tocid=Remove-IAMClientIDFromOpenIDConnectProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMClientIDFromOpenIDConnectProvider.html&tocid=Remove-IAMClientIDFromOpenIDConnectProvider)
+ IAM API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveClientIDFromOpenIDConnectProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveClientIDFromOpenIDConnectProvider.html)

To update the list of server certificate thumbprints for an existing OIDC provider 
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/update-open-id-connect-provider-thumbprint.html](http://docs.aws.amazon.com/cli/latest/reference/iam/update-open-id-connect-provider-thumbprint.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMOpenIDConnectProviderThumbprint.html&tocid=Update-IAMOpenIDConnectProviderThumbprint](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMOpenIDConnectProviderThumbprint.html&tocid=Update-IAMOpenIDConnectProviderThumbprint)
+ IAM API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateOpenIDConnectProviderThumbprint.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateOpenIDConnectProviderThumbprint.html)

To get a list of all the OIDC providers in your AWS account
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-providers.html](http://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-providers.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMOpenIDConnectProviders.html&tocid=Get-IAMOpenIDConnectProviders](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMOpenIDConnectProviders.html&tocid=Get-IAMOpenIDConnectProviders)
+ IAM API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviders.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviders.html)

To get detailed information about an OIDC provider
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/get-open-id-connect-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/get-open-id-connect-provider.html) 
+ Tools for Windows PowerShell[http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMOpenIDConnectProvider.html&tocid=Get-IAMOpenIDConnectProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMOpenIDConnectProvider.html&tocid=Get-IAMOpenIDConnectProvider): 
+ IAM API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetOpenIDConnectProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetOpenIDConnectProvider.html)

To delete an OIDC provider
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/delete-open-id-connect-provider.html](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-open-id-connect-provider.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMOpenIDConnectProvider.html&tocid=Remove-IAMOpenIDConnectProvider](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMOpenIDConnectProvider.html&tocid=Remove-IAMOpenIDConnectProvider)
+ IAM API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteOpenIDConnectProvider.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteOpenIDConnectProvider.html)