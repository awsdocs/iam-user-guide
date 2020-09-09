# Permissions for GetSessionToken<a name="id_credentials_temp_control-access_getsessiontoken"></a>

The primary occasion for calling the `GetSessionToken` API operation or the `get-session-token` CLI command is when a user must be authenticated with multi\-factor authentication \(MFA\)\. It is possible to write a policy that allows certain actions only when those actions are requested by a user who has been authenticated with MFA\. In order to successfully pass the MFA authorization check, a user must first call `GetSessionToken` and include the optional `SerialNumber` and `TokenCode` parameters\. If the user is successfully authenticated with an MFA device, the credentials returned by the `GetSessionToken` API operation include the MFA context\. This context indicates that the user is authenticated with MFA and is authorized for API operations that require MFA authentication\.

## Permissions required for GetSessionToken<a name="getsessiontoken-permissions-required"></a>

No permissions are required for a user to get a session token\. The purpose of the `GetSessionToken` operation is to authenticate the user using MFA\. You cannot use policies to control authentication operations\.

To grant permissions to perform most AWS operations, you add the action with the same name to a policy\. For example, to create a user, you must use the `CreateUser` API operation, the `create-user` CLI command, or the AWS Management Console\. To perform these operations, you must have a policy that allows you to access the `CreateUser` action\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:CreateUser",
            "Resource": "*"
        }
    ]
}
```

You can include the `GetSessionToken` action in your policies, but it has no effect on a user's ability to perform the `GetSessionToken` operation\.

## Permissions granted by GetSessionToken<a name="getsessiontoken-permissions-granted"></a>

If `GetSessionToken` is called with the credentials of an IAM user, the temporary security credentials have the same permissions as the IAM user\. Similarly, if `GetSessionToken` is called with AWS account root user credentials, the temporary security credentials have root user permissions\.

**Note**  
We recommend that you do not call `GetSessionToken` with root user credentials\. Instead, follow our [best practices](IAMBestPracticesAndUseCases.md) and create IAM users with the permissions they need\. Then use these IAM users for everyday interaction with AWS\.

The temporary credentials that you get when you call `GetSessionToken` have the following capabilities and limitations:
+ You can use the credentials to access the AWS Management Console by passing the credentials to the federation single sign\-on endpoint at `https://signin.aws.amazon.com/federation`\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.
+ You **cannot** use the credentials to call IAM or AWS STS API operations\. You **can** use them to call API operations for other AWS services\.

Compare this API operation and its limitations and capability with the other API operations that create temporary security credentials at [Comparing the AWS STS API operations](id_credentials_temp_request.md#stsapi_comparison)

For more information about MFA\-protected API access using `GetSessionToken`, see [Configuring MFA\-protected API access](id_credentials_mfa_configure-api-require.md)\.