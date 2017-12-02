# Actions and Condition Context Keys for Amazon SES<a name="list_ses"></a>

Amazon SES \(service prefix: ses\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon SES**

For information about using the following Amazon SES API actions in an IAM policy, see [Controlling User Access to Amazon SES](http://alpha-docs-aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html) in the *Amazon Simple Email Service Developer Guide*\.

+ `[ses:VerifyDomainIdentity](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_VerifyDomainIdentity.html)`

+ `[ses:VerifyEmailIdentity](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_VerifyEmailIdentity.html)`

+ `[ses:CreateReceiptRule](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_CreateReceiptRule.html)`

+ `[ses:DeleteReceiptFilter](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptFilter.html)`

+ `[ses:GetIdentityPolicies](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_GetIdentityPolicies.html)`

+ `[ses:CreateReceiptFilter](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_CreateReceiptFilter.html)`

+ `[ses:DeleteIdentityPolicy](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DeleteIdentityPolicy.html)`

+ `[ses:SetActiveReceiptRuleSet](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SetActiveReceiptRuleSet.html)`

+ `[ses:SendEmail](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SendEmail.html)`

+ `[ses:VerifyEmailAddress](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_VerifyEmailAddress.html)`

+ `[ses:ListReceiptRuleSets](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_ListReceiptRuleSets.html)`

+ `[ses:GetIdentityMailFromDomainAttributes](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_GetIdentityMailFromDomainAttributes.html)`

+ `[ses:VerifyDomainDkim](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_VerifyDomainDkim.html)`

+ `[ses:SendRawEmail](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SendRawEmail.html)`

+ `[ses:SetReceiptRulePosition](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SetReceiptRulePosition.html)`

+ `[ses:DeleteReceiptRule](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptRule.html)`

+ `[ses:CloneReceiptRuleSet](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_CloneReceiptRuleSet.html)`

+ `[ses:ListIdentities](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_ListIdentities.html)`

+ `[ses:UpdateReceiptRule](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_UpdateReceiptRule.html)`

+ `[ses:SendBounce](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SendBounce.html)`

+ `[ses:DeleteVerifiedEmailAddress](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DeleteVerifiedEmailAddress.html)`

+ `[ses:DescribeActiveReceiptRuleSet](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DescribeActiveReceiptRuleSet.html)`

+ `[ses:ListIdentityPolicies](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_ListIdentityPolicies.html)`

+ `[ses:SetIdentityDkimEnabled](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SetIdentityDkimEnabled.html)`

+ `[ses:GetIdentityNotificationAttributes](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_GetIdentityNotificationAttributes.html)`

+ `[ses:PutIdentityPolicy](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_PutIdentityPolicy.html)`

+ `[ses:GetIdentityVerificationAttributes](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_GetIdentityVerificationAttributes.html)`

+ `[ses:ListVerifiedEmailAddresses](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_ListVerifiedEmailAddresses.html)`

+ `[ses:GetSendStatistics](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_GetSendStatistics.html)`

+ `[ses:SetIdentityHeadersInNotificationsEnabled](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SetIdentityHeadersInNotificationsEnabled.html)`

+ `[ses:SetIdentityMailFromDomain](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SetIdentityMailFromDomain.html)`

+ `[ses:DeleteReceiptRuleSet](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptRuleSet.html)`

+ `[ses:DescribeReceiptRuleSet](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DescribeReceiptRuleSet.html)`

+ `[ses:SetIdentityFeedbackForwardingEnabled](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SetIdentityFeedbackForwardingEnabled.html)`

+ `[ses:GetSendQuota](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_GetSendQuota.html)`

+ `[ses:CreateReceiptRuleSet](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_CreateReceiptRuleSet.html)`

+ `[ses:SetIdentityNotificationTopic](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_SetIdentityNotificationTopic.html)`

+ `[ses:ListReceiptFilters](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_ListReceiptFilters.html)`

+ `[ses:DeleteIdentity](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DeleteIdentity.html)`

+ `[ses:DescribeReceiptRule](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_DescribeReceiptRule.html)`

+ `[ses:ReorderReceiptRuleSet](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_ReorderReceiptRuleSet.html)`

+ `[ses:GetIdentityDkimAttributes](http://alpha-docs-aws.amazon.com/ses/latest/APIReference/API_GetIdentityDkimAttributes.html)`

**Condition context keys for Amazon SES**

Amazon SES has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `[ses:FeedbackAddress](http://alpha-docs-aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`

+ `[ses:FromAddress](http://alpha-docs-aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`

+ `[ses:FromDisplayName](http://alpha-docs-aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`

+ `[ses:Recipients](http://alpha-docs-aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`