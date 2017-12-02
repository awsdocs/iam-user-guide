# Actions and Condition Context Keys for Amazon SNS<a name="list_sns"></a>

Amazon SNS \(service prefix: sns\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon SNS**

For information about using the following Amazon SNS API actions in an IAM policy, see [Amazon SNS Actions](http://alpha-docs-aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#UsingWithSNS_Actions) in the *Amazon Simple Notification Service Developer Guide*\.

+ `[sns:GetEndpointAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_GetEndpointAttributes.html)`

+ `[sns:ListTopics](http://alpha-docs-aws.amazon.com/sns/latest/api/API_ListTopics.html)`

+ `[sns:SetSMSAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_SetSMSAttributes.html)`

+ `[sns:GetPlatformApplicationAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_GetPlatformApplicationAttributes.html)`

+ `[sns:AddPermission](http://alpha-docs-aws.amazon.com/sns/latest/api/API_AddPermission.html)`

+ `[sns:ListPhoneNumbersOptedOut](http://alpha-docs-aws.amazon.com/sns/latest/api/API_ListPhoneNumbersOptedOut.html)`

+ `[sns:DeleteTopic](http://alpha-docs-aws.amazon.com/sns/latest/api/API_DeleteTopic.html)`

+ `[sns:Subscribe](http://alpha-docs-aws.amazon.com/sns/latest/api/API_Subscribe.html)`

+ `[sns:GetTopicAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_GetTopicAttributes.html)`

+ `[sns:GetSubscriptionAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_GetSubscriptionAttributes.html)`

+ `[sns:RemovePermission](http://alpha-docs-aws.amazon.com/sns/latest/api/API_RemovePermission.html)`

+ `[sns:ListPlatformApplications](http://alpha-docs-aws.amazon.com/sns/latest/api/API_ListPlatformApplications.html)`

+ `[sns:SetPlatformApplicationAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_SetPlatformApplicationAttributes.html)`

+ `[sns:CreateTopic](http://alpha-docs-aws.amazon.com/sns/latest/api/API_CreateTopic.html)`

+ `[sns:ListSubscriptionsByTopic](http://alpha-docs-aws.amazon.com/sns/latest/api/API_ListSubscriptionsByTopic.html)`

+ `[sns:ListEndpointsByPlatformApplication](http://alpha-docs-aws.amazon.com/sns/latest/api/API_ListEndpointsByPlatformApplication.html)`

+ `[sns:Unsubscribe](http://alpha-docs-aws.amazon.com/sns/latest/api/API_Unsubscribe.html)`

+ `[sns:SetSubscriptionAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_SetSubscriptionAttributes.html)`

+ `[sns:OptInPhoneNumber](http://alpha-docs-aws.amazon.com/sns/latest/api/API_OptInPhoneNumber.html)`

+ `[sns:Publish](http://alpha-docs-aws.amazon.com/sns/latest/api/API_Publish.html)`

+ `[sns:SetEndpointAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_SetEndpointAttributes.html)`

+ `[sns:GetSMSAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_GetSMSAttributes.html)`

+ `[sns:CheckIfPhoneNumberIsOptedOut](http://alpha-docs-aws.amazon.com/sns/latest/api/API_CheckIfPhoneNumberIsOptedOut.html)`

+ `[sns:DeleteEndpoint](http://alpha-docs-aws.amazon.com/sns/latest/api/API_DeleteEndpoint.html)`

+ `[sns:SetTopicAttributes](http://alpha-docs-aws.amazon.com/sns/latest/api/API_SetTopicAttributes.html)`

+ `[sns:DeletePlatformApplication](http://alpha-docs-aws.amazon.com/sns/latest/api/API_DeletePlatformApplication.html)`

+ `[sns:CreatePlatformEndpoint](http://alpha-docs-aws.amazon.com/sns/latest/api/API_CreatePlatformEndpoint.html)`

+ `[sns:ListSubscriptions](http://alpha-docs-aws.amazon.com/sns/latest/api/API_ListSubscriptions.html)`

+ `[sns:CreatePlatformApplication](http://alpha-docs-aws.amazon.com/sns/latest/api/API_CreatePlatformApplication.html)`

+ `[sns:ConfirmSubscription](http://alpha-docs-aws.amazon.com/sns/latest/api/API_ConfirmSubscription.html)`

**Condition context keys for Amazon SNS**

For information about using condition keys in an IAM policy to control access to Amazon SNS, see [Amazon SNS Keys](http://alpha-docs-aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#d0e2187) in the *Amazon Simple Notification Service Developer Guide*\.

Amazon SNS has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `sns:Endpoint`

+ `sns:Protocol`