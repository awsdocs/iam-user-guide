# AWS global condition context keys<a name="reference_policies_condition-keys"></a>

When a [principal](intro-structure.md#intro-structure-principal) makes a [request](intro-structure.md#intro-structure-request) to AWS, AWS gathers the request information into a [request context](intro-structure.md#intro-structure-request)\. You can use the `Condition` element of a JSON policy to compare keys in the request context with key values that you specify in your policy\. To learn more about the circumstances under which a global key is included in the request context, see the **Availability** information for each global condition key\. For information about how to use the `Condition` element in a JSON policy, see [IAM JSON policy elements: Condition](reference_policies_elements_condition.md)\.

**Note**  
If you use condition keys that are available only in some circumstances, you can use the [IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists) versions of the condition operators\. If the condition keys are missing from a request context, the policy can fail the evaluation\. For example, use the following condition block with `...IfExists` operators to match when a request comes from a specific IP range or from a specific VPC\. If either or both keys are not included in the request context, the condition still returns `true`\. The values are only checked if the specified key is included in the request context\.   

```
"Condition": {
    "IpAddressIfExists": {"aws:SourceIp" : ["xxx"] },
    "StringEqualsIfExists" : {"aws:SourceVpc" : ["yyy"]} 
}
```

Global condition keys are condition keys with an `aws:` prefix\. AWS services can support global condition keys or provide service\-specific keys that include their service prefix\. For example, IAM condition keys include the `iam:` prefix\. For more information, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html) and choose the service whose keys you want to view\.

**Important**  
To compare your condition against a request context with multiple key values, you must use the `ForAllValues` or `ForAnyValue` set operators\. Use set operators only with multivalued condition keys\. Do not use set operators with single\-valued condition keys\. For more information, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)\.

## aws:CalledVia<a name="condition-keys-calledvia"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the services in the policy with the services that made requests on behalf of the IAM principal \(user or role\)\. When a principal makes a request to an AWS service, that service might use the principal's credentials to make subsequent requests to other services\. The `aws:CalledVia` key contains an ordered list of each service in the chain that made requests on the principal's behalf\.

For example, you can use AWS CloudFormation to read and write from an Amazon DynamoDB table\. DynamoDB then uses encryption supplied by AWS Key Management Service \(AWS KMS\)\.
+ **Availability** – This key is present in the request when a service that supports `aws:CalledVia` uses the credentials of an IAM principal to make a request to another service\. This key is not present if the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\. This key is also not present when the principal makes the call directly\.
+ **Value type** – Multivalued<a name="calledvia-services"></a>

To use the `aws:CalledVia` condition key in a policy, you must provide the service principals to allow or deny AWS service requests\. AWS supports using the following services with `aws:CalledVia`\.


**CalledVia services**  

| AWS service | Service principal | 
| --- | --- | 
| Amazon Athena | athena\.amazonaws\.com | 
| AWS CloudFormation | cloudformation\.amazonaws\.com | 
| Amazon DynamoDB | dynamodb\.amazonaws\.com | 
| AWS Key Management Service \(AWS KMS\) | kms\.amazonaws\.com | 

To allow or deny access when *any* service makes a request using the principal's credentials, use the `aws:ViaAWSService` condition key\. That condition key supports AWS services\.

The `aws:CalledVia` key is a [multivalued key](reference_policies_multi-value-conditions.md)\. However, you can't enforce order using this key in a condition\. Using the example above, **User 1** makes a request to AWS CloudFormation, which calls DynamoDB, which calls AWS KMS\. These are three separate requests\. The final call to AWS KMS is performed by User 1 *via* AWS CloudFormation and then DynamoDB\. 

![\[Example using aws:CalledVia\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

In this case, the `aws:CalledVia` key in the request context includes `cloudformation.amazonaws.com` and `dynamodb.amazonaws.com`, in that order\. If you care only that the call was made via DynamoDB somewhere in the chain of requests, you can use this condition key in your policy\. 

For example, the following policy allows managing the AWS KMS key named `my-example-key`, but only if DynamoDB is one of the requesting services\. The `ForAnyValue:StringEquals` condition operator ensures that DynamoDB is one of the calling services\. If the principal makes the call to AWS KMS directly, the condition returns `false` and the request is not allowed by this policy\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "KmsActionsIfCalledViaDynamodb",
            "Effect": "Allow",
            "Action": [
                "kms:Encrypt",
                "kms:Decrypt",
                "kms:ReEncrypt*",
                "kms:GenerateDataKey",
                "kms:DescribeKey"
            ],
            "Resource": "arn:aws:kms:region:111122223333:key/my-example-key",
            "Condition": {
                "ForAnyValue:StringEquals": {
                    "aws:CalledVia": ["dynamodb.amazonaws.com"]
                }
            }
        }
    ]
}
```

If you want to enforce which service makes the first or last call in the chain, you can use the `aws:CalledViaFirst` and `aws:CalledViaLast` keys\. For example, the following policy allows managing the key named `my-example-key` in AWS KMS\. These AWS KMS operations are allowed only if multiple requests were included in the chain\. The first request must be made via AWS CloudFormation and the last via DynamoDB\. If other services make requests in the middle of the chain, the operation is still allowed\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "KmsActionsIfCalledViaChain",
            "Effect": "Allow",
            "Action": [
                "kms:Encrypt",
                "kms:Decrypt",
                "kms:ReEncrypt*",
                "kms:GenerateDataKey",
                "kms:DescribeKey"
            ],
            "Resource": "arn:aws:kms:region:111122223333:key/my-example-key",
            "Condition": {
                "StringEquals": {
                    "aws:CalledViaFirst": "cloudformation.amazonaws.com",
                    "aws:CalledViaLast": "dynamodb.amazonaws.com"
                }
            }
        }
    ]
}
```

The `aws:CalledViaFirst` and `aws:CalledViaLast` keys are present in the request when a service uses an IAM principal's credentials to call another service\. They indicate the first and last services that made calls in the chain of requests\. For example, assume that AWS CloudFormation calls another service named `X Service`, which calls DynamoDB, which then calls AWS KMS\. The final call to AWS KMS is performed by `User 1` *via* AWS CloudFormation, then `X Service`, and then DynamoDB\. It was first called via AWS CloudFormation and last called via DynamoDB\. 

