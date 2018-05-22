# Actions, Resources, and Condition Keys for Amazon Lex<a name="list_amazonlex"></a>

Amazon Lex \(service prefix: `lex`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/lex/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/lex/latest/dg/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/lex/latest/dg/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Lex](#amazonlex-actions-as-permissions)
+ [Resources Defined by Lex](#amazonlex-resources-for-iam-policies)
+ [Condition Keys for Amazon Lex](#amazonlex-policy-keys)

## Actions Defined by Amazon Lex<a name="amazonlex-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_CreateBotVersion.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_CreateBotVersion.html) | Creates a new version based on the $LATEST version of the specified bot\. | Write | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_CreateIntentVersion.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_CreateIntentVersion.html) | Creates a new version based on the $LATEST version of the specified intent\. | Write | [intent\*](#amazonlex-intent)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_CreateSlotTypeVersion.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_CreateSlotTypeVersion.html) | Creates a new version based on the $LATEST version of the specified slot type\. | Write | [slottype\*](#amazonlex-slottype)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteBot.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteBot.html) | Deletes all versions of a bot\. | Write | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteBotAlias.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteBotAlias.html) | Deletes an alias for a specific bot\. | Write | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteBotChannelAssociation.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteBotChannelAssociation.html) | Deletes the association between a Amazon Lex bot alias and a messaging platform\. | Write | [channel\*](#amazonlex-channel)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteBotVersion.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteBotVersion.html) | Deletes a specific version of a bot\. | Write | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteIntent.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteIntent.html) | Deletes all versions of an intent\. | Write | [intent\*](#amazonlex-intent)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteIntentVersion.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteIntentVersion.html) | Deletes a specific version of an intent\. | Write | [intent\*](#amazonlex-intent)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteSlotType.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteSlotType.html) | Deletes all versions of a slot type\. | Write | [slottype\*](#amazonlex-slottype)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteSlotTypeVersion.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteSlotTypeVersion.html) | Deletes a specific version of a slot type\. | Write | [slottype\*](#amazonlex-slottype)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteUtterances.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_DeleteUtterances.html) | Deletes the information Amazon Lex maintains for utterances on a specific bot and userId\. | Write | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBot.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBot.html) | Returns information for a specific bot\. In addition to the bot name, the bot version or alias is required\. | Read | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotAlias.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotAlias.html) | Returns information about a Amazon Lex bot alias\. | Read | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotAliases.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotAliases.html) | Returns a list of aliases for a given Amazon Lex bot\. | List | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotChannelAssociation.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotChannelAssociation.html) | Returns information about the association between a Amazon Lex bot and a messaging platform\. | Read | [channel\*](#amazonlex-channel)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotChannelAssociations.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotChannelAssociations.html) | Returns a list of all of the channels associated with a single bot\. | List | [channel\*](#amazonlex-channel)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotVersions.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBotVersions.html) | Returns information for all versions of a specific bot\. | List | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBots.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBots.html) | Returns information for the $LATEST version of all bots, subject to filters provided by the client\. | List |  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBuiltinIntent.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBuiltinIntent.html) | Returns information about a built\-in intent\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBuiltinIntents.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBuiltinIntents.html) | Gets a list of built\-in intents that meet the specified criteria\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBuiltinSlotTypes.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetBuiltinSlotTypes.html) | Gets a list of built\-in slot types that meet the specified criteria\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetIntent.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetIntent.html) | Returns information for a specific intent\. In addition to the intent name, you must also specify the intent version\. | Read | [intent\*](#amazonlex-intent)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetIntentVersions.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetIntentVersions.html) | Returns information for all versions of a specific intent\. | List | [intent\*](#amazonlex-intent)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetIntents.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetIntents.html) | Returns information for the $LATEST version of all intents, subject to filters provided by the client\. | List |  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetSlotType.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetSlotType.html) | Returns information about a specific version of a slot type\. In addition to specifying the slot type name, you must also specify the slot type version\. | Read | [slottype\*](#amazonlex-slottype)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetSlotTypeVersions.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetSlotTypeVersions.html) | Returns information for all versions of a specific slot type\. | List | [slottype\*](#amazonlex-slottype)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetSlotTypes.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetSlotTypes.html) | Returns information for the $LATEST version of all slot types, subject to filters provided by the client\. | List |  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetUtterancesView.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_GetUtterancesView.html) | Returns a view of aggregate utterance data for versions of a bot for a recent time period\. | List | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_runtime_PostContent.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_runtime_PostContent.html) | Sends user input \(text or speech\) to Amazon Lex\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_runtime_PostText.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_runtime_PostText.html) | Sends user input \(text\-only\) to Amazon Lex\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_PutBot.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_PutBot.html) | Creates or updates the $LATEST version of a Amazon Lex conversational bot\. | Write | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_PutBotAlias.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_PutBotAlias.html) | Creates or updates an alias for the specific bot\. | Write | [bot\*](#amazonlex-bot)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_PutIntent.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_PutIntent.html) | Creates or updates the $LATEST version of an intent\. | Write | [intent\*](#amazonlex-intent)  |  |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_PutSlotType.html](http://docs.aws.amazon.com/lex/latest/dg/APIReference/API_PutSlotType.html) | Creates or updates the $LATEST version of a slot type\. | Write | [slottype\*](#amazonlex-slottype)  |  |  | 

## Resources Defined by Lex<a name="amazonlex-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonlex-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/lex/latest/dg/API_BotMetadata.html](http://docs.aws.amazon.com/lex/latest/dg/API_BotMetadata.html) | arn:$\{Partition\}:lex:$\{Region\}:$\{Account\}:bot:$\{BotName\}:$\{BotVersionOrAlias\} |  | 
| channel | arn:$\{Partition\}:lex:$\{Region\}:$\{Account\}:bot\-channel:$\{BotName\}:$\{BotAlias\}:$\{ChannelName\} |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/API_Intent.html](http://docs.aws.amazon.com/lex/latest/dg/API_Intent.html) | arn:$\{Partition\}:lex:$\{Region\}:$\{Account\}:intent:$\{IntentName\}:$\{IntentVersion\} |  | 
| [http://docs.aws.amazon.com/lex/latest/dg/API_SlotTypeMetadata.html](http://docs.aws.amazon.com/lex/latest/dg/API_SlotTypeMetadata.html) | arn:$\{Partition\}:lex:$\{Region\}:$\{Account\}:slottype:$\{SlotName\}:$\{SlotVersion\} |  | 

## Condition Keys for Amazon Lex<a name="amazonlex-policy-keys"></a>

Amazon Lex defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| lex:associatedIntents | Enables you to control access based on the intents included in the request\. | String | 
| lex:associatedSlotTypes | Enables you to control access based on the slot types included in the request\. | String | 
| lex:channelType | Enables you to control access based on the channel type included in the request\. | String | 