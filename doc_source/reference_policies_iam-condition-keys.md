# IAM Condition Context Keys<a name="reference_policies_iam-condition-keys"></a>

You can use the `Condition` element of a JSON policy in IAM to test the value of keys that are included in the evaluation context of all AWS API requests\. These keys provide information about the request itself or the resources that the request references\. You can check that keys have specified values before allowing the action requested by the user\. This gives you granular control over when your JSON policy statements match or don't match an incoming API request\. For information about how to use the `Condition` element in a JSON policy, see [IAM JSON Policy Elements: Condition](reference_policies_elements_condition.md)\.

This topic describes the keys defined and provided by the IAM service \(with an `iam:` prefix\)\. Several other AWS services also provide service\-specific keys that are relevant to the actions and resources defined by that service\. For more information, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\. The documentation for a service that supports condition keys often has additional information\. For example, for information about keys that you can use in policies for Amazon S3 resources, see [Amazon S3 Policy Keys](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#AvailableKeys-iamV2) in the *Amazon Simple Storage Service Developer Guide*\.

**Topics**
+ [Available Keys for IAM](#available-keys-for-iam)
+ [Available Keys for Web Identity Federation](#condition-keys-wif)
+ [Available Keys for SAML\-Based Federation](#condition-keys-saml)

## Available Keys for IAM<a name="available-keys-for-iam"></a>

You can use the following condition keys in policies that control access to IAM resources: 

**iam:AWSServiceName**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Specifies the AWS service to which this role is attached\.

**iam:PassedToService**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Specifies the service principal of the service to which a role can be passed\. A service principal is the name of a service that can be specified in the `Principal` element of a policy\. This is the usual format: `SERVICE_NAME_URL.amazonaws.com`\. In the `iam:PassedToService` condition key, provide the service principal of the service that will assume the role\.   
You can use `iam:PassedToService` to restrict your users so that they can pass roles only to specific services\. For example, a user might create a [service role](id_roles_terms-and-concepts.md#iam-term-service-role) that trusts CloudWatch to write log data to an Amazon S3 bucket on their behalf\. Then the user must attach a permissions policy and a trust policy to the new service role\. In this case, the trust policy must specify `cloudwatch.amazonaws.com` in the `Principal` element\. Attach the following policy to allow the user to pass the role to CloudWatch:  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:PassRole",
            "Resource": "*",
            "Condition": {"StringEquals": {"iam:PassedToService": "cloudwatch.amazonaws.com"}}
        }
    ]
}
```
By using this condition key, you can ensure that users create service roles only for the services that you specify\. For example, if a user with the preceding policy attempts to create a service role for Amazon EC2, the operation will fail because the user does not have permission to pass the role to Amazon EC2\. 

**iam:PolicyARN**  
Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN)\.  
Checks the Amazon Resource Name \(ARN\) of a managed policy in requests that involve a managed policy\. For more information, see [Controlling Access to Policies](access_controlling.md#access_controlling-policies)\. 

## Available Keys for Web Identity Federation<a name="condition-keys-wif"></a>

You can use web identity federation to give temporary security credentials to users who have been authenticated through an identity provider \(IdP\) such as Login with Amazon, Amazon Cognito, Google, or Facebook\. In that case, additional condition keys are available when the temporary security credentials are used to make a request\. You can use these keys to write policies that make sure that federated users can get access only to resources that are associated with a specific provider, app, or user\. 

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

**Application ID and User ID**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
You can also use two keys that provide a unique identifier for the user and an identifier for the application or site that the user authenticated with\. These keys have the following IdP\-specific names:  
+ For Amazon Cognito users, the keys are `cognito-identity.amazonaws.com:aud` \(for the identity pool ID\) and `cognito-identity.amazonaws.com:sub` \(for the user ID\)\. 
+ For Login with Amazon users, the keys are `www.amazon.com:app_id` and `www.amazon.com:user_id`
+ For Facebook users, the keys are `graph.facebook.com:app_id` and `graph.facebook.com:id`
+ For Google users, the keys are `accounts.google.com:aud` \(for the app ID\) and `accounts.google.com:sub` \(for the user ID\)\.

**The amr Key in Amazon Cognito**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
If you are using Amazon Cognito for web identity federation, the `cognito-identity.amazonaws.com:amr` key \(Authentication Methods Reference\) in a trust policy includes login information about the user\. The key is multivalued, meaning that you test it in a policy using [condition set operators](reference_policies_multi-value-conditions.md)\. The key can contain the following values:   
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

**More Information About Web Identity Federation**  
For more information about web identity federation, see the following:  
+ [Amazon Cognito Overview](http://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html#d0e840) in the *AWS Mobile SDK for Android Developer Guide* guide
+ [Amazon Cognito Overview](http://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html#d0e664) in the *AWS Mobile SDK for iOS Developer Guide* guide
+ [About Web Identity Federation](id_roles_providers_oidc.md)

## Available Keys for SAML\-Based Federation<a name="condition-keys-saml"></a>

If you are working with [SAML\-based federation](http://docs.aws.amazon.com/STS/latest/UsingSTS/CreatingSAML.html), you can include additional condition keys in the policy\. 

### SAML Role Trust Policies<a name="condition-keys-saml_trust-policy"></a>

In the trust policy of a role, you can include the following keys, which help you establish whether the caller is allowed to assume the role\. Except for `saml:doc`, all the values are derived from the SAML assertion\. Items in the list that are marked with an asterisk \(\*\) are available in the console UI to create conditions\. Items marked with **\[\]** *can* have a value that is a list of the specified type\.

**saml:aud**   
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
An endpoint URL to which SAML assertions are presented\. The value for this key comes from the `SAML Recipient` field in the assertion, ***not ***the `Audience` field\.

**saml:cn**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:doc**\*  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This represents the principal that was used to assume the role\. The format is *account\-ID*/*provider\-friendly\-name*, such as `123456789012/SAMLProviderName`\. The *account\-ID* value refers to the account that owns the [SAML provider](id_roles_providers_create_saml.md)\. 

**saml:edupersonaffiliation**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonassurance**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonentitlement**\[\]\*  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonnickname**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonorgdn**\*  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersonorgunitdn**\[\]  
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

**saml:edupersonscopedaffiliation**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:edupersontargetedid**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduPerson` attribute\.

**saml:eduorghomepageuri**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:eduorgidentityauthnpolicyuri**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:eduorglegalname**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:eduorgsuperioruri**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:eduorgwhitepagesuri**\[\]  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is an `eduOrg` attribute\.

**saml:namequalifier**\*  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
A hash value based on the concatenation of the `Issuer` response value \(`saml:iss`\), the `AWS` account ID and the friendly name \(the last part of the ARN\) of the SAML provider in IAM, separated by a '/' character\. The concatenation of the account ID and friendly name of the SAML provider is available to IAM policies as the key `saml:doc`\. For more information, see [Uniquely Identifying Users in SAML\-Based Federation](id_roles_providers_saml.md#CreatingSAML-userid)\.

**saml:iss**\*  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
The issuer, which is represented by a URN\. 

**saml:sub**\*  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is the subject of the claim, which includes a value that uniquely identifies an individual user within an organization \(for example, `_cbb88bf52c2510eabe00c1642d4643f41430fe25e3`\)\. 

**saml:sub\_type**\*  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This key can have the value `persistent`, `transient`, or consist of the full `Format` URI from the `Subject` and `NameID` elements used in your SAML assertion\. A value of `persistent` indicates that the value in `saml:sub` is the same for a user between sessions\. If the value is `transient`, the user has a different `saml:sub` value for each session\. For information about the `NameID` element's `Format` attribute, see [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\.

For general information about `eduPerson` and `eduOrg` attributes, see the [Internet2 website](https://www.internet2.edu/products-services/trust-identity-middleware/eduperson-eduorg/eduperson-eduorg-documentation/)\. For a list of `eduPerson` attributes, see [eduPerson Object Class Specification \(201203\)](https://www.internet2.edu/media/medialibrary/2013/09/04/internet2-mace-dir-eduperson-201203.html)\. 

Condition keys whose type is a list can include multiple values\. To create conditions in the policy for list values, you can use [set operators](reference_policies_multi-value-conditions.md) \(`ForAllValues`, `ForAnyValue`\)\. For example, to allow any user whose affiliation is "faculty", "staff", or "employee" \(but not "student", "alum", or other possible affiliations\), you might use a condition like the following: 

```
"Condition": {
   "ForAllValues:StringLike": {
     "saml:edupersonaffiliation":[ "faculty", "staff", "employee" ] 
   }
}
```

### SAML Role Permission Policies<a name="condition-keys-saml_permission-policy"></a>

In the permission policy of a role for SAML federation that defines what users are allowed to access in AWS, you can include the following keys:

**saml:namequalifier**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This contains a hash value that represents the combination of the `saml:doc` and `saml:iss` values\. It is used as a namespace qualifier; the combination of `saml:namequalifier` and `saml:sub` uniquely identifies a user\. 

**saml:sub**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is the subject of the claim, which includes a value that uniquely identifies an individual user within an organization \(for example, `_cbb88bf52c2510eabe00c1642d4643f41430fe25e3`\)\. 

**saml:sub\_type**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This key can have the value `persistent`, `transient`, or consist of the full `Format` URI from the `Subject` and `NameID` elements used in your SAML assertion\. A value of `persistent` indicates that the value in `saml:sub` is the same for a user between sessions\. If the value is `transient`, the user has a different `saml:sub` value for each session\. For information about the `NameID` element's `Format` attribute, see [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\.

For more information about using these keys, see [About SAML 2\.0\-based Federation](id_roles_providers_saml.md)\. 