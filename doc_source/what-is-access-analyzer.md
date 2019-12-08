# What Is IAM Access Analyzer?<a name="what-is-access-analyzer"></a>

IAM Access Analyzer informs you which resources in your account that you are sharing with external principals\. It does this by using logic\-based reasoning to analyze resource\-based policies in your AWS environment\. An external entity can be another AWS account, a root user, an IAM user or role, a federated user, an AWS service, an anonymous user, or other entity that you can use to [create a filter](access-analyzer-findings-filter.md)\. For more information, see [AWS JSON Policy Elements: Principal](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html)\.

When you enable Access Analyzer, you create an analyzer for your account\. Your account is the zone of trust for the analyzer\. The analyzer monitors all of the supported resources within your zone of trust\. Any access to resources by principals that are within your zone of trust is considered trusted\. Once enabled, Access Analyzer analyzes the policies applied to all of the supported resources in your account\. After the first analysis, Access Analyzer analyzes these policies once every 24 hours\. If a new policy is added, or an existing policy is changed, Access Analyzer analyzes the new or updated policy within about 30 minutes\.

When analyzing the policies, if Access Analyzer identifies one that grants access to an external principal that isn't within your zone of trust, it generates a finding\. Each finding includes details about the resource, the external entity that has access to it, and the permissions granted so that you can take appropriate action\. You can view the details included in the finding to determine whether the resource access is intentional or a potential risk that you should resolve\. When you add a policy to a resource, or update an existing policy, Access Analyzer analyzes the policy\. Access Analyzer also analyzes all resource\-based policies every 24 hours\.

On rare occasions under certain conditions, Access Analyzer is not notified that a policy was added or updated\. When this happens, Access Analyzer analyzes the new or updated policy during the next periodic scan, which is within 24 hours\. If you want to confirm that a change you make to a policy resolves an access issue reported in a finding, you can rescan the resource reported in a finding\. To learn more, see [Resolving Findings](access-analyzer-findings-remediate.md)\.

**Important**  
Access Analyzer analyzes only policies that are applied to resources in the same AWS Region that it's enabled in\. To monitor all resources in your AWS environment, you must create an analyzer to enable Access Analyzer in each Region where you're using supported AWS resources\.

Access Analyzer analyzes the following resource types:
+ [Amazon Simple Storage Service Buckets](access-analyzer-resources.md#access-analyzer-s3)
+ [AWS Identity and Access Management Roles](access-analyzer-resources.md#access-analyzer-iam-role)
+ [AWS Key Management Service Keys](access-analyzer-resources.md#access-analyzer-kms-key)
+ [AWS Lambda Functions and Layers](access-analyzer-resources.md#access-analyzer-lambda)
+ [Amazon Simple Queue Service Queues](access-analyzer-resources.md#access-analyzer-sqs)