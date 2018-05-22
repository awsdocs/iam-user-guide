# AWS Global Condition Context Keys<a name="reference_policies_condition-keys"></a>

You can use the `Condition` element of a JSON policy in IAM to test the value of keys that are included in the evaluation context of all AWS API requests\. These keys provide information about the request itself or the resources that the request references\. You can check that keys have specified values before allowing the action that is requested by the user\. This gives you granular control over when your JSON policy statements match or don't match an incoming API request\. For information about how to use the `Condition` element in a JSON policy, see [IAM JSON Policy Elements: Condition](reference_policies_elements_condition.md)\.

This topic describes the globally available keys \(with an `aws:` prefix\), as well as the keys that are defined and provided by the IAM service \(with an `iam:` prefix\)\. Several other AWS services also provide service\-specific keys that are relevant to the actions and resources that are defined by that service\. For more information, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\. The documentation for a service that supports condition keys often has additional information\. For example, for information about keys that you can use in policies for Amazon S3 resources, see [Amazon S3 Policy Keys](http://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#AvailableKeys-iamV2) in the *Amazon Simple Storage Service Developer Guide*\.

**Note**  
If you use condition keys that are available only in some scenarios \(such as `aws:SourceIp` and `aws:SourceVpc`\), you can use the [IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists) versions of the comparison operators\. If the condition keys are missing from a request context \(and you haven't set `IfExists`\), the policy engine can fail the evaluation\. For example, if you want to write a policy that restricts access from a particular IP range or from a particular VPC, you can construct the conditions as follows:   

```
"Condition": {"IpAddressIfExists": {"aws:SourceIp" : ["xxx"] },
      "StringEqualsIfExissts" : {"aws:SourceVpc" : ["yyy"]} }
```
This condition matches \(1\) if the `aws:SourceIp` context key exists and has the value `xxx` ***or*** \(2\) if the `aws:SourceVpc` context key exists and has the value `yyy`\. If either or both keys do not exist, the condition still matches\. The test is only made if the specified key exists in the request context\. If it is not there, it is treated as "I don't care\."

 AWS provides the following predefined condition keys for all AWS services that support IAM for access control:

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
Checks whether multi\-factor authentication \(MFA\) was used to validate the temporary security credentials that made the current request\. This key is present in the request context only when the user uses temporary credentials to call the API\. Such credentials are used with IAM roles, federated users, IAM users with credentials from `sts:GetSessionToken`, and users of the AWS Management Console\. \(The console uses temporary credentials that are generated on the users' behalf in the background\.\) The `aws:MultiFactorAuthPresent` key is never present when an API or CLI command is called with long\-term credentials, such as standard access key pairs\. Therefore we recommend that when you check for this key that you use the `[\.\.\.IfExists](reference_policies_elements_condition_operators.md#Conditions_IfExists)` versions of the condition operators\.  
It is important to understand that the following Condition element is ***not*** a reliable way to check for the use of MFA:  

```
#####     THIS EXAMPLE DOES NOT WORK      #####

"Condition" : { "Bool" : { "aws:MultiFactorAuthPresent" : false } }
```
This is because when long\-term credentials are used, the `aws:MultiFactorAuthPresent` key is not present in the request and the test *always* fails, resulting in a nonmatch\. Instead, we recommend that you use the [`BoolIfExists`](reference_policies_elements_condition_operators.md#Conditions_IfExists) operator to check the value\. For example:  

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

**aws:PrincipalOrgID**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
The identifier of an organization that you created using AWS Organizations\. This global key provides an alternative to listing all the account IDs for all AWS accounts in an organization\. You can use this condition key to simplify specifying the `Principal` element in your permissions [policy](access_policies.md)\. Instead of listing all the accounts that are members of an organization, you can specify the [organization ID](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_details.html) in the condition element\. When you add and remove accounts, policies that include `aws:PrincipalOrgID` automatically include the correct accounts and don't require manual updating\.  
For example, the following Amazon S3 bucket policy allows members of any account in the `o-xxxxxxxxxxx` organization to add an object into the `policy-ninja-dev` bucket\.   

```
 {
    "Version": "2012-10-17",
    "Statement": {
      "Sid": "AllowPutObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:putobject",
      "Resource": "arn:aws:s3:::policy-ninja-dev/*",
      "Condition": {"StringEquals":
        {"aws:PrincipalOrgID":["o-xxxxxxxxxxx"]}
      }
    }
}
```
For more information about AWS Organizations, see [What Is AWS Organizations?](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) in the *AWS Organizations User Guide*\.

**aws:PrincipalType**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the type of principal \(user, account, federated user, etc\.\) for the current request\.

**aws:Referer**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks who referred the client browser to the address that the request is being sent to\. It is only supported by some services, such as [Amazon S3, as a service that can be directly addressed by a web browser](http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html#example-bucket-policies-use-case-4)\. The value comes from the referer header in the HTTPS request that is made to AWS\.  
This key should be used carefully: `aws:referer` allows Amazon S3 bucket owners to help prevent their content from being served up by unauthorized third\-party sites to standard web browsers\. For more information, see the link in the previous paragraph\. Since the `aws:referer` value is provided by the caller in an HTTP header, unauthorized parties can use modified or custom browsers to provide any `aws:referer` value that they choose\. As a result, `aws:referer` should not be used to prevent unauthorized parties from making direct AWS requests\. It is offered only to allow customers to protect their digital content, stored in Amazon S3, from being referenced on unauthorized third\-party sites\.

**aws:RequestedRegion**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks whether an AWS request is made to a specific region\. You can use this global condition key to control which regions your users can make calls to\. To view the AWS regions for each service, see [AWS Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/rande.html) in the *Amazon Web Services General Reference*\.  
Global services, such as IAM, have a single endpoint\. However, because this endpoint is physically located in the US East \(N\. Virginia\) region, IAM calls are always made to the us\-east\-1 region\. For example, if you create a policy that denies access to all services if the requested region is not us\-west\-2, the IAM calls will always fail\. To view an example of how to work around this, see [NotAction with Deny](reference_policies_elements_notaction.md)\.   
The `aws:RequestedRegion` condition key allows you to control which endpoint of a service is invoked but does not control the impact of the operation\. Some services have cross\-region impacts\. For example, Amazon S3 has API operations that control cross\-region replication\. You can invoke `s3:PutBucketReplication` in one region \(which is affected by the `aws:RequestedRegion` condition key\), but other regions are affected based on the replications configuration settings\. 
You can use this context key to limit access to AWS services within a given set of regions\. For example, the following policy allows a user to view all of the Amazon EC2 instances in the AWS Management Console\. However it only allows them to make changes to instances in Ireland \(eu\-west\-1\), London \(eu\-west\-2\), or Paris \(eu\-west\-3\)\.  

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

**aws:RequestTag/*tag\-key***  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This context key is formatted `"aws:RequestTag/tag-key":"tag-value"` where *tag\-key* and *tag\-value* are a tag key and value pair\.  
Checks a tag and its value in an AWS request\. For example, you could check to see that the request includes the tag key `"Dept"` and that it has the value `"Accounting"`\.   
This AWS condition key was [introduced for Amazon EC2](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html) and is supported by a limited number of additional services\. Check your service to see whether it supports using this condition key\.

**aws:SecureTransport**  
Works with [Boolean operators](reference_policies_elements_condition_operators.md#Conditions_Boolean)\.  
Checks whether the request was sent using SSL\.

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
If the request comes from a host that uses an Amazon VPC endpoint, then the `aws:SourceIp` key is not available\. You should instead use a VPC\-specific key\. For more information, see [VPC Endpoints \- Controlling the Use of Endpoints](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html#vpc-endpoints-iam-access) in the *Amazon VPC User Guide*\.

**aws:SourceVpc**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Restricts access to a specific VPC\. For more information, see [Restricting Access to a Specific VPC](http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc) in the *Amazon Simple Storage Service Developer Guide*\. \(This condition key is supported for traffic to an AWS service over a VPC endpoint\.\)

**aws:SourceVpce**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Restricts access to a specific VPC endpoint\. For more information, see [Restricting Access to a Specific VPC Endpoint](http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies-vpc-endpoint.html#example-bucket-policies-restrict-access-vpc-endpoint) in the *Amazon Simple Storage Service Developer Guide*\.

**aws:TagKeys**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
This context key is formatted `"aws:TagKeys":"tag-key"` where *tag\-key* is a list of tag keys without values \(for example, `["Dept","Cost-Center"]`\)\.  
Checks the tag keys that are present in an AWS request\. This AWS condition key was [introduced for Amazon EC2](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html) and is supported by a limited number of additional services\. Check your service to see whether it supports using this condition key\.

**aws:TokenIssueTime**  
Works with [date operators](reference_policies_elements_condition_operators.md#Conditions_Date)\.  
Checks the date/time that temporary security credentials were issued\. This key is only present in requests that are signed using temporary security credentials\. For more information about temporary security credentials, see [Temporary Security Credentials](id_credentials_temp.md)\.

**aws:UserAgent**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's client application\.

**aws:userid**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's user ID\.

**aws:username**  
Works with [string operators](reference_policies_elements_condition_operators.md#Conditions_String)\.  
Checks the requester's user name\.