![\[Example using aws:CalledViaFirst and aws:CalledViaLast\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

## aws:CalledViaFirst<a name="condition-keys-calledviafirst"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the services in the policy with the ***first service*** that made a request on behalf of the IAM principal \(user or role\)\. For more information, see `aws:CalledVia`\.
+ **Availability** – This key is present in the request when a service uses the credentials of an IAM principal to make at least one other request to a different service\. This key is not present if the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\. This key is also not present when the principal makes the call directly\.
+ **Value type** – Single\-valued

## aws:CalledViaLast<a name="condition-keys-calledvialast"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the services in the policy with the *last service* that made a request on behalf of the IAM principal \(user or role\)\. For more information, see `aws:CalledVia`\.
+ **Availability** – This key is present in the request when a service uses the credentials of an IAM principal to make at least one other request to a different service\. This key is not present if the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\. This key is also not present when the principal makes the call directly\.
+ **Value type** – Single\-valued

## aws:CurrentTime<a name="condition-keys-currenttime"></a>

Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.

Use this key to compare the date and time of the request with the date and time that you specify in the policy\. To view an example policy that uses this condition key, see [AWS: Allows access based on date and time](reference_policies_examples_aws-dates.md)\.
+ **Availability** – This key is always included in the request context\.
+ **Value type** – Single\-valued

## aws:EpochTime<a name="condition-keys-epochtime"></a>

Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date) or [numeric operators](reference_policies_elements_condition_operators.md#Conditions_Numeric)\.

Use this key to compare the date and time of the request in epoch or Unix time with the value that you specify in the policy\. This key also accepts the number of seconds since January 1, 1970\. 
+ **Availability** – This key is always included in the request context\.
+ **Value type** – Single\-valued

## aws:FederatedProvider<a name="condition-keys-federatedprovider"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the principal's issuing identity provider \(IdP\) with the IdP that you specify in the policy\. This means that an IAM role was assumed using the `AssumeRoleWithWebIdentity` or `AssumeRoleWithSAML` AWS STS operations\. When the resulting role session's temporary credentials are used to make a request, the request context identifies the IdP that authenticated the original federated identity\.
+ **Availability** – This key is present when the principal is a role session principal and that session was issued using a third\-party identity provider\. 
+ **Value type** – Single\-valued

For example, if the user was authenticated through Amazon Cognito, the request context includes the value `cognito-identity.amazonaws.com`\. Similarly, if the user was authenticated through Login with Amazon, the request context includes the value `www.amazon.com`\.

You can use any single\-valued condition key as a [variable](reference_policies_variables.md)\. The following example resource\-based policy uses the `aws:FederatedProvider` key as a policy variable in the ARN of a resource\. This policy allows any principal who authenticated using an IdP to get objects out of an Amazon S3 bucket with a path that's specific to the issuing identity provider\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": "*",
    "Action": "s3:GetObject",
    "Resource": "arn:aws:s3:::DOC-EXAMPLE-BUCKET/${aws:FederatedProvider}/*"
  }
}
```

## aws:MultiFactorAuthAge<a name="condition-keys-multifactorauthage"></a>

Works with [numeric operators](reference_policies_elements_condition_operators.md#Conditions_Numeric)\.

Use this key to compare the number of seconds since the requesting principal was authorized using MFA with the number that you specify in the policy\. For more information about MFA, see [Using multi\-factor authentication \(MFA\) in AWS](id_credentials_mfa.md)\.
+ **Availability** – This key is included in the request context only if the principal making the call was authenticated using MFA\. If MFA was not used, this key is not present\.
+ **Value type** – Single\-valued

## aws:MultiFactorAuthPresent<a name="condition-keys-multifactorauthpresent"></a>

Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.

Use this key to check whether multi\-factor authentication \(MFA\) was used to validate the temporary security credentials that made the request\.
+ **Availability** – This key is included in the request context only when the principal uses temporary credentials to make the request\. The key is not present in AWS CLI, AWS API, or AWS SDK requests that are made using long\-term credentials\. 
+ **Value type** – Single\-valued

Temporary credentials are used to authenticate IAM roles, federated users, IAM users with temporary tokens from `sts:GetSessionToken`, and users of the AWS Management Console\. IAM user access keys are long\-term credentials, but in some cases, AWS creates temporary credentials on behalf of IAM users to perform operations\. In these cases, the `aws:MultiFactorAuthPresent` key is present in the request and set to a value of `false`\. There are two common cases where this can happen:
+ IAM users in the AWS Management Console unknowingly use temporary credentials\. Users sign into the console using their user name and password, which are long\-term credentials\. However, in the background, the console generates temporary credentials on behalf of the user\. 
+ If an IAM user makes a call to an AWS service, the service re\-uses the user's credentials to make another request to a different service\. For example, when calling Athena to access an Amazon S3 bucket, or when using AWS CloudFormation to create an Amazon EC2 instance\. For the subsequent request, AWS uses temporary credentials\.

To learn which services support using temporary credentials, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

The `aws:MultiFactorAuthPresent` key is not present when an API or CLI command is called with long\-term credentials, such as user access key pairs\. Therefore we recommend that when you check for this key that you use the `\.\.\.IfExists` versions of the condition operators\.

It is important to understand that the following `Condition` element is ***not*** a reliable way to check whether a request is authenticated using MFA\.

```
#####   WARNING: NOT RECOMMENDED   #####
"Effect" : "Deny",
"Condition" : { "Bool" : { "aws:MultiFactorAuthPresent" : "false" } }
```

This combination of the `Deny` effect, `Bool` element, and `false` value denies requests that can be authenticated using MFA, but were not\. This applies only to temporary credentials that support using MFA\. This statement does not deny access to requests that are made using long\-term credentials, or to requests that are authenticated using MFA\. Use this example with caution because its logic is complicated and it does not test whether MFA\-authentication was actually used\. 

Also do not use the combination of the `Deny` effect, `Null` element, and `true` because it behaves the same way and the logic is even more complicated\.

**Recommended Combination**  
We recommend that you use the [`BoolIfExists`](reference_policies_elements_condition_operators.md#Conditions_IfExists) operator to check whether a request is authenticated using MFA\.

```
"Effect" : "Deny",
"Condition" : { "BoolIfExists" : { "aws:MultiFactorAuthPresent" : "false" } }
```

This combination of `Deny`, `BoolIfExists`, and `false` denies requests that are not authenticated using MFA\. Specifically, it denies requests from temporary credentials that do not include MFA\. It also denies requests that are made using long\-term credentials, such as AWS CLI or AWS API operations made using access keys\. The `*IfExists` operator checks for the presence of the `aws:MultiFactorAuthPresent` key and whether or not it could be present, as indicated by its existence\. Use this when you want to deny any request that is not authenticated using MFA\. This is more secure, but can break any code or scripts that use access keys to access the AWS CLI or AWS API\. 

**Alternative Combinations**  
You can also use the [`BoolIfExists`](reference_policies_elements_condition_operators.md#Conditions_IfExists) operator to allow MFA\-authenticated requests and AWS CLI or AWS API requests that are made using long\-term credentials\.

```
"Effect" : "Allow",
"Condition" : { "BoolIfExists" : { "aws:MultiFactorAuthPresent" : "true" } }
```

This condition matches either if the key exists and is present **or** if the key does not exist\. This combination of `Allow`, `BoolIfExists`, and `true` allows requests that are authenticated using MFA, or requests that cannot be authenticated using MFA\. This means that AWS CLI, AWS API, and AWS SDK operations are allowed when the requester uses their long\-term access keys\. This combination does not allow requests from temporary credentials that could, but do not include MFA\. 

When you create a policy using the IAM console visual editor and choose **MFA required**, this combination is applied\. This setting requires MFA for console access, but allows programmatic access with no MFA\. 

Alternatively, you can use the `Bool` operator to allow programmatic and console requests only when authenticated using MFA\.

```
"Effect" : "Allow",
"Condition" : { "Bool" : { "aws:MultiFactorAuthPresent" : "true" } }
```

This combination of the `Allow`, `Bool`, and `true` allows only MFA\-authenticated requests\. This applies only to temporary credentials that support using MFA\. This statement does not allow access to requests that were made using long\-term access keys, or to requests made using temporary credentials without MFA\. 

***Do not*** use a policy construct similar to the following to check whether the MFA key is present:

```
#####   WARNING: USE WITH CAUTION   #####

