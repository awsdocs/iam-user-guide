# Getting started with AWS Identity and Access Management Access Analyzer findings<a name="access-analyzer-getting-started"></a>

Use the information in this topic to learn about the requirements necessary to use and manage AWS Identity and Access Management Access Analyzer, and then how to enable IAM Access Analyzer\. To learn more about the service\-linked role for IAM Access Analyzer, see [Using service\-linked roles for AWS Identity and Access Management Access Analyzer](access-analyzer-using-service-linked-roles.md)\.

## Permissions required to use IAM Access Analyzer<a name="access-analyzer-permissions"></a>

To successfully configure and use IAM Access Analyzer, the account you use must be granted the required permissions\. 

### AWS managed policies for IAM Access Analyzer<a name="access-analyzer-permissions-awsmanpol"></a>

AWS Identity and Access Management Access Analyzer provides AWS managed policies to help you get started quickly\.
+ IAMAccessAnalyzerFullAccess \- Allows full access to IAM Access Analyzer for administrators\. This policy also allows creating the service\-linked roles that are required to allow IAM Access Analyzer to analyze resources in your account or AWS organization\.
+ IAMAccessAnalyzerReadOnlyAccess \- Allows read\-only access to IAM Access Analyzer\. You must add additional policies to your IAM identities \(users, groups of users, or roles\) to allow them to view their findings\.

### Resources defined by AWS Identity and Access Management Access Analyzer<a name="permission-resources"></a>

To view the resources defined by IAM Access Analyzer, see [Resource types defined by AWS Identity and Access Management Access Analyzer](https://docs.aws.amazon.com/service-authorization/latest/reference/list_awsiamaccessanalyzer.html#awsiamaccessanalyzer-resources-for-iam-policies) in the *Service Authorization Reference*\.

### Required IAM Access Analyzer service permissions<a name="access-analyzer-permissions-service"></a>

IAM Access Analyzer uses a service\-linked role named `AWSServiceRoleForAccessAnalyzer` to grant the service read\-only access to analyze AWS resources with resource\-based policies on your behalf\. When you create an analyzer with your account as the zone of trust, the service creates the role in your account\. For more information, see [Using service\-linked roles for AWS Identity and Access Management Access Analyzer](access-analyzer-using-service-linked-roles.md)\.

**Note**  
IAM Access Analyzer is Regional\. You must enable IAM Access Analyzer in each Region independently\.

In some cases, after you enable IAM Access Analyzer, the **Findings** page loads with no findings\. This might be due to a delay in the console for populating your findings\. You need to manually refresh the browser to view your findings\. If you still don't see any findings, it's because you have no supported resources in your account that can be accessed by an external entity\. If a policy that grants access to an external entity is applied to a resource, IAM Access Analyzer generates a finding\.

**Note**  
It may take up to 30 minutes after a policy is modified for IAM Access Analyzer to analyze the resource and then either generate a new finding or update an existing finding for the access to the resource\.

## Enabling IAM Access Analyzer<a name="access-analyzer-enabling"></a>

To enable IAM Access Analyzer in a Region, you must create an analyzer in that Region\. You must create an analyzer in each Region in which you want to monitor access to your resources\.

**To create an analyzer with the account as the zone of trust**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Access analyzer**\. 

1. Choose **Create analyzer**\.

1. On the **Create analyzer** page, confirm that the Region displayed is the Region where you want to enable IAM Access Analyzer\.

1. Enter a name for the analyzer\.

1. Choose the account as the zone of trust for the analyzer\.
**Note**  
If your account is not the AWS Organizations management account or [delegated administrator](access-analyzer-settings.md#access-analyzer-delegated-administrator) account, you can create only one analyzer with your account as the zone of trust\.

1. Optional\. Add any tags that you want to apply to the analyzer\.

1. Choose **Create Analyzer**\.

When you create an analyzer to enable IAM Access Analyzer, a service\-linked role named `AWSServiceRoleForAccessAnalyzer` is created in your account\.

**To create an analyzer with the organization as the zone of trust**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Access analyzer**\. 

1. Choose **Create analyzer**\.

1. On the **Create analyzer** page, confirm that the Region displayed is the Region where you want to enable IAM Access Analyzer\.

1. Enter a name for the analyzer\.

1. Choose your organization as the zone of trust for the analyzer\.

1. Optional\. Add any tags that you want to apply to the analyzer\.

1. Choose **Create Analyzer**\.

When you create an analyzer with the organization as the zone of trust, a service\-linked role named `AWSServiceRoleForAccessAnalyzer` is created in each account of your organization\.

## IAM Access Analyzer status<a name="access-analyzer-status"></a>

To view the status of your analyzers, choose **Analyzers**\. Analyzers created for an organization or account can have the following status:


| Status | Description | 
| --- | --- | 
|  Active  |  The analyzer is actively monitoring resources within its zone of trust\. The analyzer actively generates new findings and updates existing findings\.  | 
|  Creating  |  The creation of the analyzer is still in progress\. The analyzer becomes active once creation is complete\.  | 
|  Disabled  |  The analyzer is disabled due to an action taken by the AWS Organizations administrator\. For example, removing the analyzer’s account as the delegated administrator for IAM Access Analyzer\. When the analyzer is in a disabled state it does not generate new findings or update existing findings\.  | 
|  Failed  |  The creation of the analyzer failed due to a configuration issue\. The analyzer won't generate any findings\. Delete the analyzer and create a new analyzer\.  | 