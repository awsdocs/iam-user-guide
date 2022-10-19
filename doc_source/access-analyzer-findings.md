# Findings for public and cross\-account access<a name="access-analyzer-findings"></a>

IAM Access Analyzer generates a finding for each instance of a resource\-based policy that grants access to a resource within your zone of trust to a principal that is not within your zone of trust\. When you create an analyzer, you choose an organization or AWS account to analyze\. Any principal in the organization or account that you choose for the analyzer is considered trusted\. Because principals in the same organization or account are trusted, the resources and principals within the organization or account comprise the zone of trust for the analyzer\. Any sharing that is within the zone of trust is considered safe, so IAM Access Analyzer does not generate a finding\. For example, if you select an organization as the zone of trust for an analyzer, all resources and principals in the organization are within the zone of trust\. If you grant permissions to an S3 bucket in one of your organization member accounts to a principal in another organization member account, IAM Access Analyzer does not generate a finding\. But if you grant permission to a principal in an account that is not a member of the organization, IAM Access Analyzer generates a finding\.

**Topics**
+ [How IAM Access Analyzer findings work](access-analyzer-concepts.md)
+ [Getting started with AWS Identity and Access Management Access Analyzer findings](access-analyzer-getting-started.md)
+ [Working with findings](access-analyzer-work-with-findings.md)
+ [Reviewing findings](access-analyzer-findings-view.md)
+ [Filtering findings](access-analyzer-findings-filter.md)
+ [Archiving findings](access-analyzer-findings-archive.md)
+ [Resolving findings](access-analyzer-findings-remediate.md)
+ [IAM Access Analyzer resource types](access-analyzer-resources.md)
+ [Settings for IAM Access Analyzer](access-analyzer-settings.md)
+ [Archive rules](access-analyzer-archive-rules.md)
+ [Monitoring AWS Identity and Access Management Access Analyzer with Amazon EventBridge](access-analyzer-eventbridge.md)
+ [Integration with AWS Security Hub](access-analyzer-securityhub-integration.md)
+ [Logging IAM Access Analyzer API calls with AWS CloudTrail](logging-using-cloudtrail.md)
+ [IAM Access Analyzer filter keys](access-analyzer-reference-filter-keys.md)
+ [Using service\-linked roles for AWS Identity and Access Management Access Analyzer](access-analyzer-using-service-linked-roles.md)