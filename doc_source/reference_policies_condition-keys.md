# AWS Global Condition Context Keys<a name="reference_policies_condition-keys"></a>

You can use the `Condition` element of a JSON policy in IAM to test the value of keys that are included in the evaluation context of all AWS API requests\. These keys provide information about the request itself or the resources that the request references\. You can check that keys have specified values before allowing the action that is requested by the user\. This gives you granular control over when your JSON policy statements match or don't match an incoming API request\. For information about how to use the `Condition` element in a JSON policy, see [IAM JSON Policy Elements: Condition](reference_policies_elements_condition.md)\.

This topic describes the globally available keys \(with an `aws:` prefix\)\. AWS services, [such as IAM,](reference_policies_iam-condition-keys.md) provide service\-specific keys that are relevant to the actions and resources that are defined by that service\. For more information, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\. The documentation for a service that supports condition keys often has additional information\. For example, for information about keys that you can use in policies for Amazon S3 resources, see [Amazon S3 Policy Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#AvailableKeys-iamV2) in the *Amazon Simple Storage Service Developer Guide*\.

Some global condition keys are available for all AWS services, and some are only supported by some services\. You can use these keys in IAM policies, but not necessarily in resource\-based policies\.

**Topics**
+ [Keys Available for All Services](#condition-keys-globally-available)
+ [Keys Available for Some Services](#condition-keys-service-available)

## Keys Available for All Services<a name="condition-keys-globally-available"></a>

 AWS provides the following predefined condition keys for all AWS services that support IAM access control\. To learn more about writing policies for these services, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\.

**aws:CurrentTime**  
Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.  
The current date and time to check for date/time conditions\.

**aws:EpochTime**  
Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.  
The current date and time in epoch or Unix time to check for date/time conditions\.

**aws:MultiFactorAuthAge**  
Works with [numeric operators](reference_policies_elements_condition_operators.md#Conditions_Numeric)\.  
Checks how long ago \(in seconds\) the MFA\-validated security credentials that made the request were issued using multi\-factor authentication \(MFA\)\. If MFA was not used, this key is not present\. See [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)\. Therefore, this is another key with which you should consider using the [\*IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists) versions of the comparison operators\. This ensures that the results of the comparison are what you expect even when the key is not present in the request context\.

**aws:MultiFactorAuthPresent**  
Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.  
Checks whether multi\-factor authentication \(MFA\) was used to validate the temporary security credentials that made the current request\. This key is present in the request context only when the user uses temporary credentials to make the request\. They key is not present in AWS CLI, AWS API, or AWS SDK requests made using access keys\.  
Temporary credentials are used with IAM roles, federated users, IAM users with temporary tokens from `sts:GetSessionToken`, and users of the AWS Management Console\. Users sign into the console using long\-term user name and password credentials\. However, in the background, the console generates temporary credentials on behalf of the user\. The `aws:MultiFactorAuthPresent` key is never present when an API or CLI command is called with long\-term credentials, such as access key pairs\. Therefore we recommend that when you check for this key that you use the `[\.\.\.IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists)` versions of the condition operators\.  
It is important to understand that the following Condition element is ***not*** a reliable way to check whether a request is authenticated using MFA\.  

```
#####   WARNING: NOT RECOMMENDED   #####

"Effect" : "Deny",
"Condition" : { "Bool" : { "aws:MultiFactorAuthPresent" : false } }
```
This combination of the `Deny` effect, `Bool` element, and `false` value denies requests that can be authenticated using MFA, but were not\. This applies only to temporary credentials that support using MFA\. This statement does not deny access to requests made using long\-term credentials, or to requests that were authenticated using MFA\. Use this example with caution because its logic is complicated and it does not test whether MFA\-authentication was actually used\.   
Also do not use the combination of the `Deny` effect, `Null` element, and `true` because it behaves the same way and the logic is even more complicated\.  
**Recommended Combination**  
We recommend that you use the [`BoolIfExists`](reference_policies_elements_condition_operators.md#Conditions_IfExists) operator to check whether a request is authenticated using MFA\.  

```
"Effect" : "Deny",
"Condition" : { "BoolIfExists" : { "aws:MultiFactorAuthPresent" : false } }
```
This combination of `Deny`, `BoolIfExists`, and `false` denies requests that are not authenticated using MFA\. Specifically, it denies requests from temporary credentials that do not include MFA\. It also denies requests made using long\-term credentials, such as AWS CLI or AWS API operations made using access keys\. The `*IfExists` operator checks for the presence of the `aws:MultiFactorAuthPresent` key and whether or not it COULD be present, as indicated by its existence\. Use this when you want to deny any request that is not authenticated using MFA\. This is more secure, but can break any code or scripts that use access keys to access the AWS CLI or AWS API\.   
**Alternative Combinations**  
You can also use the [`BoolIfExists`](reference_policies_elements_condition_operators.md#Conditions_IfExists) operator to allow MFA\-authenticated requests and AWS CLI or AWS API requests made using long\-term credentials\.  

```
"Effect" : "Allow",
"Condition" : { "BoolIfExists" : { "aws:MultiFactorAuthPresent" : true } }
```
This condition matches either if the key exists and is present **or** if the key does not exist\. This combination of `Allow`, `BoolIfExists`, and `true` allows requests that are authenticated using MFA, or requests that cannot be authenticated using MFA\. This means that AWS CLI, AWS API, and AWS SDK operations are allowed when the requester uses their long\-term access keys\. This combination does not allow requests from temporary credentials that could, but do not include MFA\.   
When you create a policy using the IAM console visual editor and choose **MFA required**, this combination is applied\. This setting requires MFA for console access, but allows programmatic access with no MFA\.   
Alternatively, you can use the `Bool` operator to allow programmatic and console requests only when authenticated using MFA\.  

```
"Effect" : "Allow",
"Condition" : { "Bool" : { "aws:MultiFactorAuthPresent" : true } }
```
This combination of the `Allow`, `Bool`, and `true` allows only MFA\-authenticated requests\. This applies only to temporary credentials that support using MFA\. This statement does not allow access to requests made using long\-term access keys, or to requests made using temporary credentials without MFA\.   
***Do not*** use a policy construct similar to the following to check whether the MFA key is present:  

```
#####   WARNING: USE WITH CAUTION   #####

"Effect" : "Allow",
"Condition" : { "Null" : { "aws:MultiFactorAuthPresent" : false } }
```
This combination of the `Allow` effect, `Null` element, and `false` value allows only requests that can be authenticated using MFA, regardless of whether the request is actually authenticated\. This allows all requests made using temporary credentials, and denies access for long\-term credentials\. Use this example with caution because it does not test whether MFA\-authentication was actually used\. 

**aws:PrincipalOrgID**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
The identifier of an organization that you created using AWS Organizations\. This global key provides an alternative to listing all the account IDs for all AWS accounts in an organization\. You can use this condition key to simplify specifying the `Principal` element in a [resource\-based policy](access_policies_identity-vs-resource.md)\. Instead of listing all the accounts that are members of an organization, you can specify the [organization ID](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_details.html) in the condition element\. When you add and remove accounts, policies that include `aws:PrincipalOrgID` automatically include the correct accounts and don't require manual updating\.  
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
This global condition also applies to the master account of an AWS organization\.
For more information about AWS Organizations, see [What Is AWS Organizations?](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) in the *AWS Organizations User Guide*\.

**aws:PrincipalArn**  
Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN)\.  
Checks the [Amazon Resource Name](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) \(ARN\) of the IAM user or role that made the request\.

**aws:RequestedRegion**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks whether an AWS request is made to a specific Region\. You can use this global condition key to control which Regions your users can make calls to\. To view the AWS Regions for each service, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.  
Global services, such as IAM, have a single endpoint\. However, because this endpoint is physically located in the US East \(N\. Virginia\) Region, IAM calls are always made to the us\-east\-1 Region\. For example, if you create a policy that denies access to all services if the requested Region is not us\-west\-2, the IAM calls will always fail\. To view an example of how to work around this, see [NotAction with Deny](reference_policies_elements_notaction.md)\.   
The `aws:RequestedRegion` condition key allows you to control which endpoint of a service is invoked but does not control the impact of the operation\. Some services have cross\-region impacts\. For example, Amazon S3 has API operations that control cross\-region replication\. You can invoke `s3:PutBucketReplication` in one region \(which is affected by the `aws:RequestedRegion` condition key\), but other Regions are affected based on the replications configuration settings\. 
You can use this context key to limit access to AWS services within a given set of Regions\. For example, the following policy allows a user to view all of the Amazon EC2 instances in the AWS Management Console\. However it only allows them to make changes to instances in Ireland \(eu\-west\-1\), London \(eu\-west\-2\), or Paris \(eu\-west\-3\)\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "InstanceConsoleReadOnly",
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances",
                "ec2:DescribeIamInstanceProfileAssociations",
                "ec2:DescribeInstanceAttribute",
                "ec2:DescribeReservedInstancesOfferings",
                "ec2:DescribeClassicLinkInstances",
                "ec2:DescribeSpotInstanceRequests",
                "ec2:GetReservedInstancesExchangeQuote",
                "ec2:DescribeInstanceCreditSpecifications",
                "ec2:DescribeSpotFleetInstances",
                "ec2:DescribeScheduledInstances",
                "ec2:DescribeScheduledInstanceAvailability",
                "ec2:DescribeReservedInstancesModifications",
                "ec2:DescribeReservedInstances",
                "ec2:DescribeReservedInstancesListings",
                "ec2:DescribeInstanceStatus"
            ],
            "Resource": "*"
        },
        {
            "Sid": "InstanceWriteRegionRestricted",
            "Effect": "Allow",
            "Action": [
                "ec2:ModifyInstancePlacement",
                "ec2:TerminateInstances",
                "ec2:ImportInstance",
                "ec2:StartInstances",
                "ec2:MonitorInstances",
                "ec2:RunScheduledInstances",
                "ec2:ResetInstanceAttribute",
                "ec2:RunInstances",
                "ec2:ModifyInstanceAttribute",
                "ec2:StopInstances",
                "ec2:AssociateIamInstanceProfile",
                "ec2:ModifyReservedInstances"
            ],
            "Resource": "*",
            "Condition": {"StringEquals": {"aws:RequestedRegion": [
                "eu-west-1",
                "eu-west-2",
                "eu-west-3"
            ]}}
        }
    ]
}
```

**aws:SecureTransport**  
Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.  
Checks whether the request was sent using SSL\.

**aws:UserAgent**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's client application\.  
This key should be used carefully\. Since the `aws:UserAgent` value is provided by the caller in an HTTP header, unauthorized parties can use modified or custom browsers to provide any `aws:UserAgent` value that they choose\. As a result, `aws:UserAgent` should not be used to prevent unauthorized parties from making direct AWS requests\. You can use it to allow only specific client applications, and only after testing your policy\.

## Keys Available for Some Services<a name="condition-keys-service-available"></a>

 AWS provides the following predefined condition keys for only some AWS services that support these features\. To learn whether a service supports one of these condition keys, you must view the documentation for that service\. 

**Note**  
If you use condition keys that are available only in some scenarios, you can use the [IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists) versions of the condition operators\. If the condition keys are missing from a request context, the policy engine can fail the evaluation\. For example, use the following policy with `...IfExists` operators to match if a request comes from a specific IP range or from a specific VPC\. If either or both keys don't exist, the condition still matches\. The values are only checked if the specified key exists in the request\.   

```
"Condition": {"IpAddressIfExists": {"aws:SourceIp" : ["xxx"] },
      "StringEqualsIfExists" : {"aws:SourceVpc" : ["yyy"]} }
```

**aws:PrincipalTag/*tag\-key***  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks that the tag attached to the principal making the request matches the specified key name and value\.  
You can add custom attributes to a user or role in the form of a key–value pair\. For more information about IAM tags, see [Tagging IAM Entities](id_tags.md)\. You can use `aws:PrincipalTag` to [control access](access_iam-tags.md#access_iam-tags_control-resources) for AWS principals\.  
This example shows how you might create a policy that allows users with the **tagManager=true** tag to manage IAM users, groups, or roles\. To use this policy, replace the red italicized text in the example policy with your own information\.  

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

**aws:PrincipalType**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the type of principal \(user, account, federated user, etc\.\) for the current request\.  
This condition key is available for only some services\.

**aws:Referer**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks who referred the client browser to the address that the request is being sent to\. It is only supported by some services, such as [Amazon S3, as a service that can be directly addressed by a web browser](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html#example-bucket-policies-use-case-4)\. `aws:referer` allows Amazon S3 bucket owners to help prevent their content from being served up by unauthorized third\-party sites to standard web browsers\. The value comes from the referer header in the HTTPS request that is made to AWS\. The `aws:referer` value is provided by the caller in an HTTP header\.  
This key should be used carefully\. It is dangerous to include a publicly\-known referer header value\. Unauthorized parties can use modified or custom browsers to provide any `aws:referer` value that they choose\. As a result, `aws:referer` should not be used to prevent unauthorized parties from making direct AWS requests\. It is offered only to allow customers to protect their digital content, stored in Amazon S3, from being referenced on unauthorized third\-party sites\.
 This condition key is available for only some services\.

**aws:RequestTag/*tag\-key***  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This context key is formatted `"aws:RequestTag/tag-key":"tag-value"` where *tag\-key* and *tag\-value* are a tag key and value pair\.  
Checks that the tag key–value pair is present in an AWS request\. For example, you could check to see that the request includes the tag key `"Dept"` and that it has the value `"Accounting"`\. For more information, see [Controlling Access During AWS Requests](access_tags.md#access_tags_control-requests)\.  
This condition key is available for only some services, and was [introduced for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html)\.

**aws:ResourceTag/*tag\-key***  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This context key is formatted `"aws:ResourceTag/tag-key":"tag-value"` where *tag\-key* and *tag\-value* are a tag key and value pair\.  
Checks that the tag key–value pair is attached to the resource\. For example, you could require that access to a resource is allowed only if the resource has the attached tag key `"Dept"` with the value `"Marketing"`\. For more information, see [Controlling Access to AWS Resources](access_tags.md#access_tags_control-resources)\.  
This condition key is available for only some services\.

**aws:SourceAccount**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks whether the source of the request comes from a specific account\. For example, assume that you have an S3 bucket in your account that is configured to deliver object creation events to an SNS topic\. In that case, you could use this condition key to check that Amazon S3 is not being used as a confused deputy\. Amazon S3 tells Amazon SNS the account that the bucket belongs to\.   
This condition key is available for only some services\.

**aws:SourceArn**  
Works with [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN)\.  
Checks the source of the request, using the [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns) of the source\.   
This condition key is available for only some services\.

**aws:SourceIp**  
Works with [IP address operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.  
Checks the requester's IP address, see [IP Address Condition Operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.  
The `aws:SourceIp` condition key should be used in a JSON policy only for IAM users, groups, roles, or federated users that make API calls from within the specified IP range\. This policy denies access to an AWS service that makes calls on your behalf\. For example, assume that you have a [service role](id_roles_terms-and-concepts.md#iam-term-service-role) that allows AWS CloudFormation to call Amazon EC2 to stop an instance\. In that case, the request is denied because the target service \(Amazon EC2\) sees the IP address of the calling service \(AWS CloudFormation\) rather than the IP address of the originating user\. There is no way to pass the originating IP address through a calling service to the target service for evaluation in a JSON policy\.
If the request comes from a host that uses an Amazon VPC endpoint, then the `aws:SourceIp` key is not available\. You should instead use a VPC\-specific key\. For more information, see [VPC Endpoints \- Controlling the Use of Endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html#vpc-endpoints-iam-access) in the *Amazon VPC User Guide*\.

**aws:SourceVpc**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Restricts access to a specific VPC\. For more information, see [Restricting Access to a Specific VPC](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc) in the *Amazon Simple Storage Service Developer Guide*\.   
This condition key is available for services that support traffic over a VPC endpoint\.

**aws:SourceVpce**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Restricts access to a specific VPC endpoint\. For more information, see [Restricting Access to a Specific VPC Endpoint](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc-endpoint) in the *Amazon Simple Storage Service Developer Guide*\.  
This condition key is available for services that support traffic over a VPC endpoint\.

**aws:TagKeys**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This context key is formatted `"aws:TagKeys":"tag-key"` where *tag\-key* is a list of tag keys without values \(for example, `["Dept","Cost-Center"]`\)\.  
Checks the tag keys that are present in an AWS request\.   
As a best practice when you use policies to control access using tags, you should use the `aws:TagKeys` condition key to define what tag keys are allowed\. For example policies and more information, see [Controlling Access Based on Tag Keys](access_tags.md#access_tags_control-tag-keys)   
Some services support tagging with resource operations, such as creating, modifying, or deleting a resource\. To allow tagging and operations as a single call, you must create a policy that includes both the tagging action and the resource\-modifying action\. You can then use the `aws:TagKeys` condition key to enforce using specific tag keys in the request\. For example, to limit tags when someone creates an Amazon EC2 snapshot, you must include the `ec2:CreateSnapshot` creation action ***and*** the `ec2:CreateTags` tagging action in the policy\. To view a policy for this scenario that uses `aws:TagKeys`, see [Creating a Snapshot with Tags](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ExamplePolicies_EC2.html#iam-creating-snapshot-with-tags) in the *Amazon EC2 User Guide for Linux Instances*\. 
This condition key is available for only some services, and was [introduced for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html)\.

**aws:TokenIssueTime**  
Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.  
Checks the date/time that temporary security credentials were issued\.   
This condition key is available for only some services that support using temporary security credentials\. To learn which services support using temporary credentials, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md)\.

**aws:userid**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's user ID\.  
 This condition key is available for only some services\.

**aws:username**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's user name\.  
 This condition key is available for only some services\.

**aws:VpcSourceIp**  
Works with [IP address operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress)\.  
When used in VPC endpoint policies, restricts access to specific IPs from within the principal’s VPC\.   
This condition key can be used only in VPC endpoint policies\. For more information, see [Controlling Access to Services with VPC Endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints-access.html) in the *Amazon VPC User Guide*\.