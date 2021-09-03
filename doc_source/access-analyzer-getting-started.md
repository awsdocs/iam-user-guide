# Getting started with AWS IAM Access Analyzer<a name="access-analyzer-getting-started"></a>

Use the information in this topic to learn about the requirements necessary to use and manage AWS IAM Access Analyzer, and then how to enable Access Analyzer\. To learn more about the service\-linked role for Access Analyzer, see [Using service\-linked roles for AWS IAM Access Analyzer](access-analyzer-using-service-linked-roles.md)\.

## Permissions required to use Access Analyzer<a name="access-analyzer-permissions"></a>

To successfully configure and use Access Analyzer, the account you use must be granted the required permissions\. 

### AWS managed policies for Access Analyzer<a name="access-analyzer-permissions-awsmanpol"></a>

AWS IAM Access Analyzer provides AWS managed policies to help you get started quickly\.
+ IAMAccessAnalyzerFullAccess \- Allows full access to Access Analyzer for administrators\. This policy also allows creating the service\-linked roles that are required to allow Access Analyzer to analyze resources in your account or AWS organization\.
+ IAMAccessAnalyzerReadOnlyAccess \- Allows read\-only access to Access Analyzer\. You must add additional policies to your IAM identities \(users, groups of users, or roles\) to allow them to view

### Resources defined by AWS IAM Access Analyzer<a name="permission-resources"></a>

To view the resources defined by Access Analyzer, see [https://docs.aws.amazon.com/service-authorization/latest/reference/list_awsiamaccessanalyzer.html#awsiamaccessanalyzer-resources-for-iam-policies](https://docs.aws.amazon.com/service-authorization/latest/reference/list_awsiamaccessanalyzer.html#awsiamaccessanalyzer-resources-for-iam-policies)Resource types defined by AWS IAM Access Analyzer in the *Service Authorization Reference*\.

### Required Access Analyzer service permissions<a name="access-analyzer-permissions-service"></a>

Access Analyzer uses a service\-linked role named `AWSServiceRoleForAccessAnalyzer` to grant the service read\-only access to analyze AWS resources with resource\-based policies on your behalf\. When you create an analyzer with your account as the zone of trust, the service creates the role your account\. When you create an analyzer with your organization as the zone of trust, the service creates a role in each account that belongs to your organization\. For more information, see [Using service\-linked roles for AWS IAM Access Analyzer](access-analyzer-using-service-linked-roles.md)\.

**Note**  
Access Analyzer is Regional\. You must enable Access Analyzer in each Region independently\.

In some cases, after you enable Access Analyzer, the **Findings** page loads with no findings\. This might be due to a delay in the console for populating your findings\. You need to manually refresh the browser to view your findings\. If you still don't see any findings, it's because you have no supported resources in your account that can be accessed by an external entity\. If a policy that grants access to an external entity is applied to a resource, Access Analyzer generates a finding\.

**Note**  
It may take up to 30 minutes after a policy is modified for Access Analyzer to analyze the resource and then either generate a new finding or update an existing finding for the access to the resource\.

## Enabling Access Analyzer<a name="access-analyzer-enabling"></a>

To enable Access Analyzer in a Region, you must create an analyzer in that Region\. You must create an analyzer in each Region in which you want to monitor access to your resources\.

**To create an analyzer with the account as the zone of trust**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Access analyzer**\. 

1. Choose **Create analyzer**\.

1. On the **Create analyzer** page, confirm that the Region displayed is the Region where you want to enable Access Analyzer\.

1. Enter a name for the analyzer\.

1. Choose the account as the zone of trust for the analyzer\.
**Note**  
If your account is not the AWS Organizations management account or [delegated administrator](access-analyzer-settings.md#access-analyzer-delegated-administrator) account, you can create only one analzyer with your account as the zone of trust\.

1. Optional\. Add any tags that you want to apply to the analyzer\.

1. Choose **Create Analyzer**\.

When you create an analyzer to enable Access Analyzer, a service\-linked role named `AWSServiceRoleForAccessAnalyzer` is created in your account\.

**To create an analyzer with the organization as the zone of trust**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Access analyzer**\. 

1. Choose **Create analyzer**\.

1. On the **Create analyzer** page, confirm that the Region displayed is the Region where you want to enable Access Analyzer\.

1. Enter a name for the analyzer\.

1. Choose your organization as the zone of trust for the analyzer\.

1. Optional\. Add any tags that you want to apply to the analyzer\.

1. Choose **Create Analyzer**\.

When you create an analyzer with the organization as the zone of trust, a service\-linked role named `AWSServiceRoleForAccessAnalyzer` is created in each account of your organization\.

## Access Analyzer status<a name="access-analyzer-status"></a>

To view the status of your analyzers, choose **Analyzers**\. Analyzers created for an organization or account can have the following status:


| Status | Description | 
| --- | --- | 
|  Active  |  The analyzer is actively monitoring resources within its zone of trust\. The analyzer actively generates new findings and updates existing findings\.  | 
|  Creating  |  The creation of the analyzer is still in progress\. The analyzer becomes active once creation is complete\.  | 
|  Disabled  |  The analyzer is disabled due to an action taken by the AWS Organizations administrator\. For example, removing the analyzer’s account as the delegated administrator for IAM Access Analyzer\. When the analyzer is in a disabled state it does not generate new findings or update existing findings\.  | 
|  Failed  |  The creation of the analyzer failed due to a configuration issue\. The analyzer won't generate any findings\. Delete the analyzer and create a new analyzer\.  | 

## Access Analyzer quotas<a name="access-analyzer-quotas"></a>

Access Analyzer has the following quotas:


| Resource | Default quota | Maximum quota | 
| --- | --- | --- | 
|  Maximum analyzers with an account zone of trust  |  1  |  1  | 
|  Maximum analyzers with an organization zone of trust  |  5  |  20\*  | 
|  Maximum archive rules per analyzer  |  100 Each archive rule can have up to 20 values per criterion\.  |  1,000\*  | 
| Maximum number of access previews per analyzer per hour | 1,000 | 1,000 | 
| AWS CloudTrail log files processed per policy generations | 100,000 | 100,000 | 
| Concurrent policy generations | 1 | 1 | 
| Policy generation AWS CloudTrail data size | 25 GB | 25 GB | 
| Policy generation AWS CloudTrail time range | 90 days | 90 days | 
| Policy generations per day | 5 Canceled policy generation requests apply to the daily quota\. | 5 | 

\* Some quotas are customer\-configurable using [Service Quotas](https://docs.aws.amazon.com/servicequotas/latest/userguide/intro.html)\.