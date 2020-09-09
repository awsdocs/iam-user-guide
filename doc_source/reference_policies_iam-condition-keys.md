# IAM and AWS STS condition context keys<a name="reference_policies_iam-condition-keys"></a>

You can use the `Condition` element in a JSON policy to test the value of keys that are included in the request context of all AWS requests\. These keys provide information about the request itself or the resources that the request references\. You can check that keys have specified values before allowing the action requested by the user\. This gives you granular control over when your JSON policy statements match or don't match an incoming request\. For information about how to use the `Condition` element in a JSON policy, see [IAM JSON policy elements: Condition](reference_policies_elements_condition.md)\.

This topic describes the keys defined and provided by the IAM service \(with an `iam:` prefix\) and the AWS Security Token Service \(AWS STS\) service \(with an `sts:` prefix\)\. Several other AWS services also provide service\-specific keys that are relevant to the actions and resources defined by that service\. For more information, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\. The documentation for a service that supports condition keys often has additional information\. For example, for information about keys that you can use in policies for Amazon S3 resources, see [Amazon S3 Policy Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#AvailableKeys-iamV2) in the *Amazon Simple Storage Service Developer Guide*\.

**Topics**
+ [Available keys for IAM](#available-keys-for-iam)
+ [Available keys for AWS web identity federation](#condition-keys-wif)
+ [Available keys for SAML\-based AWS STS federation](#condition-keys-saml)
+ [Available keys for AWS STS](#condition-keys-sts)

## Available keys for IAM<a name="available-keys-for-iam"></a>

You can use the following condition keys in policies that control access to IAM resources: 

**iam:AssociatedResourceArn**  
Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN)\.  
Specifies the ARN of the resource to which this role will be associated at the destination service\. The resource usually belongs to the service to which the principal is passing the role\. Sometimes, the resource might belong to a third service\. For example, you might pass a role to Amazon EC2 Auto Scaling that they use on an Amazon EC2 instance\. In this case, the condition would match the ARN of the Amazon EC2 instance\.   
This condition key applies to only the [PassRole](id_roles_use_passrole.md) action in a policy\. It can't be used to limit any other action\.   
Use this condition key in a policy to allow an entity to pass a role, but only if that role is associated with the specified resource\. You can use wildcards \(\*\) to allow operations performed on a specific type of resource without restricting the Region or resource ID\. For example, you can allow an IAM user or role to pass any role to the Amazon EC2 service to be used with instances in the Region "us\-east\-1" or "us\-west\-1"\. The IAM user or role would not be allowed to pass roles to other services, and it doesn't allow Amazon EC2 to use the role with instances in other Regions\.   

```
{
    "Effect": "Allow",
    "Action": "iam:PassRole",
    "Resource": "*",
    "Condition": {
        "StringEquals": {"iam:PassedToService": "ec2.amazonaws.com"},
        "StringLike": {
            "iam:AssociatedResourceARN": [
                "arn:aws:ec2:us-east-1:111122223333:instance/*",
                "arn:aws:ec2:us-west-1:111122223333:instance/*"
            ]
        }
    }
}
```
AWS services that support [iam:PassedToService](#ck_PassedToService) also support this condition key\.

**iam:AWSServiceName**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Specifies the AWS service to which this role is attached\.

**iam:OrganizationsPolicyId**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks that the policy with the specified AWS Organizations ID matches the policy used in the request\. To view an example IAM policy that uses this condition key, see [IAM: View service last accessed information for an Organizations policy](reference_policies_examples_iam_service-accessed-data-orgs.md)\.

**iam:PassedToService**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Specifies the service principal of the service to which a role can be passed\. This condition key applies to only the [PassRole](id_roles_use_passrole.md) action in a policy\. It can't be used to limit any other action\.   
When you use this condition key in a policy, specify the service using a service principal\. A service principal is the name of a service that can be specified in the `Principal` element of a policy\. This is the usual format: `SERVICE_NAME_URL.amazonaws.com`\.   
You can use `iam:PassedToService` to restrict your users so that they can pass roles only to specific services\. For example, a user might create a [service role](id_roles_terms-and-concepts.md#iam-term-service-role) that trusts CloudWatch to write log data to an Amazon S3 bucket on their behalf\. Then the user must attach a permissions policy and a trust policy to the new service role\. In this case, the trust policy must specify `cloudwatch.amazonaws.com` in the `Principal` element\. To view a policy that allows the user to pass the role to CloudWatch, see [IAM: Pass an IAM role to a specific AWS service](reference_policies_examples_iam-passrole-service.md)\.  
By using this condition key, you can ensure that users create service roles only for the services that you specify\. For example, if a user with the preceding policy attempts to create a service role for Amazon EC2, the operation will fail\. The failure occurs because the user does not have permission to pass the role to Amazon EC2\.   
Some services, such as AWS CodeBuild and AWS CodeCommit do not support this condition key\.

**iam:PermissionsBoundary**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks that the specified policy is attached as permissions boundary on the IAM principal resource\. For more information, see [Permissions boundaries for IAM entities](access_policies_boundaries.md)

**iam:PolicyARN**  
Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN)\.  
Checks the Amazon Resource Name \(ARN\) of a managed policy in requests that involve a managed policy\. For more information, see [Controlling access to policies](access_controlling.md#access_controlling-policies)\. 

**iam:ResourceTag/*key\-name***  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks that the tag attached to the identity resource \(user or role\) matches the specified key name and value\.  
IAM does not support using the `aws:ResourceTag` global condition key\. AWS STS supports both the IAM key and the global key\.
You can add custom attributes to a user or role in the form of a key\-value pair\. For more information about IAM tags, see [Tagging IAM users and roles](id_tags.md)\. You can use `iam:ResourceTag` to [control access](access_iam-tags.md#access_iam-tags_control-resources) to IAM users and roles\. However, because IAM does not support tags for groups, you cannot use tags to control access to groups\.  
This example shows how you might create a policy that allows deleting users with the **status=terminated** tag\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.  

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "iam:DeleteUser",
        "Resource": "*",
        "Condition": {"StringLike": {"iam:ResourceTag/status": "terminated"}}
    }]
}
```

## Available keys for AWS web identity federation<a name="condition-keys-wif"></a>

You can use web identity federation to give temporary security credentials to users who have been authenticated through an identity provider \(IdP\)\. Examples of such providers include Login with Amazon, Amazon Cognito, Google, or Facebook\. In that case, additional condition keys are available when the temporary security credentials are used to make a request\. You can use these keys to write policies that limit the access of federated users to resources that are associated with a specific provider, app, or user\. These keys are typically used in the trust policy for a role\.

**aws:FederatedProvider**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
The `FederatedProvider` key identifies which of the IdPs was used to authenticate the user\. For example, if the user was authenticated through Amazon Cognito, the key would contain `cognito-identity.amazonaws.com`\. Similarly, if the user was authenticated through Login with Amazon, the key would contain the value `www.amazon.com`\. You might use the key in a resource policy like the following, which uses the `aws:FederatedProvider` key as a policy variable in the ARN of a resource\. The policy allows any user who has been authenticated using an IdP to get objects out of a folder in an Amazon S3 bucket\. However, the bucket must be specific to the provider that the user authenticates with\.  

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": "*",
    "Action": "s3:GetObject",
    "Resource": "arn:aws:s3:::BUCKET-NAME/${aws:FederatedProvider}/*"
  }
}
```

**amr**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
**Example**: `cognito-identity.amazonaws.com.com:amr`  
If you are using Amazon Cognito for web identity federation, the `cognito-identity.amazonaws.com:amr` key \(Authentication Methods Reference\) includes login information about the user\. The key is multivalued, meaning that you test it in a policy using [condition set operators](reference_policies_multi-value-conditions.md)\. The key can contain the following values:   
+ If the user is unauthenticated, the key contains only `unauthenticated`\.
+ If the user is authenticated, the key contains the value `authenticated` and the name of the login provider used in the call \(`graph.facebook.com`, `accounts.google.com`, or `www.amazon.com`\)\. 
As an example, the following condition in the trust policy for an Amazon Cognito role tests whether the user is unauthenticated:  

```
"Condition": {
  "StringEquals": 
    { "cognito-identity.amazonaws.com:aud": "us-east-2:identity-pool-id" },
  "ForAnyValue:StringLike": 
    { "cognito-identity.amazonaws.com:amr": "unauthenticated" }
}
```

**aud**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Use the `aud` condition key to verify that the Google client ID or Amazon Cognito identity pool ID matches the one that you specify in the policy\. You can use the `aud` key with the `sub` key for the same identity provider\.  
**Examples**:  
+ `accounts.google.com:aud`
+ `cognito-identity.amazonaws.com:aud`
The `accounts.google.com:aud` condition key matches the following Google ID Token fields\.   
+ `aud` for OAuth 2\.0 Google client IDs of your application, when the `azp` field is not set\. When the `azp` field is set, the `aud` field matches the [ `accounts.google.com:oaud`](#ck_oaud) condition key\.
+ `azp` when the `azp` field is set\. This can happen for hybrid apps where a web application and Android app have a different OAuth 2\.0 Google client ID but share the same Google APIs project\. 
For more information about Google `aud` and `azp` fields, see the [Google Identity Platform OpenID Connect](https://developers.google.com/identity/protocols/OpenIDConnect) Guide\.  
When you write a policy using the `accounts.google.com:aud` condition key, you must know whether the app is a hybrid app that sets the `azp` field\.   
`azp` Field Not Set  
The following example policy works for non\-hybrid apps that do not set the `azp` field\. In this case the Google ID Token `aud` field value matches both the `accounts.google.com:aud` and the `accounts.google.com:oaud` condition key values\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {"Federated": "accounts.google.com"},
            "Action": "sts:AssumeRoleWithWebIdentity",
            "Condition": {
                "StringEquals": {
                    "accounts.google.com:aud": "aud-value",
                    "accounts.google.com:oaud": "aud-value",
                    "accounts.google.com:sub": "sub-value"
                }
            }
        }
    ]
}
```
`azp` Field Set  
The following example policy works for hybrid apps that do set the `azp` field\. In this case the Google ID Token `aud` field value matches only the `accounts.google.com:oaud` condition key value\. The `azp` field value matches the `accounts.google.com:aud` condition key value\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {"Federated": "accounts.google.com"},
            "Action": "sts:AssumeRoleWithWebIdentity",
            "Condition": {
                "StringEquals": {
                    "accounts.google.com:aud": "azp-value",
                    "accounts.google.com:oaud": "aud-value",
                    "accounts.google.com:sub": "sub-value"
                }
            }
        }
    ]
}
```

**id**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
**Examples**:  
+ `graph.facebook.com:app_id`
+ `graph.facebook.com:id`
+ `www.amazon.com:app_id`
+ `www.amazon.com:user_id`
Use these keys to verify that the application \(or site\) ID or user ID matches the one that you specify in the policy\. This works for Facebook or Login with Amazon\. You can use the `app_id` key with the `id` key for the same identity provider\.

**oaud**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
**Example**: `accounts.google.com:oaud`  
If you use Google for web identity federation, this key specifies the Google audience \(`aud`\) that this ID token is intended for\. It must be one of the OAuth 2\.0 client IDs of your application\.

**sub**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
**Examples**:   
+ `accounts.google.com:sub`
+ `cognito-identity.amazonaws.com:sub`
Use these keys to verify that the user ID matches the one that you specify in the policy\. You can use the `sub` key with the `aud` key for the same identity provider\.

**More Information About Web Identity Federation**  
For more information about web identity federation, see the following:  
+ [Amazon Cognito Overview](https://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html#d0e840) in the *AWS Mobile SDK for Android Developer Guide* guide
+ [Amazon Cognito Overview](https://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html#d0e664) in the *AWS Mobile SDK for iOS Developer Guide* guide
+ [About web identity federation](id_roles_providers_oidc.md)

## Available keys for SAML\-based AWS STS federation<a name="condition-keys-saml"></a>

If you are working with [SAML\-based federation](https://docs.aws.amazon.com/STS/latest/UsingSTS/CreatingSAML.html) using AWS Security Token Service \(AWS STS\), you can include additional condition keys in the policy\. 

### SAML role trust policies<a name="condition-keys-saml_trust-policy"></a>

In the trust policy of a role, you can include the following keys, which help you establish whether the caller is allowed to assume the role\. Except for `saml:doc`, all the values are derived from the SAML assertion\. All items in the list are available in the IAM console visual editor when you create or edit a policy with conditions\. Items marked with `[]` *can* have a value that is a list of the specified type\.

**saml:aud **  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
An endpoint URL to which SAML assertions are presented\. The value for this key comes from the `SAML Recipient` field in the assertion, *not *the `Audience` field\.

**saml:commonName\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is a `commonName` attribute\.

**saml:cn\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:doc**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This represents the principal that was used to assume the role\. The format is *account\-ID*/*provider\-friendly\-name*, such as `123456789012/SAMLProviderName`\. The *account\-ID* value refers to the account that owns the [SAML provider](id_roles_providers_create_saml.md)\. 

**saml:edupersonaffiliation\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonassurance\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonentitlement\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonnickname\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonorgdn**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonorgunitdn\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonprimaryaffiliation**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonprimaryorgunitdn**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonprincipalname**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonscopedaffiliation\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersontargetedid\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:eduorghomepageuri\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:eduorgidentityauthnpolicyuri\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:eduorglegalname\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:eduorgsuperioruri\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:eduorgwhitepagesuri\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:givenName\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is a `givenName` attribute\.

**saml:iss**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
The issuer, which is represented by a URN\. 

**saml:mail\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is a `mail` attribute\.

**saml:name\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is a `name` attribute\.

**saml:namequalifier**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
A hash value based on the friendly name of the SAML provider\. The value is the concatenation of the following values, in order and separated by a '/' character:  

1. The `Issuer` response value \(`saml:iss`\)

1. The `AWS` account ID

1.  The friendly name \(the last part of the ARN\) of the SAML provider in IAM 
The concatenation of the account ID and friendly name of the SAML provider is available to IAM policies as the key `saml:doc`\. For more information, see [Uniquely identifying users in SAML\-based federation](id_roles_providers_saml.md#CreatingSAML-userid)\.

**saml:organizationStatus\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `organizationStatus` attribute\.

**saml:primaryGroupSID\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is a `primaryGroupSID` attribute\.

**saml:sub**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is the subject of the claim, which includes a value that uniquely identifies an individual user within an organization \(for example, `_cbb88bf52c2510eabe00c1642d4643f41430fe25e3`\)\. 

**saml:sub\_type**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This key can have the value `persistent`, `transient`, or consist of the full `Format` URI from the `Subject` and `NameID` elements used in your SAML assertion\. A value of `persistent` indicates that the value in `saml:sub` is the same for a user between sessions\. If the value is `transient`, the user has a different `saml:sub` value for each session\. For information about the `NameID` element's `Format` attribute, see [Configuring SAML assertions for the authentication response](id_roles_providers_create_saml_assertions.md)\.

**saml:surname\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is a `surnameuid` attribute\.

**saml:uid\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is a `uid` attribute\.

**saml:x500UniqueIdentifier\[\]**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `x500UniqueIdentifier` attribute\.

For general information about `eduPerson` and `eduOrg` attributes, see the [Internet2 website](https://www.internet2.edu/products-services/trust-identity-middleware/eduperson-eduorg/eduperson-eduorg-documentation/)\. For a list of `eduPerson` attributes, see [eduPerson Object Class Specification \(201203\)](https://www.internet2.edu/media/medialibrary/2013/09/04/internet2-mace-dir-eduperson-201203.html)\. 

Condition keys whose type is a list can include multiple values\. To create conditions in the policy for list values, you can use [set operators](reference_policies_multi-value-conditions.md) \(`ForAllValues`, `ForAnyValue`\)\. For example, to allow any user whose affiliation is "faculty" or "staff" \(but not "student"\), you might use a condition like the following: 

```
"Condition": {
   "ForAllValues:StringLike": {
     "saml:edupersonaffiliation":[ "faculty", "staff"] 
   }
}
```

### SAML role permissions policies<a name="condition-keys-saml_permission-policy"></a>

In the permissions policy of a role for SAML federation that defines what users are allowed to access in AWS, you can include the following keys:

**saml:namequalifier**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This contains a hash value that represents the combination of the `saml:doc` and `saml:iss` values\. It is used as a namespace qualifier; the combination of `saml:namequalifier` and `saml:sub` uniquely identifies a user\. 

**saml:sub**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is the subject of the claim, which includes a value that uniquely identifies an individual user within an organization \(for example, `_cbb88bf52c2510eabe00c1642d4643f41430fe25e3`\)\. 

**saml:sub\_type**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This key can have the value `persistent`, `transient`, or consist of the full `Format` URI from the `Subject` and `NameID` elements used in your SAML assertion\. A value of `persistent` indicates that the value in `saml:sub` is the same for a user between sessions\. If the value is `transient`, the user has a different `saml:sub` value for each session\. For information about the `NameID` element's `Format` attribute, see [Configuring SAML assertions for the authentication response](id_roles_providers_create_saml_assertions.md)\.

For more information about using these keys, see [About SAML 2\.0\-based federation](id_roles_providers_saml.md)\. 

## Available keys for AWS STS<a name="condition-keys-sts"></a>

You can use the following condition keys in IAM role trust policies for roles that are assumed using AWS Security Token Service \(AWS STS\) operations\. 

**sts:AWSServiceName**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Use this key to specify a service where a bearer token can be used\. When you use this condition key in a policy, specify the service using a service principal\. A service principal is the name of a service that can be specified in the `Principal` element of a policy\. For example, `codeartifact.amazonaws.com` is the AWS CodeArtifact service principal\.  
Some AWS services require that you have permission to get an AWS STS service bearer token before you can access their resources programmatically\. For example, AWS CodeArtifact requires principals to use bearer tokens to perform some operations\. The `aws codeartifact get-authorization-token` command returns a bearer token\. You can then use the bearer token to perform AWS CodeArtifact operations\. For more information about bearer tokens, see [Using bearer tokens](id_credentials_bearer.md)\.   
**Availability** – This key is present in requests that get a bearer token\. You cannot make a direct call to AWS STS to get a bearer token\. When you perform some operations in other services, the service requests the bearer token on your behalf\.  
You can use this condition key to allow principals to get a bearer token for use with a specific service\.

**sts:DurationSeconds**  
Works with [numeric operators](reference_policies_elements_condition_operators.md#Conditions_Numeric)\.  
Use this key to specify the duration \(in seconds\) that a principal can use when getting an AWS STS bearer token\.  
Some AWS services require that you have permission to get an AWS STS service bearer token before you can access their resources programmatically\. For example, AWS CodeArtifact requires principals to use bearer tokens to perform some operations\. The aws codeartifact get\-authorization\-token command returns a bearer token\. You can then use the bearer token to perform AWS CodeArtifact operations\. For more information about bearer tokens, see [Using bearer tokens](id_credentials_bearer.md)\.   
**Availability** – This key is present in requests that get a bearer token\. You cannot make a direct call to AWS STS to get a bearer token\. When you perform some operations in other services, the service requests the bearer token on your behalf\. The key is not present for AWS STS assume\-role operations\.

**sts:ExternalId**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Use this key to require that a principal provide a specific identifier when assuming an IAM role\.  
**Availability** – This key is present in the request when the principal provides an external ID while assuming a role using the AWS CLI or AWS API\.   
A unique identifier that might be required when you assume a role in another account\. If the administrator of the account to which the role belongs provided you with an external ID, then provide that value in the `ExternalId` parameter\. This value can be any string, such as a passphrase or account number\. The primary function of the external ID is to address and prevent the confused deputy problem\. For more information about the external ID and the confused deputy problem, see [How to use an external ID when granting access to your AWS resources to a third party](id_roles_create_for-user_externalid.md)\.  
The `ExternalId` value must have a minimum of 2 characters and a maximum of 1,224 characters\. The value must be alphanumeric without white space\. It can also include the following symbols: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), colon \(:\), forward slash \(/\), and hyphen \(\-\)\.

**sts:RoleSessionName**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Use this key to compare the session name that a principal specifies when assuming a role with the value that is specified in the policy\.  
**Availability** – This key is present in the request when the principal assumes the role using the AWS Management Console, the assume\-role CLI command, or the AssumeRole API operation\.  
You can use this key in a role trust policy to require that your users provide a specific session name when they assume a role\. For example, you can require that IAM users specify their own user name as their session name\. After the IAM user assumes the role, activity appears in [AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) with the session name that matches their user name\. This makes it easier for administrators to determine which user performed a specific action in AWS\.  
The following role trust policy requires that IAM users in account `111122223333` provide their IAM user name as the session name when they assume the role\. This requirement is enforced using the `aws:username` [condition variable](reference_policies_variables.md) in the condition key\. This policy allows IAM users to assume the role to which the policy is attached\. This policy does not allow anyone using temporary credentials to assume the role because the `username` variable is present for only IAM users\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "RoleTrustPolicyRequireUsernameForSessionName",
            "Effect": "Allow",
            "Action": "sts:AssumeRole",
            "Principal": {"AWS": "arn:aws:iam::111122223333:root"},
            "Condition": {
                "StringLike": {"sts:RoleSessionName": "${aws:username}"}
            }
        }
    ]
}
```
When an administrator views the AWS CloudTrail log for an action, they can compare the session name to the user names in their account\. In the following example, the user named `matjac` performed the operation using the role named `MateoRole`\. The administrator can then contact Mateo Jackson, who has the user named `matjac`\.  

```
    "assumedRoleUser": {
        "assumedRoleId": "AROACQRSTUVWRAOEXAMPLE:matjac",
        "arn": "arn:aws:sts::111122223333:assumed-role/MateoRole/matjac"
    }
```
If you allow [cross\-account access using roles](id_roles_common-scenarios_aws-accounts.md), then users in one account can assume a role in another account\. The ARN of the assumed role user listed in CloudTrail includes the account *where the role exists*\. It does not include the account of the user that assumed the role\. Users are unique only within an account\. Therefore, we recommend that you use this method for checking CloudTrail logs only for roles that are assumed by users in accounts that you administer\. Your users might use the same user name in multiple accounts\.

**sts:TransitiveTagKeys**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Use this key to compare the transitive session tag keys in the request with those specified in the policy\.   
**Availability** – This key is present in the request when you make a request using temporary security credentials\. These include credentials created using any assume\-role operation, or the `GetFederationToken` operation\.  
When you make a request using temporary security credentials, the [request context](reference_policies_elements_condition.md#AccessPolicyLanguage_RequestContext) includes the `aws:PrincipalTag` context key\. This key includes a list of [session tags](id_session-tags.md), [transitive session tags](id_session-tags.md#id_session-tags_role-chaining), and role tags\. Transitive session tags are tags that persist into all subsequent sessions when you use the session credentials to assume another role\. Assuming one role from another is called [role chaining](id_roles_terms-and-concepts.md#iam-term-role-chaining)\.   
You can use this condition key in a policy to require setting specific session tags as transitive when assuming a role or federating a user\.