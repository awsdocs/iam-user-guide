# Access Analyzer Findings<a name="access-analyzer-findings"></a>

Access Analyzer generates a finding for each instance of a resource\-based policy that grants access to a resource within your zone of trust to a principal that is not within your zone of trust\. When you create an analyzer, you choose an organization or AWS account to analyze\. Any principal in the organization or account that you choose for the analyzer is considered trusted\. Because principals in the same organization or account are trusted, the resources and principals within the organization or account comprise the zone of trust for the analyzer\. Any sharing that is within the zone of trust is considered safe, so Access Analyzer does not generate a finding\. For example, if you select an organization as the zone of trust for an analyzer, all resources and principals in the organization are within the zone of trust\. If you grant permissions to an S3 bucket in one of your organization member accounts to a principal in another organization member account, Access Analyzer does not generate a finding\. But if you grant permission to a principal in an account that is not a member of the organization, Access Analyzer generates a finding\.

**Topics**
+ [Working with Findings](access-analyzer-work-with-findings.md)
+ [Review Findings](access-analyzer-findings-view.md)
+ [Filtering Findings](access-analyzer-findings-filter.md)
+ [Archiving Findings](access-analyzer-findings-archive.md)
+ [Resolving Findings](access-analyzer-findings-remediate.md)