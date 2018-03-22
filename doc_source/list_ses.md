# Actions and Condition Context Keys for Amazon SES<a name="list_ses"></a>

Amazon SES \(service prefix: ses\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon SES**

For information about using the following Amazon SES API actions in an IAM policy, see [Controlling User Access to Amazon SES](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html) in the *Amazon Simple Email Service Developer Guide*\.
+ `[ses:CloneReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_CloneReceiptRuleSet.html)`
+ `[ses:CreateConfigurationSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateConfigurationSet.html)`
+ `[ses:CreateConfigurationSetEventDestination](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateConfigurationSetEventDestination.html)`
+ `[ses:CreateConfigurationSetTrackingOptions](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateConfigurationSetTrackingOptions.html)`
+ `[ses:CreateCustomVerificationEmailTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateCustomVerificationEmailTemplate.html)`
+ `[ses:CreateReceiptFilter](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptFilter.html)`
+ `[ses:CreateReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptRule.html)`
+ `[ses:CreateReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptRuleSet.html)`
+ `[ses:CreateTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateTemplate.html)`
+ `[ses:DeleteConfigurationSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteConfigurationSet.html)`
+ `[ses:DeleteConfigurationSetEventDestination](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteConfigurationSetEventDestination.html)`
+ `[ses:DeleteConfigurationSetTrackingOptions](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteConfigurationSetTrackingOptions.html)`
+ `[ses:DeleteCustomVerificationEmailTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteCustomVerificationEmailTemplate.html)`
+ `[ses:DeleteIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteIdentity.html)`
+ `[ses:DeleteIdentityPolicy](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteIdentityPolicy.html)`
+ `[ses:DeleteReceiptFilter](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptFilter.html)`
+ `[ses:DeleteReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptRule.html)`
+ `[ses:DeleteReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptRuleSet.html)`
+ `[ses:DeleteTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteTemplate.html)`
+ `[ses:DeleteVerifiedEmailAddress](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteVerifiedEmailAddress.html)`
+ `[ses:DescribeActiveReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeActiveReceiptRuleSet.html)`
+ `[ses:DescribeConfigurationSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeConfigurationSet.html)`
+ `[ses:DescribeReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeReceiptRule.html)`
+ `[ses:DescribeReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeReceiptRuleSet.html)`
+ `[ses:GetAccountSendingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetAccountSendingEnabled.html)`
+ `[ses:GetCustomVerificationEmailTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetCustomVerificationEmailTemplate.html)`
+ `[ses:GetIdentityDkimAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityDkimAttributes.html)`
+ `[ses:GetIdentityMailFromDomainAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityMailFromDomainAttributes.html)`
+ `[ses:GetIdentityNotificationAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityNotificationAttributes.html)`
+ `[ses:GetIdentityPolicies](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityPolicies.html)`
+ `[ses:GetIdentityVerificationAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityVerificationAttributes.html)`
+ `[ses:GetSendQuota](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetSendQuota.html)`
+ `[ses:GetSendStatistics](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetSendStatistics.html)`
+ `[ses:GetTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetTemplate.html)`
+ `[ses:ListConfigurationSets](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListConfigurationSets.html)`
+ `[ses:ListCustomVerificationEmailTemplates](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListCustomVerificationEmailTemplates.html)`
+ `[ses:ListIdentities](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListIdentities.html)`
+ `[ses:ListIdentityPolicies](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListIdentityPolicies.html)`
+ `[ses:ListReceiptFilters](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListReceiptFilters.html)`
+ `[ses:ListReceiptRuleSets](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListReceiptRuleSets.html)`
+ `[ses:ListTemplates](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListTemplates.html)`
+ `[ses:ListVerifiedEmailAddresses](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListVerifiedEmailAddresses.html)`
+ `[ses:PutIdentityPolicy](http://docs.aws.amazon.com/ses/latest/APIReference/API_PutIdentityPolicy.html)`
+ `[ses:ReorderReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_ReorderReceiptRuleSet.html)`
+ `[ses:SendBounce](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendBounce.html)`
+ `[ses:SendBulkTemplatedEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendBulkTemplatedEmail.html)`
+ `[ses:SendCustomVerificationEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendCustomVerificationEmail.html)`
+ `[ses:SendEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendEmail.html)`
+ `[ses:SendRawEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendRawEmail.html)`
+ `[ses:SendTemplatedEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendTemplatedEmail.html)`
+ `[ses:SetActiveReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetActiveReceiptRuleSet.html)`
+ `[ses:SetIdentityDkimEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityDkimEnabled.html)`
+ `[ses:SetIdentityFeedbackForwardingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityFeedbackForwardingEnabled.html)`
+ `[ses:SetIdentityHeadersInNotificationsEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityHeadersInNotificationsEnabled.html)`
+ `[ses:SetIdentityMailFromDomain](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityMailFromDomain.html)`
+ `[ses:SetIdentityNotificationTopic](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityNotificationTopic.html)`
+ `[ses:SetReceiptRulePosition](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetReceiptRulePosition.html)`
+ `[ses:TestRenderTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_TestRenderTemplate.html)`
+ `[ses:UpdateAccountSendingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateAccountSendingEnabled.html)`
+ `[ses:UpdateConfigurationSetEventDestination](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateConfigurationSetEventDestination.html)`
+ `[ses:UpdateConfigurationSetReputationMetricsEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateConfigurationSetReputationMetricsEnabled.html)`
+ `[ses:UpdateConfigurationSetSendingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateConfigurationSetSendingEnabled.html)`
+ `[ses:UpdateConfigurationSetTrackingOptions](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateConfigurationSetTrackingOptions.html)`
+ `[ses:UpdateCustomVerificationEmailTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateCustomVerificationEmailTemplate.html)`
+ `[ses:UpdateReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateReceiptRule.html)`
+ `[ses:UpdateTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateTemplate.html)`
+ `[ses:VerifyDomainDkim](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyDomainDkim.html)`
+ `[ses:VerifyDomainIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyDomainIdentity.html)`
+ `[ses:VerifyEmailAddress](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyEmailAddress.html)`
+ `[ses:VerifyEmailIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyEmailIdentity.html)`

**Condition context keys for Amazon SES**

Amazon SES has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ `[ses:FeedbackAddress](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`
+ `[ses:FromAddress](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`
+ `[ses:FromDisplayName](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`
+ `[ses:Recipients](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html#iam-and-ses-restrict-addresses)`