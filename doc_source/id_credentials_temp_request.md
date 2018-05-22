# Requesting Temporary Security Credentials<a name="id_credentials_temp_request"></a>

To request temporary security credentials, you can use the AWS STS API actions\. You can use AWS Security Token Service \(AWS STS\) to create and provide trusted users with temporary security credentials that can control access to your AWS resources\. For more information about AWS STS, see [Temporary Security Credentials](id_credentials_temp.md)\. To learn about the different methods that you can use to request temporary security credentials by assuming a role, see [Using IAM Roles](id_roles_use.md)\.

To call the API operations, you can use one of the [AWS SDKs](http://aws.amazon.com/tools/), which are available for a variety of programming languages and environments, including Java, \.NET, Python, Ruby, Android, and iOS\. The SDKs take care of tasks such as cryptographically signing your requests, retrying requests if necessary, and handling error responses\. You can also use the AWS STS Query API, which is described in the [AWS Security Token Service API Reference](http://docs.aws.amazon.com/STS/latest/APIReference/)\. Finally, two command line tools support the AWS STS commands: the [AWS Command Line Interface](https://aws.amazon.com/documentation/cli), and the [AWS Tools for Windows PowerShell](https://aws.amazon.com/documentation/powershell)\. 

The AWS STS API actions return temporary security credentials that consist of an access key and a session token\. The access key consists of an access key ID and a secret key\. Users \(or an application that the user runs\) can use these credentials to access your resources\. When the credentials are created, they are associated with an IAM access control policy that limits what the user can do when using the credentials\. For more information, see [Using Temporary Security Credentials to Request Access to AWS Resources](id_credentials_temp_use-resources.md)\. 

**Important**  
Although temporary security credentials are short lived, users who have temporary access can make lasting changes to your AWS resources\. For example, if a user with temporary access launches an Amazon EC2 instance, the instance can continue to run and incur charges to your AWS account\. The instance can continue running even after the user's temporary security credentials expire\.

**Note**  
The size of the security token that STS API operations return is not fixed\. We strongly recommend that you make no assumptions about the maximum size\. As of this writing, the typical size is less than 4096 bytes, but that can vary\. Also, future updates to AWS might require larger sizes\.

## Using AWS STS with AWS Regions<a name="using_sts_regions"></a>

You can send AWS STS API calls either to a global endpoint or to one of the regional endpoints\. If you choose an endpoint closer to you, you can reduce latency and improve the performance of your API calls\. You also can choose to direct your calls to an alternative regional endpoint if you can no longer communicate with the original endpoint\. If you are using one of the various AWS SDKs, then use that SDK's method to select a region before you make the API call\. If you are manually constructing HTTP API requests, then you must direct the request to the correct endpoint yourself\. For more information, see the [AWS STS section of *Regions and Endpoints*](http://docs.aws.amazon.com/general/latest/gr/rande.html#sts_region) and [Activating and Deactivating AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\.

The following are the API operations that you can use to acquire temporary credentials for use in your AWS environment and applications\.

## [AssumeRole](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html)—Cross\-Account Delegation and Federation Through a Custom Identity Broker<a name="api_assumerole"></a>

This API action is useful for allowing existing IAM users to access AWS resources that they don't already have access to, such as resources in another AWS account\. It is also useful for existing IAM users as a means to temporarily gain privileged access—for example, to provide multi\-factor authentication \(MFA\)\. You must call this API using existing IAM user credentials\. For more information, see [Creating a Role to Delegate Permissions to an IAM User](id_roles_create_for-user.md) and [Configuring MFA\-Protected API Access](id_credentials_mfa_configure-api-require.md)\.

This call must be made using valid AWS security credentials\. When you make this call, you pass the following information:
+ The Amazon Resource Name \(ARN\) of the role that the app should assume\. 
+ The duration, which specifies the duration of the temporary security credentials\. Use the `DurationSeconds` parameter to specify the duration of the role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the Maximum Session Duration Setting for a Role](id_roles_use.md#id_roles_use_view-role-max-session)\. If you do not pass this parameter, the temporary credentials expire in one hour\. The `DurationSeconds` parameter from this API is separate from the `SessionDuration` HTTP parameter that you use to specify the duration of a console session\. Use the `SessionDuration` HTTP parameter in the request to the federation endpoint for a console sign\-in token\. For more information, see [Creating a URL that Enables Federated Users to Access the AWS Management Console \(Custom Federation Broker\)](id_roles_providers_enable-console-custom-url.md)\.
+ A role session name, which is a string value that you can use to identify the session\. This value can be captured and logged by CloudTrail to help you distinguish between your role users during an audit\.
+ Optionally, a policy \(in JSON format\)\. This policy is combined with the policy associated with the role\. If specified, the permissions are the intersection of those granted to the role and those granted by this policy\. You can use this policy to you further restrict the access permissions that are associated with the temporary credentials, beyond the restrictions already established by the role permission policy\. Note that this policy cannot be used to elevate permissions beyond what the assumed role is allowed to access\.
+ If configured to use multi\-factor authentication \(MFA\), then you include the identifier for an MFA device and the one\-time code provided by that device\.
+ An optional ExternalID value that can be used when delegating access to your account to a third party\. This value helps ensure that only the specified third party can access the role\. For more information, see [How to Use an External ID When Granting Access to Your AWS Resources to a Third Party](id_roles_create_for-user_externalid.md)\.

The following example shows a sample request and response using `AssumeRole`\. In this example, the request includes the name for the session named Bob\. The `Policy` parameter includes a JSON document that specifies that the resulting credentials have permissions to access only Amazon S3\.

**Example Request**  

```
https://sts.amazonaws.com/
?Version=2011-06-15
&Action=AssumeRole
&RoleSessionName=Bob
&RoleArn=arn:aws::iam::123456789012:role/demo
&Policy=%7B%22Version%22%3A%222012-10-17%22%2C%22Statement%22%3A%5B%7B%22Sid%22%3A%20%22Stmt1%22%2C%22Effect%22%3A%20%22Allow%22%2C%22Action%22%3A%20%22s3%3A*%22%2C%22Resource%22%3A%20%22*%22%7D%5D%7D
&DurationSeconds=1800
&ExternalId=123ABC
&AUTHPARAMS
```

**Note**  
The policy value shown in the preceding example is the URL\-encoded version of the following policy:  
`{"Version":"2012-10-17","Statement":[{"Sid":"Stmt1","Effect":"Allow","Action":"s3:*","Resource":"*"}]}`  
Also, note that the `AUTHPARAMS` parameter in the example is meant as a placeholder for the authentication information—that is, the *signature*—that you must include with AWS HTTP API requests\. We recommend using the [AWS SDKs](https://aws.amazon.com/tools/) to create API requests, and one benefit of doing so is that the SDKs handle request signing for you\. If you must create and sign API requests manually, go to [Signing AWS Requests By Using Signature Version 4](http://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html) in the *Amazon Web Services General Reference* to learn how to sign a request\.

In addition to the temporary security credentials, the response includes the Amazon Resource Name \(ARN\) for the federated user and the expiration time of the credentials\.

**Example Response**  

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
  <Expiration>2011-07-15T23:28:33.359Z</Expiration>
  <AccessKeyId>AKIAIOSFODNN7EXAMPLE</AccessKeyId>
</Credentials>
<AssumedRoleUser>
  <Arn>arn:aws:sts::123456789012:assumed-role/demo/Bob</Arn>
  <AssumedRoleId>ARO123EXAMPLE123:Bob</AssumedRoleId>
</AssumedRoleUser>
<PackedPolicySize>6</PackedPolicySize>
</AssumeRoleResult>
<ResponseMetadata>
<RequestId>c6104cbe-af31-11e0-8154-cbc7ccf896c7</RequestId>
</ResponseMetadata>
</AssumeRoleResponse>
```

**Note**  
`AssumeRole` stores the policy in a packed format\. `AssumeRole` returns the size as a percentage of the maximum size allowed so you can adjust the calling parameters\. For more information about the size constraints on the policy, go to [AssumeRole](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) in the *AWS Security Token Service API Reference*\. 

## [AssumeRoleWithWebIdentity](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html)—Federation Through a Web\-based Identity Provider<a name="api_assumerolewithwebidentity"></a>

This API operation returns a set of temporary security credentials for federated users who are authenticated through a public identity provider\. Examples of public identity providers include Login with Amazon, Facebook, Google, or any OpenID Connect \(OIDC\)\-compatible identity provider\. This API is useful for creating mobile applications or client\-based web applications that require access to AWS in which users do not have their own AWS or IAM identities\. For more information, see [About Web Identity Federation](id_roles_providers_oidc.md)\.

**Note**  
Instead of directly calling `AssumeRoleWithWebIdentity`, we recommend that you use Amazon Cognito and the Amazon Cognito credentials provider with the AWS SDKs for mobile development\. For more information, see the following:   
[Amazon Cognito Identity](http://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html) in the *AWS Mobile SDK for Android Developer Guide*
[Amazon Cognito Identity](http://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html) in the *AWS Mobile SDK for iOS Developer Guide*

If you are not using Amazon Cognito, you call the `AssumeRoleWithWebIdentity` action of AWS STS\. This is an unsigned call, meaning that the app does not need to have access to any AWS security credentials in order to make the call\. When you make this call, you pass the following information:
+ The Amazon Resource Name \(ARN\) of the role that the app should assume\. If your app supports multiple ways for users to sign in, you must define multiple roles, one per identity provider\. The call to `AssumeRoleWithWebIdentity` should include the ARN of the role that is specific to the provider through which the user signed in\. 
+ The token that the app gets from the IdP after the app authenticates the user\.
+ The duration, which specifies the duration of the temporary security credentials\. Use the `DurationSeconds` parameter to specify the duration of the role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the Maximum Session Duration Setting for a Role](id_roles_use.md#id_roles_use_view-role-max-session)\. If you do not pass this parameter, the temporary credentials expire in one hour\. The `DurationSeconds` parameter from this API is separate from the `SessionDuration` HTTP parameter that you use to specify the duration of a console session\. Use the `SessionDuration` HTTP parameter in the request to the federation endpoint for a console sign\-in token\. For more information, see [Creating a URL that Enables Federated Users to Access the AWS Management Console \(Custom Federation Broker\)](id_roles_providers_enable-console-custom-url.md)\.
+ A role session name, which is a string value that you can use to identify the session\. This value can be captured and logged by CloudTrail to help you distinguish between your role users during an audit\.
+ Optionally, a policy \(in JSON format\)\. This policy is combined with the policy associated with the role\. If specified, the permissions are the intersection of those granted to the role and those granted by this policy\. You can use this policy to you further restrict the access permissions that are associated with the temporary credentials, beyond the restrictions already established by the role permission policy\. Note that this policy cannot be used to elevate privileges beyond what the assumed role is allowed to access\.
**Note**  
A call to `AssumeRoleWithWebIdentity` is not signed \(encrypted\)\. Therefore, you should only include this optional policy if the request is not being transmitted through an untrusted intermediary\. In this case, someone could alter the policy to remove the restrictions\.

When you call `AssumeRoleWithWebIdentity`, AWS verifies the authenticity of the token\. For example, depending on the provider, AWS might make a call to the provider and include the token that the app has passed\. Assuming that the identity provider validates the token, AWS returns the following information to you: 
+ A set of temporary security credentials\. These consist of an access key ID, a secret access key, and a session token\. 
+ The role ID and the ARN of the assumed role\. 
+ A `SubjectFromWebIdentityToken` value that contains the unique user ID\.

When you have the temporary security credentials, you can use them to make AWS API calls\. This is the same process as making an AWS API call with long\-term security credentials, except that you must include the session token, which lets AWS verify that the temporary security credentials are valid\.

Your app should cache the credentials\. As noted, by default the credentials expire after an hour\. If you are not using the [AmazonSTSCredentialsProvider](http://aws.amazon.com/blogs/mobile/using-the-amazoncredentialsprovider-protocol-in-the-aws-sdk-for-ios/) operation in the AWS SDK, it's up to you and your app to call `AssumeRoleWithWebIdentity` again\. Call this operation to get a new set of temporary security credentials before the old ones expire\.

## [AssumeRoleWithSAML](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html)—Federation Through an Enterprise Identity Provider Compatible with SAML 2\.0<a name="api_assumerolewithsaml"></a>

This API returns a set of temporary security credentials for federated users who are authenticated by your organization's existing identity system\. The users must also use [SAML](https://www.oasis-open.org/standards#samlv2.0) 2\.0 \(Security Assertion Markup Language\) to pass authentication and authorization information to AWS\. This API operation is useful in organizations that have integrated their identity systems \(such as Windows Active Directory or OpenLDAP\) with software that can produce SAML assertions\. Such an integration provides information about user identity and permissions \(such as Active Directory Federation Services or Shibboleth\)\. For more information, see [About SAML 2\.0\-based Federation](id_roles_providers_saml.md)\.

This is an unsigned call, which means that the app does not need to have access to any AWS security credentials in order to make the call\. When you make this call, you pass the following information:
+ The Amazon Resource Name \(ARN\) of the role that the app should assume\. 
+ The ARN of the SAML provider created in IAM that describes the identity provider\.
+ The SAML assertion, encoded in base\-64, that was provided by the SAML identity provider in its authentication response to the sign\-in request from your app\.
+ The duration, which specifies the duration of the temporary security credentials\. Use the `DurationSeconds` parameter to specify the duration of the role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the Maximum Session Duration Setting for a Role](id_roles_use.md#id_roles_use_view-role-max-session)\. If you do not pass this parameter, the temporary credentials expire in one hour\. The `DurationSeconds` parameter from this API is separate from the `SessionDuration` HTTP parameter that you use to specify the duration of a console session\. Use the `SessionDuration` HTTP parameter in the request to the federation endpoint for a console sign\-in token\. For more information, see [Creating a URL that Enables Federated Users to Access the AWS Management Console \(Custom Federation Broker\)](id_roles_providers_enable-console-custom-url.md)\.
+ A policy \(in JSON format\)\. This policy is combined with the policy associated with the role\. If specified, the permissions are the intersection of those granted to the role and those granted by this policy\. You can use this policy to further restrict the access permissions that are associated with the temporary credentials, beyond the restrictions already established by the role permission policy\. Note that this policy cannot be used to elevate permissions beyond what the assumed role is allowed to access\.

When you call `AssumeRoleWithSAML`, AWS verifies the authenticity of the SAML assertion\. Assuming that the identity provider validates the assertion, AWS returns the following information to you: 
+ A set of temporary security credentials\. These consist of an access key ID, a secret access key, and a session token\. 
+ The role ID and the ARN of the assumed role\. 
+ An `Audience` value that contains the value of the `Recipient` attribute of the `SubjectConfirmationData` element of the SAML assertion\.
+ An `Issuer` value that contains the value of the `Issuer` element of the SAML assertion\.
+ A `NameQualifier` element that contains a hash value built from the `Issuer` value, the AWS account ID, and the friendly name of the SAML provider\. When combined with the `Subject` element, they can uniquely identify the federated user\.
+ A `Subject` element that contains the value of the `NameID` element in the `Subject` element of the SAML assertion\.
+ A `SubjectType` element that indicates the format of the `Subject` element\. The value can be `persistent`, `transient`, or the full `Format` URI from the `Subject` and `NameID` elements used in your SAML assertion\. For information about the `NameID` element's `Format` attribute, see [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\. 

When you have the temporary security credentials, you can use them to make AWS API calls\. This is the same process as making an AWS API call with long\-term security credentials, except that you must include the session token, which lets AWS verify that the temporary security credentials are valid\.

Your app should cache the credentials\. By default the credentials expire after an hour\. If you are not using the [AmazonSTSCredentialsProvider](http://aws.amazon.com/blogs/mobile/using-the-amazoncredentialsprovider-protocol-in-the-aws-sdk-for-ios) action in the AWS SDK, it's up to you and your app to call `AssumeRoleWithSAML` again\. Call this operation to get a new set of temporary security credentials before the old ones expire\.

## [GetFederationToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)—Federation Through a Custom Identity Broker<a name="api_getfederationtoken"></a>

This API returns a set of temporary security credentials for federated users\. This API differs from `AssumeRole` in that the default expiration period is substantially longer \(12 hours instead of one hour\)\. Additionally, you can use the `DurationSeconds` parameter to specify a duration for the temporary security credentials to remain valid\. The resulting credentials are valid for the specified duration, between 900 seconds \(15 minutes\) to 129,600 seconds \(36 hours\)\.The longer expiration period can help reduce the number of calls to AWS because you do not need to get new credentials as often\. For more information, see [Requesting Temporary Security Credentials](#id_credentials_temp_request)\.

When you make a request to get temporary security credentials for a federated user, you use the credentials of a specific user identity \(an IAM user\) to make the request\. The permissions for the temporary security credentials are determined by the IAM policy that you pass when you call `GetFederationToken`\. 

The `GetFederationToken` call returns temporary security credentials that consist of the security token, access key, secret key, and expiration\. You can use `GetFederationToken` if you want to manage permissions inside your organization \(for example, using the proxy application to assign permissions\)\. To view a sample application that uses `GetFederationToken`, go to [Identity Federation Sample Application for an Active Directory Use Case](https://aws.amazon.com/code/1288653099190193) in the *AWS Sample Code & Libraries*\.

The following example shows a sample request and response that uses `GetFederationToken`\. In this example, the request includes the name for a federated user named Jean\. The `Policy` parameter includes a JSON document that specifies that the resulting credentials have permissions to access only Amazon S3\. In addition to the temporary security credentials, the response includes the Amazon Resource Name \(ARN\) for the federated user and the expiration time of the credentials\.

**Example Request**  

```
https://sts.amazonaws.com/
?Version=2011-06-15
&Action=GetFederationToken
&Name=Jean
&Policy=%7B%22Version%22%3A%222012-10-17%22%2C%22Statement%22%3A%5B%7B%22Sid%22%3A%22Stmt1%22%2C%22Effect%22%3A%22Allow%22%2C%22Action%22%3A%22s3%3A*%22%2C%22Resource%22%3A%22*%22%7D%5D%7D
&DurationSeconds=1800
&AUTHPARAMS
```

**Note**  
The policy value shown in the preceding example is the URL\-encoded version of this policy:   
`{"Version":"2012-10-17","Statement":[{"Sid":"Stmt1","Effect":"Allow","Action":"s3:*","Resource":"*"}]}`  
Also, note that the `&AUTHPARAMS` parameter in the example is meant as a placeholder for the authentication information—that is, the *signature*—that you must include with AWS HTTP API requests\. We recommend using the [AWS SDKs](https://aws.amazon.com/tools/) to create API requests, and one benefit of doing so is that the SDKs handle request signing for you\. If you must create and sign API requests manually, go to [Signing AWS Requests By Using Signature Version 4](http://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html) in the *Amazon Web Services General Reference* to learn how to sign a request\.

**Example Response**  

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
  <Expiration>2011-07-15T23:28:33.359Z</Expiration>
  <AccessKeyId>AKIAIOSFODNN7EXAMPLE;</AccessKeyId>
</Credentials>
<FederatedUser>
  <Arn>arn:aws:sts::123456789012:federated-user/Jean</Arn>
  <FederatedUserId>123456789012:Jean</FederatedUserId>
</FederatedUser>
<PackedPolicySize>6</PackedPolicySize>
</GetFederationTokenResult>
<ResponseMetadata>
<RequestId>c6104cbe-af31-11e0-8154-cbc7ccf896c7</RequestId>
</ResponseMetadata>
</GetFederationTokenResponse>
```

**Note**  
`GetFederationToken` stores the policy in a packed format\. The operation returns the size as a percentage of the maximum size allowed so that you can adjust the calling parameters\. For more information about size constraints on the policy, go to [GetFederationToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html) in the *AWS Security Token Service API Reference*\. 

If you prefer to grant permissions at the resource level \(for example, you attach a policy to an Amazon S3 bucket\), you can omit the `Policy` parameter\. However, if you do not include a policy for the federated user, the temporary security credentials will not grant any permissions\. In this case, you *must* use resource policies to grant the federated user access to your AWS resources\.

For example, assume your AWS account number is 111122223333, and you have an Amazon S3 bucket that you want to allow Susan to access\. Susan's temporary security credentials don't include a policy for the bucket\. In that case, you would need to ensure that the bucket has a policy with an ARN that matches Susan's ARN, such as `arn:aws:sts::111122223333:federated-user/Susan`\. 

## [GetSessionToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html)—Temporary Credentials for Users in Untrusted Environments<a name="api_getsessiontoken"></a>

This API returns a set of temporary security credentials to an existing IAM user\. It is useful for providing enhanced security, for example, to restrict AWS requests to only when MFA is enabled for the IAM user\. Because the credentials are temporary, they provide enhanced security when you have an IAM user who accesses your resources through a less secure environment, such as a mobile device or web browser\. For more information, see [Requesting Temporary Security Credentials](#id_credentials_temp_request) or [GetSessionToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html) in the *AWS Security Token Service API Reference*\.

By default, temporary security credentials for an IAM user are valid for a maximum of 12 hours\. But you can request a duration as short as 15 minutes or as long as 36 hours using the `DurationSeconds` parameter\. For security reasons, a token for an AWS account root user is restricted to a duration of one hour\. 

`GetSessionToken` returns temporary security credentials consisting of a security token, an access key ID, and a secret access key\. The following example shows a sample request and response using `GetSessionToken`\. The response also includes the expiration time of the temporary security credentials\. 

**Example Request**  

```
https://sts.amazonaws.com/
?Version=2011-06-15
&Action=GetSessionToken
&DurationSeconds=1800
&AUTHPARAMS
```

**Note**  
The `&AUTHPARAMS` parameter in the preceding example is meant as a placeholder for the authentication information—that is, the *signature*—that you must include with AWS HTTP API requests\. We recommend using the [AWS SDKs](https://aws.amazon.com/tools/) to create API requests, and one benefit of doing so is that the SDKs handle request signing for you\. If you must create and sign API requests manually, go to [Signing AWS Requests By Using Signature Version 4](http://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html) in the *Amazon Web Services General Reference* to learn how to sign a request\.

**Example Response**  

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
The call to AWS STS can be to the global endpoint or to any of the regional endpoints for which you activate your AWS account\. For more information, see the [AWS STS section of *Regions and Endpoints*](http://docs.aws.amazon.com/general/latest/gr/rande.html#sts_region)\.  
Also, note that the `&AUTHPARAMS` parameter in the preceding example is meant as a placeholder for the authentication information—that is, the *signature*—that you must include with AWS HTTP API requests\. We recommend using the [AWS SDKs](https://aws.amazon.com/tools/) to create API requests, and one benefit of doing so is that the SDKs handle request signing for you\. If you must create and sign API requests manually, go to [Signing AWS Requests By Using Signature Version 4](http://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html) in the *Amazon Web Services General Reference* to learn how to sign a request\.

## Comparing the AWS STS API Operations<a name="stsapi_comparison"></a>

The following table compares features of the API operations in AWS STS that return temporary security credentials\. To learn about the different methods you can use to request temporary security credentials by assuming a role, see [Using IAM Roles](id_roles_use.md)\.


**Comparing your API options**  

|  **AWS STS API**  |  **Who can call**  |  **Credential lifetime \(min \| max \| default\)**  |  **MFA support**¹  |  **Passed policy support**²  |  **Restrictions on resulting temporary credentials**  | 
| --- | --- | --- | --- | --- | --- | 
|  [AssumeRole](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html)  | IAM user or user with existing temporary security credentials  | 15m \| Maximum session duration setting³ \| 1hr  | Yes  | Yes |  Cannot call `GetFederationToken` or `GetSessionToken`\.  | 
|  [AssumeRoleWithSAML](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html)  | Any user; caller must pass a SAML authentication response that indicates authentication from a known identity provider | 15m \| Maximum session duration setting³ \| 1hr  | No | Yes |  Cannot call `GetFederationToken` or `GetSessionToken`\.  | 
|  [AssumeRoleWithWebIdentity](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html)  | Any user; caller must pass a web identity token that indicates authentication from a known identity provider | 15m \| Maximum session duration setting³ \| 1hr  | No | Yes |  Cannot call `GetFederationToken` or `GetSessionToken`\.  | 
| [GetFederationToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html) | IAM user or AWS account root user |  IAM user: 15m \| 36hr \| 12hr Root user: 15m \| 1hr \| 1hr  | No  | Yes  |  Cannot call IAM API operations directly\. Cannot call AWS STS API operations except `GetCallerIdentity`\. SSO to console is allowed\.⁴  | 
| [GetSessionToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html) | IAM user or root user |  IAM user: 15m \| 36hr \| 12hr Root user: 15m \| 1hr \| 1hr  | Yes  | No  |  Cannot call IAM API operations unless MFA information is included with the request\. Cannot call AWS STS API operations except `AssumeRole` or `GetCallerIdentity`\. SSO to console is not allowed,\.⁵  | 

 ¹ **MFA support**\. You can include information about a multi\-factor authentication \(MFA\) device when you call the AssumeRole and GetSessionToken API operations\. This ensures that the temporary security credentials that result from the API call can be used only by users who are authenticated with an MFA device\. For more information, see [Configuring MFA\-Protected API Access](id_credentials_mfa_configure-api-require.md)\. 

 ² **Passed policy support**\. You can pass an IAM policy as a parameter to most of the AWS STS API operations to be used in conjunction with other policies that affect the user \(if any\)\. Using a policy as a parameter can help you determine what the user is allowed to do with the temporary credentials that result from the API call\. For more information, see the following topics:
+ [Permissions for AssumeRole, AssumeRoleWithSAML, and AssumeRoleWithWebIdentity](id_credentials_temp_control-access_assumerole.md) 
+ [Permissions for GetFederationToken](id_credentials_temp_control-access_getfederationtoken.md)
+ [Permissions for GetSessionToken](id_credentials_temp_control-access_getsessiontoken.md)

³ **Maximum session duration setting**\. Use the `DurationSeconds` parameter to specify the duration of your role session from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the Maximum Session Duration Setting for a Role](id_roles_use.md#id_roles_use_view-role-max-session)\.

⁴ **Single sign\-on \(SSO\) to the console**\. To support SSO, AWS lets you call a federation endpoint \(`https://signin.aws.amazon.com/federation`\) and pass temporary security credentials\. The endpoint returns a token that you can use to construct a URL that signs a user directly into the console without requiring a password\. For more information, see [Enabling SAML 2\.0 Federated Users to Access the AWS Management Console](id_roles_providers_enable-console-saml.md) and [ How to Enable Cross\-Account Access to the AWS Management Console](http://aws.amazon.com/blogs/security/how-to-enable-cross-account-access-to-the-aws-management-console) in the AWS Security Blog\. 

⁵ After you retrieve your temporary credentials, you can access the AWS Management Console by passing the credentials to the federation single sign\-on endpoint at `https://signin.aws.amazon.com/federation`\. For more information, see [Creating a URL that Enables Federated Users to Access the AWS Management Console \(Custom Federation Broker\)](id_roles_providers_enable-console-custom-url.md)\.