"Effect" : "Allow",
"Condition" : { "Null" : { "aws:MultiFactorAuthPresent" : "false" } }
```

This combination of the `Allow` effect, `Null` element, and `false` value allows only requests that can be authenticated using MFA, regardless of whether the request is actually authenticated\. This allows all requests that are made using temporary credentials, and denies access for long\-term credentials\. Use this example with caution because it does not test whether MFA\-authentication was actually used\. 

## aws:PrincipalAccount<a name="condition-keys-principalaccount"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the account to which the requesting principal belongs with the account identifier that you specify in the policy\. For anonymous requests, the request context returns `anonymous`\.
+ **Availability** – This key is included in the request context for all requests, including anonymous requests\.
+ **Value type** – Single\-valued

In the following example, access is denied except to principals with the account number `123456789012`\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyAccessFromPrincipalNotInSpecificAccount",
      "Action": "service:*",
      "Effect": "Deny",
      "Resource": [
        "arn:partition:service:region:accountID:resource"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:PrincipalAccount": [
            "123456789012"
          ]
        }
      }
    }
  ]
}
```

## aws:PrincipalArn<a name="condition-keys-principalarn"></a>

Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN) and [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the [Amazon Resource Name](reference_identifiers.md#identifiers-arns) \(ARN\) of the principal that made the request with the ARN that you specify in the policy\. For IAM roles, the request context returns the ARN of the role, not the ARN of the user that assumed the role\. 
+ **Availability** – This key is included in the request context for all signed requests\. Anonymous requests do not include this key\. You can specify the following types of principals in this condition key: 
  + IAM role
  + IAM user
  + AWS STS federated user session
  + AWS account root user
+ **Value type** – Single\-valued

The following list shows the request context value returned for different types of principals that you can specify in the `aws:PrincipalArn` condition key:
+ **IAM role** – The request context contains the following value for condition key `aws:PrincipalArn`\. Do not specify the assumed role session ARN as a value for this condition key\. For more information about the assumed role session principal, see [Role session principals](reference_policies_elements_principal.md#principal-role-session)\.

  ```
  arn:aws:iam::123456789012:role/role-name
  ```
+ **IAM user** – The request context contains the following value for condition key `aws:PrincipalArn`\.

  ```
  arn:aws:iam::123456789012:user/user-name
  ```
+ **AWS STS federated user sessions** – The request context contains the following value for condition key `aws:PrincipalArn`\.

  ```
  arn:aws:sts::123456789012:federated-user/user-name
  ```
+ **AWS account root user** – The request context contains the following value for condition key `aws:PrincipalArn`\. When you specify the root user ARN as the value for the `aws:PrincipalArn` condition key, it limits permissions only for the root user of the AWS account\. This is different from specifying the root user ARN in the principal element of a resource\-based policy, which delegates authority to the AWS account\. For more information about specifying the root user ARN in the principal element of a resource\-based policy, see [AWS account principals](reference_policies_elements_principal.md#principal-accounts)\. 

  ```
  arn:aws:iam::123456789012:root
  ```

  You can specify the root user ARN as a value for condition key `aws:PrincipalArn` in AWS Organizations service control policies \(SCPs\)\. SCPs are a type of organization policy used to manage permissions in your organization and affect only member accounts in the organization\. An SCP restricts permissions for IAM users and roles in member accounts, including the member account's root user\. For more information about the effect of SCPs on permissions, see [SCP effects on permissions](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html#scp-effects-on-permissions) in the *Organizations User Guide*\.

## aws:PrincipalIsAWSService<a name="condition-keys-principalisawsservice"></a>

Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.

Use this key to check whether the call to your resource is being made directly by an AWS [service principal](reference_policies_elements_principal.md#principal-services)\. For example, AWS CloudTrail uses the service principal `cloudtrail.amazonaws.com` to write logs to your Amazon S3 bucket\. The request context key is set to true when a service uses a service principal to perform a direct action on your resources\. The context key is set to false if the service uses the credentials of an IAM principal to make a request on the principal's behalf\. It is also set to false if the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\.
+ **Availability** – This key is present in the request context for all signed API requests that use AWS credentials\. Anonymous requests do not include this key\.
+ **Value type** – Single\-valued

You can use this condition key to limit access to your trusted identities and expected network locations while safely granting access to AWS services\.

In the following Amazon S3 bucket policy example, access to the bucket is restricted unless the request originates from `vpc-111bbb22` or is from a service principal, such as CloudTrail\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Expected-network+service-principal",
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::DOC-EXAMPLE-BUCKET1/AWSLogs/AccountNumber/*",
      "Condition": {
        "StringNotEqualsIfExists": {
          "aws:SourceVpc": "vpc-111bbb22"
        },
        "BoolIfExists": {
          "aws:PrincipalIsAWSService": "false"
        }
      }
    }
  ]
}
```

## aws:PrincipalOrgID<a name="condition-keys-principalorgid"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the identifier of the organization in AWS Organizations to which the requesting principal belongs with the identifier specified in the policy\.
+ **Availability** – This key is included in the request context only if the principal is a member of an organization\. Anonymous requests do not include this key\.
+ **Value type** – Single\-valued

This global key provides an alternative to listing all the account IDs for all AWS accounts in an organization\. You can use this condition key to simplify specifying the `Principal` element in a [resource\-based policy](access_policies_identity-vs-resource.md)\. You can specify the [organization ID](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_details.html) in the condition element\. When you add and remove accounts, policies that include the `aws:PrincipalOrgID` key automatically include the correct accounts and don't require manual updating\.

For example, the following Amazon S3 bucket policy allows members of any account in the `o-xxxxxxxxxxx` organization to add an object into the `policy-ninja-dev` bucket\. 

```
 {
  "Version": "2012-10-17",
  "Statement": {
    "Sid": "AllowPutObject",
    "Effect": "Allow",
    "Principal": "*",
    "Action": "s3:PutObject",
    "Resource": "arn:aws:s3:::policy-ninja-dev/*",
    "Condition": {"StringEquals":
      {"aws:PrincipalOrgID":"o-xxxxxxxxxxx"}
    }
  }
}
```

**Note**  
This global condition also applies to the management account of an AWS organization\. This policy prevents all principals outside of the specified organization from accessing the Amazon S3 bucket\. This includes any AWS services that interact with your internal resources, such as AWS CloudTrail sending log data to your Amazon S3 buckets\. To learn how you can safely grant access for AWS services, see [aws:PrincipalIsAWSService](#condition-keys-principalisawsservice)\.

For more information about AWS Organizations, see [What Is AWS Organizations?](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) in the *AWS Organizations User Guide*\.

## aws:PrincipalOrgPaths<a name="condition-keys-principalorgpaths"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the AWS Organizations path for the principal who is making the request to the path in the policy\. That principal can be an IAM user, IAM role, federated user, or AWS account root user\. In a policy, this condition key ensures that the requester is an account member within the specified organization root or organizational units \(OUs\) in AWS Organizations\. An AWS Organizations path is a text representation of the structure of an Organizations entity\. For more information about using and understanding paths, see [Understand the AWS Organizations entity path](access_policies_access-advisor-view-data-orgs.md#access_policies_access-advisor-viewing-orgs-entity-path)\.
+ **Availability** – This key is included in the request context only if the principal is a member of an organization\. Anonymous requests do not include this key\.
+ **Value type** – Multivalued

**Note**  
Organization IDs are globally unique but OU IDs and root IDs are unique only within an organization\. This means that no two organizations share the same organization ID\. However, another organization might have an OU or root with the same ID as yours\. We recommend that you always include the organization ID when you specify an OU or root\.

For example, the following condition returns `true` for principals in accounts that are attached directly to the `ou-ab12-22222222` OU, but not in its child OUs\.

```
"Condition" : { "ForAnyValue:StringEquals" : {
     "aws:PrincipalOrgPaths":["o-a1b2c3d4e5/r-ab12/ou-ab12-11111111/ou-ab12-22222222/"]
}}
```

The following condition returns `true` for principals in an account that is attached directly to the OU or any of its child OUs\. When you include a wildcard, you must use the `StringLike` condition operator\.

```
"Condition" : { "ForAnyValue:StringLike" : {
     "aws:PrincipalOrgPaths":["o-a1b2c3d4e5/r-ab12/ou-ab12-11111111/ou-ab12-22222222/*"]
}}
```

The following  condition returns `true` for principals in an account that is attached directly to any of the child OUs, but not directly to the parent OU\. The previous condition is for the OU or any children\. The following condition is for only the children \(and any children of those children\)\.

```
"Condition" : { "ForAnyValue:StringLike" : {
     "aws:PrincipalOrgPaths":["o-a1b2c3d4e5/r-ab12/ou-ab12-11111111/ou-ab12-22222222/ou-*"]
}}
```

The following condition allows access for every principal in the `o-a1b2c3d4e5` organization, regardless of their parent OU\.

```
"Condition" : { "ForAnyValue:StringLike" : {
     "aws:PrincipalOrgPaths":["o-a1b2c3d4e5/*"]
}}
```

`aws:PrincipalOrgPaths` is a multivalued condition key\. Multivalued keys can have multiple values in the request context\. When you use multiple values with the `ForAnyValue` condition operator, the principal's path must match one of the paths listed in the policy\. For more information about multivalued condition keys, see [Using multiple keys and values](reference_policies_multi-value-conditions.md#reference_policies_multi-key-or-value-conditions)\.

```
    "Condition": {
        "ForAnyValue:StringLike": {
            "aws:PrincipalOrgPaths": [
                "o-a1b2c3d4e5/r-ab12/ou-ab12-33333333/*",
                "o-a1b2c3d4e5/r-ab12/ou-ab12-22222222/*"
            ]
        }
    }
```

## aws:PrincipalServiceName<a name="condition-keys-principalservicename"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the [service principal](reference_policies_elements_principal.md#principal-services) name in the policy with the service principal that is making requests to your resources\. You can use this key to check whether this call is made by a specific service principal\. When a service principal makes a direct request to your resource, the `aws:PrincipalServiceName` key contains the name of the service principal\. For example, the AWS CloudTrail service principal name is `cloudtrail.amazonaws.com`\.
+ **Availability** – This key is present in the request when the call is made by an AWS service principal\. This key is not present in any other situation, including the following:
  + If the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\.
  + If the service uses the credentials of an IAM principal to make a request on the principal's behalf\.
  + If the call is made directly by an IAM principal\.
  + If the call is made by an anonymous requester\.
+ **Value type** – Single\-valued

You can use this condition key to limit access to your trusted identities and expected network locations while safely granting access to an AWS service\.

In the following Amazon S3 bucket policy example, access to the bucket is restricted unless the request originates from `vpc-111bbb22` or is from a service principal, such as CloudTrail\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "expected-network+service-principal",
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::DOC-EXAMPLE-BUCKET1/AWSLogs/AccountNumber/*",
      "Condition": {
        "StringNotEqualsIfExists": {
          "aws:SourceVpc": "vpc-111bbb22",
          "aws:PrincipalServiceName": "cloudtrail.amazonaws.com"
        }
      }
    }
  ]
}
```

## aws:PrincipalServiceNamesList<a name="condition-keys-principalservicenameslist"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

This key provides a list of all [service principal](reference_policies_elements_principal.md#principal-services) names that belong to the service\. This is an advanced condition key\. You can use it to restrict the service from accessing your resource from a specific Region only\. Some services may create Regional service principals to indicate a particular instance of the service within a specific Region\. You can limit access to a resource to a particular instance of the service\. When a service principal makes a direct request to your resource, the `aws:PrincipalServiceNamesList` contains an unordered list of all service principal names associated with the Regional instance of the service\.
+ **Availability** – This key is present in the request when the call is made by an AWS service principal\. This key is not present in any other situation, including the following:
  + If the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\.
  + If the service uses the credentials of an IAM principal to make a request on the principal's behalf\.
  + If the call is made directly by an IAM principal\.
  + If the call is made by an anonymous requester\.
+ **Value type** – Multivalued

`aws:PrincipalServiceNamesList` is a multivalued condition key\. Multivalued keys can have multiple values in the request context\. You must use the `ForAnyValue` or `ForAllValues` set operators with [string condition operators](reference_policies_elements_condition_operators.md#Conditions_String) for this key\. For more information about multivalued condition keys, see [Using multiple keys and values](reference_policies_multi-value-conditions.md#reference_policies_multi-key-or-value-conditions)\.

## aws:PrincipalTag/*tag\-key*<a name="condition-keys-principaltag"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the tag attached to the principal making the request with the tag that you specify in the policy\. If the principal has more than one tag attached, the request context includes one `aws:PrincipalTag` key for each attached tag key\.
+ **Availability** – This key is included in the request context if the principal is using an IAM user with attached tags\. It is included for a principal using an IAM role with attached tags or [session tags](id_session-tags.md)\. Anonymous requests do not include this key\.
+ **Value type** – Single\-valued

You can add custom attributes to a user or role in the form of a key\-value pair\. For more information about IAM tags, see [Tagging IAM resources](id_tags.md)\. You can use `aws:PrincipalTag` to [control access](access_iam-tags.md#access_iam-tags_control-principals) for AWS principals\.

This example shows how you might create an identity\-based policy that allows users with the **department=hr** tag to manage IAM users, groups, or roles\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "iam:*",
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "aws:PrincipalTag/department": "hr"
        }
      }
    }
  ]
}
```

This example shows how you might create a resource\-based policy with the `aws:PrincipalTag` key in the resource ARN\. The policy allows the `s3:GetObject` action only if the bucket name ends with a team name from the `team` principal tag\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": "*",
    "Action": "s3:GetObject",
    "Resource": "arn:aws:s3:::DOC-EXAMPLE-BUCKET-${aws:PrincipalTag/team}/"
  }
}
```

## aws:PrincipalType<a name="condition-keys-principaltype"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the type of principal making the request with the principal type that you specify in the policy\. For more information, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\. For specific examples of `principal` key values, see [Principal key values](reference_policies_variables.md#principaltable)\.
+ **Availability** – This key is included in the request context for all requests, including anonymous requests\.
+ **Value type** – Single\-valued

## aws:referer<a name="condition-keys-referer"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare who referred the request in the client browser with the referer that you specify in the policy\. The `aws:referer` request context value is provided by the caller in an HTTP header\. The `Referer` header is included in a web browser request when you select a link on a web page\. The `Referer` header contains the URL of the web page where the link was selected\.
+ **Availability** – This key is included in the request context only if the request to the AWS resource was invoked by linking from a web page URL in the browser\. This key is not included for programmatic requests because it doesn't use a browser link to access the AWS resource\.
+ **Value type** – Single\-valued

For example, you can access an Amazon S3 object directly using a URL or using direct API invocation\. For more information, see [Amazon S3 API operations directly using a web browser](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html#example-bucket-policies-use-case-4)\. When you access an Amazon S3 object from a URL that exists in a webpage, the URL of the source web page is in used in `aws:referer`\. When you access an Amazon S3 object by typing the URL into your browser, `aws:referer` is not present\. When you invoke the API directly, `aws:referer` is also not present\. You can use the `aws:referer` condition key in a policy to allow requests made from a specific referer, such as a link on a web page in your company's domain\. 

**Warning**  
This key should be used carefully\. It is dangerous to include a publicly known referer header value\. Unauthorized parties can use modified or custom browsers to provide any `aws:referer` value that they choose\. As a result, `aws:referer` should not be used to prevent unauthorized parties from making direct AWS requests\. It is offered only to allow customers to protect their digital content, such as content stored in Amazon S3, from being referenced on unauthorized third\-party sites\.

## aws:RequestedRegion<a name="condition-keys-requestedregion"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the AWS Region that was called in the request with the Region that you specify in the policy\. You can use this global condition key to control which Regions can be requested\. To view the AWS Regions for each service, see [Service endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html) in the *Amazon Web Services General Reference*\.
+ **Availability** – This key is always included in the request context\.
+ **Value type** – Single\-valued

Some global services, such as IAM, have a single endpoint\. Because this endpoint is physically located in the US East \(N\. Virginia\) Region, IAM calls are always made to the us\-east\-1 Region\. For example, if you create a policy that denies access to all services if the requested Region is not us\-west\-2, then IAM calls always fail\. To view an example of how to work around this, see [NotAction with Deny](reference_policies_elements_notaction.md)\. 

**Note**  
The `aws:RequestedRegion` condition key allows you to control which endpoint of a service is invoked but does not control the impact of the operation\. Some services have cross\-Region impacts\. For example, Amazon S3 has API operations that control cross\-Region replication\. You can invoke `s3:PutBucketReplication` in one Region \(which is affected by the `aws:RequestedRegion` condition key\), but other Regions are affected based on the replications configuration settings\. 

You can use this context key to limit access to AWS services within a given set of Regions\. For example, the following policy allows a user to view all of the Amazon EC2 instances in the AWS Management Console\. However it only allows them to make changes to instances in Ireland \(eu\-west\-1\), London \(eu\-west\-2\), or Paris \(eu\-west\-3\)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "InstanceConsoleReadOnly",
            "Effect": "Allow",
            "Action": [
                "ec2:Describe*",
                "ec2:Export*",
                "ec2:Get*",
                "ec2:Search*"
            ],
            "Resource": "*"
        },
        {
            "Sid": "InstanceWriteRegionRestricted",
            "Effect": "Allow",
            "Action": [
                "ec2:Associate*",
                "ec2:Import*",
                "ec2:Modify*",
                "ec2:Monitor*",
                "ec2:Reset*",
                "ec2:Run*",
                "ec2:Start*",
                "ec2:Stop*",
                "ec2:Terminate*"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws:RequestedRegion": [
                        "eu-west-1",
                        "eu-west-2",
                        "eu-west-3"
                    ]
                }
            }
        }
    ]
}
```

## aws:RequestTag/*tag\-key*<a name="condition-keys-requesttag"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the tag key\-value pair that was passed in the request with the tag pair that you specify in the policy\. For example, you could check whether the request includes the tag key `"Dept"` and that it has the value `"Accounting"`\. For more information, see [Controlling access during AWS requests](access_tags.md#access_tags_control-requests)\.
+ **Availability** – This key is included in the request context when tag key\-value pairs are passed in the request\. When multiple tags are passed in the request, there is one context key for each tag key\-value pair\.
+ **Value type** – Single\-valued

This context key is formatted `"aws:RequestTag/tag-key":"tag-value"` where *tag\-key* and *tag\-value* are a tag key and value pair\. Tag keys and values are not case\-sensitive\. This means that if you specify `"aws:RequestTag/TagKey1": "Value1"` in the condition element of your policy, then the condition matches a request tag key named either `TagKey1` or `tagkey1`, but not both\.

This example shows that while the key is single\-valued, you can still use multiple key\-value pairs in a request if the keys are different\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "ec2:CreateTags",
    "Resource": "arn:aws:ec2:::instance/*",
    "Condition": {
      "StringEquals": {
        "aws:RequestTag/environment": [
          "preprod",
          "production"
        ],
        "aws:RequestTag/team": [
          "engineering"
        ]
      }
    }
  }
}
```

## aws:ResourceAccount<a name="condition-keys-resourceaccount"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the requested resource owner's [AWS account ID](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) with the resource account in the policy\. You can then allow or deny access to that resource based on the account that owns the resource\.
+ **Availability** – This key is always included in the request context for most service actions\. The following actions don't support this key:
  + Amazon Elastic Block Store – All actions
  + Amazon EC2
    + `ec2:CopyFpgaImage`
    + `ec2:CopyImage`
    + `ec2:CopySnapshot`
    + `ec2:CreateTransitGatewayPeeringAttachment`
    + `ec2:CreateVolume`
    + `ec2:CreateVpcPeeringConnection`
  + Amazon EventBridge – All actions
  + Amazon WorkSpaces
    + `workspaces:CopyWorkspaceImage`
    + `workspaces:DescribeWorkspaceImages`
+ **Value type** – Single\-valued

This key is equal to the AWS account ID for the account with the resources evaluated in the request\.

For most resources in your account, the [ARN](reference_policies_elements_condition_operators.md#Conditions_ARN) contains the owner account ID for that resource\. For certain resources, such as Amazon S3 buckets, the resource ARN does not include the account ID\. The following two examples show the difference between a resource with an account ID in the ARN, and an Amazon S3 ARN without an account ID:
+ `arn:aws:iam::123456789012:role/AWSExampleRole` – IAM role created and owned within the account 123456789012\. 
+ `arn:aws:s3:::DOC-EXAMPLE-BUCKET2` – Amazon S3 bucket created and owned within the account `111122223333`, not displayed in the ARN\.

Use the AWS console, or API, or CLI, to find all of your resources and corresponding ARNs\.

You write a policy that denies permissions to resources based on the resource owner's account ID\. For example, the following identity\-based policy denies access to the *specified resource* if the resource does not belong to the *specified account*\.

To use this policy, replace the *italicized placeholder text* with your account information\. 

**Important**  
This policy does not allow any actions\. Instead, it uses the `Deny` effect which explicitly denies access to all of the resources listed in the statement that do not belong to the listed account\. Use this policy in combination with other policies that allow access to specific resources\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyInteractionWithResourcesNotInSpecificAccount",
      "Action": "service:*",
      "Effect": "Deny",
      "Resource": [
        "arn:partition:service:region:account:*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "account"
          ]
        }
      }
    }
  ]
}
```

This policy denies access to all resources for a specific AWS service unless the specified AWS account owns the resource\. 

**Note**  
Some AWS services require access to AWS owned resources that are hosted in another AWS account\. Using `aws:ResourceAccount` in your identity\-based policies might impact your identity's ability to access these resources\.

Certain AWS services, such as AWS Data Exchange, rely on access to resources outside of your AWS accounts for normal operations\. If you use the element `aws:ResourceAccount` in your policies, include additional statements to create exemptions for those services\. The example policy [AWS: Deny access to Amazon S3 resources outside your account except AWS Data Exchange](reference_policies_examples_resource_account_data_exch.md) demonstrates how to deny access based on the resource account while defining exceptions for service\-owned resources\.

Use this policy example as a template for creating your own custom policies\. Refer to your service [documentation](https://docs.aws.amazon.com/index.html) for more information\.

## aws:ResourceOrgID<a name="condition-keys-resourceorgid"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the identifier of the organization in AWS Organizations to which the requested resource belongs with the identifier specified in the policy\.
+ **Availability** – This key is included in the request context only if the account that owns the resource is a member of an organization\. This global condition key does not support the following actions:
  + Amazon Elastic Block Store – All actions
  + Amazon EC2
    + `ec2:CopyFpgaImage`
    + `ec2:CopyImage`
    + `ec2:CopySnapshot`
    + `ec2:CreateTransitGatewayPeeringAttachment`
    + `ec2:CreateVolume`
    + `ec2:CreateVpcPeeringConnection`
  + Amazon EventBridge – All actions
+ **Value type** – Single\-valued

This global key returns the resource organization ID for a given request\. It allows you to create rules that apply to all resources in an organization that are specified in the `Resource` element of an [identity\-based policy](access_policies_identity-vs-resource.md)\. You can specify the [organization ID](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_details.html) in the condition element\. When you add and remove accounts, policies that include the `aws:ResourceOrgID` key automatically include the correct accounts and you don't have to manually update it\.

For example, the following policy prevents the principal from adding objects to the `policy-genius-dev` resource unless the Amazon S3 resource belongs to the same organization as the principal making the request\.

**Important**  
This policy does not allow any actions\. Instead, it uses the `Deny` effect which explicitly denies access to all of the resources listed in the statement that do not belong to the listed account\. Use this policy in combination with other policies that allow access to specific resources\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Sid": "DenyPutObjectToS3ResourcesOutsideMyOrganization",
    "Effect": "Deny",
    "Action": "s3:PutObject",
    "Resource": "arn:partition:s3:::policy-genius-dev/*",
    "Condition": {
      "StringNotEquals": {
        "aws:ResourceOrgID": "${aws:PrincipalOrgID}"
      }
    }
  }
}
```

**Note**  
Some AWS services require access to AWS owned resources that are hosted in another AWS account\. Using `aws:ResourceOrgID` in your identity\-based policies might impact your identity's ability to access these resources\.

Certain AWS services, such as AWS Data Exchange, rely on access to resources outside of your AWS accounts for normal operations\. If you use the `aws:ResourceOrgID` key in your policies, include additional statements to create exemptions for those services\. The example policy [AWS: Deny access to Amazon S3 resources outside your account except AWS Data Exchange](reference_policies_examples_resource_account_data_exch.md) demonstrates how to deny access based on the resource account while defining exceptions for service\-owned resources\. You can create a similar policy to restrict access to resources within your organization using the `aws:ResourceOrgID` key, while accounting for service\-owned resources\.

Use this policy example as a template for creating your own custom policies\. Refer to your service [documentation](https://docs.aws.amazon.com/index.html) for more information\.

## aws:ResourceOrgPaths<a name="condition-keys-resourceorgpaths"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the AWS Organizations path for the accessed resource to the path in the policy\. In a policy, this condition key ensures that the resource belongs to an account member within the specified organization root or organizational units \(OUs\) in AWS Organizations\. An AWS Organizations path is a text representation of the structure of an Organizations entity\. For more information about using and understanding paths, see [Understand the AWS Organizations entity path](access_policies_access-advisor-view-data-orgs.md#access_policies_access-advisor-viewing-orgs-entity-path) 
+ **Availability** – This key is included in the request context only if the account that owns the resource is a member of an organization\. This global condition key does not support the following actions:
  + Amazon Elastic Block Store – All actions
  + Amazon EC2
    + `ec2:CopyFpgaImage`
    + `ec2:CopyImage`
    + `ec2:CopySnapshot`
    + `ec2:CreateTransitGatewayPeeringAttachment`
    + `ec2:CreateVolume`
    + `ec2:CreateVpcPeeringConnection`
  + Amazon EventBridge – All actions
  + Amazon WorkSpaces
    + `workspaces:CopyWorkspaceImage`
    + `workspaces:DescribeWorkspaceImages`
+ **Value type** – Multivalued

`aws:ResourceOrgPaths` is a multivalued condition key\. Multivalued keys can have multiple values in the request context\. You must use the `ForAnyValue` or `ForAllValues` set operators with [string condition operators](reference_policies_elements_condition_operators.md#Conditions_String) for this key\. For more information about multivalued condition keys, see [Using multiple keys and values](reference_policies_multi-value-conditions.md#reference_policies_multi-key-or-value-conditions)\.

For example, the following condition returns `True` for resources that belong to the organization `o-a1b2c3d4e5`\. When you include a wildcard, you must use the [StringLike](reference_policies_elements_condition_operators.md) condition operator\.

```
"Condition": { 
      "ForAnyValue:StringLike": {
             "aws:ResourceOrgPaths":["o-a1b2c3d4e5/*"]
   }
}
```

The following condition returns `True` for resources with the OU ID `ou-ab12-11111111`\. It will match resources owned by accounts attached to the OU ou\-ab12\-11111111 or any of the child OUs\.

```
"Condition": { "ForAnyValue:StringLike" : {
     "aws:ResourceOrgPaths":["o-a1b2c3d4e5/r-ab12/ou-ab12-11111111/*"]
}}
```

The following condition returns `True` for resources owned by accounts attached directly to the OU ID `ou-ab12-22222222`, but not the child OUs\. The following example uses the [StringEquals](reference_policies_elements_condition_operators.md) condition operator to specify the exact match requirement for the OU ID and not a wildcard match\.

```
"Condition": { "ForAnyValue:StringEquals" : {
     "aws:ResourceOrgPaths":["o-a1b2c3d4e5/r-ab12/ou-ab12-11111111/ou-ab12-22222222/"]
}}
```

**Note**  
Some AWS services require access to AWS owned resources that are hosted in another AWS account\. Using `aws:ResourceOrgPaths` in your identity\-based policies might impact your identity's ability to access these resources\.

Certain AWS services, such as AWS Data Exchange, rely on access to resources outside of your AWS accounts for normal operations\. If you use the `aws:ResourceOrgPaths` key in your policies, include additional statements to create exemptions for those services\. The example policy [AWS: Deny access to Amazon S3 resources outside your account except AWS Data Exchange](reference_policies_examples_resource_account_data_exch.md) demonstrates how to deny access based on the resource account while defining exceptions for service\-owned resources\. You can create a similar policy to restrict access to resources within an organizational unit \(OU\) using the `aws:ResourceOrgPaths` key, while accounting for service\-owned resources\.

Use this policy example as a template for creating your own custom policies\. Refer to your service [documentation](https://docs.aws.amazon.com/index.html) for more information\.

## aws:ResourceTag/*tag\-key*<a name="condition-keys-resourcetag"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the tag key\-value pair that you specify in the policy with the key\-value pair attached to the resource\. For example, you could require that access to a resource is allowed only if the resource has the attached tag key `"Dept"` with the value `"Marketing"`\. For more information, see [Controlling access to AWS resources](access_tags.md#access_tags_control-resources)\.
+ **Availability** – This key is included in the request context when the requested resource already has attached tags or in requests that create a resource with an attached tag\. This key is returned only for resources that [support authorization based on tags](reference_aws-services-that-work-with-iam.md)\. There is one context key for each tag key\-value pair\.
+ **Value type** – Single\-valued

This context key is formatted `"aws:ResourceTag/tag-key":"tag-value"` where *tag\-key* and *tag\-value* are a tag key and value pair\. Tag keys and values are not case\-sensitive\. This means that if you specify `"aws:ResourceTag/TagKey1": "Value1"` in the condition element of your policy, then the condition matches a resource tag key named either `TagKey1` or `tagkey1`, but not both\.

For examples of using the `aws:ResourceTag` key to control access to IAM resources, see [Controlling access to AWS resources](access_tags.md#access_tags_control-resources)\.

For examples of using the `aws:ResourceTag` key to control access to other AWS resources, see [Controlling access to AWS resources using tags](access_tags.md)\.

For a tutorial on using the `aws:ResourceTag` condition key for attribute based access control \(ABAC\), see [IAM tutorial: Define permissions to access AWS resources based on tags](tutorial_attribute-based-access-control.md)\.

## aws:SecureTransport<a name="condition-keys-securetransport"></a>

Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.

Use this key to check whether the request was sent using SSL\. The request context returns `true` or `false`\. In a policy, you can allow specific actions only if the request is sent using SSL\.
+ **Availability** – This key is always included in the request context\.
+ **Value type** – Single\-valued

## aws:SourceAccount<a name="condition-keys-sourceaccount"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the account ID of the resource making a service\-to\-service request with the account ID that you specify in the policy\. 
+ **Availability** – This key is included in the request context only if accessing a resource triggers an AWS service to call another service on behalf of the resource owner\. The calling service must pass the resource account ID of the source to the called service\. This account ID includes the source account ID\.
+ **Value type** – Single\-valued

You can use this condition key to prevent an AWS service from being used as a [confused deputy](confused-deputy.md) during transactions between services\. Set the value of this condition key to the account of the resource in the request\. For example, when an Amazon S3 bucket update triggers an Amazon SNS topic post, the Amazon S3 service invokes the `sns:Publish` API operation\. In the policy that allows the `sns:Publish` operation, set the value of the condition key to the account ID of the Amazon S3 bucket\. For information about how and when these condition keys are recommended, see the documentation for the AWS services you are using\.

## aws:SourceArn<a name="condition-keys-sourcearn"></a>

Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN) and [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\. AWS recommends that you use ARN operators instead of string operators when comparing ARNs\.

Use this key to compare the [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns) of the resource making a service\-to\-service request with the ARN that you specify in the policy\. 

This key does not work with the ARN of the principal making the request\. Instead, use [aws:PrincipalArn](#condition-keys-principalarn)\. The source's ARN includes the account ID, so it is not necessary to use `aws:SourceAccount` with `aws:SourceArn`\.
+ **Availability** – This key is included in the request context only if accessing a resource triggers an AWS service to call another service on behalf of the resource owner\. The calling service must pass the ARN of the original resource to the called service\.
+ **Value type** – Single\-valued

You can use this condition key to prevent an AWS service from being used as a [confused deputy](confused-deputy.md) during transactions between services\. Set the value of this condition key to the ARN of the resource in the request\. For example, when an Amazon S3 bucket update triggers an Amazon SNS topic post, the Amazon S3 service invokes the `sns:Publish` API operation\. In the policy that allows the `sns:Publish` operation, set the value of the condition key to the ARN of the Amazon S3 bucket\. For information about how and when these condition keys are recommended, see the documentation for the AWS services you are using\.

## aws:SourceIdentity<a name="condition-keys-sourceidentity"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the source identity that was set by the principal with the source identity that you specify in the policy\. 
+ **Availability** – This key is included in the request context after a source identity has been set when a role is assumed using any AWS STS assume\-role CLI command, or AWS STS `AssumeRole` API operation\.
+ **Value type** – Single\-valued

You can use this key in a policy to allow actions in AWS by principals that have set a source identity when assuming a role\. Activity for the role's specified source identity appears in [AWS CloudTrail](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds)\. This makes it easier for administrators to determine who or what performed actions with a role in AWS\.

Unlike [`sts:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname), after the source identity is set, the value cannot be changed\. It is present in the request context for all actions taken by the role\. The value persists into subsequent role sessions when you use the session credentials to assume another role\. Assuming one role from another is called [role chaining](id_roles_terms-and-concepts.md#iam-term-role-chaining)\. 

The [`sts:SourceIdentity`](reference_policies_iam-condition-keys.md#ck_sourceidentity) key is present in the request when the principal initially sets a source identity while assuming a role using any AWS STS assume\-role CLI command, or AWS STS `AssumeRole` API operation\. The `aws:SourceIdentity` key is present in the request for any actions that are taken with a role session that has a source identity set\.

The following role trust policy for `CriticalRole` in account `111122223333` contains a condition for `aws:SourceIdentity` that prevents a principal without a source identity that is set to Saanvi or Diego from assuming the role\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AssumeRoleIfSourceIdentity",
            "Effect": "Allow",
            "Principal": {"AWS": " arn:aws:iam::123456789012:role/CriticalRole"},
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

To learn more about using source identity information, see [Monitor and control actions taken with assumed roles](id_credentials_temp_control-access_monitor.md)\.

## aws:SourceIp<a name="condition-keys-sourceip"></a>

Works with [IP address operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.

Use this key to compare the requester's IP address with the IP address that you specify in the policy\. The `aws:SourceIp` condition key can only be used for public IP address ranges\.
+ **Availability** – This key is included in the request context, except when the requester uses a VPC endpoint to make the request\.
+ **Value type** – Single\-valued

The `aws:SourceIp` condition key can be used in a policy to allow principals to make requests only from within a specified IP range\. However, this policy denies access if an AWS service makes calls on the principal's behalf\. In this case, you can use `aws:SourceIp` with the `aws:ViaAWSService` key to ensure that the source IP restriction applies only to requests made directly by a principal\. 

For example, you can attach the following policy to an IAM user\. This policy allows the user to put an object into the `DOC-EXAMPLE-BUCKET3` Amazon S3 bucket directly if they make the call from the specified IP address\. However, if the user makes another request that causes a service to call Amazon S3, the IP address restriction does not apply\. The `PrincipalPutObjectIfIpAddress` statement restricts the IP address only if the request is not made by a service\. The `ServicePutObject` statement allows the operation without IP address restriction if the request is made by a service\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PrincipalPutObjectIfIpAddress",
            "Effect": "Allow",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::DOC-EXAMPLE-BUCKET3/*",
            "Condition": {
                "Bool": {"aws:ViaAWSService": "false"},
                "IpAddress": {"aws:SourceIp": "203.0.113.0"}
            }
        },
        {
            "Sid": "ServicePutObject",
            "Effect": "Allow",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*",
            "Condition": {
                "Bool": {"aws:ViaAWSService": "true"}
            }
        }
    ]
}
```

If the request comes from a host that uses an Amazon VPC endpoint, then the `aws:SourceIp` key is not available\. You should instead use a VPC\-specific key such as [aws:VpcSourceIp](#condition-keys-sourceip)\. For more information about using VPC endpoints, see [Identity and access management for VPC endpoints and VPC endpoint services](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-iam.html) in the *AWS PrivateLink Guide*\.

## aws:SourceVpc<a name="condition-keys-sourcevpc"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to check whether the request comes from the VPC that you specify in the policy\. In a policy, you can use this key to allow access to only a specific VPC\. For more information, see [Restricting Access to a Specific VPC](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc) in the *Amazon Simple Storage Service User Guide*\. 
+ **Availability** – This key is included in the request context only if the requester uses a VPC endpoint to make the request\.
+ **Value type** – Single\-valued

## aws:SourceVpce<a name="condition-keys-sourcevpce"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the VPC endpoint identifier of the request with the endpoint ID that you specify in the policy\. In a policy, you can use this key to restrict access to a specific VPC endpoint\. For more information, see [Restricting Access to a Specific VPC Endpoint](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc-endpoint) in the *Amazon Simple Storage Service User Guide*\.
+ **Availability** – This key is included in the request context only if the requester uses a VPC endpoint to make the request\.
+ **Value type** – Single\-valued

## aws:TagKeys<a name="condition-keys-tagkeys"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the tag keys in a request with the keys that you specify in the policy\. We recommend that when you use policies to control access using tags, use the `aws:TagKeys` condition key to define what tag keys are allowed\. For example policies and more information, see [Controlling access based on tag keys](access_tags.md#access_tags_control-tag-keys)\.
+ **Availability** – This key is included in the request context if the operation supports passing tags in the request\.
+ **Value type** – Multivalued

This context key is formatted `"aws:TagKeys":"tag-key"` where *tag\-key* is a list of tag keys without values \(for example, `["Dept","Cost-Center"]`\)\.

Because you can include multiple tag key\-value pairs in a request, the request content could be a [multivalued](reference_policies_multi-value-conditions.md) request\. In this case, you must use the `ForAllValues` or `ForAnyValue` set operators\. For more information, see [Using multiple keys and values](reference_policies_multi-value-conditions.md#reference_policies_multi-key-or-value-conditions)\.

Some services support tagging with resource operations, such as creating, modifying, or deleting a resource\. To allow tagging and operations as a single call, you must create a policy that includes both the tagging action and the resource\-modifying action\. You can then use the `aws:TagKeys` condition key to enforce using specific tag keys in the request\. For example, to limit tags when someone creates an Amazon EC2 snapshot, you must include the `ec2:CreateSnapshot` creation action ***and*** the `ec2:CreateTags` tagging action in the policy\. To view a policy for this scenario that uses `aws:TagKeys`, see [Creating a Snapshot with Tags](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ExamplePolicies_EC2.html#iam-creating-snapshot-with-tags) in the *Amazon EC2 User Guide for Linux Instances*\. 

## aws:TokenIssueTime<a name="condition-keys-tokenissuetime"></a>

Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.

Use this key to compare the date and time that temporary security credentials were issued with the date and time that you specify in the policy\. 
+ **Availability** – This key is included in the request context only when the principal uses temporary credentials to make the request\. The key is not present in AWS CLI, AWS API, or AWS SDK requests that are made using access keys\.
+ **Value type** – Single\-valued

To learn which services support using temporary credentials, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

## aws:UserAgent<a name="condition-keys-useragent"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the requester's client application with the application that you specify in the policy\.
+ **Availability** – This key is always included in the request context\.
+ **Value type** – Single\-valued

**Warning**  
This key should be used carefully\. Since the `aws:UserAgent` value is provided by the caller in an HTTP header, unauthorized parties can use modified or custom browsers to provide any `aws:UserAgent` value that they choose\. As a result, `aws:UserAgent` should not be used to prevent unauthorized parties from making direct AWS requests\. You can use it to allow only specific client applications, and only after testing your policy\.

## aws:userid<a name="condition-keys-userid"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the requester's principal identifier with the ID that you specify in the policy\. For IAM users, the request context value is the user ID\. For IAM roles, this value format can vary\. For details about how the information appears for different principals, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\. For specific examples of `principal` key values, see [Principal key values](reference_policies_variables.md#principaltable)\.
+ **Availability** – This key is included in the request context for all requests, including anonymous requests\.
+ **Value type** – Single\-valued

## aws:username<a name="condition-keys-username"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the requester's user name with the user name that you specify in the policy\. For details about how the information appears for different principals, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\. For specific examples of `principal` key values, see [Principal key values](reference_policies_variables.md#principaltable)\.
+ **Availability** – This key is always included in the request context for IAM users\. Anonymous requests and requests that are made using the AWS account root user or IAM roles do not include this key\. Requests made using IAM Identity Center credentials do not include this key in the context\. To learn how to control access to users in IAM Identity Center, see `identitystore:UserId` in [Using predefined attributes from the IAM Identity Center identity store for access control in AWS](https://docs.aws.amazon.com/singlesignon/latest/userguide/using-predefined-attributes.html)\. Users in IAM Identity Center are the people in your workforce who need access to your AWS accounts or to your cloud applications\.
+ **Value type** – Single\-valued

## aws:ViaAWSService<a name="condition-keys-viaawsservice"></a>

Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.

Use this key to check whether an AWS service makes a request to another service on your behalf\.

The request context key returns `true` when a service uses the credentials of an IAM principal to make a request on behalf of the principal\. The context key returns `false` if the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\. The request context key also returns `false` when the principal makes the call directly\.
+ **Availability** – This key is always included in the request context\.
+ **Value type** – Single\-valued

You can use this condition key to allow or deny access based on whether a request was made by a service\. To view an example policy, see [AWS: Denies access to AWS based on the source IP](reference_policies_examples_aws_deny-ip.md)\.

## aws:VpcSourceIp<a name="condition-keys-vpcsourceip"></a>

Works with [IP address operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.

Use this key to compare the IP address from which a request was made with the IP address that you specify in the policy\. In a policy, the key matches only if the request originates from the specified IP address and it goes through a VPC endpoint\.
+ **Availability** – This key is included in the request context only if the request is made using a VPC endpoint\.
+ **Value type** – Single\-valued

For more information, see [Controlling Access to Services with VPC Endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints-access.html) in the *Amazon VPC User Guide*\.

## Other cross\-service condition keys<a name="condition-keys-other"></a>

Global condition keys are condition keys with an `aws:` prefix\. Individual services can create their own condition keys\. These service\-specific condition keys include a prefix that matches the name of the service, such as `iam:` or `sts:`\.

Services can create service\-specific keys that are available in the request context for other services\. These keys are available across multiple services, but are not global condition keys\. For example, AWS STS supports [SAML\-based federation condition keys](reference_policies_iam-condition-keys.md#condition-keys-saml)\. These keys are available when a user who was federated using SAML performs AWS operations in other services\. Other examples include `[identitystore:UserId](https://docs.aws.amazon.com/singlesignon/latest/userguide/using-predefined-attributes.html)` and `[ec2:SourceInstanceArn](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)`\.

To view the service\-specific condition keys for a service, see [Actions, Resources, and Condition Keys for AWS Services](https://docs.aws.amazon.com/service-authorization/latest/reference/reference_policies_actions-resources-contextkeys.html) and choose the service whose keys you want to view\.