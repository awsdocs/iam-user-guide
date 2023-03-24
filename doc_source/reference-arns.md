# Amazon Resource Names \(ARNs\)<a name="reference-arns"></a>

Amazon Resource Names \(ARNs\) uniquely identify AWS resources\. We require an ARN when you need to specify a resource unambiguously across all of AWS, such as in IAM policies, Amazon Relational Database Service \(Amazon RDS\) tags, and API calls\.

## ARN format<a name="arns-syntax"></a>

The following are the general formats for ARNs\. The specific formats depend on the resource\. To use an ARN, replace the *italicized* text with the resource\-specific information\. Be aware that the ARNs for some resources omit the Region, the account ID, or both the Region and the account ID\.

```
arn:partition:service:region:account-id:resource-id
arn:partition:service:region:account-id:resource-type/resource-id
arn:partition:service:region:account-id:resource-type:resource-id
```

*partition*  
The partition in which the resource is located\. A *partition* is a group of AWS Regions\. Each AWS account is scoped to one partition\.  
The following are the supported partitions:  
+ `aws` \- AWS Regions
+ `aws-cn` \- China Regions
+ `aws-us-gov` \- AWS GovCloud \(US\) Regions

*service*  
The service namespace that identifies the AWS product\.

*region*  
The Region code\. For example, `us-east-2` for US East \(Ohio\)\. For the list of Region codes, see [Regional endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#regional-endpoints) in the *AWS General Reference*\.

*account\-id*  
The ID of the AWS account that owns the resource, without the hyphens\. For example, `123456789012`\.

*resource\-type*  
The resource type\. For example, `vpc` for a virtual private cloud \(VPC\)\.

*resource\-id*  
The resource identifier\. This is the name of the resource, the ID of the resource, or a [resource path](#arns-paths)\. Some resource identifiers include a parent resource \(sub\-resource\-type/parent\-resource/sub\-resource\) or a qualifier such as a version \(resource\-type:resource\-name:qualifier\)\.Examples

IAM user  
arn:aws:iam::*123456789012*:user/*johndoe*

SNS topic  
arn:aws:sns:*us\-east\-1*:*123456789012*:*example\-sns\-topic\-name*

VPC  
arn:aws:ec2:*us\-east\-1*:*123456789012*:vpc/*vpc\-0e9801d129EXAMPLE*

## Look up the ARN format for a resource<a name="supported-arns"></a>

To look up the ARN format for a specific AWS resource, open the [Service Authorization Reference](https://docs.aws.amazon.com/service-authorization/latest/reference/), open the page for the service, and navigate to the resource types table\.

## Paths in ARNs<a name="arns-paths"></a>

Resource ARNs can include a path\. For example, in Amazon S3, the resource identifier is an object name that can include slashes \(`/`\) to form a path\. Similarly, IAM user names and group names can include paths\.

Paths can include a wildcard character, namely an asterisk \(`*`\)\. For example, if you are writing an IAM policy, you can specify all IAM users that have the path `product_1234` using a wildcard as follows:

```
arn:aws:iam::123456789012:user/Development/product_1234/*
```

Similarly, you can specify `user/*` to mean all users or `group/*` to mean all groups, as in the following examples:

```
"Resource":"arn:aws:iam::123456789012:user/*"
"Resource":"arn:aws:iam::123456789012:group/*"
```

The following example shows ARNs for an Amazon S3 bucket in which the resource name includes a path:

```
arn:aws:s3:::my_corporate_bucket/*
arn:aws:s3:::my_corporate_bucket/Development/*
```

**Incorrect wildcard usage**  
You cannot use a wildcard in the portion of the ARN that specifies the resource type, such as the term `user` in an IAM ARN\. For example, the following is not allowed\.

```
arn:aws:iam::123456789012:u*   <== not allowed
```