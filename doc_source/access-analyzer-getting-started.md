# Getting Started with AWS IAM Access Analyzer<a name="access-analyzer-getting-started"></a>

Use the information in this topic to learn about the requirements necessary to use and manage AWS IAM Access Analyzer, and then how to enable Access Analyzer\. To learn more about the service\-linked role for Access Analyzer, see [Using Service\-Linked Roles for AWS IAM Access Analyzer](access-analyzer-using-service-linked-roles.md)\.

## Permissions Required to Use Access Analyzer<a name="access-analyzer-permissions"></a>

To successfully configure and use Access Analyzer, the account you use must be granted the required permissions\. To access and use all Access Analyzer features, you can apply the IAMAccessAnalyzerFullAccess managed policy to the account\. The full access policy grants the following permissions:

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

A custom policy for managing Access Analyzer must include the following permissions:
+ access\-analyzer: \*
+ iam:CreateServiceLinkedRole

To allow read\-only access to Access Analyzer, use the IAMAccessAnalyzerReadOnlyAccess managed policy\. This policy grants the following permissions:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "access-analyzer:Get*",
        "access-analyzer:List*"
      ],
      "Resource": "*"
    }
  ]
}
```

### Resources Defined by AWS IAM Access Analyzer<a name="permission-resources"></a>

Access Analyzer defines the following resources:


| **Resource** | **ARN** | 
| --- | --- | 
| analyzer | arn:$\{Partition\}:access\-analyzer:$\{Region\}:$\{Account\}:analyzer/$\{analyzerName\} | 
| archive\-rule | arn:$\{Partition\}:access\-analyzer:$\{Region\}:$\{Account\}:analyzer/$\{analyzerName\}/archive\-rule/$\{ruleName\} | 

### Required Access Analyzer Service Permissions<a name="access-analyzer-permissions-service"></a>

Access Analyzer uses a service\-linked role named `AWSServiceRoleForAccessAnalyzer` to grant the service read\-only access to analyze AWS resources with resource\-based policies on your behalf\. When you create an analyzer to enable Access Analyzer, the service creates the role your account\. For more information, see [Using Service\-Linked Roles for AWS IAM Access Analyzer](access-analyzer-using-service-linked-roles.md)\.

**Note**  
Access Analyzer is Regional\. You must enable Access Analyzer in each Region independently\.

In some cases, after you enable Access Analyzer, the **Findings** page loads with no findings\. This might be due to a delay in the console for populating your findings\. You need to manually refresh the browser to view your findings\. If you still don't see any findings, it's because you have no supported resources in your account that can be accessed by an external entity\. If a policy that grants access to an external entity is applied to a resource, Access Analyzer generates a finding\.

**Note**  
It may take up to 30 minutes after a policy is modified for Access Analyzer to analyze the resource and then either generate a new finding or update an existing finding for the access to the resource\.

## Enabling Access Analyzer<a name="access-analyzer-enabling"></a>

To enable Access Analyzer in a Region, you must create an analyzer in that Region\. You must create an analyzer in each Region in which you want to monitor access to your resources\.

**To create an analyzer**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Access analyzer**\. 

1. Choose **Create analyzer**\.

1. On the **Create analyzer** page, confirm that the Region displayed is the Region where you want to enable Access Analyzer\.

1. Enter a name for the analyzer\.

1. Optional\. Add any tags that you want to apply to the analyzer\.

1. Choose **Create Analyzer**\.

When you create an analyzer to enable Access Analyzer, a service\-linked role named `AWSServiceRoleForAccessAnalyzer` is created in your account\.

## Access Analyzer Quotas<a name="access-analyzer-quotas"></a>

Access Analyzer has the following quotas:


| Resource | Default quota | 
| --- | --- | 
|  Maximum analyzers with an account zone of trust  |  1  | 
|  Maximum archive rules per analyzer  |  100 Each archive rule can have up to 20 values per criterion\.  | 