# AWS Global and IAM Condition Context Keys<a name="reference_policies_condition-keys"></a>

The `Condition` element of an JSON policy in IAM allows you to test the value of keys that are included in the evaluation context of all AWS API requests\. These keys provide information about the request itself, or the resources that the request references\. You can check that keys have specified values before allowing the action requested by the user\. This gives you granular control over when your JSON policy statements match or don't match an incoming API request\. For information about how to use the `Condition` element in an JSON policy, see [IAM JSON Policy Elements: Condition](reference_policies_elements_condition.md)\.

This topic describes the globally available keys \(with an "aws:" prefix\), as well as the keys defined and provided by the IAM service \(with an "iam:" prefix\)\. Several other AWS services also provide service\-specific keys that are relevant to the actions and resources defined by that service\. For more information, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\. The documentation for a service that supports condition keys often has additional information\. For example, for information about keys that you can use in policies for Amazon S3 resources, see [Amazon S3 Policy Keys](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#AvailableKeys-iamV2) in the *Amazon Simple Storage Service Developer Guide*\.

**Note**  
If you use condition keys that are available only in some scenarios \(such as aws:SourceIp and aws:SourceVpc\) you can use the [IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists) versions of the comparison operators\. If the condition keys are missing from a request context \(and you haven't set IfExists\), the policy engine can fail the evaluation\. For example, if you want to write a policy that restricts access from a particular IP range or from a particular VPC, you can construct the conditions as follows:   
`"Condition": {"IpAddressIfExists": {"aws:SourceIp" : ["xxx"] }, "StringEqualsIfExists" : {"aws:SourceVpc" : ["yyy"]} }`  
This condition matches \(1\) if the aws:SourceIp context key exists and has the value xxx **or** \(2\) if the aws:SourceVpc context key exists and has the value yyy\. If either or both keys do not exist, the condition still matches\. The test is only made if the specified key exists in the request context\. If it is not there, it is treated as "I don't care"\.

**Topics**
+ [Available Global Condition Keys](#AvailableKeys)
+ [Available Keys for IAM](#available-keys-for-iam)
+ [Available Keys for Web Identity Federation](#condition-keys-wif)
+ [Available Keys for SAML\-Based Federation](#condition-keys-saml)

## Available Global Condition Keys<a name="AvailableKeys"></a>

 AWS provides the following predefined condition keys for all AWS services that support IAM for access control:

**aws:CurrentTime**  
Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.  
The current date and time to check for date/time conditions\.

**aws:EpochTime**  
Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.  
The current date and time in epoch or UNIX time to check for date/time conditions\.

**aws:TokenIssueTime**  
Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.  
Checks the date/time that temporary security credentials were issued\. This key is only present in requests that are signed using temporary security credentials\. For more information about temporary security credentials, see [Temporary Security Credentials](id_credentials_temp.md)\.

**aws:MultiFactorAuthPresent**  
Works with [boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.  
Checks whether multi\-factor authentication \(MFA\) was used to validate the temporary security credentials that made the current request\. This key is present in the request context only when the user uses temporary credentials to call the API\. Such credentials are used with IAM roles, federated users, IAM users with credentials from `sts:GetSessionToken`, and users of the AWS Management Console\. \(The console uses temporary credentials that are generated on the users' behalf in the background\.\) The `aws:MultiFactorAuthPresent` key is never present when an API or CLI command is called with long\-term credentials, such as standard access key pairs\. Therefore we recommend that when you check for this key that you use the `[\.\.\.IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists)` versions of the condition operators\.  
It is important to understand that the following Condition element is ***not*** a reliable way to check for the use of MFA:  

```
#####     THIS EXAMPLE DOES NOT WORK      #####

"Condition" : { "Bool" : { "aws:MultiFactorAuthPresent" : false } }
```
This is because when long\-term credentials are used, the `aws:MultiFactorAuthPresent` key is not present in the request and the test *always* fails, resulting in a non\-match\. Instead, we recommend that you use the [`BoolIfExists`](reference_policies_elements_condition_operators.md#Conditions_IfExists) operator to check the value\. For example::  

```
    "Condition" : { "BoolIfExists" : { "aws:MultiFactorAuthPresent" : false } }
```
The `*IfExists` operator indicates that the statement matches either if the value exists and has the value of "false" **or** if the value does not exist\. `*IfExists` means that you only care about the value if it is used\. Use this when you don't want the match to fail when the value is not used\.   
***Do not*** use a policy construct similar to the following to check whether the MFA key is present:  

```
#####     THIS EXAMPLE DOES NOT WORK      #####

"Action" : "Deny",
"Condition" : { "Null" : { "aws:MultiFactorAuthPresent" : true } }
```
You might expect the previous example to deny access if MFA is not used\. However, when you make an API request with long\-term credentials \(access keys\), the MFA condition context keys are *always* missing\. Consequently, testing for MFA this way always results in denied access to long\-term credentials\.

**aws:MultiFactorAuthAge**  
Works with [numeric operators](reference_policies_elements_condition_operators.md#Conditions_Numeric)\.  
Checks how long ago \(in seconds\) the MFA\-validated security credentials making the request were issued using multi\-factor authentication \(MFA\)\. If MFA was not used, this key is not present\. See [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\. Therefore, this is another key with which you should consider using the [\*IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists) versions of the comparison operators\. This ensures that the results of the comparison are what you expect even when the key is not present in the request context\.

**aws:PrincipalType**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the type of principal \(user, account, federated user, etc\.\) for the current request\.

**aws:Referer**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks who referred the client browser to the address the request is being sent to\. It is only supported by some services, such as [Amazon S3, as a service that can be directly addressed by a web browser](http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html#example-bucket-policies-use-case-4)\. The value comes from the referer header in the HTTPS request made to AWS\.  
This key should be used carefully: `aws:referer` allows Amazon S3 bucket owners to help prevent their content from being served up by unauthorized third\-party sites to standard web browsers For more information, see the link in the previous paragraph\. Since the `aws:referer` value is provided by the caller in an http header, unauthorized parties can use modified or custom browsers to provide any `aws:referer` value that they choose\. As a result, `aws:referer` should not be used to prevent unauthorized parties from making direct AWS requests\. It is offered only to allow customers to protect their digital content, stored in Amazon S3, from being referenced on unauthorized, third\-party sites\.

**aws:RequestTag/*tag\-key***  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This context key is formatted "aws:RequestTag/*tag\-key*":"*tag\-value*" where *tag\-key* and *tag\-value* are a tag key and value pair\.  
Checks a tag and its value in an AWS request\. For example, you could check to see that the request includes the tag key "Dept" and that it has the value "Accounting"\.   
This AWS condition key was [introduced for Amazon EC2](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html) and is supported by a limited number of additional services\. Check your service to see whether it supports using this condition key\.

**aws:RequestedRegion**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks that an AWS request is made to a specific region\. You can use this global condition key to control which regions your users can make calls to, regardless of whether the AWS service supports region\-level controls\. To view the AWS regions for each service, see [AWS Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.  
You can use this context key to limit access to AWS services within a given set of regions\. For example, to deny access to AWS services that are not in Frankfurt \(eu\-central\-1\) or Ireland \(eu\-west\-1\), use the following policy:  

```
{
    "Sid": "Deny_All_Outside_EU",
    "Effect": "Deny",
    "Action": "*",
    "Resource": "*",
    "Condition": {"StringNotEquals": {"aws:RequestedRegion": [
        "eu-central-1",
        "eu-west-1"
    ]}}
}
```
This policy denies access to all actions and resources when the call is submitted to a region other than eu\-central\-1 or eu\-west\-1\. This policy does not grant access and must be used with another policy or statement\.

**aws:SecureTransport**  
Works with [boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.  
Checks whether the request was sent using SSL\.

**aws:SourceAccount**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks that the source of the request comes from a specific account\. For example, if an S3 bucket in your account is configured to deliver object creation events to an SNS topic, use this condition key to check that Amazon S3 is not being used as a confused deputy\. Amazon S3 tells SNS the account that the bucket belongs to\.   
This condition key is available for only some services\.

**aws:SourceArn**  
Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN)\.  
Checks the source of the request, using the [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns) of the source\.   
This condition key is available for only some services\.

**aws:SourceIp**  
Works with [IP address operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.  
Checks the requester's IP address, see [IP Address Condition Operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.  
The `aws:SourceIp` condition key should be used in a JSON policy only for IAM users, groups, roles, or federated users that make API calls from within the specified IP range\. This policy denies access to an AWS service that makes calls on your behalf\. For example, assume that you have a [service role](id_roles_terms-and-concepts.md#iam-term-service-role) that allows AWS CloudFormation to call Amazon EC2 to stop an instance\. In that case, the request is denied because the target service \(EC2\) sees the IP address of the calling service \(AWS CloudFormation\) rather than the IP address of the originating user\. There is no way to pass the originating IP address through a calling service to the target service for evaluation in a JSON policy\.
If the request comes from a host that uses an Amazon VPC endpoint, then the `aws:SourceIp` key is not available\. You should instead use a VPC\-specific key\. For more information, see [VPC Endpoints \- Controlling the Use of Endpoints](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html#vpc-endpoints-iam-access) in the *Amazon VPC User Guide*\.

**aws:SourceVpc**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
To restrict access to a specific VPC\. For more information, see [Restricting Access to a Specific VPC](http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc) in the *Amazon Simple Storage Service Developer Guide*\. \(This condition key is supported for traffic to an AWS service over a VPC endpoint\.\)

**aws:SourceVpce**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
To restrict access to a specific VPC endpoint\. For more information, see [Restricting Access to a Specific VPC Endpoint](http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc-endpoint) in the *Amazon Simple Storage Service Developer Guide*\.

**aws:TagKeys**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This context key is formatted "aws:TagKeys":"*tag\-key*" where *tag\-key* is a list of tag keys without values \(for example, `["Dept","Cost-Center"]`\)\.  
Checks the tag keys that are present in an AWS request\. This AWS condition key was [introduced for Amazon EC2](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html) and is supported by a limited number of additional services\. Check your service to see whether it supports using this condition key\.

**aws:UserAgent**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's client application\.

**aws:userid**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's user ID\.

**aws:username**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's user name\.

## Available Keys for IAM<a name="available-keys-for-iam"></a>

You can use the following condition keys in policies that control access to IAM resources: 

**iam:PolicyArn**  
Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN)\.  
Checks the Amazon Resource Name \(ARN\) of a managed policy in requests that involve a managed policy\. For more information, see [Controlling Access to Policies](access_controlling.md#access_controlling-policies)\. 

## Available Keys for Web Identity Federation<a name="condition-keys-wif"></a>

You can use web identity federation to give temporary security credentials to users who have been authenticated using an identity provider \(IdP\) such as Login with Amazon, Amazon Cognito, Google, or Facebook\. In that case, additional condition keys are available when the temporary security credentials are used to make a request\. You can use these keys to write policies that make sure that federated users can get access only to resources that are associated with a specific provider, app, or user\. 

**aws:FederatedProvider**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
The FederatedProvider key identifies which of the IdPs was used to authenticate the user\. For example, if the user authenticated using Amazon Cognito, the key would contain `cognito-identity.amazonaws.com`\. Similarly, if the user authenticated using Login with Amazon, the key would contain the value `www.amazon.com`\. You might use the key in a resource policy like the following, which uses the `aws:FederatedProvider` key as a policy variable in the ARN of a resource\. The policy allows any user who has been authenticated using an IdP to get objects out of a folder in an Amazon S3 bucket\. However, the bucket must be specific to the provider that the user authenticates with\.  

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

### Trust Policies<a name="condition-keys-saml_trust-policy"></a>

In the trust policy of a role, you can include the following keys, which help you establish whether the caller is allowed to assume the role\. Except for `saml:doc`, all the values are derived from the SAML assertion\. Items in the list that are marked with an asterisk \(\*\) are available in the console UI to create conditions\. Items marked with **\[\]** *can* have a value that is a list of the specified type\.

**saml:aud**   
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
An endpoint URL to which SAML assertions are presented\. The value for this key comes from the SAML Recipient field in the assertion, ***not ***the Audience field\.

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
This key can have the value "persistent", "transient", or consist of the full `Format` URI from the `Subject` and `NameID` elements used in your SAML assertion\. A value of "persistent" indicates that the value in `saml:sub` is the same for a user between sessions\. If the value is "transient", the user has a different `saml:sub` value for each session\. For information about the `NameID` element's `Format` attribute, see [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\.

For general information about `eduPerson` and `eduOrg` attributes, see the [Internet2 website](https://www.internet2.edu/products-services/trust-identity-middleware/eduperson-eduorg/eduperson-eduorg-documentation/)\. For a list of `eduPerson` attributes, see [eduPerson Object Class Specification \(201203\)](https://www.internet2.edu/media/medialibrary/2013/09/04/internet2-mace-dir-eduperson-201203.html)\. 

Condition keys whose type is a list can include multiple values\. To create conditions in the policy for list values, you can use [set operators](reference_policies_multi-value-conditions.md) \(`ForAllValues`, `ForAnyValue`\)\. For example, to allow any user whose affiliation is "faculty", "staff", or "employee" \(but not "student", "alum", or other possible affiliations\), you might use a condition like the following: 

```
"Condition": {
   "ForAllValues:StringLike": {
     "saml:edupersonaffiliation":[ "faculty", "staff", "employee" ] 
   }
}
```

### Permission \(Access\) Policies<a name="condition-keys-saml_permission-policy"></a>

In the permission policy of a role for SAML federation that defines what users are allowed to access in AWS, you can include the following keys:

**saml:namequalifier**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This contains a hash value that represents the combination of the `saml:doc` and `saml:iss` values\. It is used as a namespace qualifier; the combination of `saml:namequalifier` and `saml:sub` uniquely identifies a user\. 

**saml:sub**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This is the subject of the claim, which includes a value that uniquely identifies an individual user within an organization \(for example, `_cbb88bf52c2510eabe00c1642d4643f41430fe25e3`\)\. 

**saml:sub\_type**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This key can have the value "persistent", "transient", or consist of the full `Format` URI from the `Subject` and `NameID` elements used in your SAML assertion\. A value of "persistent" indicates that the value in `saml:sub` is the same for a user between sessions\. If the value is "transient", the user has a different `saml:sub` value for each session\. For information about the `NameID` element's `Format` attribute, see [Configuring SAML Assertions for the Authentication Response](id_roles_providers_create_saml_assertions.md)\.

For more information about using these keys, see [About SAML 2\.0\-based Federation](id_roles_providers_saml.md)\. 