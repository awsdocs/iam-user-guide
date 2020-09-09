# Creating OpenID Connect \(OIDC\) identity providers<a name="id_roles_providers_create_oidc"></a>

*IAM OIDC identity providers* are entities in IAM that describe an external identity provider \(IdP\) service that supports the [OpenID Connect](http://openid.net/connect/) \(OIDC\) standard, such as Google or Salesforce\. You use an IAM OIDC identity provider when you want to establish trust between an OIDC\-compatible IdP and your AWS account\. This is useful when creating a mobile app or web application that requires access to AWS resources, but you don't want to create custom sign\-in code or manage your own user identities\. For more information about this scenario, see [About web identity federation](id_roles_providers_oidc.md)\.

You can create and manage an IAM OIDC identity provider using the AWS Management Console, the AWS Command Line Interface, the Tools for Windows PowerShell, or the IAM API\. 

**Topics**
+ [Creating and managing an OIDC provider \(console\)](#manage-oidc-provider-console)
+ [Creating and managing an IAM OIDC identity provider \(AWS CLI\)](#manage-oidc-provider-cli)
+ [Creating and managing an OIDC Identity Provider \(AWS API\)](#manage-oidc-provider-api)
+ [Obtaining the root CA thumbprint for an OpenID Connect Identity Provider](id_roles_providers_create_oidc_verify-thumbprint.md)

## Creating and managing an OIDC provider \(console\)<a name="manage-oidc-provider-console"></a>

Follow these instructions to create and manage an IAM OIDC identity provider in the AWS Management Console\.

**To create an IAM OIDC identity provider \(console\)**

1. <a name="idpoidcstep1"></a>Before you create an IAM OIDC identity provider, you must register your application with the IdP to receive a *client ID*\. The client ID \(also known as *audience*\) is a unique identifier for your app that is issued to you when you register your app with the IdP\. For more information about obtaining a client ID, see the documentation for your IdP\. 

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Identity Providers**, and then choose **Create Provider**\.

1. For **Provider Type**, choose **Choose a provider type**, and then choose **OpenID Connect**\. 

1. For **Provider URL**, type the URL of the IdP\. The URL must comply with these restrictions:
   + The URL is case\-sensitive\.
   + The URL must begin with **https://**\.
   + The URL cannot include a colon \(:\) character, and therefore cannot specify a port number\. This means that the server must be listening on the default port 443\.
   + Within your AWS account, each IAM OIDC identity provider must use a unique URL\.

1. For **Audience**, type the client ID of the application that you registered with the IdP and received in [Step 1](#idpoidcstep1), and that will make requests to AWS\. If you have additional client IDs \(also known as *audiences*\) for this IdP, you can add them later on the provider detail page\. Choose **Next Step**\. 

1. Use the **Thumbprint** to verify the server certificate of your IdP\. To learn how, see [Obtaining the root CA thumbprint for an OpenID Connect Identity Provider](id_roles_providers_create_oidc_verify-thumbprint.md)\. Choose **Create**\.

1. In the confirmation message at the top of the screen, choose **Do this now** to go to the **Roles** tab to create a role for this identity provider\. For more information about creating a role for an OIDC identity provider, see [Creating a role for a third\-party Identity Provider \(federation\)](id_roles_create_for-idp.md)\. OIDC identity providers must have a role in order to access your AWS account\. To skip this step and create the role later, choose **Close**\. 

**To add or remove a thumbprint or client ID \(also known as audience\) for an IAM OIDC identity provider \(console\)**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Identity Providers**, then choose the name of the IAM identity provider that you want to update\.

1. To add a thumbprint or audience, choose **Add a Thumbprint** or **Add an Audience**\. To remove a thumbprint or audience, choose **Remove** next to the item that you want to remove\. 
**Note**  
An IAM OIDC identity provider must have at least one and can have a maximum of five thumbprints\. An OIDC identity provider must have at least one and can have a maximum of 100 audiences\.

    When you are done, choose **Save Changes**\.

**To delete an IAM OIDC identity provider \(console\)**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Identity Providers**\. 

1. Select the check box next to the IAM identity provider that you want to delete\.

1. Choose **Delete Providers**\.

## Creating and managing an IAM OIDC identity provider \(AWS CLI\)<a name="manage-oidc-provider-cli"></a>

You can use the following AWS CLI commands to create and manage IAM OIDC identity providers\.

**To create an IAM OIDC identity provider \(AWS CLI\)**

1. \(Optional\) To get a list of all the IAM OIDC identity providers in your AWS account, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-providers.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-providers.html)

1. To create a new IAM OIDC identity provider, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/create-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/create-open-id-connect-provider.html)

**To update the list of server certificate thumbprints for an existing IAM OIDC identity provider \(AWS CLI\)**
+ To update the list of server certificate thumbprints for an IAM OIDC identity provider, run the following command:
  + [https://docs.aws.amazon.com/cli/latest/reference/iam/update-open-id-connect-provider-thumbprint.html](https://docs.aws.amazon.com/cli/latest/reference/iam/update-open-id-connect-provider-thumbprint.html)

**To add or remove a client ID from an existing IAM OIDC identity provider \(AWS CLI\)**

1. \(Optional\) To get a list of all the IAM OIDC identity provider in your AWS account, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-providers.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-providers.html)

1. \(Optional\) To get detailed information about an IAM OIDC identity provider, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/get-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-open-id-connect-provider.html)

1. To add a new client ID to an existing IAM OIDC identity provider, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/add-client-id-to-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/add-client-id-to-open-id-connect-provider.html)

1. To remove a client from an existing IAM OIDC identity provider, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/remove-client-id-from-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/remove-client-id-from-open-id-connect-provider.html)

