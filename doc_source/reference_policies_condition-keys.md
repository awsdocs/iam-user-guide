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

## aws:CalledVia<a name="condition-keys-calledvia"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the services in the policy with the services that made requests on behalf of the IAM principal \(user or role\)\. When a principal makes a request to an AWS service, that service might use the principal's credentials to make subsequent requests to other services\. The `aws:CalledVia` key contains an ordered list of each service in the chain that made requests on the principal's behalf\.

For example, you can use AWS CloudFormation to read and write from an Amazon DynamoDB table\. DynamoDB then uses encryption supplied by AWS Key Management Service \(AWS KMS\)\.
+ **Availability** – This key is present in the request when a service that supports `aws:CalledVia` uses the credentials of an IAM principal to make a request to another service\. This key is not present if the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\. This key is also not present when the principal makes the call directly\.<a name="calledvia-services"></a>

To use the `aws:CalledVia` condition key in a policy, you must provide the service principals to allow or deny AWS service requests\. AWS supports using the following services with `aws:CalledVia`\.


**CalledVia services**  

| AWS service | Service principal | 
| --- | --- | 
| Amazon Athena | athena\.amazonaws\.com | 
| AWS CloudFormation | cloudformation\.amazonaws\.com | 
| Amazon DynamoDB | dynamodb\.amazonaws\.com | 
| AWS Key Management Service \(AWS KMS\) | kms\.amazonaws\.com | 

To allow or deny access when *any* service makes a request using the principal's credentials, use the `` condition key\. That condition key supports all AWS services\.

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

## aws:CalledViaLast<a name="condition-keys-calledvialast"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the services in the policy with the *last service* that made a request on behalf of the IAM principal \(user or role\)\. For more information, see `aws:CalledVia`\.
+ **Availability** – This key is present in the request when a service uses the credentials of an IAM principal to make at least one other request to a different service\. This key is not present if the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\. This key is also not present when the principal makes the call directly\.

## aws:CurrentTime<a name="condition-keys-currenttime"></a>

Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.

Use this key to compare the date and time of the request with the date and time that you specify in the policy\. To view an example policy that uses this condition key, see [AWS: Allows access based on date and time](reference_policies_examples_aws-dates.md)\.
+ **Availability** – This key is always included in the request context\.

