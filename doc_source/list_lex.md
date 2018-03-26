# Actions and Condition Context Keys for Amazon Lex<a name="list_lex"></a>

Amazon Lex \(service prefix: lex\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for Amazon Lex**

For information about using the following Amazon Lex API actions in an IAM policy, see [Authentication and Access Control for Amazon Lex](http://docs.aws.amazon.com/lex/latest/dg/auth-and-access-control.html) in the *Amazon Lex Developer Guide*\.
+ `[lex:CreateBotVersion](http://docs.aws.amazon.com/lex/latest/dg/API_CreateBotVersion.html)`
+ `[lex:CreateIntentVersion](http://docs.aws.amazon.com/lex/latest/dg/API_CreateIntentVersion.html)`
+ `[lex:CreateSlotTypeVersion](http://docs.aws.amazon.com/lex/latest/dg/API_CreateSlotTypeVersion.html)`
+ `[lex:DeleteBot](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteBot.html)`
+ `[lex:DeleteBotAlias](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteBotAlias.html)`
+ `[lex:DeleteBotChannelAssociation](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteBotChannelAssociation.html)`
+ `[lex:DeleteBotVersion](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteBotVersion.html)`
+ `[lex:DeleteIntent](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteIntent.html)`
+ `[lex:DeleteIntentVersion](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteIntentVersion.html)`
+ `[lex:DeleteSlotType](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteSlotType.html)`
+ `[lex:DeleteSlotTypeVersion](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteSlotTypeVersion.html)`
+ `[lex:DeleteUtterances](http://docs.aws.amazon.com/lex/latest/dg/API_DeleteUtterances.html)`
+ `[lex:GetBot](http://docs.aws.amazon.com/lex/latest/dg/API_GetBot.html)`
+ `[lex:GetBotAlias](http://docs.aws.amazon.com/lex/latest/dg/API_GetBotAlias.html)`
+ `[lex:GetBotAliases](http://docs.aws.amazon.com/lex/latest/dg/API_GetBotAliases.html)`
+ `[lex:GetBotChannelAssociation](http://docs.aws.amazon.com/lex/latest/dg/API_GetBotChannelAssociation.html)`
+ `[lex:GetBotChannelAssociations](http://docs.aws.amazon.com/lex/latest/dg/API_GetBotChannelAssociations.html)`
+ `[lex:GetBotVersions](http://docs.aws.amazon.com/lex/latest/dg/API_GetBotVersions.html)`
+ `[lex:GetBots](http://docs.aws.amazon.com/lex/latest/dg/API_GetBots.html)`
+ `[lex:GetBuiltinIntent](http://docs.aws.amazon.com/lex/latest/dg/API_GetBuiltinIntent.html)`
+ `[lex:GetBuiltinIntents](http://docs.aws.amazon.com/lex/latest/dg/API_GetBuiltinIntents.html)`
+ `[lex:GetBuiltinSlotTypes](http://docs.aws.amazon.com/lex/latest/dg/API_GetBuiltinSlotTypes.html)`
+ `[lex:GetIntent](http://docs.aws.amazon.com/lex/latest/dg/API_GetIntent.html)`
+ `[lex:GetIntentVersions](http://docs.aws.amazon.com/lex/latest/dg/API_GetIntentVersions.html)`
+ `[lex:GetIntents](http://docs.aws.amazon.com/lex/latest/dg/API_GetIntents.html)`
+ `[lex:GetSlotType](http://docs.aws.amazon.com/lex/latest/dg/API_GetSlotType.html)`
+ `[lex:GetSlotTypeVersions](http://docs.aws.amazon.com/lex/latest/dg/API_GetSlotTypeVersions.html)`
+ `[lex:GetSlotTypes](http://docs.aws.amazon.com/lex/latest/dg/API_GetSlotTypes.html)`
+ `[lex:GetUtterancesView](http://docs.aws.amazon.com/lex/latest/dg/API_GetUtterancesView.html)`
+ `[lex:PostContent](http://docs.aws.amazon.com/lex/latest/dg/API_PostContent.html)`
+ `[lex:PostText](http://docs.aws.amazon.com/lex/latest/dg/API_PostText.html)`
+ `[lex:PutBot](http://docs.aws.amazon.com/lex/latest/dg/API_PutBot.html)`
+ `[lex:PutBotAlias](http://docs.aws.amazon.com/lex/latest/dg/API_PutBotAlias.html)`
+ `[lex:PutIntent](http://docs.aws.amazon.com/lex/latest/dg/API_PutIntent.html)`
+ `[lex:PutSlotType](http://docs.aws.amazon.com/lex/latest/dg/API_PutSlotType.html)`

**Condition context keys for Amazon Lex**

Amazon Lex has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ `lex:associatedIntents`
+ `lex:associatedSlotTypes`
+ `lex:channelType`