# Monitor and control actions taken with assumed roles<a name="id_credentials_temp_control-access_monitor"></a>

An [IAM role](id_roles.md) is an object in IAM that is assigned [permissions](access_policies.md)\. When you [assume that role](id_roles_use.md) using an IAM identity or an identity from outside of AWS, you receive a session with the permissions that are assigned to the role\. 

When you perform actions in AWS, the information about your session can be logged to AWS CloudTrail for your [account administrator](getting-started_create-admin-group.md) to monitor\. Administrators can configure roles to require identities to pass a custom string that identifies the person or application that is performing actions in AWS\. This identity information is stored as the *source identity* in AWS CloudTrail\. When the administrator reviews activity in CloudTrail, they can view the source identity information to determine who or what performed actions with assumed role sessions\.

After a source identity is set, it is present in requests for any AWS action taken during the role session\. The value that is set persists when a role is used to assume another role through the AWS CLI or AWS API, known as [role chaining](id_roles_terms-and-concepts.md#iam-term-role-chaining)\. The value that is set cannot be changed during the role session\. Administrators can configure granular permissions based on the presence or value of the source identity to further control AWS actions that are taken with shared roles\. You can decide whether the source identity attribute can be used, whether it is required, and what value can be used\.



The way that you use source identity differs from role session name and session tags in an important way\. The source identity value can't be changed after it is set, and it persists for any additional actions that are taken with the role session\. Here's how you can use session tags and role session name: 
+ **Session tags** – You can pass session tags when you assume a role or federate a user\. Session tags are present when a role is assumed\. You can define policies that use tag condition keys to grant permissions to your principals based on their tags\. Then you can use CloudTrail to view the requests made to assume roles or federate users\. To learn more about session tags, see [Passing session tags in AWS STS](id_session-tags.md)\.
+ **Role session name** – You can use the `sts:RoleSessionName` condition key in a role trust policy to require that your users provide a specific session name when they assume a role\. Role session name can be used to differentiate role sessions when a role is used by different principals\. To learn more about role session name, see [sts:RoleSessionName](reference_policies_iam-condition-keys.md#ck_rolesessionname)\.

We recommend that you use source identity when you want to control the identity that assumes a role\. Source identity is also useful for mining CloudTrail logs to determine who used the role to perform actions\. 

**Topics**
+ [Setting up to use source identity](#id_credentials_temp_control-access_monitor-setup)
+ [Things to know about source identity](#id_credentials_temp_control-access_monitor-know)
+ [Permissions required to set source identity](#id_credentials_temp_control-access_monitor-perms)
+ [Specifying a source identity when assuming a role](#id_credentials_temp_control-access_monitor-specify-sourceid)
+ [Using source identity with AssumeRole](#id_credentials_temp_control-access_monitor-assume-role)
+ [Using source identity with AssumeRoleWithSAML](#id_credentials_temp_control-access_monitor-assume-role-saml)
+ [Using source identity with AssumeRoleWithWebIdentity](#id_credentials_temp_control-access_monitor-assume-role-web-id)
+ [Control access using source identity information](#id_credentials_temp_control-access_monitor-control-access)
+ [Viewing source identity in CloudTrail](#id_credentials_temp_control-access_monitor-ct)

## Setting up to use source identity<a name="id_credentials_temp_control-access_monitor-setup"></a>

The way that you set up to use source identity depends on the method used when your roles are assumed\. For example, your IAM users might assume roles directly using the `AssumeRole` operation\. If you have enterprise identities, also known as workforce identities, they might access your AWS resources using `AssumeRoleWithSAML`\. If end users access your mobile or web applications, they might do so using `AssumeRoleWithWebIdentity`\. The following is a high\-level workflow overview to help you understand how you can set up to utilize source identity information in your existing environment\.

1. **Configure test users and roles** – Using a preproduction environment, configure test users and roles and configure their policies to allow setting a source identity\.

   If you use an identity provider \(IdP\) for your federated identities, configure your IdP to pass a user attribute of your choice for source identity in the assertion or token\.

1. **Assume the role** – Test assuming roles and passing a source identity with the users and roles that you set up for testing\.

1. **Review CloudTrail** – Review the source identity information for your test roles in your CloudTrail logs\.

1. **Train your users** – After you've tested in your preproduction environment, ensure that your users know how to pass in the source identity information, if necessary\. Set a deadline for when you will require your users to provide a source identity in your production environment\.

1. **Configure production policies** – Configure your policies for your production environment, and then add them to your production users and roles\.

1. **Monitor activity** – Monitor your production role activity using CloudTrail logs\.

## Things to know about source identity<a name="id_credentials_temp_control-access_monitor-know"></a>

Keep the following in mind when working with source identity\.
+ Trust policies for all roles connected to an identity provider \(IdP\) must have the `sts:SetSourceIdentity` permission\. For roles that don't have this permission in the role trust policy, the `AssumeRole*` operation will fail\. If you don't want to update the role trust policy for each role, you can use a separate IdP instance for passing source identity\. Then add the `sts:SetSourceIdentity` permission to only the roles that are connected to the separate IdP\.
+ When an identity sets a source identity, the `sts:SourceIdentity` key is present in the request\. For subsequent actions taken during the role session, the `aws:SourceIdentity` key is present in the request\. AWS doesn’t control the value of the source identity in either the `sts:SourceIdentity` or `aws:SourceIdentity` keys\. If you choose to require a source identity, you must choose an attribute that you want your users or IdP to provide\. For security purposes, you must ensure that you can control how those values are provided\.
+ The value of source identity must be between 2 and 64 characters long, can contain only alphanumeric characters, underscores, and the following characters: **\. , \+ = @ \-** \(hyphen\)\. You cannot use a value that begins with the text **aws:**\. This prefix is reserved for AWS internal use\.
+ The source identity information is not captured by CloudTrail when an AWS service or service\-linked role carries out an action on behalf of a federated or workforce identity\. 

**Important**  
You cannot switch to a role in the AWS Management Console that requires a source identity to be set when the role is assumed\. To assume such a role, you can use the AWS CLI or AWS API to call the `AssumeRole` operation and specify the source identity parameter\.

## Permissions required to set source identity<a name="id_credentials_temp_control-access_monitor-perms"></a>

In addition to the action that matches the API operation, you must have the following permissions\-only action in your policy: 

```
sts:SetSourceIdentity
```
+ To specify a source identity, principals \(IAM users and roles\) must have permissions to `sts:SetSourceIdentity`\. As the administrator, you can configure this in the role trust policy and in the principal’s permissions policy\.
+ When you assume a role with another role, called [role chaining](id_roles_terms-and-concepts.md#iam-term-role-chaining), permissions for `sts:SetSourceIdentity` are required in both the permissions policy of the principal who is assuming the role and in the role trust policy of the target role\. Otherwise, the assume role operation will fail\.
+ When using source identity, the role trust policies for all roles connected to an IdP must have the `sts:SetSourceIdentity` permission\. The `AssumeRole*` operation will fail for any role connected to an IdP without this permission\. If you don't want to update the role trust policy for each role, you can use a separate IdP instance for passing source identity and add the `sts:SetSourceIdentity` permission to only the roles that are connected to the separate IdP\.
+ To set a source identity across account boundaries, you must include the `sts:SetSourceIdentity` permission in two places\. It must be in the permissions policy of the principal in the originating account and in the role trust policy of the role in the target account\. You might need to do this, for example, when a role is used to assume a role in another account with [role chaining](id_roles_terms-and-concepts.md#iam-term-role-chaining)\.

As the account administrator, imagine that you want to allow the IAM user `DevUser` in your account to assume the `Developer_Role` in the same account\. But you want to allow this action only if the user has set the source identity to their IAM user name\. You can attach the following policy to the IAM user\.

**Example identity\-based policy attached to DevUser**  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AssumeRole",
            "Effect": "Allow",
            "Action": "sts:AssumeRole",
            "Resource": "arn:aws:iam::123456789012:role/Developer_Role"
        },
        {
            "Sid": "Set_AWSUserName_as_SourceIdentity",
            "Effect": "Allow",
            "Action": "sts:SetSourceIdentity",
            "Resource": "arn:aws:iam::123456789012:role/Developer_Role",
            "Condition": {
                "StringLike": {"sts:SourceIdentity": "${aws:username}"}
            }
        }
    ]
}
```

To enforce the acceptable source identity values, you can configure the following role trust policy\. The policy gives the IAM user `DevUser` permissions to assume the role and set a source identity\. The `sts:SourceIdentity` condition key defines the acceptable source identity value\.

**Example role trust policy for source identity**  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowDevUserAssumeRole",
            "Effect": "Allow",
            "Principal": {"AWS": " arn:aws:iam::123456789012:user/DevUser"},
            "Action": [
                "sts:AssumeRole",
                "sts:SetSourceIdentity"
            ],
            "Condition": {
                "StringEquals": {"sts:SourceIdentity": "DevUser"}
            }
        }
    ]
}
```

Using the credentials for the IAM user `DevUser`, the user attempts to assume the `DeveloperRole` using the following AWS CLI request\.

**Example AssumeRole CLI request**  

```
aws sts assume-role \
--role-arn arn:aws:iam::123456789012:role/Developer_Role \
--role-session-name Dev-project \ 
--source-identity DevUser \
```

When AWS evaluates the request, the request context contains the `sts:SourceIdentity` of `DevUser`\.

## Specifying a source identity when assuming a role<a name="id_credentials_temp_control-access_monitor-specify-sourceid"></a>

You can specify a source identity when you use one of the AWS STS `AssumeRole*` API operations to get temporary security credentials for a role\. The API operation that you use differs depending on your use case\. For example, if you use IAM roles to give IAM users access to AWS resources that they don’t normally have access to, you might use the `AssumeRole` operation\. If you use enterprise identity federation to manage your workforce users, you might use the `AssumeRoleWithSAML` operation\. If you use web identity federation to allow end users to access your mobile or web applications, you might use the `AssumeRoleWithWebIdentity` operation\. The following sections explain how to use source identity with each operation\. To learn more about common scenarios for temporary credentials, see [Common scenarios for temporary credentials](id_credentials_temp.md#sts-introduction)\.

## Using source identity with AssumeRole<a name="id_credentials_temp_control-access_monitor-assume-role"></a>

The `AssumeRole` operation returns a set of temporary credentials that you can use to access AWS resources\. You can use IAM user or role credentials to call `AssumeRole`\. To pass source identity while assuming a role, use the `-–source-identity` AWS CLI option or the `SourceIdentity` AWS API parameter\. The following example shows how to specify the source identity using the AWS CLI\.

**Example AssumeRole CLI request**  

```
aws sts assume-role \
--role-arn arn:aws:iam::123456789012:role/developer \
--role-session-name Audit \ 
--source-identity Admin \
```

## Using source identity with AssumeRoleWithSAML<a name="id_credentials_temp_control-access_monitor-assume-role-saml"></a>

The principal calling the `AssumeRoleWithSAML` operation is authenticated using SAML\-based federation\. This operation returns a set of temporary credentials that you can use to access AWS resources\. For more information about using SAML\-based federation for AWS Management Console access, see [Enabling SAML 2\.0 federated users to access the AWS Management Console](id_roles_providers_enable-console-saml.md)\. For details about AWS CLI or AWS API access, see [About SAML 2\.0\-based federation](id_roles_providers_saml.md)\. For a tutorial of setting up SAML federation for your Active Directory users, see [AWS Federated Authentication with Active Directory Federation Services \(ADFS\)](http://aws.amazon.com/blogs/security/aws-federated-authentication-with-active-directory-federation-services-ad-fs/) in the AWS Security Blog\. 

As an administrator, you can allow members of your company directory to federate into AWS using the AWS STS `AssumeRoleWithSAML` operation\. To do this, you must complete the following tasks:

1. [Configure a SAML provider in your organization](id_roles_providers_saml_3rd-party.md)\.

1. [Create a SAML provider in IAM](id_roles_providers_create_saml.md)\.

1. [Configure a role and its permissions in AWS for your federated users](id_roles_create_for-idp_saml.md)\.

1. [Finish configuring the SAML IdP and create assertions for the SAML authentication response](id_roles_providers_create_saml_assertions.md)\.

To set a SAML attribute for source identity, include the `Attribute` element with the `Name` attribute set to `https://aws.amazon.com/SAML/Attributes/SourceIdentity`\. Use the `AttributeValue` element to specify the value of the source identity\. For example, assume that you want to pass the following identity attribute as the source identity\. 

`SourceIdentity:DiegoRamirez`

To pass this attribute, include the following element in your SAML assertion\.

**Example snippet of a SAML assertion**  

```
<Attribute Name="https://aws.amazon.com/SAML/Attributes/SourceIdentity">
<AttributeValue>DiegoRamirez</AttributeValue>
</Attribute>
```

## Using source identity with AssumeRoleWithWebIdentity<a name="id_credentials_temp_control-access_monitor-assume-role-web-id"></a>

The principal calling the `AssumeRoleWithWebIdentity` operation is authenticated using OpenID Connect \(OIDC\)\-compliant web identity federation\. This operation returns a set of temporary credentials that you can use to access AWS resources\. For more information about using web identity federation for AWS Management Console access, see [About web identity federation](id_roles_providers_oidc.md)\.

To pass source identity from OpenID Connect \(OIDC\), you must include the source identity in the JSON Web Token \(JWT\)\. Include source identity in the `[https://aws.amazon.com/](https://aws.amazon.com/)source_identity` namespace in the token when you submit the `AssumeRoleWithWebIdentity` request\. To learn more about OIDC tokens and claims, see [Using Tokens with User Pools](https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-tokens-with-identity-providers.html) in the *Amazon Cognito Developer Guide*\.

For example, the following decoded JWT is a token that is used to call `AssumeRoleWithWebIdentity` with the `Admin` source identity\.

**Example decoded JSON Web Token**  

```
{
    "sub": "johndoe",
    "aud": "ac_oic_client",
    "jti": "ZYUCeRMQVtqHypVPWAN3VB",
    "iss": "https://xyz.com",
    "iat": 1566583294,
    "exp": 1566583354,
    "auth_time": 1566583292,
    "https://aws.amazon.com/source_identity":"Admin"
}
```

## Control access using source identity information<a name="id_credentials_temp_control-access_monitor-control-access"></a>

When a source identity is initially set, the [sts:SourceIdentity](reference_policies_iam-condition-keys.md#ck_sourceidentity) key is present in the request\. After a source identity is set, the [aws:SourceIdentity](reference_policies_condition-keys.md#condition-keys-sourceidentity) key is present in all subsequent requests made during the role session\. As the administrator, you can write policies that grant conditional authorization to perform AWS actions based on the existence or value of the source identity attribute\.

Imagine that you want to require your developers to set a source identity to assume a critical role that has permission to write to a production critical AWS resource\. Also imagine that you grant AWS access to your workforce identities using `AssumeRoleWithSAML`\. You only want senior developers Saanvi and Diego to have access to the role, so you create the following trust policy for the role\.

**Example role trust policy for source identity**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AssumeRoleAndSetSourceIdentity",
      "Effect": "Allow",
      "Principal": {
        "AWS": " arn:aws:iam::111111111111:role/CriticalRole"
      },
      "Action": [
        "sts:AssumeRoleWithSAML",
        "sts:SetSourceIdentity"
      ],
      "Condition": {
        "StringLike": {
          "sts:SourceIdentity": ["Saanvi", "Diego"]
        }
      }
    }
  ]
}
```

The trust policy contains a condition for `sts:SourceIdentity` that requires a source identity that is set to Saanvi or Diego to assume the critical role\.

### Role chaining and cross\-account requirements<a name="id_credentials_temp_control-access_monitor-chain"></a>

Imagine that you want to allow users who have assumed `CriticalRole` to assume a `CriticalRole_2` in another account\. The role session credentials that were obtained to assume `CriticalRole` are used to [role chain](id_roles_terms-and-concepts.md#iam-term-role-chaining) to a second role, `CriticalRole_2`, in a different account\. The role is being assumed across an account boundary\. Therefore, the `sts:SetSourceIdentity` permission must be granted in both the permissions policy on `CriticalRole` and in the role trust policy on `CriticalRole_2`\.

**Example permissions policy on CriticalRole**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AssumeRoleAndSetSourceIdentity",
      "Effect": "Allow",
      "Action": [
        "sts:AssumeRole",
        "sts:SetSourceIdentity"
      ],
      "Resource": "arn:aws:iam::222222222222:role/CriticalRole_2"
    }
  ]
}
```

To secure setting source identity across the account boundary, the following role trust policy trusts only the role principal for `CriticalRole` to set the source identity\.

**Example role trust policy on CriticalRole\_2**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": " arn:aws:iam::111111111111:role/CriticalRole"
      },
      "Action": [
        "sts:AssumeRole",
        "sts:SetSourceIdentity"
      ],
      "Condition": {
        "StringLike": {
          "aws:SourceIdentity": ["Saanvi","Diego"]
        }
      }
    }
  ]
}
```

The user makes the following call using role session credentials obtained from assuming CriticalRole\. The source identity was set during the assumption of CriticalRole, so it does not need to be explicitly set again\. If the user attempts to set a source identity that is different from the value set when `CriticalRole` was assumed, the assume role request will be denied\.

**Example AssumeRole CLI request**  

```
aws sts assume-role \ 
--role-arn arn:aws:iam::222222222222:role/CriticalRole_2 \
--role-session-name Audit \
```

When the calling principal assumes the role, the source identity in the request persists from the first assumed role session\. Therefore, both the `aws:SourceIdentity` and `sts:SourceIdentity` keys are present in the request context\.

## Viewing source identity in CloudTrail<a name="id_credentials_temp_control-access_monitor-ct"></a>

You can use CloudTrail to view the requests made to assume roles or federate users\. You can also view the role or user requests to take actions in AWS\. The CloudTrail log file includes information about the source identity set for the assumed\-role or federated user session\. For more information, see 

For example, assume that a user makes an AWS STS `AssumeRole` request, and sets a source identity\. You can find the `sourceIdentity` information in the `requestParameters` key in your CloudTrail log\.

**Example requestParameters section in an AWS CloudTrail log**  

```
"eventVersion": "1.05",
    "userIdentity": {
        "type": "AWSAccount",
        "principalId": "AIDAJ45Q7YFFAREXAMPLE",
        "accountId": "123456789012"
    },
    "eventTime": "2020-04-02T18:20:53Z",
    "eventSource": "sts.amazonaws.com",
    "eventName": "AssumeRole",
    "awsRegion": "us-east-1",
    "sourceIPAddress": "203.0.113.64",
    "userAgent": "aws-cli/1.16.96 Python/3.6.0 Windows/10 botocore/1.12.86",
    "requestParameters": {
        "roleArn": "arn:aws:iam::123456789012:role/Assumed_Role",
        "roleSessionName": "Test1",
        "sourceIdentity": "source-identity-value-set",
    },
```

If the user uses the assumed role session to perform an action, the source identity information is present in the `userIdentity` key in the CloudTrail log\.

**Example userIdentity key in an AWS CloudTrail log**  

```
{
  "eventVersion": "1.08",
  "userIdentity": {
    "type": "AssumedRole",
    "principalId": "AROAJ45Q7YFFAREXAMPLE: Dev1",
    "arn": "arn: aws: sts: : 123456789012: assumed-role/DevRole/Dev1",
    "accountId": "123456789012",
    "accessKeyId": "ASIAIOSFODNN7EXAMPLE",
    "sessionContext": {
      "sessionIssuer": {
        "type": "Role",
        "principalId": "AROAJ45Q7YFFAREXAMPLE",
        "arn": "arn: aws: iam: : 123456789012: role/DevRole",
        "accountId": "123456789012",
        "userName": "DevRole"
      },
      "webIdFederationData": {},
      "attributes": {
        "mfaAuthenticated": "false",
        "creationDate": "2021-02-21T23: 46: 28Z"
      },
      "sourceIdentity": "source-identity-value-present"
    }
  }
}
```

To see example AWS STS API events in CloudTrail logs, see [Example IAM API events in CloudTrail log](cloudtrail-integration.md#cloudtrail-integration_examples-iam-api)\. For more details about the information contained in CloudTrail log files, see [CloudTrail Event Reference](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/eventreference.html) in the *AWS CloudTrail User Guide*\.