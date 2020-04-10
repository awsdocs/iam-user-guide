# Actions, Resources, and Condition Keys for Amazon Chime<a name="list_amazonchime"></a>

Amazon Chime \(service prefix: `chime`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/chime/latest/ug/what-is-chime.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/chime/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/chime/latest/ag/control-access.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Chime](#amazonchime-actions-as-permissions)
+ [Resource Types Defined by Amazon Chime](#amazonchime-resources-for-iam-policies)
+ [Condition Keys for Amazon Chime](#amazonchime-policy-keys)

## Actions Defined by Amazon Chime<a name="amazonchime-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AcceptDelegate ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to accept the delegate invitation to share management of an Amazon Chime account with another AWS Account | Write |  |  |  | 
|   [ ActivateUsers ](https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to activate users in an Amazon Chime Enterprise account | Write |  |  |  | 
|   [ AddDomain ](https://docs.aws.amazon.com/chime/latest/ag/claim-domain.html)  | Grants permission to add a domain to your Amazon Chime account | Write |  |  |  | 
|   [ AddOrUpdateGroups ](https://docs.aws.amazon.com/chime/latest/ag/manage-chime-account.html)  | Grants permission to add new or update existing Active Directory or Okta user groups associated with your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ AssociatePhoneNumberWithUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_AssociatePhoneNumberWithUser.html)  | Grants permission to associate a phone number with an Amazon Chime user | Write |  |  |  | 
|   [ AssociatePhoneNumbersWithVoiceConnector ](https://docs.aws.amazon.com/chime/latest/APIReference/API_AssociatePhoneNumbersWithVoiceConnector.html)  | Grants permission to associate multiple phone numbers with an Amazon Chime Voice Connector | Write |  |  |  | 
|   [ AssociatePhoneNumbersWithVoiceConnectorGroup ](https://docs.aws.amazon.com/chime/latest/APIReference/API_AssociatePhoneNumbersWithVoiceConnectorGroup.html)  | Grants permission to associate multiple phone numbers with an Amazon Chime Voice Connector Group | Write |  |  |  | 
|   [ AssociateSigninDelegateGroupsWithAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_AssociateSigninDelegateGroupsWithAccount.html)  | Grants permission to associate the specified sign\-in delegate groups with the specified Amazon Chime account\. | Write |  |  |  | 
|   [ AuthorizeDirectory ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to authorize an Active Directory for your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ BatchCreateAttendee ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchCreateAttendee.html)  | Grants permission to create new attendees for an active Amazon Chime SDK meeting | Write |  |  |  | 
|   [ BatchCreateRoomMembership ](API_BatchCreateRoomMembership.html)  | Grants permission to batch add room members | Write |  |  |  | 
|   [ BatchDeletePhoneNumber ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchDeletePhoneNumber.html)  | Grants permission to move up to 50 phone numbers to the deletion queue | Write |  |  |  | 
|   [ BatchSuspendUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchSuspendUser.html)  | Grants permission to suspend up to 50 users from a Team or EnterpriseLWA Amazon Chime account | Write |  |  |  | 
|   [ BatchUnsuspendUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchUnsuspendUser.html)  | Grants permission to remove the suspension from up to 50 previously suspended users for the specified Amazon Chime EnterpriseLWA account | Write |  |  |  | 
|   [ BatchUpdatePhoneNumber ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchUpdatePhoneNumber.html)  | Grants permission to update phone number details within the UpdatePhoneNumberRequestItem object for up to 50 phone numbers | Write |  |  |  | 
|   [ BatchUpdateUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchUpdateUser.html)  | Grants permission to update user details within the UpdateUserRequestItem object for up to 20 users for the specified Amazon Chime account | Write |  |  |  | 
|   [ ConnectDirectory ](https://docs.aws.amazon.com/chime/latest/ag/active_directory.html)  | Grants permission to connect an Active Directory to your Amazon Chime Enterprise account | Write |  |  |   ds:ConnectDirectory   | 
|   [ CreateAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreateAccount.html)  | Grants permission to create an Amazon Chime account under the administrator's AWS account | Write |  |  |  | 
|   [ CreateApiKey ](https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to create a new SCIM access key for your Amazon Chime account and Okta configuration | Write |  |  |  | 
|   [ CreateAttendee ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreateAttendee.html)  | Grants permission to create a new attendee for an active Amazon Chime SDK meeting | Write |  |  |  | 
|   [ CreateBot ](API_CreateBot.html)  | Grants permission to create a bot for an Amazon Chime Enterprise account | Write |  |  |  | 
|   [ CreateBotMembership ](API_CreateBotMembership.html)  | Grants permission to add a bot to a chat room in your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ CreateCDRBucket ](https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to create a new Call Detail Record S3 bucket | Write |  |  |   s3:CreateBucket   s3:ListAllMyBuckets   | 
|   [ CreateMeeting ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreateMeeting.html)  | Grants permission to create a new Amazon Chime SDK meeting in the specified media Region, with no initial attendees | Write |  |  |  | 
|   [ CreatePhoneNumberOrder ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreatePhoneNumberOrder.html)  | Grants permission to create a phone number order with the Carriers | Write |  |  |  | 
|   [ CreateProxySession ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreateProxySession.html)  | Grants permission to create a proxy session for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ CreateRoom ](API_CreateRoom.html)  | Grants permission to create a room | Write |  |  |  | 
|   [ CreateRoomMembership ](API_CreateRoomMembership.html)  | Grants permission to add a room member | Write |  |  |  | 
|   [ CreateUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreateUser.html)  | Grants permission to create a user under the specified Amazon Chime account\. | Write |  |  |  | 
|   [ CreateVoiceConnector ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreateVoiceConnector.html)  | Grants permission to create a Amazon Chime Voice Connector under the administrator's AWS account | Write |  |  |  | 
|   [ CreateVoiceConnectorGroup ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreateVoiceConnectorGroup.html)  | Grants permission to create a Amazon Chime Voice Connector Group under the administrator's AWS account | Write |  |  |  | 
|   [ DeleteAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteAccount.html)  | Grants permission to delete the specified Amazon Chime account | Write |  |  |  | 
|   [ DeleteAccountOpenIdConfig ](https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to delete the OpenIdConfig attributes from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteApiKey ](https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to delete the specified SCIM access key associated with your Amazon Chime account and Okta configuration | Write |  |  |  | 
|   [ DeleteAttendee ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteAttendee.html)  | Grants permission to delete the specified attendee from an Amazon Chime SDK meeting | Write |  |  |  | 
|   [ DeleteCDRBucket ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to delete a Call Detail Record S3 bucket from your Amazon Chime account | Write |  |  |   s3:DeleteBucket   | 
|   [ DeleteDelegate ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to delete delegated AWS account management from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteDomain ](https://docs.aws.amazon.com/chime/latest/ag/claim-domain.html)  | Grants permission to delete a domain from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteEventsConfiguration ](API_DeleteEventsConfiguration.html)  | Grants permission to delete an events configuration for a bot to receive outgoing events | Write |  |  |  | 
|   [ DeleteGroups ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to delete Active Directory or Okta user groups from your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ DeleteMeeting ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteMeeting.html)  | Grants permission to delete the specified Amazon Chime SDK meeting | Write |  |  |  | 
|   [ DeletePhoneNumber ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeletePhoneNumber.html)  | Grants permission to move a phone number to the deletion queue | Write |  |  |  | 
|   [ DeleteProxySession ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteProxySession.html)  | Grants permission to delete a proxy session for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ DeleteRoom ](API_DeleteRoom.html)  | Grants permission to delete a room | Write |  |  |  | 
|   [ DeleteRoomMembership ](API_DeleteRoomMembership.html)  | Grants permission to remove a room member | Write |  |  |  | 
|   [ DeleteVoiceConnector ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteVoiceConnector.html)  | Grants permission to delete the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ DeleteVoiceConnectorGroup ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteVoiceConnectorGroup.html)  | Grants permission to delete the specified Amazon Chime Voice Connector Group | Write |  |  |  | 
|   [ DeleteVoiceConnectorOrigination ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteVoiceConnectorOrigination.html)  | Grants permission to delete the origination settings for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ DeleteVoiceConnectorProxy ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteVoiceConnectorProxy.html)  | Grants permission to delete proxy configuration for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ DeleteVoiceConnectorStreamingConfiguration ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteVoiceConnectorStreamingConfiguration.html)  | Grants permission to delete streaming configuration for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ DeleteVoiceConnectorTermination ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteVoiceConnectorTermination.html)  | Grants permission to delete the termination settings for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ DeleteVoiceConnectorTerminationCredentials ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteVoiceConnectorTerminationCredentials.html)  | Grants permission to delete SIP termination credentials for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ DisassociatePhoneNumberFromUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DisassociatePhoneNumberFromUser.html)  | Grants permission to disassociate the primary provisioned number from the specified Amazon Chime user | Write |  |  |  | 
|   [ DisassociatePhoneNumbersFromVoiceConnector ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DisassociatePhoneNumbersFromVoiceConnector.html)  | Grants permission to disassociate multiple phone numbers from the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ DisassociatePhoneNumbersFromVoiceConnectorGroup ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DisassociatePhoneNumbersFromVoiceConnectorGroup.html)  | Grants permission to disassociate multiple phone numbers from the specified Amazon Chime Voice Connector Group | Write |  |  |  | 
|   [ DisassociateSigninDelegateGroupsFromAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DisassociateSigninDelegateGroupsFromAccount.html)  | Grants permission to disassociate the specified sign\-in delegate groups from the specified Amazon Chime account\. | Write |  |  |  | 
|   [ DisconnectDirectory ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to disconnect the Active Directory from your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ GetAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetAccount.html)  | Grants permission to get details for the specified Amazon Chime account | Read |  |  |  | 
|   [ GetAccountResource ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to get details for the account resource associated with your Amazon Chime account | Read |  |  |  | 
|   [ GetAccountSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetAccountSettings.html)  | Grants permission to get account settings for the specified Amazon Chime account ID | Read |  |  |  | 
|   [ GetAccountWithOpenIdConfig ](https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to get the account details and OpenIdConfig attributes for your Amazon Chime account | Read |  |  |  | 
|   [ GetAttendee ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetAttendee.html)  | Grants permission to get attendee details for a specified meeting ID and attendee ID | Read |  |  |  | 
|   [ GetBot ](API_GetBot.html)  | Grants permission to retrieve details for the specified bot | Read |  |  |  | 
|   [ GetCDRBucket ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to get details of a Call Detail Record S3 bucket associated with your Amazon Chime account | Read |  |  |   s3:GetBucketAcl   s3:GetBucketLocation   s3:GetBucketLogging   s3:GetBucketVersioning   s3:GetBucketWebsite   | 
|   [ GetDomain ](https://docs.aws.amazon.com/chime/latest/ag/claim-domain.html)  | Grants permission to get domain details for a domain associated with your Amazon Chime account | Read |  |  |  | 
|   [ GetEventsConfiguration ](API_GetEventsConfiguration.html)  | Grants permission to retrieve details for an events configuration for a bot to receive outgoing events | Read |  |  |  | 
|   [ GetGlobalSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetGlobalSettings.html)  | Grants permission to get global settings related to Amazon Chime for the AWS account | Read |  |  |  | 
|   [ GetMeeting ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetMeeting.html)  | Grants permission to get the meeting record for a specified meeting ID | Read |  |  |  | 
|   [ GetMeetingDetail ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to get attendee, connection, and other details for a meeting | Read |  |  |  | 
|   [ GetPhoneNumber ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetPhoneNumber.html)  | Grants permission to get details for the specified phone number | Read |  |  |  | 
|   [ GetPhoneNumberOrder ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetPhoneNumberOrder.html)  | Grants permission to get details for the specified phone number order | Read |  |  |  | 
|   [ GetPhoneNumberSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetPhoneNumberSettings.html)  | Grants permission to get phone number settings related to Amazon Chime for the AWS account | Read |  |  |  | 
|   [ GetProxySession ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetProxySession.html)  | Grants permission to get details of the specified proxy session for the specified Amazon Chime Voice Connector | Read |  |  |  | 
|   [ GetRoom ](API_GetRoom.html)  | Grants permission to retrieve a room | Read |  |  |  | 
|   [ GetTelephonyLimits ](https://docs.aws.amazon.com/chime/latest/ag/phone-numbers.html)  | Grants permission to get telephony limits for the AWS account | Read |  |  |  | 
|   [ GetUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetUser.html)  | Grants permission to get details for the specified user ID | Read |  |  |  | 
|   [ GetUserActivityReportData ](https://docs.aws.amazon.com/chime/latest/ag/user-details.html)  | Grants permission to get a summary of user activity on the user details page | Read |  |  |  | 
|   [ GetUserByEmail ](https://docs.aws.amazon.com/chime/latest/ag/user-details.html)  | Grants permission to get user details for an Amazon Chime user based on the email address in an Amazon Chime Enterprise or Team account | Read |  |  |  | 
|   [ GetUserSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetUserSettings.html)  | Grants permission to get user settings related to the specified Amazon Chime user | Read |  |  |  | 
|   [ GetVoiceConnector ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetVoiceConnector.html)  | Grants permission to get details for the specified Amazon Chime Voice Connector | Read |  |  |  | 
|   [ GetVoiceConnectorGroup ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetVoiceConnectorGroup.html)  | Grants permission to get details for the specified Amazon Chime Voice Connector Group | Read |  |  |  | 
|   [ GetVoiceConnectorLoggingConfiguration ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetVoiceConnectorLoggingConfiguration.html)  | Grants permission to get details of the logging configuration for the specified Amazon Chime Voice Connector | Read |  |  |  | 
|   [ GetVoiceConnectorOrigination ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetVoiceConnectorOrigination.html)  | Grants permission to get details of the origination settings for the specified Amazon Chime Voice Connector | Read |  |  |  | 
|   [ GetVoiceConnectorProxy ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetVoiceConnectorProxy.html)  | Grants permission to get details of the proxy configuration for the specified Amazon Chime Voice Connector | Read |  |  |  | 
|   [ GetVoiceConnectorStreamingConfiguration ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetVoiceConnectorStreamingConfiguration.html)  | Grants permission to get details of the streaming configuration for the specified Amazon Chime Voice Connector | Read |  |  |  | 
|   [ GetVoiceConnectorTermination ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetVoiceConnectorTermination.html)  | Grants permission to get details of the termination settings for the specified Amazon Chime Voice Connector | Read |  |  |  | 
|   [ GetVoiceConnectorTerminationHealth ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetVoiceConnectorTerminationHealth.html)  | Grants permission to get details of the termination health for the specified Amazon Chime Voice Connector | Read |  |  |  | 
|   [ InviteDelegate ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to send an invitation to accept a request for AWS account delegation for an Amazon Chime account | Write |  |  |  | 
|   [ InviteUsers ](https://docs.aws.amazon.com/chime/latest/APIReference/API_InviteUsers.html)  | Grants permission to invite as many as 50 users to the specified Amazon Chime account | Write |  |  |  | 
|   InviteUsersFromProvider  | Grants permission to invite users from a third party provider to your Amazon Chime account | Write |  |  |  | 
|   [ ListAccountUsageReportData ](https://docs.aws.amazon.com/chime/latest/ag/view-reports.html)  | Grants permission to list Amazon Chime account usage reporting data | List |  |  |  | 
|   [ ListAccounts ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListAccounts.html)  | Grants permission to list the Amazon Chime accounts under the administrator's AWS account | List |  |  |  | 
|   [ ListApiKeys ](https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to list the SCIM access keys defined for your Amazon Chime account and Okta configuration | List |  |  |  | 
|   [ ListAttendeeTags ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListAttendeeTags.html)  | Grants permission to list the tags applied to an Amazon Chime SDK attendee resource | Read |  |  |  | 
|   [ ListAttendees ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListAttendees.html)  | Grants permission to list up to 100 attendees for a specified Amazon Chime SDK meeting | Read |  |  |  | 
|   [ ListBots ](API_ListBots.html)  | Grants permission to list the bots associated with the administrator's Amazon Chime Enterprise account | List |  |  |  | 
|   [ ListCDRBucket ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to list Call Detail Record S3 buckets | List |  |  |   s3:ListAllMyBuckets   s3:ListBucket   | 
|   [ ListCallingRegions ](https://docs.aws.amazon.com/chime/latest/ag/phone-numbers.html)  | Grants permission to list the calling regions available for the administrator's AWS account | List |  |  |  | 
|   [ ListDelegates ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to list account delegate information associated with your Amazon Chime account | List |  |  |  | 
|   [ ListDirectories ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to list active Active Directories hosted in the Directory Service of your AWS account | List |  |  |  | 
|   [ ListDomains ](https://docs.aws.amazon.com/chime/latest/ag/claim-domain.html)  | Grants permission to list domains associated with your Amazon Chime account | List |  |  |  | 
|   [ ListGroups ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to list Active Directory or Okta user groups associated with your Amazon Chime Enterprise account | List |  |  |  | 
|   [ ListMeetingEvents ](https://docs.aws.amazon.com/chime/latest/ag/view-reports.html)  | Grants permission to list all events that occurred for a specified meeting | List |  |  |  | 
|   [ ListMeetingTags ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListMeetingTags.html)  | Grants permission to list the tags applied to an Amazon Chime SDK meeting resource\. | Read |  |  |  | 
|   [ ListMeetings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListMeetings.html)  | Grants permission to list up to 100 active Amazon Chime SDK meetings | Read |  |  |  | 
|   [ ListMeetingsReportData ](https://docs.aws.amazon.com/chime/latest/ag/view-reports.html)  | Grants permission to list meetings ended during the specified date range | List |  |  |  | 
|   [ ListPhoneNumberOrders ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListPhoneNumberOrders.html)  | Grants permission to list the phone number orders under the administrator's AWS account | List |  |  |  | 
|   [ ListPhoneNumbers ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListPhoneNumbers.html)  | Grants permission to list the phone numbers under the administrator's AWS account | List |  |  |  | 
|   [ ListProxySessions ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListProxySessions.html)  | Grants permission to list proxy sessions for the specified Amazon Chime Voice Connector | List |  |  |  | 
|   [ ListRoomMemberships ](API_ListRoomMemberships.html)  | Grants permission to list all room members | Read |  |  |  | 
|   [ ListRooms ](API_ListRooms.html)  | Grants permission to list rooms | Read |  |  |  | 
|   [ ListTagsForResource ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListTagsForResource.html)  | Grants permission to list the tags applied to an Amazon Chime SDK meeting resource\. | Read |  |  |  | 
|   [ ListUsers ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListUsers.html)  | Grants permission to list the users that belong to the specified Amazon Chime account | List |  |  |  | 
|   [ ListVoiceConnectorGroups ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListVoiceConnectorGroups.html)  | Grants permission to list the Amazon Chime Voice Connector Groups under the administrator's AWS account | List |  |  |  | 
|   [ ListVoiceConnectorTerminationCredentials ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListVoiceConnectorTerminationCredentials.html)  | Grants permission to list the SIP termination credentials for the specified Amazon Chime Voice Connector | List |  |  |  | 
|   [ ListVoiceConnectors ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListVoiceConnectors.html)  | Grants permission to list the Amazon Chime Voice Connectors under the administrator's AWS account | List |  |  |  | 
|   [ LogoutUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_LogoutUser.html)  | Grants permission to log out the specified user from all of the devices they are currently logged into | Write |  |  |  | 
|   [ PutEventsConfiguration ](API_PutEventsConfiguration.html)  | Grants permission to update details for an events configuration for a bot to receive outgoing events | Write |  |  |  | 
|   [ PutVoiceConnectorLoggingConfiguration ](https://docs.aws.amazon.com/chime/latest/APIReference/API_PutVoiceConnectorLoggingConfiguration.html)  | Grants permission to add logging configuration for the specified Amazon Chime Voice Connector | Write |  |  |   logs:CreateLogDelivery   logs:CreateLogGroup   logs:DeleteLogDelivery   logs:DescribeLogGroups   logs:GetLogDelivery   logs:ListLogDeliveries   | 
|   [ PutVoiceConnectorOrigination ](https://docs.aws.amazon.com/chime/latest/APIReference/API_PutVoiceConnectorOrigination.html)  | Grants permission to update the origination settings for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ PutVoiceConnectorProxy ](https://docs.aws.amazon.com/chime/latest/APIReference/API_PutVoiceConnectorProxy.html)  | Grants permission to add proxy configuration for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ PutVoiceConnectorStreamingConfiguration ](https://docs.aws.amazon.com/chime/latest/APIReference/API_PutVoiceConnectorStreamingConfiguration.html)  | Grants permission to add streaming configuration for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ PutVoiceConnectorTermination ](https://docs.aws.amazon.com/chime/latest/APIReference/API_PutVoiceConnectorTermination.html)  | Grants permission to update the termination settings for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ PutVoiceConnectorTerminationCredentials ](https://docs.aws.amazon.com/chime/latest/APIReference/API_PutVoiceConnectorTerminationCredentials.html)  | Grants permission to add SIP termination credentials for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ RegenerateSecurityToken ](API_RegenerateSecurityToken.html)  | Grants permission to regenerate the security token for the specified bot | Write |  |  |  | 
|   [ RenameAccount ](https://docs.aws.amazon.com/chime/latest/ag/rename-account.html)  | Grants permission to modify the account name for your Amazon Chime Enterprise or Team account | Write |  |  |  | 
|   [ RenewDelegate ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to renew the delegation request associated with an Amazon Chime account | Write |  |  |  | 
|   [ ResetAccountResource ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to reset the account resource in your Amazon Chime account | Write |  |  |  | 
|   [ ResetPersonalPIN ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ResetPersonalPIN.html)  | Grants permission to reset the personal meeting PIN for the specified user on an Amazon Chime account | Write |  |  |  | 
|   [ RestorePhoneNumber ](https://docs.aws.amazon.com/chime/latest/APIReference/API_RestorePhoneNumber.html)  | Grants permission to restore the specified phone number from the deltion queue back to the phone number inventory | Write |  |  |  | 
|   [ RetrieveDataExports ](https://docs.aws.amazon.com/chime/latest/ag/request-attachments.html)  | Grants permission to download the file containing links to all user attachments returned as part of the "Request attachments" action | List |  |  |  | 
|   [ SearchAvailablePhoneNumbers ](https://docs.aws.amazon.com/chime/latest/APIReference/API_SearchAvailablePhoneNumbers.html)  | Grants permission to search phone numbers that can be ordered from the carrier | Read |  |  |  | 
|   [ StartDataExport ](https://docs.aws.amazon.com/chime/latest/ag/request-attachments.html)  | Grants permission to submit the "Request attachments" request | Write |  |  |  | 
|   [ SubmitSupportRequest ](https://docs.aws.amazon.com/chime/latest/ag/chime-getting-admin-support.html)  | Grants permission to submit a customer service support request | Write |  |  |  | 
|   [ SuspendUsers ](https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to suspend users from an Amazon Chime Enterprise account | Write |  |  |  | 
|   [ TagAttendee ](https://docs.aws.amazon.com/chime/latest/APIReference/API_TagAttendee.html)  | Grants permission to apply the specified tags to the specified Amazon Chime SDK attendee | Tagging |  |  |  | 
|   [ TagMeeting ](https://docs.aws.amazon.com/chime/latest/APIReference/API_TagMeeting.html)  | Grants permission to apply the specified tags to the specified Amazon Chime SDK meeting\. | Tagging |  |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/chime/latest/APIReference/API_TagResource.html)  | Grants permission to apply the specified tags to the specified Amazon Chime SDK meeting resource\. | Tagging |  |  |  | 
|   [ UnauthorizeDirectory ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to unauthorize an Active Directory from your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ UntagAttendee ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UntagAttendee.html)  | Grants permission to untag the specified tags from the specified Amazon Chime SDK attendee\. | Tagging |  |  |  | 
|   [ UntagMeeting ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UntagMeeting.html)  | Grants permission to untag the specified tags from the specified Amazon Chime SDK meeting\. | Tagging |  |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UntagResource.html)  | Grants permission to untag the specified tags from the specified Amazon Chime SDK meeting resource\. | Tagging |  |  |  | 
|   [ UpdateAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateAccount.html)  | Grants permission to update account details for the specified Amazon Chime account | Write |  |  |  | 
|   [ UpdateAccountOpenIdConfig ](https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to update the OpenIdConfig attributes for your Amazon Chime account | Write |  |  |  | 
|   [ UpdateAccountResource ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to update the account resource in your Amazon Chime account | Write |  |  |  | 
|   [ UpdateAccountSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateAccountSettings.html)  | Grants permission to update the settings for the specified Amazon Chime account | Write |  |  |  | 
|   [ UpdateBot ](API_UpdateBot.html)  | Grants permission to update the status of the specified bot | Write |  |  |  | 
|   [ UpdateCDRSettings ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to update your Call Detail Record S3 bucket | Write |  |  |   s3:CreateBucket   s3:DeleteBucket   s3:ListAllMyBuckets   | 
|   [ UpdateGlobalSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateGlobalSettings.html)  | Grants permission to update the global settings related to Amazon Chime for the AWS account | Write |  |  |  | 
|   [ UpdatePhoneNumber ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdatePhoneNumber.html)  | Grants permission to update phone number details for the specified phone number | Write |  |  |  | 
|   [ UpdatePhoneNumberSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdatePhoneNumberSettings.html)  | Grants permission to update phone number settings related to Amazon Chime for the AWS account | Write |  |  |  | 
|   [ UpdateProxySession ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateProxySession.html)  | Grants permission to update a proxy session for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ UpdateRoom ](API_UpdateRoom.html)  | Grants permission to update a room | Write |  |  |  | 
|   [ UpdateRoomMembership ](API_UpdateRoomMembership.html)  | Grants permission to update room membership role | Write |  |  |  | 
|   [ UpdateSupportedLicenses ](https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to update the supported license tiers available for users in your Amazon Chime account | Write |  |  |  | 
|   [ UpdateUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateUser.html)  | Grants permission to update user details for a specified user ID | Write |  |  |  | 
|   [ UpdateUserLicenses ](https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to update the licenses for your Amazon Chime users | Write |  |  |  | 
|   [ UpdateUserSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateUserSettings.html)  | Grants permission to update user settings related to the specified Amazon Chime user | Write |  |  |  | 
|   [ UpdateVoiceConnector ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateVoiceConnector.html)  | Grants permission to update Amazon Chime Voice Connector details for the specified Amazon Chime Voice Connector | Write |  |  |  | 
|   [ UpdateVoiceConnectorGroup ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateVoiceConnectorGroup.html)  | Grants permission to update Amazon Chime Voice Connector Group details for the specified Amazon Chime Voice Connector Group | Write |  |  |  | 
|   [ ValidateAccountResource ](https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to validate the account resource in your Amazon Chime account | Read |  |  |  | 

## Resource Types Defined by Amazon Chime<a name="amazonchime-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonchime-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   meeting  |  arn:$\{Partition\}:chime::$\{AccountId\}:meeting/$\{MeetingId\}  |  | 

## Condition Keys for Amazon Chime<a name="amazonchime-policy-keys"></a>

Chime has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.