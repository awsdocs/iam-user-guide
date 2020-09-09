# Requesting temporary security credentials<a name="id_credentials_temp_request"></a>

To request temporary security credentials, you can use AWS Security Token Service \(AWS STS\) operations in the AWS API\. These include operations to create and provide trusted users with temporary security credentials that can control access to your AWS resources\. For more information about AWS STS, see [Temporary security credentials in IAM](id_credentials_temp.md)\. To learn about the different methods that you can use to request temporary security credentials by assuming a role, see [Using IAM roles](id_roles_use.md)\.

To call the API operations, you can use one of the [AWS SDKs](http://aws.amazon.com/tools/)\. The SDKs are available for a variety of programming languages and environments, including Java, \.NET, Python, Ruby, Android, and iOS\. The SDKs take care of tasks such as cryptographically signing your requests, retrying requests if necessary, and handling error responses\. You can also use the AWS STS Query API, which is described in the [AWS Security Token Service API Reference](https://docs.aws.amazon.com/STS/latest/APIReference/)\. Finally, two command line tools support the AWS STS commands: the [AWS Command Line Interface](https://aws.amazon.com/documentation/cli), and the [AWS Tools for Windows PowerShell](https://aws.amazon.com/documentation/powershell)\. 

The AWS STS API operations create a new session with temporary security credentials that include an access key pair and a session token\. The access key pair consists of an access key ID and a secret key\. Users \(or an application that the user runs\) can use these credentials to access your resources\. You can create a role session and pass session policies and session tags programmatically using AWS STS API operations\. The resulting session's permissions are the intersection of the role's identity\-based policies and the session policies\. For more information about session policies, see [Session policies](access_policies.md#policies_session)\. For more information about session tags, see [Passing session tags in AWS STS](id_session-tags.md)\.

**Note**  
The size of the security token that AWS STS API operations return is not fixed\. We strongly recommend that you make no assumptions about the maximum size\. The typical token size is less than 4096 bytes, but that can vary\.

## Using AWS STS with AWS regions<a name="using_sts_regions"></a>

You can send AWS STS API calls either to a global endpoint or to one of the Regional endpoints\. If you choose an endpoint closer to you, you can reduce latency and improve the performance of your API calls\. You also can choose to direct your calls to an alternative Regional endpoint if you can no longer communicate with the original endpoint\. If you are using one of the various AWS SDKs, then use that SDK's method to select a Region before you make the API call\. If you are manually constructing HTTP API requests, then you must direct the request to the correct endpoint yourself\. For more information, see the [AWS STS section of *Regions and Endpoints*](https://docs.aws.amazon.com/general/latest/gr/rande.html#sts_region) and [Managing AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\.

The following are the API operations that you can use to acquire temporary credentials for use in your AWS environment and applications\.

## [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html)—cross\-account delegation and federation through a custom identity broker<a name="api_assumerole"></a>

The `AssumeRole` API operation is useful for allowing existing IAM users to access AWS resources that they don't already have access to\. For example, the user might need access to resources in another AWS account\. It is also useful as a means to temporarily gain privileged access—for example, to provide multi\-factor authentication \(MFA\)\. You must call this API using existing IAM user credentials\. For more information, see [Creating a role to delegate permissions to an IAM user](id_roles_create_for-user.md) and [Configuring MFA\-protected API access](id_credentials_mfa_configure-api-require.md)\.

This call must be made using valid AWS security credentials\. When you make this call, you pass the following information:
+ The Amazon Resource Name \(ARN\) of the role that the app should assume\. 
+ \(Optional\) Duration, which specifies the duration of the temporary security credentials\. Use the `DurationSeconds` parameter to specify the duration of the role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\. If you do not pass this parameter, the temporary credentials expire in one hour\. The `DurationSeconds` parameter from this API is separate from the `SessionDuration` HTTP parameter that you use to specify the duration of a console session\. Use the `SessionDuration` HTTP parameter in the request to the federation endpoint for a console sign\-in token\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.
+ Role session name, which is a string value that you can use to identify the session\. For security purposes, administrators can view this field in [AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) to learn who performed an action in AWS\. Your administrator might require that you specify your IAM user name as the session name when you assume the role\. For more information, see [`aws:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname)\.
+ \(Optional\) Inline or managed session policies\. These policies limit the permissions from the role's identity\-based policy that are assigned to the role session\. The resulting session's permissions are the intersection of the role's identity\-based policies and the session policies\. Session policies cannot be used to grant more permissions than those allowed by the identity\-based policy of the role that is being assumed\. For more information about role session permissions, see [Session policies](access_policies.md#policies_session)\.
+ \(Optional\) Session tags\. You can assume a role and then use the temporary credentials to make a request\. When you do, the session's principal tags include the role's tags and the passed session tags\. If you make this call using temporary credentials, the new session also inherits transitive session tags from the calling session\. For more information about session tags, see [Passing session tags in AWS STS](id_session-tags.md)\.
+ \(Optional\) MFA information\. If configured to use multi\-factor authentication \(MFA\), then you include the identifier for an MFA device and the one\-time code provided by that device\.
+ \(Optional\) `ExternalId` value that can be used when delegating access to your account to a third party\. This value helps ensure that only the specified third party can access the role\. For more information, see [How to use an external ID when granting access to your AWS resources to a third party](id_roles_create_for-user_externalid.md)\.

The following example shows a sample request and response using `AssumeRole`\. This example request assumes the `demo` role for the specified duration with the included [session policy](access_policies.md#policies_session), [session tags](id_session-tags.md), and [external ID](id_roles_create_for-user_externalid.md)\. The resulting session is named `John-session`\. 

**Example request**  

```
https://sts.amazonaws.com/
?Version=2011-06-15
&Action=AssumeRole
&RoleSessionName=John-session
&RoleArn=arn:aws::iam::123456789012:role/demo
&Policy=%7B%22Version%22%3A%222012-10-17%22%2C%22Statement%22%3A%5B%7B%22Sid%22%3A%20%22Stmt1%22%2C%22Effect%22%3A%20%22Allow%22%2C%22Action%22%3A%20%22s3%3A*%22%2C%22Resource%22%3A%20%22*%22%7D%5D%7D
&DurationSeconds=1800
&Tags.member.1.Key=Project
&Tags.member.1.Value=Pegasus
&Tags.member.2.Key=Cost-Center
&Tags.member.2.Value=12345
&ExternalId=123ABC
&AUTHPARAMS
```

The policy value shown in the preceding example is the URL\-encoded version of the following policy:

`{"Version":"2012-10-17","Statement":[{"Sid":"Stmt1","Effect":"Allow","Action":"s3:*","Resource":"*"}]}`

The `AUTHPARAMS` parameter in the example is a placeholder for your *signature*\. A signature is the authentication information that you must include with AWS HTTP API requests\. We recommend using the [AWS SDKs](https://aws.amazon.com/tools/) to create API requests, and one benefit of doing so is that the SDKs handle request signing for you\. If you must create and sign API requests manually, see [Signing AWS Requests By Using Signature Version 4](https://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html) in the *Amazon Web Services General Reference* to learn how to sign a request\.

In addition to the temporary security credentials, the response includes the Amazon Resource Name \(ARN\) for the federated user and the expiration time of the credentials\.

**Example response**  

```
<AssumeRoleResponse xmlns="https://sts.amazonaws.com/doc/2011-06-15/">
<AssumeRoleResult>
<Credentials>
  <SessionToken>
   AQoDYXdzEPT//////////wEXAMPLEtc764bNrC9SAPBSM22wDOk4x4HIZ8j4FZTwdQW
   LWsKWHGBuFqwAeMicRXmxfpSPfIeoIYRqTflfKD8YUuwthAx7mSEI/qkPpKPi/kMcGd
   QrmGdeehM4IC1NtBmUpp2wUE8phUZampKsburEDy0KPkyQDYwT7WZ0wq5VSXDvp75YU
   9HFvlRd8Tx6q6fE8YQcHNVXAkiY9q6d+xo0rKwT38xVqr7ZD0u0iPPkUL64lIZbqBAz
   +scqKmlzm8FDrypNC9Yjc8fPOLn9FX9KSYvKTr4rvx3iSIlTJabIQwj2ICCR/oLxBA==
  </SessionToken>
  <SecretAccessKey>
   wJalrXUtnFEMI/K7MDENG/bPxRfiCYzEXAMPLEKEY
  </SecretAccessKey>
  <Expiration>2019-07-15T23:28:33.359Z</Expiration>
  <AccessKeyId>AKIAIOSFODNN7EXAMPLE</AccessKeyId>
</Credentials>
<AssumedRoleUser>
  <Arn>arn:aws:sts::123456789012:assumed-role/demo/John</Arn>
  <AssumedRoleId>ARO123EXAMPLE123:John</AssumedRoleId>
</AssumedRoleUser>
<PackedPolicySize>8</PackedPolicySize>
</AssumeRoleResult>
<ResponseMetadata>
<RequestId>c6104cbe-af31-11e0-8154-cbc7ccf896c7</RequestId>
</ResponseMetadata>
</AssumeRoleResponse>
```

**Note**  
An AWS conversion compresses the passed session policies and session tags into a packed binary format that has a separate limit\. Your request can fail for this limit even if your plain text meets the other requirements\. The `PackedPolicySize` response element indicates by percentage how close the policies and tags for your request are to the upper size limit\.

## [AssumeRoleWithWebIdentity](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html)—federation through a web\-based identity provider<a name="api_assumerolewithwebidentity"></a>

The `AssumeRoleWithWebIdentity` API operation returns a set of temporary security credentials for federated users who are authenticated through a public identity provider\. Examples of public identity providers include Login with Amazon, Facebook, Google, or any OpenID Connect \(OIDC\)\-compatible identity provider\. This operation is useful for creating mobile applications or client\-based web applications that require access to AWS\. Using this operation means that your users do not need their own AWS or IAM identities\. For more information, see [About web identity federation](id_roles_providers_oidc.md)\.

Instead of directly calling `AssumeRoleWithWebIdentity`, we recommend that you use Amazon Cognito and the Amazon Cognito credentials provider with the AWS SDKs for mobile development\. For more information, see the following: 
+ [Amazon Cognito Identity](https://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html) in the *AWS Mobile SDK for Android Developer Guide*
+ [Amazon Cognito Identity](https://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html) in the *AWS Mobile SDK for iOS Developer Guide*

If you are not using Amazon Cognito, you call the `AssumeRoleWithWebIdentity` action of AWS STS\. This is an unsigned call, meaning that the app does not need to have access to any AWS security credentials to make the call\. When you make this call, you pass the following information:
+ The Amazon Resource Name \(ARN\) of the role that the app should assume\. If your app supports multiple ways for users to sign in, you must define multiple roles, one per identity provider\. The call to `AssumeRoleWithWebIdentity` should include the ARN of the role that is specific to the provider through which the user signed in\. 
+ The token that the app gets from the IdP after the app authenticates the user\.
+ You can configure your IdP to pass attributes into your token as [session tags](id_session-tags.md)\.
+ \(Optional\) Duration, which specifies the duration of the temporary security credentials\. Use the `DurationSeconds` parameter to specify the duration of the role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\. If you do not pass this parameter, the temporary credentials expire in one hour\. The `DurationSeconds` parameter from this API is separate from the `SessionDuration` HTTP parameter that you use to specify the duration of a console session\. Use the `SessionDuration` HTTP parameter in the request to the federation endpoint for a console sign\-in token\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.
+ Role session name, which is a string value that you can use to identify the session\. For security purposes, administrators can view this field in [AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) to learn who performed an action in AWS\. Your administrator might require that you provide a specific value for the session name when you assume the role\. For more information, see [`aws:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname)\.
+ \(Optional\) Inline or managed session policies\. These policies limit the permissions from the role's identity\-based policy that are assigned to the role session\. The resulting session's permissions are the intersection of the role's identity\-based policies and the session policies\. Session policies cannot be used to grant more permissions than those allowed by the identity\-based policy of the role that is being assumed\. For more information about role session permissions, see [Session policies](access_policies.md#policies_session)\.
**Note**  
A call to `AssumeRoleWithWebIdentity` is not signed \(encrypted\)\. Therefore, you should only include optional session policies if the request is transmitted through a trusted intermediary\. In this case, someone could alter the policy to remove the restrictions\.

When you call `AssumeRoleWithWebIdentity`, AWS verifies the authenticity of the token\. For example, depending on the provider, AWS might make a call to the provider and include the token that the app has passed\. Assuming that the identity provider validates the token, AWS returns the following information to you: 
+ A set of temporary security credentials\. These consist of an access key ID, a secret access key, and a session token\. 
+ The role ID and the ARN of the assumed role\. 
+ A `SubjectFromWebIdentityToken` value that contains the unique user ID\.

When you have the temporary security credentials, you can use them to make AWS API calls\. This is the same process as making an AWS API call with long\-term security credentials\. The difference is that you must include the session token, which lets AWS verify that the temporary security credentials are valid\.

Your app should cache the credentials\. As noted, by default the credentials expire after an hour\. If you are not using the [AmazonSTSCredentialsProvider](http://aws.amazon.com/blogs/mobile/using-the-amazoncredentialsprovider-protocol-in-the-aws-sdk-for-ios/) operation in the AWS SDK, it's up to you and your app to call `AssumeRoleWithWebIdentity` again\. Call this operation to get a new set of temporary security credentials before the old ones expire\.

## [AssumeRoleWithSAML](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html)—federation through an enterprise Identity Provider compatible with SAML 2\.0<a name="api_assumerolewithsaml"></a>

The `AssumeRoleWithSAML` API operation returns a set of temporary security credentials for federated users who are authenticated by your organization's existing identity system\. The users must also use [SAML](https://www.oasis-open.org/standards#samlv2.0) 2\.0 \(Security Assertion Markup Language\) to pass authentication and authorization information to AWS\. This API operation is useful in organizations that have integrated their identity systems \(such as Windows Active Directory or OpenLDAP\) with software that can produce SAML assertions\. Such an integration provides information about user identity and permissions \(such as Active Directory Federation Services or Shibboleth\)\. For more information, see [About SAML 2\.0\-based federation](id_roles_providers_saml.md)\.

This is an unsigned call, which means that the app does not need to have access to any AWS security credentials in order to make the call\. When you make this call, you pass the following information:
+ The Amazon Resource Name \(ARN\) of the role that the app should assume\. 
+ The ARN of the SAML provider created in IAM that describes the identity provider\.
+ The SAML assertion, encoded in base64, that was provided by the SAML identity provider in its authentication response to the sign\-in request from your app\.
+ You can configure your IdP to pass attributes into your SAML assertion as [session tags](id_session-tags.md)\.
+ \(Optional\) Duration, which specifies the duration of the temporary security credentials\. Use the `DurationSeconds` parameter to specify the duration of the role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\. If you do not pass this parameter, the temporary credentials expire in one hour\. The `DurationSeconds` parameter from this API is separate from the `SessionDuration` HTTP parameter that you use to specify the duration of a console session\. Use the `SessionDuration` HTTP parameter in the request to the federation endpoint for a console sign\-in token\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.
+ \(Optional\) Inline or managed session policies\. These policies limit the permissions from the role's identity\-based policy that are assigned to the role session\. The resulting session's permissions are the intersection of the role's identity\-based policies and the session policies\. Session policies cannot be used to grant more permissions than those allowed by the identity\-based policy of the role that is being assumed\. For more information about role session permissions, see [Session policies](access_policies.md#policies_session)\.

When you call `AssumeRoleWithSAML`, AWS verifies the authenticity of the SAML assertion\. Assuming that the identity provider validates the assertion, AWS returns the following information to you: 
+ A set of temporary security credentials\. These consist of an access key ID, a secret access key, and a session token\. 
+ The role ID and the ARN of the assumed role\. 
+ An `Audience` value that contains the value of the `Recipient` attribute of the `SubjectConfirmationData` element of the SAML assertion\.
+ An `Issuer` value that contains the value of the `Issuer` element of the SAML assertion\.
+ A `NameQualifier` element that contains a hash value built from the `Issuer` value, the AWS account ID, and the friendly name of the SAML provider\. When combined with the `Subject` element, they can uniquely identify the federated user\.
+ A `Subject` element that contains the value of the `NameID` element in the `Subject` element of the SAML assertion\.
+ A `SubjectType` element that indicates the format of the `Subject` element\. The value can be `persistent`, `transient`, or the full `Format` URI from the `Subject` and `NameID` elements used in your SAML assertion\. For information about the `NameID` element's `Format` attribute, see [Configuring SAML assertions for the authentication response](id_roles_providers_create_saml_assertions.md)\. 

When you have the temporary security credentials, you can use them to make AWS API calls\. This is the same process as making an AWS API call with long\-term security credentials\. The difference is that you must include the session token, which lets AWS verify that the temporary security credentials are valid\.

Your app should cache the credentials\. By default the credentials expire after an hour\. If you are not using the [AmazonSTSCredentialsProvider](http://aws.amazon.com/blogs/mobile/using-the-amazoncredentialsprovider-protocol-in-the-aws-sdk-for-ios) action in the AWS SDK, it's up to you and your app to call `AssumeRoleWithSAML` again\. Call this operation to get a new set of temporary security credentials before the old ones expire\.

## [GetFederationToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)—federation through a custom identity broker<a name="api_getfederationtoken"></a>

The `GetFederationToken` API operation returns a set of temporary security credentials for federated users\. This API differs from `AssumeRole` in that the default expiration period is substantially longer \(12 hours instead of one hour\)\. Additionally, you can use the `DurationSeconds` parameter to specify a duration for the temporary security credentials to remain valid\. The resulting credentials are valid for the specified duration, between 900 seconds \(15 minutes\) to 129,600 seconds \(36 hours\)\.The longer expiration period can help reduce the number of calls to AWS because you do not need to get new credentials as often\. For more information, see [Requesting temporary security credentials](#id_credentials_temp_request)\.

When you make this request, you use the credentials of a specific IAM user\. The permissions for the temporary security credentials are determined by the session policies that you pass when you call `GetFederationToken`\. The resulting session permissions are the intersection of the IAM user policies and the session policies that you pass\. Session policies cannot be used to grant more permissions than those allowed by the identity\-based policy of the IAM user that is requesting federation\. For more information about role session permissions, see [Session policies](access_policies.md#policies_session)\.

When you use the temporary credentials that are returned by the `GetFederationToken` operation, the session's principal tags include the user's tags and the passed session tags\. For more information about session tags, see [Passing session tags in AWS STS](id_session-tags.md)\.

The `GetFederationToken` call returns temporary security credentials that consist of the security token, access key, secret key, and expiration\. You can use `GetFederationToken` if you want to manage permissions inside your organization \(for example, using the proxy application to assign permissions\)\. To view a sample application that uses `GetFederationToken`, go to [Identity Federation Sample Application for an Active Directory Use Case](https://aws.amazon.com/code/1288653099190193) in the *AWS Sample Code & Libraries*\.

The following example shows a sample request and response that uses `GetFederationToken`\. This example request federates the calling user for the specified duration with the [session policy](access_policies.md#policies_session) ARN and [session tags](id_session-tags.md)\. The resulting session is named `Jane-session`\.

**Example request**  

```
https://sts.amazonaws.com/
?Version=2011-06-15
&Action=GetFederationToken
&Name=Jane-session
&PolicyArns.member.1.arn==arn%3Aaws%3Aiam%3A%3A123456789012%3Apolicy%2FRole1policy
&DurationSeconds=1800
&Tags.member.1.Key=Project
&Tags.member.1.Value=Pegasus
&Tags.member.2.Key=Cost-Center
&Tags.member.2.Value=12345
&AUTHPARAMS
```

The policy ARN shown in the preceding example includes the following URL\-encoded ARN: 

`arn:aws:iam::123456789012:policy/Role1policy`

Also, note that the `&AUTHPARAMS` parameter in the example is meant as a placeholder for the authentication information\. This is the *signature*, which you must include with AWS HTTP API requests\. We recommend using the [AWS SDKs](https://aws.amazon.com/tools/) to create API requests, and one benefit of doing so is that the SDKs handle request signing for you\. If you must create and sign API requests manually, go to [Signing AWS Requests By Using Signature Version 4](https://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html) in the *Amazon Web Services General Reference* to learn how to sign a request\.

In addition to the temporary security credentials, the response includes the Amazon Resource Name \(ARN\) for the federated user and the expiration time of the credentials\.

**Example response**  

```
<GetFederationTokenResponse xmlns="https://sts.amazonaws.com/doc/2011-06-15/">
<GetFederationTokenResult>
<Credentials>
  <SessionToken>
   AQoDYXdzEPT//////////wEXAMPLEtc764bNrC9SAPBSM22wDOk4x4HIZ8j4FZTwdQW
   LWsKWHGBuFqwAeMicRXmxfpSPfIeoIYRqTflfKD8YUuwthAx7mSEI/qkPpKPi/kMcGd
   QrmGdeehM4IC1NtBmUpp2wUE8phUZampKsburEDy0KPkyQDYwT7WZ0wq5VSXDvp75YU
   9HFvlRd8Tx6q6fE8YQcHNVXAkiY9q6d+xo0rKwT38xVqr7ZD0u0iPPkUL64lIZbqBAz
   +scqKmlzm8FDrypNC9Yjc8fPOLn9FX9KSYvKTr4rvx3iSIlTJabIQwj2ICCEXAMPLE==
  </SessionToken>
  <SecretAccessKey>
  wJalrXUtnFEMI/K7MDENG/bPxRfiCYzEXAMPLEKEY
  </SecretAccessKey>
  <Expiration>2019-04-15T23:28:33.359Z</Expiration>
  <AccessKeyId>AKIAIOSFODNN7EXAMPLE;</AccessKeyId>
</Credentials>
<FederatedUser>
  <Arn>arn:aws:sts::123456789012:federated-user/Jean</Arn>
  <FederatedUserId>123456789012:Jean</FederatedUserId>
</FederatedUser>
<PackedPolicySize>4</PackedPolicySize>
</GetFederationTokenResult>
<ResponseMetadata>
<RequestId>c6104cbe-af31-11e0-8154-cbc7ccf896c7</RequestId>
</ResponseMetadata>
</GetFederationTokenResponse>
```

**Note**  
An AWS conversion compresses the passed session policies and session tags into a packed binary format that has a separate limit\. Your request can fail for this limit even if your plain text meets the other requirements\. The `PackedPolicySize` response element indicates by percentage how close the policies and tags for your request are to the upper size limit\.

AWS recommends that you grant permissions at the resource level \(for example, you attach a resource\-based policy to an Amazon S3 bucket\), you can omit the `Policy` parameter\. However, if you do not include a policy for the federated user, the temporary security credentials will not grant any permissions\. In this case, you *must* use resource policies to grant the federated user access to your AWS resources\.

For example, assume your AWS account number is 111122223333, and you have an Amazon S3 bucket that you want to allow Susan to access\. Susan's temporary security credentials don't include a policy for the bucket\. In that case, you would need to ensure that the bucket has a policy with an ARN that matches Susan's ARN, such as `arn:aws:sts::111122223333:federated-user/Susan`\. 

## [GetSessionToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html)—temporary credentials for users in untrusted environments<a name="api_getsessiontoken"></a>

The `GetSessionToken` API operation returns a set of temporary security credentials to an existing IAM user\. This is useful for providing enhanced security, such as allowing AWS requests only when MFA is enabled for the IAM user\. Because the credentials are temporary, they provide enhanced security when you have an IAM user who accesses your resources through a less secure environment\. Examples of less secure environments include a mobile device or web browser\. For more information, see [Requesting temporary security credentials](#id_credentials_temp_request) or [GetSessionToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html) in the *AWS Security Token Service API Reference*\.

By default, temporary security credentials for an IAM user are valid for a maximum of 12 hours\. But you can request a duration as short as 15 minutes or as long as 36 hours using the `DurationSeconds` parameter\. For security reasons, a token for an AWS account root user is restricted to a duration of one hour\. 

`GetSessionToken` returns temporary security credentials consisting of a security token, an access key ID, and a secret access key\. The following example shows a sample request and response using `GetSessionToken`\. The response also includes the expiration time of the temporary security credentials\. 

**Example request**  

```
https://sts.amazonaws.com/
?Version=2011-06-15
&Action=GetSessionToken
&DurationSeconds=1800
&AUTHPARAMS
```

The `AUTHPARAMS` parameter in the example is a placeholder for your *signature*\. A signature is the authentication information that you must include with AWS HTTP API requests\. We recommend using the [AWS SDKs](https://aws.amazon.com/tools/) to create API requests, and one benefit of doing so is that the SDKs handle request signing for you\. If you must create and sign API requests manually, go to [Signing AWS Requests By Using Signature Version 4](https://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html) in the *Amazon Web Services General Reference* to learn how to sign a request\.

**Example response**  

```
<GetSessionTokenResponse xmlns="https://sts.amazonaws.com/doc/2011-06-15/">
<GetSessionTokenResult>
<Credentials>
  <SessionToken>
   AQoEXAMPLEH4aoAH0gNCAPyJxz4BlCFFxWNE1OPTgk5TthT+FvwqnKwRcOIfrRh3c/L
   To6UDdyJwOOvEVPvLXCrrrUtdnniCEXAMPLE/IvU1dYUg2RVAJBanLiHb4IgRmpRV3z
   rkuWJOgQs8IZZaIv2BXIa2R4OlgkBN9bkUDNCJiBeb/AXlzBBko7b15fjrBs2+cTQtp
   Z3CYWFXG8C5zqx37wnOE49mRl/+OtkIKGO7fAE
  </SessionToken>
  <SecretAccessKey>
  wJalrXUtnFEMI/K7MDENG/bPxRfiCYzEXAMPLEKEY
  </SecretAccessKey>
  <Expiration>2011-07-11T19:55:29.611Z</Expiration>
  <AccessKeyId>AKIAIOSFODNN7EXAMPLE</AccessKeyId>
</Credentials>
</GetSessionTokenResult>
<ResponseMetadata>
<RequestId>58c5dbae-abef-11e0-8cfe-09039844ac7d</RequestId>
</ResponseMetadata>
</GetSessionTokenResponse>
```

Optionally, the `GetSessionToken` request can include `SerialNumber` and `TokenCode` values for AWS multi\-factor authentication \(MFA\) verification\. If the provided values are valid, AWS STS provides temporary security credentials that include the state of MFA authentication\. The temporary security credentials can then be used to access the MFA\-protected API operations or AWS websites for as long as the MFA authentication is valid\. 

The following example shows a `GetSessionToken` request that includes an MFA verification code and device serial number\. 

```
https://sts.amazonaws.com/
?Version=2011-06-15
&Action=GetSessionToken
&DurationSeconds=7200
&SerialNumber=YourMFADeviceSerialNumber
&TokenCode=123456
&AUTHPARAMS
```

**Note**  
The call to AWS STS can be to the global endpoint or to any of the Regional endpoints that you activate your AWS account\. For more information, see the [AWS STS section of *Regions and Endpoints*](https://docs.aws.amazon.com/general/latest/gr/rande.html#sts_region)\.  
The `AUTHPARAMS` parameter in the example is a placeholder for your *signature*\. A signature is the authentication information that you must include with AWS HTTP API requests\. We recommend using the [AWS SDKs](https://aws.amazon.com/tools/) to create API requests, and one benefit of doing so is that the SDKs handle request signing for you\. If you must create and sign API requests manually, see [Signing AWS Requests By Using Signature Version 4](https://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html) in the *Amazon Web Services General Reference* to learn how to sign a request\.

## Comparing the AWS STS API operations<a name="stsapi_comparison"></a>

The following table compares features of the API operations in AWS STS that return temporary security credentials\. To learn about the different methods you can use to request temporary security credentials by assuming a role, see [Using IAM roles](id_roles_use.md)\. To learn about the different AWS STS API operations that allow you to pass session tags, see [Passing session tags in AWS STS](id_session-tags.md)\.


**Comparing your API options**  

|  **AWS STS API**  |  **Who can call**  |  **Credential lifetime \(min \| max \| default\)**  |  **MFA support**¹  |  **Session policy support**²  |  **Restrictions on resulting temporary credentials**  | 
| --- | --- | --- | --- | --- | --- | 
|  [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html)  | IAM user or IAM role with existing temporary security credentials  | 15 m \| Maximum session duration setting³ \| 1 hr  | Yes  | Yes |  Cannot call `GetFederationToken` or `GetSessionToken`\.  | 
|  [AssumeRoleWithSAML](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html)  | Any user; caller must pass a SAML authentication response that indicates authentication from a known identity provider | 15 m \| Maximum session duration setting³ \| 1 hr  | No | Yes |  Cannot call `GetFederationToken` or `GetSessionToken`\.  | 
|  [AssumeRoleWithWebIdentity](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html)  | Any user; caller must pass a web identity token that indicates authentication from a known identity provider | 15 m \| Maximum session duration setting³ \| 1 hr  | No | Yes |  Cannot call `GetFederationToken` or `GetSessionToken`\.  | 
| [GetFederationToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html) | IAM user or AWS account root user |  IAM user: 15 m \| 36 hr \| 12 hr Root user: 15 m \| 1 hr \| 1 hr  | No  | Yes  |  Cannot call IAM operations using the AWS CLI or AWS API\. Cannot call AWS STS operations except `GetCallerIdentity`\.⁴ SSO to console is allowed\.⁵  | 
| [GetSessionToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html) | IAM user or AWS account root user |  IAM user: 15 m \| 36 hr \| 12 hr Root user: 15 m \| 1 hr \| 1 hr  | Yes  | No  |  Cannot call IAM API operations unless MFA information is included with the request\. Cannot call AWS STS API operations except `AssumeRole` or `GetCallerIdentity`\. SSO to console is not allowed\.⁶  | 

 ¹ **MFA support**\. You can include information about a multi\-factor authentication \(MFA\) device when you call the AssumeRole and GetSessionToken API operations\. This ensures that the temporary security credentials that result from the API call can be used only by users who are authenticated with an MFA device\. For more information, see [Configuring MFA\-protected API access](id_credentials_mfa_configure-api-require.md)\. 

 ² **Session policy support**\. Session policies are policies that you pass as a parameter when you programmatically create a temporary session for a role or federated user\. This policy limits the permissions from the role or user's identity\-based policy that are assigned to the session\. The resulting session's permissions are the intersection of the entity's identity\-based policies and the session policies\. Session policies cannot be used to grant more permissions than those allowed by the identity\-based policy of the role that is being assumed\. For more information about role session permissions, see [Session policies](access_policies.md#policies_session)\.

³ **Maximum session duration setting**\. Use the `DurationSeconds` parameter to specify the duration of your role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\.

⁴ **GetCallerIdentity**\. No permissions are required to perform this operation\. If an administrator adds a policy to your IAM user or role that explicitly denies access to the `sts:GetCallerIdentity` action, you can still perform this operation\. Permissions are not required because the same information is returned when an IAM user or role is denied access\. To view an example response, see [I Am not authorized to perform: iam:DeleteVirtualMFADevice](troubleshoot_general.md#troubleshoot_general_access-denied-delete-mfa)\.

⁵ **Single sign\-on \(SSO\) to the console**\. To support SSO, AWS lets you call a federation endpoint \(`https://signin.aws.amazon.com/federation`\) and pass temporary security credentials\. The endpoint returns a token that you can use to construct a URL that signs a user directly into the console without requiring a password\. For more information, see [Enabling SAML 2\.0 federated users to access the AWS Management Console](id_roles_providers_enable-console-saml.md) and [ How to Enable Cross\-Account Access to the AWS Management Console](http://aws.amazon.com/blogs/security/how-to-enable-cross-account-access-to-the-aws-management-console) in the AWS Security Blog\. 

⁶ After you retrieve your temporary credentials, you can't access the AWS Management Console by passing the credentials to the federation single sign\-on endpoint\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.