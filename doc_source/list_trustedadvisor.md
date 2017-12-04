# Actions and Condition Context Keys for AWS Trusted Advisor<a name="list_trustedadvisor"></a>

AWS Trusted Advisor \(service prefix: trustedadvisor\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS Trusted Advisor**

AWS Trusted Advisor provides the following service\-specific actions and condition context keys for use in IAM policies\. Note that these actions apply only to Trusted Advisor in the AWS Management Console; they do not apply to the Trusted Advisor\-related actions provided by the AWS Support API \(such as `DescribeTrustedAdvisorChecks`\)\. For more information about how these actions affect access to the Trusted Advisor console, see [Controlling Access to the Trusted Advisor Console](https://aws.amazon.com//premiumsupport/ta-iam/)\.

To use the Trusted Advisor\-related actions provided by the AWS Support API, your policy must include the `support:*` action \(explicitly or implicitly\); none of the `trustedadvisor` action permissions restrict your access\.

+ `trustedadvisor:IncludeCheckItems`

+ `trustedadvisor:DescribeCheckRefreshStatuses`

+ `trustedadvisor:UpdateNotificationPreferences`

+ `trustedadvisor:RefreshCheck`

+ `trustedadvisor:DescribeNotificationPreferences`

+ `trustedadvisor:ExcludeCheckItems`

+ `trustedadvisor:DescribeCheckSummaries`

+ `trustedadvisor:DescribeCheckItems`

**Condition context keys for AWS Trusted Advisor**

AWS Trusted Advisor has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.