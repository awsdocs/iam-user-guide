# AWS managed policies for AWS Identity and Access Management Access Analyzer<a name="security-iam-awsmanpol"></a>







To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the ReadOnlyAccess AWS managed policy provides read\-only access to all AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.









## IAMAccessAnalyzerFullAccess<a name="security-iam-awsmanpol-IAMAccessAnalyzerFullAccess"></a>

Use the `IAMAccessAnalyzerFullAccess` AWS managed policy to allow your administrators to access IAM Access Analyzer\.

### Permissions groupings<a name="IAMAccessAnalyzerFullAccess"></a>

This policy is grouped into statements based on the set of permissions provided\.
+ **IAM Access Analyzer** – Allows full administrative permissions to all resources in IAM Access Analyzer\.
+ **Create service linked role** – Allows the administrator to create a [ service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-using-service-linked-roles.html), which allows IAM Access Analyzer to analyze resources in other services on your behalf\. This permission allows creating the service\-linked role only for use by IAM Access Analyzer\.
+ **AWS Organizations** – Allows administrators to use IAM Access Analyzer for an organization in AWS Organizations\. After [enabling trusted access](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_integrate_services.html) for IAM Access Analyzer in AWS Organizations, members of the management account can view findings across their organization\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "access-analyzer:*"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "iam:CreateServiceLinkedRole",
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "iam:AWSServiceName": "access-analyzer.amazonaws.com"
        }
      }
    },
    {
      "Effect": "Allow",
      "Action": [
        "organizations:DescribeAccount",
        "organizations:DescribeOrganization",
        "organizations:DescribeOrganizationalUnit",
        "organizations:ListAccounts",
        "organizations:ListAccountsForParent",
        "organizations:ListAWSServiceAccessForOrganization",
        "organizations:ListChildren",
        "organizations:ListDelegatedAdministrators",
        "organizations:ListOrganizationalUnitsForParent",
        "organizations:ListParents",
        "organizations:ListRoots"
      ],
      "Resource": "*"
    }
  ]
}
```

## IAMAccessAnalyzerReadOnlyAccess<a name="security-iam-awsmanpol-IAMAccessAnalyzerReadOnlyAccess"></a>

Use the `IAMAccessAnalyzerReadOnlyAccess` AWS managed policy to allow read\-only access to IAM Access Analyzer\.

To also allow read\-only access to IAM Access Analyzer for AWS Organizations, create a customer managed policy that allows the Describe and List actions from the [IAMAccessAnalyzerFullAccess](#security-iam-awsmanpol-IAMAccessAnalyzerFullAccess) AWS managed policy\.

### Service\-level permissions<a name="IAMAccessAnalyzerReadOnlyAccess-service-level-permissions"></a>

This policy provides read\-only access to IAM Access Analyzer\. No other service permissions are included in this policy\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "access-analyzer:Get*",
        "access-analyzer:List*",
        "access-analyzer:ValidatePolicy"
      ],
      "Resource": "*"
    }
  ]
}
```

## AccessAnalyzerServiceRolePolicy<a name="security-iam-aa-service-role-policy"></a>

You can't attach AccessAnalyzerServiceRolePolicy to your IAM entities\. This policy is attached to a service\-linked role that allows IAM Access Analyzer to perform actions on your behalf\. For more information, see [Using service\-linked roles for AWS IAM Access Analyzer](access-analyzer-using-service-linked-roles.md)\.

### Service\-level permissions<a name="service-level-permissions"></a>

This policy allows access to IAM Access Analyzer to analyze resource metadata from multiple AWS services\. The policy also allows permissions to AWS Organizations and allows the creation of an analyzer within the AWS organization as the zone of trust\.

```
            {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetBucketPublicAccessBlock",
        "s3:GetBucketPolicyStatus",
        "s3:GetAccountPublicAccessBlock",
        "s3:ListAllMyBuckets",
        "s3:GetBucketAcl",
        "s3:GetBucketLocation",
        "s3:GetBucketPolicy",
        "s3:ListAccessPoints",
        "s3:GetAccessPoint",
        "s3:GetAccessPointPolicy",
        "s3:GetAccessPointPolicyStatus",
        "s3:DescribeMultiRegionAccessPointOperation",
        "s3:GetMultiRegionAccessPoint",
        "s3:GetMultiRegionAccessPointPolicy",
        "s3:GetMultiRegionAccessPointPolicyStatus",
        "s3:ListMultiRegionAccessPoints",
        "iam:GetRole",
        "iam:ListRoles",
        "kms:DescribeKey",
        "kms:GetKeyPolicy",
        "kms:ListGrants",
        "kms:ListKeyPolicies",
        "kms:ListKeys",
        "ec2:DescribeVpcs",
        "ec2:DescribeVpcEndpoints",
        "ec2:DescribeByoipCidrs",
        "ec2:DescribeAddresses",
        "lambda:ListFunctions",
        "lambda:GetPolicy",
        "lambda:ListLayers",
        "lambda:ListLayerVersions",
        "lambda:GetLayerVersionPolicy",
        "sqs:GetQueueAttributes",
        "sqs:ListQueues",
        "secretsmanager:DescribeSecret",
        "secretsmanager:GetResourcePolicy",
        "secretsmanager:ListSecrets",
        "organizations:ListAWSServiceAccessForOrganization",
        "organizations:ListDelegatedAdministrators",
        "organizations:ListRoots",
        "organizations:ListParents",
        "organizations:ListChildren",
        "organizations:ListOrganizationalUnitsForParent",
        "organizations:ListAccountsForParent",
        "organizations:ListAccounts",
        "organizations:DescribeAccount",
        "organizations:DescribeOrganization",
        "organizations:DescribeOrganizationalUnit"
      ],
      "Resource": "*"
    }
  ]
  }
```

## <a name="w260aac27c55c45"></a>





## IAM Access Analyzer updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>



View details about updates to AWS managed policies for IAM Access Analyzer since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the IAM Access Analyzer Document history page\.




| Change | Description | Date | 
| --- | --- | --- | 
| [AccessAnalyzerServiceRolePolicy](https://console.aws.amazon.com/iam/home#policies/AccessAnalyzerServiceRolePolicy) – Add permission for Amazon S3 multi\-region access points | IAM Access Analyzer added new Amazon S3 actions to analyze metadata associated with multi\-region access points\. | September 2, 2021 | 
|  [IAMAccessAnalyzerReadOnlyAccess](#security-iam-awsmanpol-IAMAccessAnalyzerReadOnlyAccess) – Add permission to support policy validation  |  IAM Access Analyzer added a new action to grant `ValidatePolicy` permissions to allow you to use the policy checks for validation\. This permission is required by IAM Access Analyzer to perform policy checks on your policies\. This action is associated to the `ValidatePolicy` API operation\.  | March 16, 2021 | 
|  IAM Access Analyzer started tracking changes  |  IAM Access Analyzer started tracking changes for its AWS managed policies\.  | March 1, 2021 | 