## aws:EpochTime<a name="condition-keys-epochtime"></a>

Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date) or [numeric operators](reference_policies_elements_condition_operators.md#Conditions_Numeric)\.

Use this key to compare the date and time of the request in epoch or Unix time with the value that you specify in the policy\. This key also accepts the number of seconds since January 1, 1970\. 
+ **Availability** – This key is always included in the request context\.

## aws:MultiFactorAuthAge<a name="condition-keys-multifactorauthage"></a>

Works with [numeric operators](reference_policies_elements_condition_operators.md#Conditions_Numeric)\.

Use this key to compare the number of seconds since the requesting principal was authorized using MFA with the number that you specify in the policy\. For more information about MFA, see [Using multi\-factor authentication \(MFA\) in AWS](id_credentials_mfa.md)\.
+ **Availability** – This key is included in the request context only if the principal making the call was authenticated using MFA\. If MFA was not used, this key is not present\.

## aws:MultiFactorAuthPresent<a name="condition-keys-multifactorauthpresent"></a>

Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.

Use this key to check whether multi\-factor authentication \(MFA\) was used to validate the temporary security credentials that made the request\.
+ **Availability** – This key is included in the request context only when the principal uses temporary credentials to make the request\. The key is not present in AWS CLI, AWS API, or AWS SDK requests that are made using long\-term credentials\. 

Temporary credentials are used to authenticate IAM roles, federated users, IAM users with temporary tokens from `sts:GetSessionToken`, and users of the AWS Management Console\. IAM user access keys are long\-term credentials, but in some cases, AWS creates temporary credentials on behalf of IAM users to perform operations\. In these cases, the `aws:MultiFactorAuthPresent` key is present in the request and set to a value of `false`\. There are two common cases where this can happen:
+ IAM users in the AWS Management Console unknowingly use temporary credentials\. Users sign into the console using their user name and password, which are long\-term credentials\. However, in the background, the console generates temporary credentials on behalf of the user\. 
+ If an IAM user makes a call to an AWS service, the service re\-uses the user's credentials to make another request to a different service\. For example, when calling Athena to access an Amazon S3 bucket, or when using AWS CloudFormation to create an Amazon EC2 instance\. For the subsequent request, AWS uses temporary credentials\.

To learn which services support using temporary credentials, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

The `aws:MultiFactorAuthPresent` key is not present when an API or CLI command is called with long\-term credentials, such as user access key pairs\. Therefore we recommend that when you check for this key that you use the `...IfExists` versions of the condition operators\.

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

Use this key to compare the account to which the requesting principal belongs with the account identifier that you specify in the policy\.
+ **Availability** – This key is always included in the request context\.

## aws:PrincipalArn<a name="condition-keys-principalarn"></a>

Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN) and [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the [Amazon Resource Name](reference_identifiers.md#identifiers-arns) \(ARN\) of the principal that made the request with the ARN that you specify in the policy\. For IAM roles, the request context returns the ARN of the role, not the ARN of the user that assumed the role\. To learn which types of principals you can specify in this condition key, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\.
+ **Availability** – This key is always included in the request context\.

## aws:PrincipalOrgID<a name="condition-keys-principalorgid"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the identifier of the organization in AWS Organizations to which the requesting principal belongs with the identifier specified in the policy\.
+ **Availability** – This key is included in the request context only if the principal is a member of an organization\.

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
      {"aws:PrincipalOrgID":["o-xxxxxxxxxxx"]}
    }
  }
}
```

**Note**  
This global condition also applies to the master account of an AWS organization\.

For more information about AWS Organizations, see [What Is AWS Organizations?](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) in the *AWS Organizations User Guide*\.

## aws:PrincipalOrgPaths<a name="condition-keys-principalorgpaths"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the AWS Organizations path for the principal who is making the request to the path in the policy\. That principal can be an IAM user, IAM role, federated user, or AWS account root user\. In a policy, this condition key ensures that the requester is an account member within the specified organization root or organizational units \(OUs\) in AWS Organizations\. An AWS Organizations path is a text representation of the structure of an Organizations entity\. For more information about using and understanding paths, see [Understand the AWS Organizations entity path](access_policies_access-advisor-view-data-orgs.md#access_policies_access-advisor-viewing-orgs-entity-path)\.
+ **Availability** – This key is included in the request context only if the principal is a member of an organization\.

**Note**  
Organization IDs are globally unique but OU IDs and root IDs are unique only within an organization\. This means that no two organizations share the same organization ID\. However, another organization might have an OU or root with the same ID as yours\. We recommend that you always include the organization ID when you specify an OU or root\.

For example, the following condition returns `true` for principals in accounts that are attached directly to the `ou-jkl0-awsddddd` OU, but not in its child OUs\.

```
"Condition" : { "ForAnyValue:StringEquals" : {
     "aws:PrincipalOrgPaths":["o-a1b2c3d4e5/r-f6g7h8i9j0example/ou-ghi0-awsccccc/ou-jkl0-awsddddd/"]
}}
```

The following condition returns `true` for principals in an account that is attached directly to the OU or any of its child OUs\. When you include a wildcard, you must use the `StringLike` condition operator\.

```
"Condition" : { "ForAnyValue:StringLike" : {
     "aws:PrincipalOrgPaths":["o-a1b2c3d4e5/r-f6g7h8i9j0example/ou-ghi0-awsccccc/ou-jkl0-awsddddd*"]
}}
```

The following condition returns `true` for principals in an account that is attached directly to the OU or any of its child OUs\.

```
"Condition" : { "ForAnyValue:StringLike" : {
     "aws:PrincipalOrgPaths":["o-a1b2c3d4e5/r-f6g7h8i9j0example/ou-ghi0-awsccccc/ou-jkl0-awsddddd/*"]
}}
```

The following condition allows access for every principal in the `o-a1b2c3d4e5` organization, regardless of their parent OU\.

```
"Condition" : { "ForAnyValue:StringLike" : {
     "aws:PrincipalOrgPaths":["o-a1b2c3d4e5/*"]
}}
```

`aws:PrincipalOrgPaths` is a multivalued condition key\. Multivalued keys include one or more values in a list format\. The result is a logical `OR`\. When you use multiple values with the `ForAnyValue` condition operator, the principal's path must match one of the paths listed in the policy\. For policies that include multiple values for a single key, you must enclose the conditions within brackets like an array \("Key":\["Value1", "Value2"\]\)\. You should also include these brackets when there is a single value\. For more information about multivalued condition keys, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)\.

```
    "Condition": {
        "ForAnyValue:StringLike": {
            "aws:PrincipalOrgPaths": [
                "o-a1b2c3d4e5/r-f6g7h8i9j0example/ou-def0-awsbbbbb/*",
                "o-a1b2c3d4e5/r-f6g7h8i9j0example/ou-jkl0-awsddddd/*"
            ]
        }
    }
