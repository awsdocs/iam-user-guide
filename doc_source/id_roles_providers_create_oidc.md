# Creating OpenID Connect \(OIDC\) identity providers<a name="id_roles_providers_create_oidc"></a>

*IAM OIDC identity providers* are entities in IAM that describe an external identity provider \(IdP\) service that supports the [OpenID Connect](http://openid.net/connect/) \(OIDC\) standard, such as Google or Salesforce\. You use an IAM OIDC identity provider when you want to establish trust between an OIDC\-compatible IdP and your AWS account\. This is useful when creating a mobile app or web application that requires access to AWS resources, but you don't want to create custom sign\-in code or manage your own user identities\. For more information about this scenario, see [About web identity federation](id_roles_providers_oidc.md)\.

You can create and manage an IAM OIDC identity provider using the AWS Management Console, the AWS Command Line Interface, the Tools for Windows PowerShell, or the IAM API\. 

After you create an IAM OIDC identity provider, you must create one or more IAM roles\. A role is an identity in AWS that doesn't have its own credentials \(as a user does\)\. But in this context, a role is dynamically assigned to a federated user that is authenticated by your organization's IdP\. The role permits your organization's IdP to request temporary security credentials for access to AWS\. The policies assigned to the role determine what the federated users are allowed to do in AWS\. To create a role for a third\-party identity provider, see [Creating a role for a third\-party Identity Provider \(federation\)](id_roles_create_for-idp.md)\.

**Topics**
+ [Creating and managing an OIDC provider \(console\)](#manage-oidc-provider-console)
+ [Creating and managing an IAM OIDC identity provider \(AWS CLI\)](#manage-oidc-provider-cli)
+ [Creating and managing an OIDC Identity Provider \(AWS API\)](#manage-oidc-provider-api)
+ [Obtaining the thumbprint for an OpenID Connect Identity Provider](id_roles_providers_create_oidc_verify-thumbprint.md)

## Creating and managing an OIDC provider \(console\)<a name="manage-oidc-provider-console"></a>

Follow these instructions to create and manage an IAM OIDC identity provider in the AWS Management Console\.

**Important**  
If you are using an OIDC identity provider from either Google, Facebook, or Amazon Cognito, do not create a separate IAM identity provider using this procedure\. These OIDC identity providers are already built\-in to AWS and are available for your use\. Instead, follow the steps to create new roles for your identity provider, see [Creating a role for web identity or OpenID connect federation \(console\)](id_roles_create_for-idp_oidc.md)\.

**To create an IAM OIDC identity provider \(console\)**

1. <a name="idpoidcstep1"></a>Before you create an IAM OIDC identity provider, you must register your application with the IdP to receive a *client ID*\. The client ID \(also known as *audience*\) is a unique identifier for your app that is issued to you when you register your app with the IdP\. For more information about obtaining a client ID, see the documentation for your IdP\. 
**Note**  
AWS secures communication with some OIDC identity providers \(IdPs\) through our library of trusted certificate authorities \(CAs\) instead of using a certificate thumbprint to verify your IdP server certificate\. These OIDC IdPs include Google, and those that use an Amazon S3 bucket to host a JSON Web Key Set \(JWKS\) endpoint\. In these cases, your legacy thumbprint remains in your configuration, but is no longer used for validation\.

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Identity providers**, and then choose **Add provider**\.

1. For **Configure provider**, choose **OpenID Connect**\. 

1. For **Provider URL**, type the URL of the IdP\. The URL must comply with these restrictions:
   + The URL is case\-sensitive\.
   + The URL must begin with **https://**\.
   + The URL should not contain a port number\. 
   + Within your AWS account, each IAM OIDC identity provider must use a unique URL\.

1. Choose **Get thumbprint** to verify the server certificate of your IdP\. To learn how, see [Obtaining the thumbprint for an OpenID Connect Identity Provider](id_roles_providers_create_oidc_verify-thumbprint.md)\.

1. For **Audience**, type the client ID of the application that you registered with the IdP and received in [Step 1](#idpoidcstep1), and that make requests to AWS\. If you have additional client IDs \(also known as *audiences*\) for this IdP, you can add them later on the provider detail page\.

1. \(Optional\) For **Add tags**, you can add key–value pairs to help you identify and organize your IdPs\. You can also use tags to control access to AWS resources\. To learn more about tagging IAM OIDC identity providers, see [Tagging OpenID Connect \(OIDC\) identity providers](id_tags_idps_oidc.md)\. Choose **Add tag**\. Enter values for each tag key\-value pair\. 

1. Verify the information that you have provided\. When you are done choose **Add provider**\.

1. Assign an IAM role to your identity provider to give external user identities managed by your identity provider permissions to access AWS resources in your account\. To learn more about creating roles for identity federation, see [Creating a role for a third\-party Identity Provider \(federation\)](id_roles_create_for-idp.md)\.

**To add or remove a thumbprint for an IAM OIDC identity provider \(console\)**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Identity providers**\. Then choose the name of the IAM identity provider that you want to update\.

1. In the **Thumbprints** section, choose **Manage**\. To enter a new thumbprint value, choose **Add thumbprint**\. To remove a thumbprint, choose **Remove** next to the thumbprint that you want to remove\.
**Note**  
An IAM OIDC identity provider must have at least one and can have a maximum of five thumbprints\.

    When you are done, choose **Save changes**\.

**To add an audience for an IAM OIDC identity provider \(console\)**

1. In the navigation pane, choose **Identity providers**, then choose the name of the IAM identity provider that you want to update\.

1. In the **Audiences** section, choose **Actions** and select **Add audience**\. 

1. Type the client ID of the application that you registered with the IdP and received in [Step 1](#idpoidcstep1), and that will make requests to AWS\. Then choose **Add audiences**\.
**Note**  
An IAM OIDC identity provider must have at least one and can have a maximum of 100 audiences\.

**To remove an audience for an IAM OIDC identity provider \(console\)**

1. In the navigation pane, choose **Identity providers**, then choose the name of the IAM identity provider that you want to update\.

1. In the **Audiences** section, select the radio button next to the audience that you want to remove, then select **Actions**\.

1.  Choose **Remove audience**\. A new window opens\.

1. If you remove an audience, identities federating with the audience cannot assume roles associated with the audience\. In the window, read the warning and confirm that you want to remove the audience by typing the word `remove` in the field\.

1. Choose **Remove** to remove the audience\.

**To delete an IAM OIDC identity provider \(console\)**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Identity providers**\. 

1. Select the check box next to the IAM identity provider that you want to delete\. A new window opens\.

1. Confirm that you want to delete the provider by typing the word `delete` in the field\. Then, choose **Delete**\.

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

**To tag an existing IAM OIDC identity provider \(AWS CLI\)**
+ To tag an existing IAM OIDC identity provider, run the following command:
  + [https://docs.aws.amazon.com/cli/latest/reference/iam/tag-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-open-id-connect-provider.html)

**To list tags for an existing IAM OIDC identity provider \(AWS CLI\)**
+ To list tags for an existing IAM OIDC identity provider, run the following command:
  + [https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-provider-tags.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-provider-tags.html)

**To remove tags on an IAM OIDC identity provider \(AWS CLI\)**
+ To remove tags on an existing IAM OIDC identity provider, run the following command:
  + [https://docs.aws.amazon.com/cli/latest/reference/iam/untag-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-open-id-connect-provider.html)

**To tag an existing IAM OIDC identity provider \(AWS CLI\)**
+ To tag an existing IAM OIDC identity provider, run the following command:
  + [https://docs.aws.amazon.com/cli/latest/reference/iam/tag-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-open-id-connect-provider.html)

**To list tags for an existing IAM OIDC identity provider \(AWS CLI\)**
+ To list tags for an existing IAM OIDC identity provider, run the following command:
  + [https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-provider-tags.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-provider-tags.html)

**To remove tags on an IAM OIDC identity provider \(AWS CLI\)**
+ To remove tags on an existing IAM OIDC identity provider, run the following command:
  + [https://docs.aws.amazon.com/cli/latest/reference/iam/untag-open-id-connect-provider.html](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-open-id-connect-provider.html)

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

**To tag an existing IAM OIDC identity provider \(AWS API\)**
+ To tag an existing IAM OIDC identity provider, call the following operation:
  + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagOpenIDConnectProvider.html)

**To list tags for an existing IAM OIDC identity provider \(AWS API\)**
+ To list tags for an existing IAM OIDC identity provider, call the following operation:
  + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviderTags.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviderTags.html)

**To remove tags on an existing IAM OIDC identity provider \(AWS API\)**
+ To remove tags on an existing IAM OIDC identity provider, call the following operation:
  + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagOpenIDConnectProvider.html)

**To tag an existing IAM OIDC identity provider \(AWS API\)**
+ To tag an existing IAM OIDC identity provider, call the following operation:
  + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagOpenIDConnectProvider.html)

**To list tags for an existing IAM OIDC identity provider \(AWS API\)**
+ To list tags for an existing IAM OIDC identity provider, call the following operation:
  + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviderTags.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviderTags.html)

**To remove tags on an existing IAM OIDC identity provider \(AWS API\)**
+ To remove tags on an existing IAM OIDC identity provider, call the following operation:
  + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagOpenIDConnectProvider.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagOpenIDConnectProvider.html)

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