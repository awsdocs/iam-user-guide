# Creating a role for web identity or OpenID Connect Federation \(console\)<a name="id_roles_create_for-idp_oidc"></a>

You can use Web Identity or OpenID Connect \(OIDC\) federated identity providers instead of creating AWS Identity and Access Management users in your AWS account\. With an identity provider \(IdP\), you can manage your user identities outside of AWS and give these external user identities permissions to access AWS resources in your account\. For more information about federation and IdPs, see [Identity providers and federation](id_roles_providers.md)\.

## Prerequisites for creating a role for web identity or OIDC<a name="idp_oidc_Prerequisites"></a>

Before you can create a role for web identity federation, you must first complete the following prerequisite steps\.<a name="oidc-prereqs"></a>

**To prepare to create a role for web identity federation**

1. Sign up with one or more services offering federated OIDC identity\. If you are creating an app that needs access to your AWS resources, you also configure your app with the provider information\. When you do, the provider gives you an application or audience ID that is unique to your app\. \(Different providers use different terminology for this process\. This guide uses the term *configure* for the process of identifying your app with the provider\.\) You can configure multiple apps with each provider, or multiple providers with a single app\. View information about using the identity providers as follows:
   + [Login with Amazon Developer Center](https://login.amazon.com/)
   + [Add Facebook Login to Your App or Website](https://developers.facebook.com/docs/facebook-login/v2.1) on the Facebook developers site\.
   + [Using OAuth 2\.0 for Login \(OpenID Connect\)](https://developers.google.com/accounts/docs/OAuth2Login) on the Google developers site\.

1. <a name="idpoidcstep2"></a>After you receive the required information from the IdP, create an IdP in IAM\. For more information, see [Creating OpenID Connect \(OIDC\) identity providers](id_roles_providers_create_oidc.md)\.
**Important**  
If you are using an OIDC IdP from Google, Facebook, or Amazon Cognito, don't create a separate IAM IdP in the AWS Management Console\. These OIDC identity providers are already built into AWS and are available for you to use\. Skip this step and create new roles using your IdP in the following step\.

1. Prepare the policies for the role that the IdP\-authenticated users will assume\. As with any role, a role for a mobile app includes two policies\. One is the trust policy that specifies who can assume the role\. The other is the permissions policy that specifies the AWS actions and resources that the mobile app is allowed or denied access to\.

   For web IdPs, we recommend that you use [Amazon Cognito](https://aws.amazon.com/cognito/) to manage identities\. In this case, use a trust policy similar to this example\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": {
           "Effect": "Allow",
           "Principal": {"Federated": "cognito-identity.amazonaws.com"},
           "Action": "sts:AssumeRoleWithWebIdentity",
           "Condition": {
               "StringEquals": {"cognito-identity.amazonaws.com:aud": "us-east-2:12345678-abcd-abcd-abcd-123456"},
               "ForAnyValue:StringLike": {"cognito-identity.amazonaws.com:amr": "unauthenticated"}
           }
       }
   }
   ```

   Replace `us-east-2:12345678-abcd-abcd-abcd-123456` with the identity pool ID that Amazon Cognito assigns to you\.

   If you manually configure a web identity IdP, when you create the trust policy, you must use three values that ensure that only your app can assume the role:
   + For the `Action` element, use the `sts:AssumeRoleWithWebIdentity` action\.
   + For the `Principal` element, use the string `{"Federated":providerUrl/providerArn}`\.
     + For some common OIDC IdPs, the `providerUrl` is a URL\. The following examples include methods to specify the principal for some common IdPs:

       `"Principal":{"Federated":"cognito-identity.amazonaws.com"}`

       `"Principal":{"Federated":"www.amazon.com"}`

       `"Principal":{"Federated":"graph.facebook.com"}`

       `"Principal":{"Federated":"accounts.google.com"}`
     + For other OIDC providers, use the Amazon Resource Name \(ARN\) of the OIDC IdP that you created in [Step 2](#idpoidcstep2), such as the following example:

       `"Principal":{"Federated":"arn:aws:iam::123456789012:oidc-provider/server.example.com"}`
   + For the `Condition` element, use a `StringEquals` condition to limit permissions\. Test the identity pool ID for Amazon Cognito\) or the app ID for other providers\. The identity pool ID should match the app ID that you received when you configured the app with the IdP\. This match between the IDs ensures that the request comes from your app\. Create a condition element similar to one of the following examples, depending on the IdP that you are using: 

     `"Condition": {"StringEquals": {"cognito-identity.amazonaws.com:aud": "us-east:12345678-ffff-ffff-ffff-123456"}}`

     `"Condition": {"StringEquals": {"www.amazon.com:app_id": "amzn1.application-oa2-123456"}}`

     `"Condition": {"StringEquals": {"graph.facebook.com:app_id": "111222333444555"}}`

     `"Condition": {"StringEquals": {"accounts.google.com:aud": "66677788899900pro0"}}`

     For OIDC providers, use the fully qualified URL of the OIDC IdP with the `aud` context key, such as the following example: 

     `"Condition": {"StringEquals": {"server.example.com:aud": "appid_from_oidc_idp"}}`
**Note**  
The values for the principal in the trust policy for the role are specific to an IdP\. A role for web identity or OIDC can specify only one principal\. Therefore, if the mobile app allows users to sign in from more than one IdP, create a separate role for each IdP that you want to support\. Create separate trust policies for each IdP\.

   If a user uses a mobile app to sign in from Login with Amazon, the following example trust policy would apply\. In the example, *amzn1\.application\-oa2\-123456* represents the app ID that Amazon assigns when you configured the app using Login with Amazon\.

   ```
   {
         "Version": "2012-10-17",
         "Statement": [{
             "Sid": "RoleForLoginWithAmazon",
             "Effect": "Allow",
             "Principal": {"Federated": "www.amazon.com"},
             "Action": "sts:AssumeRoleWithWebIdentity",
             "Condition": {"StringEquals": {"www.amazon.com:app_id": "amzn1.application-oa2-123456"}}
         }]
     }
   ```

   If a user uses a mobile app to sign in from Facebook, the following example trust policy would apply\. In this example, *111222333444555* represents the app ID that Facebook assigns\.

   ```
   {
         "Version": "2012-10-17",
         "Statement": [{
             "Sid": "RoleForFacebook",
             "Effect": "Allow",
             "Principal": {"Federated": "graph.facebook.com"},
             "Action": "sts:AssumeRoleWithWebIdentity",
             "Condition": {"StringEquals": {"graph.facebook.com:app_id": "111222333444555"}}
         }]
     }
   ```

   If a user uses a mobile app to sign in from Google, the following example trust policy would apply\. In this example, *666777888999000* represents the app ID that Google assigns\.

   ```
   {
         "Version": "2012-10-17",
         "Statement": [{
             "Sid": "RoleForGoogle",
             "Effect": "Allow",
             "Principal": {"Federated": "accounts.google.com"},
             "Action": "sts:AssumeRoleWithWebIdentity",
             "Condition": {"StringEquals": {"accounts.google.com:aud": "666777888999000"}}
         }]
     }
   ```

   If a user uses a mobile app to sign in from Amazon Cognito, the following example trust policy would apply\. In this example, *us\-east:12345678\-ffff\-ffff\-ffff\-123456* represents the identity pool ID that Amazon Cognito assigns\.

   ```
   {
         "Version": "2012-10-17",
         "Statement": [{
             "Sid": "RoleForCognito",
             "Effect": "Allow",
             "Principal": {"Federated": "cognito-identity.amazonaws.com"},
             "Action": "sts:AssumeRoleWithWebIdentity",
             "Condition": {"StringEquals": {"cognito-identity.amazonaws.com:aud": "us-east:12345678-ffff-ffff-ffff-123456"}}
         }]
     }
   ```

## Creating a role for web identity or OIDC<a name="idp_oidc_Create"></a>

After you complete the prerequisites, you can create the role in IAM\. The following procedure describes how to create the role for web identity or OIDC federation in the AWS Management Console\. To create a role from the AWS CLI or AWS API, see the procedures at [Creating a role for a third\-party Identity Provider \(federation\)](id_roles_create_for-idp.md)\.

**Important**  
If you use Amazon Cognito, use the Amazon Cognito console to set up the roles\. Otherwise, use the IAM console to create a role for web identity federation\.

**To create an IAM role for web identity federation**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles** and then choose **Create role**\.

1. Choose the **Web Identity** role type\.

1. For **Identity provider**, choose the IdP for your role: 
   + If you want to create a role for an individual web IdP, choose **Login with Amazon**, **Facebook**, or **Google**\. 
**Note**  
You must create a separate role for each IdP that you want to support\.
   + If you want to create an advanced scenario role for Amazon Cognito, choose **Amazon Cognito**\. 
**Note**  
You must manually create a role to use with Amazon Cognito only when you work on an advanced scenario\. Otherwise, Amazon Cognito can create roles for you\. For more information about Amazon Cognito, see [Identity pools \(federated identities\) external identity providers](https://docs.aws.amazon.com/cognito/latest/developerguide/external-identity-providers.html) in the *Amazon Cognito Developer Guide*\. 

1. Enter the identifier for your application\. The label of the identifier changes based on the provider you choose:
   + If you want to create a role for Login with Amazon, enter the app ID into the **Application ID** box\.
   + If you want to create a role for Facebook, enter the app ID into the **Application ID** box\.
   + If you want to create a role for Google, enter the audience name into the **Audience** box\.
   + If you want to create a role for Amazon Cognito, enter the ID of the identity pool that you have created for your Amazon Cognito applications into the **Identity Pool ID** box\.

1. \(Optional\) Choose **Condition \(optional\)** to create additional conditions that must be met before users of your application can use the permissions that the role grants\. For example, you can add a condition that grants access to AWS resources only for a specific IAM user ID\.

1. Review your web identity information and then choose **Next**\.

1. IAM includes a list of the AWS managed and customer managed policies in your account\. Select the policy to use for the permissions policy, or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see [Creating IAM policies](access_policies_create-console.md#access_policies_create-start)\. After you create the policy, close that tab and return to your original tab\. Select the check box next to the permissions policies that you want web identity users to have\. If you prefer, you can select no policies at this time, and then attach policies to the role later\. By default, a role has no permissions\.

1. \(Optional\) Set a [permissions boundary](access_policies_boundaries.md)\. This is an advanced feature\.

   Open the **Permissions boundary** section and choose **Use a permissions boundary to control the maximum role permissions**\. Select the policy to use for the permissions boundary\.

1. Choose **Next**\.

1. For **Role name**, enter a role name\. Role names must be unique within your AWS account\. They are not case dependent\. For example, you can't create roles named both **PRODROLE** and **prodrole**\. Because other AWS resources might reference the role, you can't edit the name of the role after you create it\.

1. \(Optional\) For **Description**, enter a description for the new role\.

1. To edit the use cases and permissions for the role, choose **Edit** in the **Step 1: Select trusted entities** or **Step 2: Add permissions** sections\. 

1. \(Optional\) To add metadata to the role, attach tags as key–value pairs\. For more information about using tags in IAM, see [Tagging IAM resources](id_tags.md)\.

1. Review the role and then choose **Create role**\.

## Configuring a role for GitHub OIDC identity provider<a name="idp_oidc_Create_GitHub"></a>

If you use GitHub as an OIDC IdP, best practice is to limit the entities that can assume the role associated with the IAM IdP\. When you include a condition statement in the trust policy, you can limit the role to a specific GitHub organization, repository, or branch\. For information about limiting roles, see [GitHub Docs \- About security hardening with OpenID Connect](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect)\. You can use the condition key `token.actions.githubusercontent.com:sub` to limit access\. We recommend that you limit the condition to a specific set of repositories or branches\. If you do not include this condition, then GitHub Actions from organizations or repositories outside of your control are able to assume roles associated with the GitHub IAM IdP in your AWS account\. For information about how to configure AWS to trust GitHub's OIDC as a federated identity, see [GitHub Docs \- Configuring OpenID Connect in Amazon Web Services](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)\.

The following example trust policy limits access to the defined GitHub organization, repository, and branch\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Federated": "arn:aws:iam::012345678910:oidc-provider/token.actions.githubusercontent.com"
      },
      "Action": "sts:AssumeRoleWithWebIdentity",
      "Condition": {
        "StringEquals": {
          "token.actions.githubusercontent.com:aud": "sts.amazonaws.com",
          "token.actions.githubusercontent.com:sub": "repo:GitHubOrg/GitHubRepo:ref:refs/heads/GitHubBranch"
        }
      }
    }
  ]
}
```

The following example condition limits access to the defined GitHub organization and repository, but grants access to any branch within the repository\.

```
"Condition": {
  "StringLike": {
    "token.actions.githubusercontent.com:aud": "sts.amazonaws.com",
    "token.actions.githubusercontent.com:sub": "repo:GitHubOrg/GitHubRepo:*"
  }
}
```

The following example condition limits access to any repository or branch within the defined GitHub organization\. We recommend this as a minimum trust policy condition for roles that use GitHub as an OIDC IdP\.

```
"Condition": {
  "StringLike": {
    "token.actions.githubusercontent.com:aud": "sts.amazonaws.com",
    "token.actions.githubusercontent.com:sub": "repo:GitHubOrg/*"
  }
}
```

For more information about the web identity federation keys available for condition checks in policies, see [Available keys for AWS web identity federation](reference_policies_iam-condition-keys.md#condition-keys-wif)\.