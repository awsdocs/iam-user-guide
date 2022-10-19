# IAM Access Analyzer resource types<a name="access-analyzer-resources"></a>

IAM Access Analyzer analyzes the resource\-based policies that are applied to AWS resources in the Region where you enabled IAM Access Analyzer\. Only resource\-based policies are analyzed\. Review the information about each resource for details about how IAM Access Analyzer generates findings for each resource type\.

**Topics**
+ [Amazon Simple Storage Service buckets](#access-analyzer-s3)
+ [AWS Identity and Access Management roles](#access-analyzer-iam-role)
+ [AWS Key Management Service keys](#access-analyzer-kms-key)
+ [AWS Lambda functions and layers](#access-analyzer-lambda)
+ [Amazon Simple Queue Service queues](#access-analyzer-sqs)
+ [AWS Secrets Manager secrets](#access-analyzer-secrets-manager)

## Amazon Simple Storage Service buckets<a name="access-analyzer-s3"></a>

When IAM Access Analyzer analyzes Amazon S3 buckets, it generates a finding when an Amazon S3 bucket policy, ACL, or access point, including a multi\-region access point, applied to a bucket grants access to an external entity\. An external entity is a principal or other entity you can use to [create a filter](access-analyzer-findings-filter.md) that isn't within your zone of trust\. For example, if a bucket policy grants access to another account or allows public access, IAM Access Analyzer generates a finding\. However, if you enable [Block public access](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html) on your bucket, you can block access at the account level or the bucket level\.

Amazon S3 *block public access* settings override the bucket policies applied to the bucket\. The settings also override the access point policies applied to the bucket’s access points\. IAM Access Analyzer analyzes block public access settings at the bucket level whenever a policy changes\. However, it evaluates the block public access settings at the account level only once every 6 hours\. This means that IAM Access Analyzer might not generate or resolve a finding for public access to a bucket for up to 6 hours\. For example, if you have a bucket policy that allows public access, IAM Access Analyzer generates a finding for that access\. If you then enable block public access to block all public access to the bucket at the account level, IAM Access Analyzer doesn't resolve the finding for the bucket policy for up to 6 hours, even though all public access to the bucket is blocked\.

For a multi\-region access point, IAM Access Analyzer uses an established policy for generating findings\. IAM Access Analyzer evaluates changes to multi\-region access points once every 6 hours\. This means IAM Access Analyzer doesn’t generate or resolve a finding for up to 6 hours, even if you create or delete a multi\-region access point, or update the policy for it\. 

## AWS Identity and Access Management roles<a name="access-analyzer-iam-role"></a>

For IAM roles, IAM Access Analyzer analyzes [trust policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#term_trust-policy)\. In a role trust policy, you define the principals that you trust to assume the role\. A role trust policy is a required resource\-based policy that is attached to a role in IAM\. IAM Access Analyzer generates findings for roles within the zone of trust that can be accessed by an external entity that is outside your zone of trust\.

**Note**  
An IAM role is a global resource\. If a role trust policy grants access to an external entity, IAM Access Analyzer generates a finding in each enabled Region\.

## AWS Key Management Service keys<a name="access-analyzer-kms-key"></a>

For AWS KMS keys, IAM Access Analyzer analyzes the key policies and grants applied to a key\. IAM Access Analyzer generates a finding if a key policy or grant allows an external entity to access the key\. For example, if you use the [kms:CallerAccount](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-caller-account) condition key in a policy statement to allow access to all users in a specific AWS account, and you specify an account other than the current account \(the zone of trust for the current analyzer\), IAM Access Analyzer generates a finding\. To learn more about AWS KMS condition keys in IAM policy statements, see [AWS KMS Condition Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awskeymanagementservice.html#awskeymanagementservice-policy-keys)\.

When IAM Access Analyzer analyzes a KMS key it reads key metadata, such as the key policy and list of grants\. If the key policy doesn't allow the IAM Access Analyzer role to read the key metadata, an Access Denied error finding is generated\. For example, if the following example policy statement is the only policy applied to a key, it results in an Access Denied error finding in IAM Access Analyzer:

```
{
    "Sid": "Allow access for Key Administrators",
    "Effect": "Allow",
    "Principal": {
       "AWS": "arn:aws:iam::111122223333:role/Admin"
    },
    "Action": "kms:*",
    "Resource": "*"
}
```

Because this statement allows only the role named *Admin* from the AWS account 111122223333 to access the key, an Access Denied error finding is generated because IAM Access Analyzer isn't able to fully analyze the key\. An error finding is displayed in red text in the **Findings** table\. The finding looks similar to the following:

```
{
    "error": "ACCESS_DENIED",
    "id": "12345678-1234-abcd-dcba-111122223333",
    "analyzedAt": "2019-09-16T14:24:33.352Z",
    "resource": "arn:aws:kms:us-west-2:1234567890:key/1a2b3c4d-5e6f-7a8b-9c0d-1a2b3c4d5e6f7g8a",
    "resourceType": "AWS::KMS::Key",
    "status": "ACTIVE",
    "updatedAt": "2019-09-16T14:24:33.352Z"
}
```

When you create a KMS key, the permissions granted to access the key depend on how you create the key\. If you receive an Access Denied error finding for a key resource, apply the following policy statement to the key resource to grant IAM Access Analyzer permission to access the key\.

```
{
    "Sid": "Allow IAM Access Analyzer access to key metadata",
    "Effect": "Allow",
    "Principal": {
        "AWS": "arn:aws:iam::111122223333:role/aws-service-role/access-analyzer.amazonaws.com/AWSServiceRoleForAccessAnalyzer"
        },
    "Action": [
        "kms:DescribeKey",
        "kms:GetKeyPolicy",
        "kms:List*"
    ],
    "Resource": "*"
},
```

After you receive an Access Denied finding for a KMS key resource, and then resolve the finding by updating the key policy, the finding is updated to a status of Resolved\. If there are policy statements or key grants that grant permission to the key to an external entity, you might see additional findings for the key resource\. 

## AWS Lambda functions and layers<a name="access-analyzer-lambda"></a>

For AWS Lambda functions, IAM Access Analyzer analyzes policies, including condition statements in a policy, that grant access to the function to an external entity\. IAM Access Analyzer also analyzes permissions granted when using the [AddPermission](https://docs.aws.amazon.com/lambda/latest/dg/API_AddPermission.html) operation of the AWS Lambda API with an `EventSourceToken`\.

## Amazon Simple Queue Service queues<a name="access-analyzer-sqs"></a>

For Amazon SQS queues, IAM Access Analyzer analyzes policies, including condition statements in a policy, that allow an external entity access to a queue\.

## AWS Secrets Manager secrets<a name="access-analyzer-secrets-manager"></a>

For AWS Secrets Manager secrets, IAM Access Analyzer analyzes policies, including condition statements in a policy, that allow an external entity to access a secret\.