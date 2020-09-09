# Using web identity federation API operations for mobile apps<a name="id_roles_providers_oidc_manual"></a>

For best results, use Amazon Cognito as your identity broker for almost all web identity federation scenarios\. Amazon Cognito is easy to use and provides additional capabilities like anonymous \(unauthenticated\) access, and synchronizing user data across devices and providers\. However, if you have already created an app that uses web identity federation by manually calling the `AssumeRoleWithWebIdentity` API, you can continue to use it and your apps will still work fine\. 

**Note**  
To help understand how web identity federation works, you can use the [Web Identity Federation Playground](http://aws.amazon.com/blogs/aws/the-aws-web-identity-federation-playground/)\. This interactive website lets you walk through the process of authenticating via Login with Amazon, Facebook, or Google, getting temporary security credentials, and then using those credentials to make a request to AWS\.

The process for using web identity federation ***without*** Amazon Cognito follows this general outline: 

1. Sign up as a developer with the external identity provider \(IdP\) and configure your app with the IdP, who gives you a unique ID for your app\. \(Different IdPs use different terminology for this process\. This outline uses the term *configure* for the process of identifying your app with the IdP\.\) Each IdP gives you an app ID that's unique to that IdP, so if you configure the same app with multiple IdPs, your app will have multiple app IDs\. You can configure multiple apps with each provider\. 

   The following external links provide information about using some of the commonly used identity providers \(IdPs\): 
   + [Login with Amazon Developer Center](https://login.amazon.com/) 
   + [Add Facebook Login to Your App or Website](https://developers.facebook.com/docs/facebook-login/v2.1) on the Facebook developers site\. 
   + [Using OAuth 2\.0 for Login \(OpenID Connect\)](https://developers.google.com/accounts/docs/OAuth2Login) on the Google developers site\.
**Note**  
Although Amazon Cognito and Google are based on OIDC technology, you don't have to create an IAM identity provider entity to use them\. Support for Amazon Cognito and Google are built\-in to AWS\.

1. If you use an IdP that is compatible with OIDC, then create an IAM identity provider entity for it\.

1. In IAM, [create one or more roles](id_roles_create_for-idp.md)\. For each role, define who can assume the role \(the trust policy\) and what permissions the app's users are to have \(the permissions policy\)\. Typically, you create one role for each IdP that an app supports\. For example, you might create a role that is assumed by an app when the user signs in through Login with Amazon, a second role for the same app where the user signs in through Facebook, and a third role for the app where the user signs in through Google\. For the trust relationship, specify the IdP \(like Amazon\.com\) as the `Principal` \(the trusted entity\), and include a `Condition` that matches the IdP assigned app ID\. Examples of roles for different providers are described later in this topic\. 

1. In your application, authenticate your users with the IdP\. The specifics of how to do this vary both according to which IdP you're using \(Login with Amazon, Facebook, or Google\) and on which platform your app runs\. For example, an Android app's method of authentication can differ from that of an iOS app or a JavaScript\-based web app\.

   Typically, if the user is not already signed in, the IdP takes care of displaying a sign\-in page\. After the IdP authenticates the user, the IdP returns an authentication token with information about the user to your app\. The information included depends on what the IdP exposes and what information the user is willing to share\. You can use this information in your app\.

1. In your app, make an *unsigned* call to the `AssumeRoleWithWebIdentity` action to request temporary security credentials\. In the request, you pass the IdP's authentication token and specify the Amazon Resource Name \(ARN\) for the IAM role that you created for that IdP\. AWS verifies that the token is trusted and valid and if so, returns temporary security credentials to your app that have the permissions for the role that you name in the request\. The response also includes metadata about the user from the IdP, such as the unique user ID that the IdP associates with the user\.

1. Using the temporary security credentials from the `AssumeRoleWithWebIdentity` response, your app makes signed requests to AWS API operations\. The user ID information from the IdP can distinguish users in your app—for example, you can put objects into Amazon S3 folders that include the user ID as prefixes or suffixes\. This lets you create access control policies that lock the folder so only the user with that ID can access it\. For more information, see [Identifying users with web identity federation](id_roles_providers_oidc_user-id.md) later in this topic\.

1. Your app should cache the temporary security credentials so that you do not have to get new ones each time the app needs to make a request to AWS\. By default, the credentials are good for one hour\. When the credentials expire \(or before then\), you make another call to `AssumeRoleWithWebIdentity` to obtain a new set of temporary security credentials\. Depending on the IdP and how they manage their tokens, you might have to refresh the IdP's token before you make a new call to `AssumeRoleWithWebIdentity`, since the IdP's tokens also usually expire after a fixed time\. If you use the AWS SDK for iOS or the AWS SDK for Android, you can use the [AmazonSTSCredentialsProvider](http://aws.amazon.com/blogs/mobile/using-the-amazoncredentialsprovider-protocol-in-the-aws-sdk-for-ios) action, which manages the IAM temporary credentials, including refreshing them as required\.