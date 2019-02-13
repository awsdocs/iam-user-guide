# Actions, Resources, and Condition Keys for Amazon Chime<a name="list_amazonchime"></a>

Amazon Chime \(service prefix: `chime`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/chime/latest/ag/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/chime/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/chime/latest/ag/control-access.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Chime](#amazonchime-actions-as-permissions)
+ [Resources Defined by Chime](#amazonchime-resources-for-iam-policies)
+ [Condition Keys for Amazon Chime](#amazonchime-policy-keys)

## Actions Defined by Amazon Chime<a name="amazonchime-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AcceptDelegate ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to accept the delegate invitation to share management of an Amazon Chime account with another AWS Account | Write |  |  |  | 
|   [ ActivateUsers ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to activate users in an Amazon Chime Enterprise account | Write |  |  |  | 
|   [ AddDomain ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/claim-domain.html)  | Grants permission to add a domain to your Amazon Chime account | Write |  |  |  | 
|   [ AddOrUpdateGroups ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/manage-chime-account.html)  | Grants permission to add new or update existing Active Directory or Okta user groups associated with your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ AuthorizeDirectory ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to authorize an Active Directory for your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ BatchSuspendUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchSuspendUser.html)  | Grants permission to suspend up to 50 users from a Team or EnterpriseLWA Amazon Chime account | Write |  |  |  | 
|   [ BatchUnsuspendUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchUnsuspendUser.html)  | Grants permission to remove the suspension from up to 50 previously suspended users for the specified Amazon Chime EnterpriseLWA account | Write |  |  |  | 
|   [ BatchUpdateUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_BatchUpdateUser.html)  | Grants permission to update user details within the UpdateUserRequestItem object for up to 20 users for the specified Amazon Chime account | Write |  |  |  | 
|   [ ConnectDirectory ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/active_directory.html)  | Grants permission to connect an Active Directory to your Amazon Chime Enterprise account | Write |  |  |   ds:ConnectDirectory   | 
|   [ CreateAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_CreateAccount.html)  | Grants permission to create an Amazon Chime account under the administrator's AWS account | Write |  |  |  | 
|   [ CreateApiKey ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to create a new SCIM access key for your Amazon Chime account and Okta configuration | Write |  |  |  | 
|   [ CreateCDRBucket ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to create a new Call Detail Record S3 bucket | Write |  |  |   s3:CreateBucket   s3:ListAllMyBuckets   | 
|   [ DeleteAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_DeleteAccount.html)  | Grants permission to delete the specified Amazon Chime account | Write |  |  |  | 
|   [ DeleteAccountOpenIdConfig ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to delete the OpenIdConfig attributes from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteApiKey ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to delete the specified SCIM access key associated with your Amazon Chime account and Okta configuration | Write |  |  |  | 
|   [ DeleteCDRBucket ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to delete a Call Detail Record S3 bucket from your Amazon Chime account | Write |  |  |   s3:DeleteBucket   | 
|   [ DeleteDelegate ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to delete delegated AWS account management from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteDomain ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/claim-domain.html)  | Grants permission to delete a domain from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteGroups ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to delete Active Directory or Okta user groups from your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ DisconnectDirectory ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to disconnect the Active Directory from your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ GetAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetAccount.html)  | Grants permission to get details for the specified Amazon Chime account | Read |  |  |  | 
|   [ GetAccountResource ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to get details for the account resource associated with your Amazon Chime account | Read |  |  |  | 
|   [ GetAccountSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetAccountSettings.html)  | Grants permission to get account settings for the specified Amazon Chime account ID | Read |  |  |  | 
|   [ GetAccountWithOpenIdConfig ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to get the account details and OpenIdConfig attributes for your Amazon Chime account | Read |  |  |  | 
|   [ GetCDRBucket ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to get details of a Call Detail Record S3 bucket associated with your Amazon Chime account | Read |  |  |   s3:GetBucketAcl   s3:GetBucketLocation   s3:GetBucketLogging   s3:GetBucketVersioning   s3:GetBucketWebsite   | 
|   [ GetDomain ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/claim-domain.html)  | Grants permission to get domain details for a domain associated with your Amazon Chime account | Read |  |  |  | 
|   [ GetMeetingDetail ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to get attendee, connection, and other details for a meeting | Read |  |  |  | 
|   [ GetUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_GetUser.html)  | Grants permission to get details for the specified user ID | Read |  |  |  | 
|   [ GetUserActivityReportData ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/user-details.html)  | Grants permission to get a summary of user activity on the user details page | Read |  |  |  | 
|   [ GetUserByEmail ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/user-details.html)  | Grants permission to get user details for an Amazon Chime user based on the email address in an Amazon Chime Enterprise or Team account | Read |  |  |  | 
|   [ InviteDelegate ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to send an invitation to accept a request for AWS account delegation for an Amazon Chime account | Write |  |  |  | 
|   [ InviteUsers ](https://docs.aws.amazon.com/chime/latest/APIReference/API_InviteUsers.html)  | Grants permission to invite as many as 50 users to the specified Amazon Chime account | Write |  |  |  | 
|   [ ListAccountUsageReportData ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/view-reports.html)  | Grants permission to list Amazon Chime account usage reporting data | List |  |  |  | 
|   [ ListAccounts ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListAccounts.html)  | Grants permission to list the Amazon Chime accounts under the administrator's AWS account | List |  |  |  | 
|   [ ListApiKeys ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to list the SCIM access keys defined for your Amazon Chime account and Okta configuration | List |  |  |  | 
|   [ ListCDRBucket ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to list Call Detail Record S3 buckets | List |  |  |   s3:ListAllMyBuckets   s3:ListBucket   | 
|   [ ListDelegates ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to list account delegate information associated with your Amazon Chime account | List |  |  |  | 
|   [ ListDirectories ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to list active Active Directories hosted in the Directory Service of your AWS account | List |  |  |  | 
|   [ ListDomains ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/claim-domain.html)  | Grants permission to list domains associated with your Amazon Chime account | List |  |  |  | 
|   [ ListGroups ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to list Active Directory or Okta user groups associated with your Amazon Chime Enterprise account | List |  |  |  | 
|   [ ListMeetingEvents ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/view-reports.html)  | Grants permission to list all events that occurred for a specified meeting | List |  |  |  | 
|   [ ListMeetingsReportData ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/view-reports.html)  | Grants permission to list meetings ended during the specified date range | List |  |  |  | 
|   [ ListUsers ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ListUsers.html)  | Grants permission to list the users that belong to the specified Amazon Chime account | List |  |  |  | 
|   [ LogoutUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_LogoutUser.html)  | Grants permission to log out the specified user from all of the devices they are currently logged into | Write |  |  |  | 
|   [ RenameAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/rename-account.html)  | Grants permission to modify the account name for your Amazon Chime Enterprise or Team account | Write |  |  |  | 
|   [ RenewDelegate ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to renew the delegation request associated with an Amazon Chime account | Write |  |  |  | 
|   [ ResetAccountResource ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to reset the account resource in your Amazon Chime account | Write |  |  |  | 
|   [ ResetPersonalPin ](https://docs.aws.amazon.com/chime/latest/APIReference/API_ResetPersonalPIN.html)  | Grants permission to reset the personal meeting PIN for the specified user on an Amazon Chime account | Write |  |  |  | 
|   [ RetrieveDataExports ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/request-attachments.html)  | Grants permission to download the file containing links to all user attachments returned as part of the "Request attachments" action | List |  |  |  | 
|   [ StartDataExport ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/request-attachments.html)  | Grants permission to submit the "Request attachments" request | Write |  |  |  | 
|   [ SubmitSupportRequest ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/chime-getting-admin-support.html)  | Grants permission to submit a customer service support request | Write |  |  |  | 
|   [ SuspendUsers ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to suspend users from an Amazon Chime Enterprise account | Write |  |  |  | 
|   [ UnauthorizeDirectory ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to unauthorize an Active Directory from your Amazon Chime Enterprise account | Write |  |  |  | 
|   [ UpdateAccount ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateAccount.html)  | Grants permission to update account details for the specified Amazon Chime account | Write |  |  |  | 
|   [ UpdateAccountOpenIdConfig ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/okta_sso.html)  | Grants permission to update the OpenIdConfig attributes for your Amazon Chime account | Write |  |  |  | 
|   [ UpdateAccountResource ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to update the account resource in your Amazon Chime account | Write |  |  |  | 
|   [ UpdateAccountSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateAccountSettings.html)  | Grants permission to update the settings for the specified Amazon Chime account | Write |  |  |  | 
|   [ UpdateCDRSettings ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to update your Call Detail Record S3 bucket | Write |  |  |   s3:CreateBucket   s3:DeleteBucket   s3:ListAllMyBuckets   | 
|   [ UpdateSupportedLicenses ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to update the supported license tiers available for users in your Amazon Chime account | Write |  |  |  | 
|   [ UpdateUser ](https://docs.aws.amazon.com/chime/latest/APIReference/API_UpdateUser.html)  | Grants permission to update user details for a specified user ID | Write |  |  |  | 
|   [ UpdateUserLicenses ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/manage-access.html)  | Grants permission to update the licenses for your Amazon Chime users | Write |  |  |  | 
|   [ ValidateAccountResource ](https://docs.aws.amazon.com/chime/latest/APIReference/https://docs.aws.amazon.com/chime/latest/ag/control-access.html)  | Grants permission to validate the account resource in your Amazon Chime account | Read |  |  |  | 

## Resources Defined by Chime<a name="amazonchime-resources-for-iam-policies"></a>

Amazon Chime has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Chime<a name="amazonchime-policy-keys"></a>

Chime has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.