```

## aws:PrincipalTag<a name="condition-keys-principaltag"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the tag attached to the principal making the request with the tag that you specify in the policy\. If the principal has more than one tag attached, the request context includes one `aws:PrincipalTag` key for each attached tag key\.
+ **Availability** – This key is included in the request context if the principal is using an IAM user with attached tags\. It is included for a principal using an IAM role with attached tags or [session tags](id_session-tags.md)\.

You can add custom attributes to a user or role in the form of a key\-value pair\. For more information about IAM tags, see [Tagging IAM users and roles](id_tags.md)\. You can use `aws:PrincipalTag` to [control access](access_iam-tags.md#access_iam-tags_control-resources) for AWS principals\.

This example shows how you might create a policy that allows users with the **tagManager=true** tag to manage IAM users, groups, or roles\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "iam:*",
      "Resource": "*",
      "Condition": {"StringEquals": {"aws:PrincipalTag/tagManager": "true"}}
    }
  ]
}
```

## aws:PrincipalType<a name="condition-keys-principaltype"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the type of principal making the request with the principal type that you specify in the policy\. For more information, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\.
+ **Availability** – This key is always included in the request context\.

## aws:referer<a name="condition-keys-referer"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare who referred the request in the client browser with the referer that you specify in the policy\. The `aws:referer` request context value is provided by the caller in an HTTP header\.
+ **Availability** – This key is included in the request context only if the request was invoked using a URL in the browser\.

