# Actions and Condition Context Keys for AWS Support<a name="list_support"></a>

AWS Support \(service prefix: support\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS Support**

AWS Support does not provide service\-specific actions or conditions, but your policy must include the `support:*` action \(explicitly or implicitly\) in order to use the AWS Support Center or to use the AWS Support API\. In addition, when you use the AWS Support API to call Trusted Advisor\-related actions \(such as `DescribeTrustedAdvisorChecks`\), none of the `trustedadvisor` actions restrict your access\. The `trustedadvisor` actions apply only to Trusted Advisor in the AWS Management Console\.
+ `support:AddAttachmentsToSet`
+ `support:AddCommunicationToCase`
+ `support:CreateCase`
+ `support:DescribeAttachment`
+ `support:DescribeCases`
+ `support:DescribeCommunications`
+ `support:DescribeServices`
+ `support:DescribeSeverityLevels`
+ `support:DescribeTrustedAdvisorCheckRefreshStatuses`
+ `support:DescribeTrustedAdvisorCheckResult`
+ `support:DescribeTrustedAdvisorCheckSummaries`
+ `support:DescribeTrustedAdvisorChecks`
+ `support:RefreshTrustedAdvisorCheck`
+ `support:ResolveCase`

**Condition context keys for AWS Support**

AWS Support has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.