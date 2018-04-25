# Actions, Resources, and Condition Keys for Amazon SNS<a name="list_amazonsns"></a>

Amazon SNS \(service prefix: `sns`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/sns/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/sns/latest/api/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon SNS](#amazonsns-actions-as-permissions)
+ [Resources Defined by SNS](#amazonsns-resources-for-iam-policies)
+ [Condition Keys for Amazon SNS](#amazonsns-policy-keys)

## Actions Defined by Amazon SNS<a name="amazonsns-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [AddPermission](http://docs.aws.amazon.com/sns/latest/api/API_AddPermission.html) | Adds a statement to a topic's access control policy, granting access for the specified AWS accounts to the specified actions\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [CheckIfPhoneNumberIsOptedOut](http://docs.aws.amazon.com/sns/latest/api/API_CheckIfPhoneNumberIsOptedOut.html) | Accepts a phone number and indicates whether the phone holder has opted out of receiving SMS messages from your account\. |   |  |  |  | 
| [ConfirmSubscription](http://docs.aws.amazon.com/sns/latest/api/API_ConfirmSubscription.html) | Verifies an endpoint owner's intent to receive messages by validating the token sent to the endpoint by an earlier Subscribe action\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [CreatePlatformApplication](http://docs.aws.amazon.com/sns/latest/api/API_CreatePlatformApplication.html) | Creates a platform application object for one of the supported push notification services, such as APNS and GCM, to which devices and mobile apps may register\. |   |  |  |  | 
| [CreatePlatformEndpoint](http://docs.aws.amazon.com/sns/latest/api/API_CreatePlatformEndpoint.html) | Creates an endpoint for a device and mobile app on one of the supported push notification services, such as GCM and APNS\. |   |  |  |  | 
| [CreateTopic](http://docs.aws.amazon.com/sns/latest/api/API_CreateTopic.html) | Creates a topic to which notifications can be published\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [DeleteEndpoint](http://docs.aws.amazon.com/sns/latest/api/API_DeleteEndpoint.html) | Deletes the endpoint for a device and mobile app from Amazon SNS\. |   |  |  |  | 
| [DeletePlatformApplication](http://docs.aws.amazon.com/sns/latest/api/API_DeletePlatformApplication.html) | Deletes a platform application object for one of the supported push notification services, such as APNS and GCM\. |   |  |  |  | 
| [DeleteTopic](http://docs.aws.amazon.com/sns/latest/api/API_DeleteTopic.html) | Deletes a topic and all its subscriptions\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [GetEndpointAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetEndpointAttributes.html) | Retrieves the endpoint attributes for a device on one of the supported push notification services, such as GCM and APNS\. |   |  |  |  | 
| [GetPlatformApplicationAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetPlatformApplicationAttributes.html) | Retrieves the attributes of the platform application object for the supported push notification services, such as APNS and GCM\. |   |  |  |  | 
| [GetSMSAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetSMSAttributes.html) | Returns the settings for sending SMS messages from your account\. |   |  |  |  | 
| [GetSubscriptionAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetSubscriptionAttributes.html) | Returns all of the properties of a subscription\. |   |  |  |  | 
| [GetTopicAttributes](http://docs.aws.amazon.com/sns/latest/api/API_GetTopicAttributes.html) | Returns all of the properties of a topic\. Topic properties returned might differ based on the authorization of the user\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [ListEndpointsByPlatformApplication](http://docs.aws.amazon.com/sns/latest/api/API_ListEndpointsByPlatformApplication.html) | Lists the endpoints and endpoint attributes for devices in a supported push notification service, such as GCM and APNS\. |   |  |  |  | 
| [ListPhoneNumbersOptedOut](http://docs.aws.amazon.com/sns/latest/api/API_ListPhoneNumbersOptedOut.html) | Returns a list of phone numbers that are opted out, meaning you cannot send SMS messages to them\. |   |  |  |  | 
| [ListPlatformApplications](http://docs.aws.amazon.com/sns/latest/api/API_ListPlatformApplications.html) | Lists the platform application objects for the supported push notification services, such as APNS and GCM\. |   |  |  |  | 
| [ListSubscriptions](http://docs.aws.amazon.com/sns/latest/api/API_ListSubscriptions.html) | Returns a list of the requester's subscriptions\. |   |  |  |  | 
| [ListSubscriptionsByTopic](http://docs.aws.amazon.com/sns/latest/api/API_ListSubscriptionsByTopic.html) | Returns a list of the subscriptions to a specific topic\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [ListTopics](http://docs.aws.amazon.com/sns/latest/api/API_ListTopics.html) | Returns a list of the requester's topics\. Each call returns a limited list of topics, up to 100\. |   |  |  |  | 
| [OptInPhoneNumber](http://docs.aws.amazon.com/sns/latest/api/API_OptInPhoneNumber.html) | Opts in a phone number that is currently opted out, which enables you to resume sending SMS messages to the number\. |   |  |  |  | 
| [Publish](http://docs.aws.amazon.com/sns/latest/api/API_Publish.html) | Sends a message to all of a topic's subscribed endpoints\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [RemovePermission](http://docs.aws.amazon.com/sns/latest/api/API_RemovePermission.html) | Removes a statement from a topic's access control policy\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [SetEndpointAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetEndpointAttributes.html) | Sets the attributes for an endpoint for a device on one of the supported push notification services, such as GCM and APNS\. |   |  |  |  | 
| [SetPlatformApplicationAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetPlatformApplicationAttributes.html) | Sets the attributes of the platform application object for the supported push notification services, such as APNS and GCM\. |   |  |  |  | 
| [SetSubscriptionAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetSubscriptionAttributes.html) | Allows a subscription owner to set an attribute of the topic to a new value\. |   |  |  |  | 
| [SetTopicAttributes](http://docs.aws.amazon.com/sns/latest/api/API_SetTopicAttributes.html) | Allows a topic owner to set an attribute of the topic to a new value\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [Subscribe](http://docs.aws.amazon.com/sns/latest/api/API_Subscribe.html) | Prepares to subscribe an endpoint by sending the endpoint a confirmation message\. |   | [topic\*](#amazonsns-topic)  |  |  | 
| [Unsubscribe](http://docs.aws.amazon.com/sns/latest/api/API_Unsubscribe.html) | Deletes a subscription\. If the subscription requires authentication for deletion, only the owner of the subscription or the topic's owner can unsubscribe, and an AWS signature is required\. |   |  |  |  | 

## Resources Defined by SNS<a name="amazonsns-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsns-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [topic](http://docs.aws.amazon.com/sns/latest/dg/CreateTopic.html) | arn:$\{Partition\}:sns:$\{Region\}:$\{Account\}:$\{TopicName\} |  | 

## Condition Keys for Amazon SNS<a name="amazonsns-policy-keys"></a>

Amazon SNS defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [sns:Endpoint](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#w2ab1c11c23c19) | The URL, email address, or ARN from a Subscribe request or a previously confirmed subscription\. | String | 
| [sns:Protocol](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#w2ab1c11c23c19) | The protocol value from a Subscribe request or a previously confirmed subscription\. | String | 