For example, you can call [Amazon S3 API operations directly using a web browser](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html#example-bucket-policies-use-case-4)\. This means that you can view S3 objects, such as images and documents, directly through a web browser\. The `aws:referer` condition allows you to restrict access to specific values in the HTTP or HTTPS request based on the value of the referrer header\.

**Warning**  
This key should be used carefully\. It is dangerous to include a publicly known referer header value\. Unauthorized parties can use modified or custom browsers to provide any `aws:referer` value that they choose\. As a result, `aws:referer` should not be used to prevent unauthorized parties from making direct AWS requests\. It is offered only to allow customers to protect their digital content, such as content stored in Amazon S3, from being referenced on unauthorized third\-party sites\.

## aws:RequestedRegion<a name="condition-keys-requestedregion"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the AWS Region that was called in the request with the Region that you specify in the policy\. You can use this global condition key to control which Regions can be requested\. To view the AWS Regions for each service, see [Service endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html) in the *Amazon Web Services General Reference*\.
+ **Availability** – This key is always included in the request context\.

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
+ **Availability** – This key is included in the request context when tags are passed in the request\. When multiple tags are passed in the request, there is one context key for each tag key\-value pair\.

This context key is formatted `"aws:RequestTag/tag-key":"tag-value"` where *tag\-key* and *tag\-value* are a tag key and value pair\.

Because you can include multiple tag key\-value pairs in a request, the request content could be a [multivalued](reference_policies_multi-value-conditions.md) request\. In this case, you should consider using the `ForAllValues` or `ForAnyValue` set operators\. For more information, see [Using multiple keys and values](reference_policies_multi-value-conditions.md#reference_policies_multi-key-or-value-conditions)\.

## aws:ResourceTag/*tag\-key*<a name="condition-keys-resourcetag"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the tag key\-value pair that you specify in the policy with the key\-value pair that is attached to the resource\. For example, you could require that access to a resource is allowed only if the resource has the attached tag key `"Dept"` with the value `"Marketing"`\. For more information, see [Controlling access to AWS resources](access_tags.md#access_tags_control-resources)\.
+ **Availability** – This key is included in the request context when the requested resource already has attached tags\. This key is returned only for resources that [support authorization based on tags](reference_aws-services-that-work-with-iam.md)\. There is one context key for each tag key\-value pair\.

This context key is formatted `"aws:ResourceTag/tag-key":"tag-value"` where *tag\-key* and *tag\-value* are a tag key and value pair\.

## aws:SecureTransport<a name="condition-keys-securetransport"></a>

Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.

Use this key to check whether the request was sent using SSL\. The request context returns `true` or `false`\. In a policy, you can allow specific actions only if the request is sent using SSL\.
+ **Availability** – This key is always included in the request context\.

## aws:SourceAccount<a name="condition-keys-sourceaccount"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the account ID of the resource making a service\-to\-service request with the account ID that you specify in the policy\. 
+ **Availability** – This key is included in the request context only if accessing a resource triggers an AWS service to call another service on behalf of the resource owner\. The calling service must pass the resource ARN of the source to the called service\. This ARN includes the source account ID\.

You can use this condition key to check that Amazon S3 is not being used as a [confused deputy](id_roles_create_for-user_externalid.md#confused-deputy)\.For example, when an Amazon S3 bucket update triggers an Amazon SNS topic post, the Amazon S3 service invokes the `sns:Publish` API operation\. The bucket is considered the source of the SNS request and the value of the key is the account ID from the bucket's ARN\.

## aws:SourceArn<a name="condition-keys-sourcearn"></a>

Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN) and [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns) of the resource making a service\-to\-service request with the ARN that you specify in the policy\. 

This key does not work with the ARN of the principal making the request\. Instead, use [aws:PrincipalArn](#condition-keys-principalarn)\. The source's ARN includes the account ID, so it is not necessary to use `aws:SourceAccount` with `aws:SourceArn`\.
+ **Availability** – This key is included in the request context only if accessing a resource triggers an AWS service to call another service on behalf of the resource owner\. The calling service must pass the ARN of the original resource to the called service\.

You can use this condition key to check that Amazon S3 is not being used as a [confused deputy](id_roles_create_for-user_externalid.md#confused-deputy)\. For example, when an Amazon S3 bucket update triggers an Amazon SNS topic post, the Amazon S3 service invokes the `sns:Publish` API operation\. The bucket is considered the source of the SNS request and the value of the key is the bucket's ARN\.

## aws:SourceIp<a name="condition-keys-sourceip"></a>

Works with [IP address operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.

Use this key to compare the requester's IP address with the IP address that you specify in the policy\.
+ **Availability** – This key is included in the request context, except when the requester uses a VPC endpoint to make the request\.

The `aws:SourceIp` condition key can be used in a policy to allow principals to make requests only from within a specified IP range\. However, this policy denies access if an AWS service makes calls on the principal's behalf\. In this case, you can use `aws:SourceIp` with the `` key to ensure that the source IP restriction applies only to requests made directly by a principal\. 

For example, you can attach the following policy to an IAM user\. This policy allows the user to put an object into the `my-service-bucket` Amazon S3 bucket directly if they make the call from the specified IP address\. However, if the user makes another request that causes a service to call Amazon S3, the IP address restriction does not apply\. The `PrincipalPutObjectIfIpAddress` statement restricts the IP address only if the request is not made by a service\. The `ServicePutObject` statement allows the operation without IP address restriction if the request is made by a service\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PrincipalPutObjectIfIpAddress",
            "Effect": "Allow",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::my-service-bucket/*",
            "Condition": {
                "Bool": {"aws:ViaAWSService": "false"},
                "IpAddress": {"aws:SourceIp": "123.45.167.89"}
            }
        },
        {
            "Sid": "ServicePutObject",
            "Effect": "Allow",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::my-service-bucket/*",
            "Condition": {
                "Bool": {"aws:ViaAWSService": "true"}
            }
        }
    ]
}
```

If the request comes from a host that uses an Amazon VPC endpoint, then the `aws:SourceIp` key is not available\. You should instead use a VPC\-specific key such as [aws:VpcSourceIp](#condition-keys-sourceip)\. For more information about using VPC endpoints, see [VPC Endpoints \- Controlling the Use of Endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html#vpc-endpoints-iam-access) in the *Amazon VPC User Guide*\.

## aws:SourceVpc<a name="condition-keys-sourcevpc"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to check whether the request comes from the VPC that you specify in the policy\. In a policy, you can use this key to allow access to only a specific VPC\. For more information, see [Restricting Access to a Specific VPC](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc) in the *Amazon Simple Storage Service Developer Guide*\. 
+ **Availability** – This key is included in the request context only if the requester uses a VPC endpoint to make the request\.

## aws:SourceVpce<a name="condition-keys-sourcevpce"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the VPC endpoint identifier of the request with the endpoint ID that you specify in the policy\. In a policy, you can use this key to restrict access to a specific VPC endpoint\. For more information, see [Restricting Access to a Specific VPC Endpoint](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc-endpoint) in the *Amazon Simple Storage Service Developer Guide*\.
+ **Availability** – This key is included in the request context only if the requester uses a VPC endpoint to make the request\.

## aws:TagKeys<a name="condition-keys-tagkeys"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the tag keys in a request with the keys that you specify in the policy\. As a best practice when you use policies to control access using tags, use the `aws:TagKeys` condition key to define what tag keys are allowed\. For example policies and more information, see [Controlling access based on tag keys](access_tags.md#access_tags_control-tag-keys)\.
+ **Availability** – This key is included in the request context only if the operation supports attaching tags to resources\.

This context key is formatted `"aws:TagKeys":"tag-key"` where *tag\-key* is a list of tag keys without values \(for example, `["Dept","Cost-Center"]`\)\.

Because you can include multiple tag key\-value pairs in a request, the request content could be a [multivalued](reference_policies_multi-value-conditions.md) request\. In this case, you should consider using the `ForAllValues` or `ForAnyValue` set operators\. For more information, see [Using multiple keys and values](reference_policies_multi-value-conditions.md#reference_policies_multi-key-or-value-conditions)\.

Some services support tagging with resource operations, such as creating, modifying, or deleting a resource\. To allow tagging and operations as a single call, you must create a policy that includes both the tagging action and the resource\-modifying action\. You can then use the `aws:TagKeys` condition key to enforce using specific tag keys in the request\. For example, to limit tags when someone creates an Amazon EC2 snapshot, you must include the `ec2:CreateSnapshot` creation action ***and*** the `ec2:CreateTags` tagging action in the policy\. To view a policy for this scenario that uses `aws:TagKeys`, see [Creating a Snapshot with Tags](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ExamplePolicies_EC2.html#iam-creating-snapshot-with-tags) in the *Amazon EC2 User Guide for Linux Instances*\. 

## aws:TokenIssueTime<a name="condition-keys-tokenissuetime"></a>

Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.

Use this key to compare the date and time that temporary security credentials were issued with the date and time that you specify in the policy\. 
+ **Availability** – This key is included in the request context only when the principal uses temporary credentials to make the request\. They key is not present in AWS CLI, AWS API, or AWS SDK requests that are made using access keys\.

To learn which services support using temporary credentials, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

## aws:UserAgent<a name="condition-keys-useragent"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the requester's client application with the application that you specify in the policy\.
+ **Availability** – This key is always included in the request context\.

**Warning**  
This key should be used carefully\. Since the `aws:UserAgent` value is provided by the caller in an HTTP header, unauthorized parties can use modified or custom browsers to provide any `aws:UserAgent` value that they choose\. As a result, `aws:UserAgent` should not be used to prevent unauthorized parties from making direct AWS requests\. You can use it to allow only specific client applications, and only after testing your policy\.

## aws:userid<a name="condition-keys-userid"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the requester's principal identifier with the ID that you specify in the policy\. For IAM users, the request context value is the user ID\. For IAM roles, this value format can vary\. For details about how the information appears for different principals, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\.
+ **Availability** – This key is included in the request context for all signed requests\. Anonymous requests do not include this key\.

## aws:username<a name="condition-keys-username"></a>

Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.

Use this key to compare the requester's user name with the user name that you specify in the policy\. For details about how the information appears for different principals, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\.
+ **Availability** – This key is always included in the request context for IAM users\. Anonymous requests and requests that are made using the AWS account root user or IAM roles do not include this key\.

## aws:ViaAWSService<a name="condition-keys-viaawsservice"></a>

Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.

Use this key to check whether an AWS service makes a request to another service on your behalf\.

The request context key returns `true` when a service uses the credentials of an IAM principal to make a request on behalf of the principal\. The context key returns `false` if the service uses a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) or [service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) to make a call on the principal's behalf\. The request context key also returns `false` when the principal makes the call directly\.
+ **Availability** – This key is always included in the request context for most services\.

The following services do not currently support `aws:ViaAWSService`:
+ Amazon EC2
+ AWS Glue
+ AWS Lake Formation
+ AWS OpsWorks

You can use this condition key to allow or deny access based on whether a request was made by a service\. To view an example policy, see [AWS: Denies access to AWS based on the source IP](reference_policies_examples_aws_deny-ip.md)\.

## aws:VpcSourceIp<a name="condition-keys-vpcsourceip"></a>

Works with [IP address operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.

Use this key to compare the IP address from which a request was made with the IP address that you specify in the policy\. In a policy, the key matches only if the request originates from the specified IP address and it goes through a VPC endpoint\.
+ **Availability** – This key is included in the request context only if the request is made using a VPC endpoint\.

For more information, see [Controlling Access to Services with VPC Endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints-access.html) in the *Amazon VPC User Guide*\.