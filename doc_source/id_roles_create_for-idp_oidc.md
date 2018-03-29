# Creating a Role for Web Identity or OpenID Connect Federation \(Console\)<a name="id_roles_create_for-idp_oidc"></a>

Before you can create a role for web identity federation, you must first complete the following prerequisite steps\.<a name="oidc-prereqs"></a>

**To prepare to create a role for web identity federation**

1. Begin by signing up as a developer with an IdP \(or more than one\)\. You also configure your app with the provider; when you do, the provider gives you an application or audience ID that's unique to your app\. \(Providers use different terminology for this process\. This guide uses the term *configure* for the process of identifying your app with the provider\.\) Each provider gives you an app ID that's unique to that provider, so if you configure the same app with multiple providers, your app will have multiple app IDs\. You can configure multiple apps with each provider\. The following external links provide information about using one of the identity providers:
   + [Login with Amazon Developer Center](https://login.amazon.com/)
   + [Add Facebook Login to Your App or Website](https://developers.facebook.com/docs/facebook-login/v2.1) on the Facebook developers site\.
   + [Using OAuth 2\.0 for Login \(OpenID Connect\)](https://developers.google.com/accounts/docs/OAuth2Login) on the Google developers site\.

1. <a name="idpoidcstep2"></a>After getting the required information from the identity provider, you can create an *identity provider* in IAM\. For more information, see [Creating OpenID Connect \(OIDC\) Identity Providers](id_roles_providers_create_oidc.md)\.

1. Prepare the policies for the role that the IdP\-authenticated users will assume\. As with any role, a role for the mobile app contains two policies\. One is the trust policy that specifies who can assume the role \(the trusted entity or principal\)\. The other policy \(the permission policy\) specifies the actual AWS actions and resources that the mobile app is allowed or denied access to \(similar to user or resource policies\)\.

   For web identity providers, we recommend that you use [Amazon Cognito](https://aws.amazon.com/cognito/) to manage identities\. In that case, the trust policy for the role must include a `Statement` similar to the following:

   ```
   {
       "Version": "2012-10-17",
       "Statement": [{
           "Effect": "Allow",
           "Principal": {"Federated": "cognito-identity.amazonaws.com"},
           "Action": "sts:AssumeRoleWithWebIdentity",
           "Condition": {
         "StringEquals": {"cognito-identity.amazonaws.com:aud": "us-east-2:12345678-abcd-abcd-abcd-123456"},
         "ForAnyValue:StringLike": {"cognito-identity.amazonaws.com:amr": "unauthenticated"}
       }]
   }
   ```

   Replace `us-east-2:12345678-abcd-abcd-abcd-123456` with the actual identity pool ID that Amazon Cognito assigned to you\.

   If you manually configure a web identity IdP, then the trust policy must grant an `Allow` effect for the `sts:AssumeRoleWithWebIdentity` action\. In this role, you use two values that ensure that only your application can assume the role:
   + For the `Principal` element, use the string `{"Federated":providerUrl/providerArn}`\.
     + For some common OpenID Connect \(OIDC\) IdPs, the `providerUrl` is the fully qualified URL\. The following are acceptable ways to specify the principal for some common IdPs:

       `"Principal":{"Federated":"cognito-identity.amazonaws.com"}`

       `"Principal":{"Federated":"www.amazon.com"}`

       `"Principal":{"Federated":"graph.facebook.com"}`

       `"Principal":{"Federated":"accounts.google.com"}`
     + For other OIDC providers, use the ARN of the OIDC identity provider you created in [Step 2](#idpoidcstep2), like the following example:

       `"Principal":{"Federated":"arn:aws:iam::123456789012:oidc-provider/server.example.com"}`
   + In the `Condition` element, use a `StringEquals` condition to limit permissions\. Test the identity pool ID \(for Amazon Cognito\) or the app ID \(for other providers\)\. It should match the app ID that you got when you configured the app with the IdP\. This ensures that the request is coming from your app\. Test the app ID that you have against the following policy variables depending on the IdP that you are using: 

     `"Condition": {"StringEquals": {"cognito-identity.amazonaws.com:aud": "us-east:12345678-ffff-ffff-ffff-123456"}}`

     `"Condition": {"StringEquals": {"www.amazon.com:app_id": "amzn1.application-oa2-123456"}}`

     `"Condition": {"StringEquals": {"graph.facebook.com:app_id": "111222333444555"}}`

     `"Condition": {"StringEquals": {"accounts.google.com:aud": "66677788899900pro0"}}`

     For OIDC providers, use the fully qualified URL of the OIDC IdP with the `aud` context key, like the following example: 

     `"Condition": {"StringEquals": {"server.example.com:aud": "appid_from_oidc_idp"}}`

   Notice that the values for the principal in the role are specific to an IdP\. A role can specify only one principal\. Therefore, if the mobile app allows users to sign in from more than one IdP, you must create a role for each IdP that you want to support\. 
**Note**  
Because the policy for the trusted entity uses [policy variables](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html) that represent the IdP and the app ID, you must set the policy's `Version` element to `2012-10-17` or a later supported version\.

   The following example shows a trust policy for a role designed for a mobile app if the user signs in from Login with Amazon\. In the example, *amzn1\.application\-oa2\-123456* represents the app ID that Amazon assigned when you configured the app using Login with Amazon\.

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

   The following example shows a policy for a role that the mobile app could assume if the user has signed in from Facebook\. In this example, *111222333444555* represents the app ID assigned by Facebook\. To learn how to create an IAM policy using this example JSON policy document, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

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

   The following example shows a policy for a role that the mobile app could assume if the user has signed in from Google\. In this example, *666777888999000* represents the app ID assigned by Google\. To learn how to create an IAM policy using this example JSON policy document, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

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

   The following example shows a policy for a role that the mobile app could assume if the application is using Amazon Cognito\. In this example, *us\-east:12345678\-ffff\-ffff\-ffff\-123456* represents the identity pool ID assigned by Amazon Cognito\. To learn how to create an IAM policy using this example JSON policy document, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

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

   After you complete the prerequisites, you can create the role itself\. The following procedure describes how to create the role for web identity/OIDC federation in the AWS Management Console\. To create a role using the AWS CLI, Tools for Windows PowerShell, or AWS API, see the procedures at [Creating a Role for a Third\-Party Identity Provider \(Federation\)](id_roles_create_for-idp.md)\.

**To create an IAM role for web identity federation**

If you are using Amazon Cognito, you should use the Amazon Cognito console to set up the roles\. Otherwise, use the IAM console to create a role for web identity federation\.

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, click **Roles** and then click **Create role**\.

1. Choose the **Web identity** role type\.

1. In the **Identity provider** list, choose the identity provider that you're creating the role for: 
   + If you're creating a role for an individual web identity provider, choose **Login with Amazon**, **Facebook**, or **Google**\. 
**Note**  
You must create a separate role for each identity provider that you want to support\.
   + Choose **Amazon Cognito** if you're creating a role for Amazon Cognito\. 
**Note**  
You only need to manually create a role for use with Amazon Cognito when you are working on an advanced scenario\. Otherwise, Amazon Cognito can create roles for you for standard scenarios\. For more information about Amazon Cognito, see [Amazon Cognito Identity](http://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html) in the *AWS Mobile SDK for iOS Developer Guide* and [Amazon Cognito Identity](http://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html) in the *AWS Mobile SDK for Android Developer Guide*\. 

1. Type the identifier for your application\. The name identifier setting changes depending on which provider you choose:
   + If you're creating a role for Login with Amazon, type the app ID into the **Application ID** box\.
   + If you're creating a role for Amazon Cognito, type the ID of the identity pool that you have created for your Amazon Cognito applications into the **Identity Pool ID** box\.
   + If you're creating a role for Facebook, type the app ID into the **Application ID** box\.
   + If you're creating a role for Google, type the audience name into the **Audience** box\.

1. \(Optional\) Click **Add condition \(optional\)** to create additional conditions that must be met before users of your application can use the permissions that the role grants\. For example, you can add a condition that grants access to AWS resources only for a specific IAM user ID\.

1. Review your web identity information and then choose **Next: Permissions**\.

1. Choose one or more permissions policies to attach to the role\. By default, roles have no permissions\. Select the box next to the policy that assigns the permissions that you want the web identity users to have\. Then choose **Next: Review**\.

1. For **Role name**, type a role name that helps you identify the purpose of this role\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because various entities might reference the role, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Role description**, type a description for the new role\.

1. Review the role and then choose **Create role**\.