**To delete an IAM OIDC identity provider \(AWS CLI\)**

1. \(Optional\) To get a list of all the IAM OIDC identity provider in your AWS account, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-providers.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-providers.html)

1. \(Optional\) To get detailed information about an IAM OIDC identity provider, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/get-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-open-id-connect-provider.html)

1. To delete an IAM OIDC identity provider, run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/delete-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-open-id-connect-provider.html)

## Creating and managing an OIDC Identity Provider \(AWS API\)<a name="manage-oidc-provider-api"></a>

You can use the following IAM API commands to create and manage OIDC providers\.

**To create an IAM OIDC identity provider \(AWS API\)**

1. \(Optional\) To get a list of all the IAM OIDC identity provider in your AWS account, call the following operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviders.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviders.html)

1. To create a new IAM OIDC identity provider, call the following operation: 
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateOpenIDConnectProvider.html)

**To update the list of server certificate thumbprints for an existing IAM OIDC identity provider \(AWS API\)**
+ To update the list of server certificate thumbprints for an IAM OIDC identity provider, call the following operation:
  + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateOpenIDConnectProviderThumbprint.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateOpenIDConnectProviderThumbprint.html)

**To add or remove a client ID from an existing IAM OIDC identity provider \(AWS API\)**

1. \(Optional\) To get a list of all the IAM OIDC identity provider in your AWS account, call the following operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviders.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviders.html)

1. \(Optional\) To get detailed information about an IAM OIDC identity provider, call the following operation: 
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetOpenIDConnectProvider.html)

1. To add a new client ID to an existing IAM OIDC identity provider, call the following operation: 
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_AddClientIDToOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_AddClientIDToOpenIDConnectProvider.html)

1. To remove a client ID from an existing IAM OIDC identity provider, call the following operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveClientIDFromOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveClientIDFromOpenIDConnectProvider.html)

**To delete an IAM OIDC identity provider \(AWS API\)**

1. \(Optional\) To get a list of all the IAM OIDC identity provider in your AWS account, call the following operation: 
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviders.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviders.html)

1. \(Optional\) To get detailed information about an IAM OIDC identity provider, call the following operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetOpenIDConnectProvider.html)

1. To delete an IAM OIDC identity provider, call the following operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteOpenIDConnectProvider.html)