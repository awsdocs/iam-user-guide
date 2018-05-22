# Permissions for GetSessionToken<a name="id_credentials_temp_control-access_getsessiontoken"></a>

If `GetSessionToken` is called with the credentials of an IAM user, the temporary security credentials have the same permissions as the IAM user\. Similarly, if `GetSessionToken` is called with AWS account root user credentials, the temporary security credentials have root user permissions\.

**Note**  
We recommend that you do not call `GetSessionToken` with root user credentials\. Instead, follow our [best practices](IAMBestPracticesAndUseCases.md) and create one or more IAM users with the permissions they need\. Then use these IAM users for everyday interaction with AWS\.

The primary reason for calling `GetSessionToken` is that a user needs to perform actions that are allowed only when the user is authenticated with multi\-factor authentication \(MFA\)\. It is possible to write a policy that allows certain actions only when those actions are requested by a user who has been authenticated with MFA\. In order to successfully pass the MFA authorization check, a user must first call `GetSessionToken` and include the optional `SerialNumber` and `TokenCode` parameters in the `GetSessionToken` API call\. If the user passes valid values for the `SerialNumber` and `TokenCode` parameters—that is, if the user is successfully authenticated with an MFA device—the credentials returned by the `GetSessionToken` API call will include the MFA context\. Subsequent calls to AWS with the credentials returned by `GetSessionToken` will allow the user to successfully call AWS API operations that require MFA authentication\.

The temporary credentials that you get when you call `GetSessionToken` have the following capabilities and limitations:
+ You can use the credentials to access the AWS Management Console by passing the credentials to the federation single sign\-on endpoint at `https://signin.aws.amazon.com/federation`\. For more information, see [Creating a URL that Enables Federated Users to Access the AWS Management Console \(Custom Federation Broker\)](id_roles_providers_enable-console-custom-url.md)\.
+ You **cannot** use the credentials to call IAM or AWS STS API operations\. You **can** use them to call API operations for other AWS services\.

Compare this API and its limitations and capability with the other API operations that create temporary security credentials at [Comparing the AWS STS API Operations](id_credentials_temp_request.md#stsapi_comparison)

For more information about MFA\-protected API access using `GetSessionToken`, see [Configuring MFA\-Protected API Access](id_credentials_mfa_configure-api-require.md)\.