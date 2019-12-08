# Access Analyzer Findings<a name="access-analyzer-findings"></a>

Access Analyzer generates a finding for each instance of a resource\-based policy that grants access to a resource in your zone of trust \(your account\) to an external entity\. Any sharing that is within the zone of trust is considered safe, so Access Analyzer doesn't generate a finding\. For example, if you grant permissions to an S3 bucket in your account to another AWS account, Access Analyzer generates a finding\. But if you grant permission to a bucket in your account to an IAM role in your account, Access Analyzer doesn't generate a finding\.

**Topics**
+ [Working with Findings](access-analyzer-work-with-findings.md)
+ [Review Findings](access-analyzer-findings-view.md)
+ [Filtering Findings](access-analyzer-findings-filter.md)
+ [Archiving Findings](access-analyzer-findings-archive.md)
+ [Resolving Findings](access-analyzer-findings-remediate.md)