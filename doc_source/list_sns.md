# Actions and Condition Context Keys for Amazon SNS<a name="list_sns"></a>

Amazon SNS \(service prefix: sns\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon SNS**

For information about using the following Amazon SNS API actions in an IAM policy, see [Amazon SNS Actions](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#UsingWithSNS_Actions) in the *Amazon Simple Notification Service Developer Guide*\.
+ `[sns:AddPermission](http://docs.aws.amazon.com/sns/latest/api/API_AddPermission.html)`
+ `[sns:CheckIfPhoneNumberIsOptedOut](http://docs.aws.amazon.com/sns/latest/api/API_CheckIfPhoneNumberIsOptedOut.html)`
+ `[sns:ConfirmSubscription](http://docs.aws.amazon.com/sns/latest/api/API_ConfirmSubscription.html)`
+ `[sns:CreatePlatformApplication](http://docs.aws.amazon.com/sns/latest/api/API_CreatePlatformApplication.html)`
+ `[sns:CreatePlatformEndpoint](http://docs.aws.amazon.com/sns/latest/api/API_CreatePlatformEndpoint.html)`
+ `[sns:CreateTopic](http://docs.aws.amazon.com/sns/latest/api/API_CreateTopic.html)`
+ `[sns:DeleteEndpoint](http://docs.aws.amazon.com/sns/latest/api/API_DeleteEndpoint.html)`
+ `[sns:DeletePlatformApplication](http://docs.aws.amazon.com/sns/latest/api/API_DeletePlatformApplication.html)`
+ `[sns:DeleteTopic](http://docs.aws.amazon.com/sns/latest/api/API_DeleteTopic.html)`
+ `[sns:GetEndpointAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetEndpointAttributes.html)`
+ `[sns:GetPlatformApplicationAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetPlatformApplicationAttributes.html)`
+ `[sns:GetSMSAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetSMSAttributes.html)`
+ `[sns:GetSubscriptionAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetSubscriptionAttributes.html)`
+ `[sns:GetTopicAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetTopicAttributes.html)`
+ `[sns:ListEndpointsByPlatformApplication](http://docs.aws.amazon.com/sns/latest/api/API_ListEndpointsByPlatformApplication.html)`
+ `[sns:ListPhoneNumbersOptedOut](http://docs.aws.amazon.com/sns/latest/api/API_ListPhoneNumbersOptedOut.html)`
+ `[sns:ListPlatformApplications](http://docs.aws.amazon.com/sns/latest/api/API_ListPlatformApplications.html)`
+ `[sns:ListSubscriptions](http://docs.aws.amazon.com/sns/latest/api/API_ListSubscriptions.html)`
+ `[sns:ListSubscriptionsByTopic](http://docs.aws.amazon.com/sns/latest/api/API_ListSubscriptionsByTopic.html)`
+ `[sns:ListTopics](http://docs.aws.amazon.com/sns/latest/api/API_ListTopics.html)`
+ `[sns:OptInPhoneNumber](http://docs.aws.amazon.com/sns/latest/api/API_OptInPhoneNumber.html)`
+ `[sns:Publish](http://docs.aws.amazon.com/sns/latest/api/API_Publish.html)`
+ `[sns:RemovePermission](http://docs.aws.amazon.com/sns/latest/api/API_RemovePermission.html)`
+ `[sns:SetEndpointAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetEndpointAttributes.html)`
+ `[sns:SetPlatformApplicationAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetPlatformApplicationAttributes.html)`
+ `[sns:SetSMSAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetSMSAttributes.html)`
+ `[sns:SetSubscriptionAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetSubscriptionAttributes.html)`
+ `[sns:SetTopicAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetTopicAttributes.html)`
+ `[sns:Subscribe](http://docs.aws.amazon.com/sns/latest/api/API_Subscribe.html)`
+ `[sns:Unsubscribe](http://docs.aws.amazon.com/sns/latest/api/API_Unsubscribe.html)`

**Condition context keys for Amazon SNS**

For information about using condition keys in an IAM policy to control access to Amazon SNS, see [Amazon SNS Keys](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#d0e2187) in the *Amazon Simple Notification Service Developer Guide*\.

Amazon SNS has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ `sns:Endpoint`
+ `sns:Protocol`