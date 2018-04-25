# Actions, Resources, and Condition Keys for Amazon SES<a name="list_amazonses"></a>

Amazon SES \(service prefix: `ses`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/ses/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/control-user-access.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon SES](#amazonses-actions-as-permissions)
+ [Resources Defined by SES](#amazonses-resources-for-iam-policies)
+ [Condition Keys for Amazon SES](#amazonses-policy-keys)

## Actions Defined by Amazon SES<a name="amazonses-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [CloneReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_CloneReceiptRuleSet.html) | Creates a receipt rule set by cloning an existing one |   |  |  |  | 
| [CreateConfigurationSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateConfigurationSet.html) | Creates a new configuration set |   |  |  |  | 
| [CreateConfigurationSetEventDestination](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateConfigurationSetEventDestination.html) | Creates a configuration set event destination |   |  |  |  | 
| [CreateConfigurationSetTrackingOptions](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateConfigurationSetTrackingOptions.html) | Creates an association between a configuration set and a custom domain for open and click event tracking |   |  |  |  | 
| [CreateCustomVerificationEmailTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateCustomVerificationEmailTemplate.html) | Creates a new custom verification email template |   |  |  |  | 
| [CreateReceiptFilter](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptFilter.html) | Creates a new IP address filter |   |  |  |  | 
| [CreateReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptRule.html) | Creates a receipt rule |   |  |  |  | 
| [CreateReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateReceiptRuleSet.html) | Creates an empty receipt rule set |   |  |  |  | 
| [CreateTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_CreateTemplate.html) | Creates an email template |   |  |  |  | 
| [DeleteConfigurationSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteConfigurationSet.html) | Deletes the configuration set |   |  |  |  | 
| [DeleteConfigurationSetEventDestination](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteConfigurationSetEventDestination.html) | Deletes a configuration set event destination |   |  |  |  | 
| [DeleteConfigurationSetTrackingOptions](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteConfigurationSetTrackingOptions.html) | Deletes an association between a configuration set and a custom domain for open and click event tracking |   |  |  |  | 
| [DeleteCustomVerificationEmailTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteCustomVerificationEmailTemplate.html) | Deletes an existing custom verification email template |   |  |  |  | 
| [DeleteIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteIdentity.html) | Deletes the specified identity \(an email address or a domain\) from the list of verified identities |   |  |  |  | 
| [DeleteIdentityPolicy](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteIdentityPolicy.html) | Deletes the specified identity \(an email address or a domain\) from the list of verified identities |   |  |  |  | 
| [DeleteReceiptFilter](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptFilter.html) | Deletes the specified IP address filter |   |  |  |  | 
| [DeleteReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptRule.html) | Deletes the specified receipt rule |   |  |  |  | 
| [DeleteReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteReceiptRuleSet.html) | Deletes the specified receipt rule set and all of the receipt rules it contains |   |  |  |  | 
| [DeleteTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteTemplate.html) | Deletes an email template |   |  |  |  | 
| [DeleteVerifiedEmailAddress](http://docs.aws.amazon.com/ses/latest/APIReference/API_DeleteVerifiedEmailAddress.html) | Deletes the specified email address from the list of verified addresses |   |  |  |  | 
| [DescribeActiveReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeActiveReceiptRuleSet.html) | Returns the metadata and receipt rules for the receipt rule set that is currently active |   |  |  |  | 
| [DescribeConfigurationSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeConfigurationSet.html) | Returns the details of the specified configuration set |   |  |  |  | 
| [DescribeReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeReceiptRule.html) | Returns the details of the specified receipt rule |   |  |  |  | 
| [DescribeReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_DescribeReceiptRuleSet.html) | Returns the details of the specified receipt rule set |   |  |  |  | 
| [GetAccountSendingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetAccountSendingEnabled.html) | Returns the email sending status of the Amazon SES account for the current region |   |  |  |  | 
| [GetCustomVerificationEmailTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetCustomVerificationEmailTemplate.html) | Returns the custom email verification template for the template name you specify |   |  |  |  | 
| [GetIdentityDkimAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityDkimAttributes.html) | Returns the current status of Easy DKIM signing for an entity |   |  |  |  | 
| [GetIdentityMailFromDomainAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityMailFromDomainAttributes.html) | Returns the custom MAIL FROM attributes for a list of identities \(email addresses and/or domains\) |   |  |  |  | 
| [GetIdentityNotificationAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityNotificationAttributes.html) | Given a list of verified identities \(email addresses and/or domains\), returns a structure describing identity notification attributes |   |  |  |  | 
| [GetIdentityPolicies](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityPolicies.html) | Returns the requested sending authorization policies for the given identity \(an email address or a domain\) |   |  |  |  | 
| [GetIdentityVerificationAttributes](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetIdentityVerificationAttributes.html) | Given a list of identities \(email addresses and/or domains\), returns the verification status and \(for domain identities\) the verification token for each identity |   |  |  |  | 
| [GetSendQuota](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetSendQuota.html) | Returns the user's current sending limits |   |  |  |  | 
| [GetSendStatistics](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetSendStatistics.html) | Returns the user's sending statistics\. The result is a list of data points, representing the last two weeks of sending activity |   |  |  |  | 
| [GetTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_GetTemplate.html) | Returns the template object \(which includes the Subject line, HTML part and text part\) for the template you specify |   |  |  |  | 
| [ListConfigurationSets](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListConfigurationSets.html) | Returns a list of the configuration sets associated with your Amazon SES account in the current AWS Region |   |  |  |  | 
| [ListCustomVerificationEmailTemplates](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListCustomVerificationEmailTemplates.html) | Lists the existing custom verification email templates for your account in the current AWS Region |   |  |  |  | 
| [ListIdentities](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListIdentities.html) | Returns a list containing all of the identities \(email addresses and domains\) for your AWS account, regardless of verification status |   |  |  |  | 
| [ListIdentityPolicies](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListIdentityPolicies.html) | Returns a list of sending authorization policies that are attached to the given identity \(an email address or a domain\) |   |  |  |  | 
| [ListReceiptFilters](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListReceiptFilters.html) | Lists the IP address filters associated with your AWS account |   |  |  |  | 
| [ListReceiptRuleSets](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListReceiptRuleSets.html) | Lists the receipt rule sets that exist under your AWS account |   |  |  |  | 
| [ListTemplates](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListTemplates.html) | Lists the email templates present in your Amazon SES account in the current AWS Region |   |  |  |  | 
| [ListVerifiedEmailAddresses](http://docs.aws.amazon.com/ses/latest/APIReference/API_ListVerifiedEmailAddresses.html) | Returns a list containing all of the email addresses that have been verified |   |  |  |  | 
| [PutIdentityPolicy](http://docs.aws.amazon.com/ses/latest/APIReference/API_PutIdentityPolicy.html) | Adds or updates a sending authorization policy for the specified identity \(an email address or a domain\) |   |  |  |  | 
| [ReorderReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_ReorderReceiptRuleSet.html) | Reorders the receipt rules within a receipt rule set |   |  |  |  | 
| [SendBounce](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendBounce.html) | Generates and sends a bounce message to the sender of an email you received through Amazon SES |   |  |  |  | 
| [SendBulkTemplatedEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendBulkTemplatedEmail.html) | Composes an email message to multiple destinations |   |  |  |  | 
| [SendCustomVerificationEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendCustomVerificationEmail.html) | Adds an email address to the list of identities for your Amazon SES account in the current AWS Region and attempts to verify it |   |  |  |  | 
| [SendEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendEmail.html) | Composes an email message based on input data, and then immediately queues the message for sending |   |  |  |  | 
| [SendRawEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendRawEmail.html) | Sends an email message, with header and content specified by the client |   |  |  |  | 
| [SendTemplatedEmail](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendTemplatedEmail.html) | Composes an email message using an email template and immediately queues it for sending |   |  |  |  | 
| [SetActiveReceiptRuleSet](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetActiveReceiptRuleSet.html) | Sets the specified receipt rule set as the active receipt rule set |   |  |  |  | 
| [SetIdentityDkimEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityDkimEnabled.html) | Enables or disables Easy DKIM signing of email sent from an identity |   |  |  |  | 
| [SetIdentityFeedbackForwardingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityFeedbackForwardingEnabled.html) | Given an identity \(an email address or a domain\), enables or disables whether Amazon SES forwards bounce and complaint notifications as email |   |  |  |  | 
| [SetIdentityHeadersInNotificationsEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityHeadersInNotificationsEnabled.html) | Given an identity \(an email address or a domain\), sets whether Amazon SES includes the original email headers in the Amazon Simple Notification Service \(Amazon SNS\) notifications of a specified type |   |  |  |  | 
| [SetIdentityMailFromDomain](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityMailFromDomain.html) | Enables or disables the custom MAIL FROM domain setup for a verified identity \(an email address or a domain\) |   |  |  |  | 
| [SetIdentityNotificationTopic](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetIdentityNotificationTopic.html) | Given an identity \(an email address or a domain\), sets the Amazon Simple Notification Service \(Amazon SNS\) topic to which Amazon SES will publish bounce, complaint, and/or delivery notifications for emails sent with that identity as the Source |   |  |  |  | 
| [SetReceiptRulePosition](http://docs.aws.amazon.com/ses/latest/APIReference/API_SetReceiptRulePosition.html) | Sets the position of the specified receipt rule in the receipt rule set |   |  |  |  | 
| [TestRenderTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_TestRenderTemplate.html) | Creates a preview of the MIME content of an email when provided with a template and a set of replacement data |   |  |  |  | 
| [UpdateAccountSendingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateAccountSendingEnabled.html) | Enables or disables email sending across your entire Amazon SES account in the current AWS Region |   |  |  |  | 
| [UpdateConfigurationSetEventDestination](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateConfigurationSetEventDestination) | Updates the event destination of a configuration set |   |  |  |  | 
| [UpdateConfigurationSetReputationMetricsEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateConfigurationSetReputationMetricsEnabled) | Enables or disables the publishing of reputation metrics for emails sent using a specific configuration set in a given AWS Region |   |  |  |  | 
| [UpdateConfigurationSetSendingEnabled](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateConfigurationSetSendingEnabled) | Enables or disables email sending for messages sent using a specific configuration set in a given AWS Region |   |  |  |  | 
| [UpdateConfigurationSetTrackingOptions](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateConfigurationSetTrackingOptions) | Modifies an association between a configuration set and a custom domain for open and click event tracking |   |  |  |  | 
| [UpdateCustomVerificationEmailTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateCustomVerificationEmailTemplate) | Updates an existing custom verification email template |   |  |  |  | 
| [UpdateReceiptRule](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateReceiptRule.html) | Updates a receipt rule |   |  |  |  | 
| [UpdateTemplate](http://docs.aws.amazon.com/ses/latest/APIReference/API_UpdateTemplate.html) | Updates an email template |   |  |  |  | 
| [VerifyDomainDkim](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyDomainDkim.html) | Returns a set of DKIM tokens for a domain |   |  |  |  | 
| [VerifyDomainIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyDomainIdentity.html) | Verifies a domain |   |  |  |  | 
| [VerifyEmailAddress](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyEmailAddress.html) | Verifies an email address\. This action causes a confirmation email message to be sent to the specified address |   |  |  |  | 
| [VerifyEmailIdentity](http://docs.aws.amazon.com/ses/latest/APIReference/API_VerifyEmailIdentity.html) | Verifies an email address\. This action causes a confirmation email message to be sent to the specified address\. This action is throttled at one request per second |   |  |  |  | 

## Resources Defined by SES<a name="amazonses-resources-for-iam-policies"></a>

SES has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon SES<a name="amazonses-policy-keys"></a>

Amazon SES defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [ses:FeedbackAddress](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/email-format.html#email-header) | The "Return\-Path" address, which specifies where bounces and complaints are sent by email feedback forwarding\. | String | 
| [ses:FromAddress](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/email-format.html#email-header) | The "From" address of a message\. | String | 
| [ses:FromDisplayName](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/email-format.html#email-header) | The "From" address that is used as the display name of a message\. | String | 
| [ses:Recipients](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/email-format.html#email-header) | The recipient addresses of a message, which include the "To", "CC", and "BCC" addresses\. | String | 