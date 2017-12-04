# Actions and Condition Context Keys for Amazon SES<a name="list_ses"></a>

Amazon SES \(service prefix: ses\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon SES**

For information about using the following Amazon SES API actions in an IAM policy, see [Controlling User Access to Amazon SES](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html) in the *Amazon Simple Email Service Developer Guide*\.

+ `[ses:VerifyDomainIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyDomainIdentity.html)`

+ `[ses:VerifyEmailIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyEmailIdentity.html)`

+ `[ses:CreateReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptRule.html)`

+ `[ses:DeleteReceiptFilter](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptFilter.html)`

+ `[ses:GetIdentityPolicies](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityPolicies.html)`

+ `[ses:CreateReceiptFilter](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptFilter.html)`

+ `[ses:DeleteIdentityPolicy](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteIdentityPolicy.html)`

+ `[ses:SetActiveReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetActiveReceiptRuleSet.html)`

+ `[ses:SendEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendEmail.html)`

+ `[ses:VerifyEmailAddress](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyEmailAddress.html)`

+ `[ses:ListReceiptRuleSets](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListReceiptRuleSets.html)`

+ `[ses:GetIdentityMailFromDomainAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityMailFromDomainAttributes.html)`

+ `[ses:VerifyDomainDkim](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyDomainDkim.html)`

+ `[ses:SendRawEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendRawEmail.html)`

+ `[ses:SetReceiptRulePosition](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetReceiptRulePosition.html)`

+ `[ses:DeleteReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptRule.html)`

+ `[ses:CloneReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_CloneReceiptRuleSet.html)`

+ `[ses:ListIdentities](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListIdentities.html)`

+ `[ses:UpdateReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateReceiptRule.html)`

+ `[ses:SendBounce](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendBounce.html)`

+ `[ses:DeleteVerifiedEmailAddress](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteVerifiedEmailAddress.html)`

+ `[ses:DescribeActiveReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeActiveReceiptRuleSet.html)`

+ `[ses:ListIdentityPolicies](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListIdentityPolicies.html)`

+ `[ses:SetIdentityDkimEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityDkimEnabled.html)`

+ `[ses:GetIdentityNotificationAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityNotificationAttributes.html)`

+ `[ses:PutIdentityPolicy](http://docs.aws.amazon.com/ses/latest/APIReference/API_PutIdentityPolicy.html)`

+ `[ses:GetIdentityVerificationAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityVerificationAttributes.html)`

+ `[ses:ListVerifiedEmailAddresses](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListVerifiedEmailAddresses.html)`

+ `[ses:GetSendStatistics](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetSendStatistics.html)`

+ `[ses:SetIdentityHeadersInNotificationsEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityHeadersInNotificationsEnabled.html)`

+ `[ses:SetIdentityMailFromDomain](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityMailFromDomain.html)`

+ `[ses:DeleteReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptRuleSet.html)`

+ `[ses:DescribeReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeReceiptRuleSet.html)`

+ `[ses:SetIdentityFeedbackForwardingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityFeedbackForwardingEnabled.html)`

+ `[ses:GetSendQuota](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetSendQuota.html)`

+ `[ses:CreateReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptRuleSet.html)`

+ `[ses:SetIdentityNotificationTopic](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityNotificationTopic.html)`

+ `[ses:ListReceiptFilters](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListReceiptFilters.html)`

+ `[ses:DeleteIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteIdentity.html)`

+ `[ses:DescribeReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeReceiptRule.html)`

+ `[ses:ReorderReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_ReorderReceiptRuleSet.html)`

+ `[ses:GetIdentityDkimAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityDkimAttributes.html)`

**Condition context keys for Amazon SES**

Amazon SES has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `[ses:FeedbackAddress](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`

+ `[ses:FromAddress](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`

+ `[ses:FromDisplayName](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`

+ `[ses:Recipients](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`