# Actions, Resources, and Condition Keys for Amazon Chime<a name="list_amazonchime"></a>

Amazon Chime \(service prefix: `chime`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/chime/latest/ag/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/chime/latest/ag/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/chime/latest/ag/working-users.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Chime](#amazonchime-actions-as-permissions)
+ [Resources Defined by Chime](#amazonchime-resources-for-iam-policies)
+ [Condition Keys for Amazon Chime](#amazonchime-policy-keys)

## Actions Defined by Amazon Chime<a name="amazonchime-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [AcceptDelegate](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Accepts the delegate invitation to share management of an Amazon Chime account with another AWS Account |   |  |  |  | 
| [ActivateUsers](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Activates users in an Amazon Chime enterprise account |   |  |  |  | 
| [AddDomain](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Adds a domain to your Amazon Chime account |   |  |  |  | 
| [AddOrUpdateGroups](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Adds new or updates existing Active Directory user groups associated with your Amazon Chime enterprise account |   |  |  |  | 
| [AuthorizeDirectory](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Authorize an Active Directory to your Amazon Chime enterprise account |   |  |  |  | 
| [ConnectDirectory](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Connects an Active Directory to your Amazon Chime enterprise account |   |  |  |  | 
| [CreateAccount](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Creates a new Amazon Chime account |   |  |  |  | 
| [CreateCDRBucket](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Creates a new Call Detail Record S3 bucket |   |  |  |  | 
| [DeleteAccount](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Deletes an Amazon Chime account |   |  |  |  | 
| [DeleteCDRBucket](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Deletes a Call Detail Record S3 bucket from your Amazon Chime account |   |  |  |  | 
| [DeleteDelegate](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Deletes delegated AWS account management from your Amazon Chime account |   |  |  |  | 
| [DeleteDomain](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Deletes a domain from your Amazon Chime account |   |  |  |  | 
| [DeleteGroups](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Deletes Active Directory user groups from your Amazon Chime enterprise account |   |  |  |  | 
| [DisconnectDirectory](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Disconnects the Active Directory from your Amazon Chime enterprise account |   |  |  |  | 
| [GetAccount](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Gets the account details for an Amazon Chime account |   |  |  |  | 
| [GetAccountResource](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Shows the details of the account resource associated with your Amazon Chime account |   |  |  |  | 
| [GetAccountSettings](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Shows your Amazon Chime account settings |   |  |  |  | 
| [GetCDRBucket](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Gets the details of a Call Detail Record S3 bucket associated with your Amazon Chime account |   |  |  |  | 
| [GetDomain](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Shows domain details for a domain associated with your Amazon Chime account |   |  |  |  | 
| [GetMeetingDetail](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Shows attendee, connection and other details for a meeting\. |   |  |  |  | 
| [GetUser](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Gets the user details for an Amazon Chime user |   |  |  |  | 
| [GetUserActivityReportData](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Shows summary of user activity on the user details page |   |  |  |  | 
| [GetUserByEmail](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Gets user details for an Amazon Chime user based on the email address in an Amazon Chime enterprise or team account |   |  |  |  | 
| [InviteDelegate](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Sends an invitation to accept a request for AWS account delegation for an Amazon Chime account |   |  |  |  | 
| [InviteUsers](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Invites new users to an Amazon Chime account |   |  |  |  | 
| [ListAccountUsageReportData](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists Amazon Chime account usage reporting data |   |  |  |  | 
| [ListAccounts](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists the Amazon Chime accounts associated with your AWS account |   |  |  |  | 
| [ListCDRBucket](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists Call Detail Record S3 buckets |   |  |  |  | 
| [ListDelegates](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists account delegate information associated with your Amazon Chime account |   |  |  |  | 
| [ListDirectories](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists active Active Directories hosted in the Directory Service of your AWS account |   |  |  |  | 
| [ListDomains](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists domains associated with your Amazon Chime account |   |  |  |  | 
| [ListGroups](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists Active Directory user groups associated with your Amazon Chime enterprise account |   |  |  |  | 
| [ListMeetingEvents](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists all events that occurred for a meeting |   |  |  |  | 
| [ListMeetingsReportData](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists meetings ended during the date range |   |  |  |  | 
| [ListUsers](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Lists the users in an Amazon Chime account |   |  |  |  | 
| [LogoutUser](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Spike an Amazon Chime user device |   |  |  |  | 
| [RenameAccount](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Modifies the account name for your Amazon Chime enterprise or team account |   |  |  |  | 
| [RenewDelegate](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Renews the delegation request associated with an Amazon Chime account |   |  |  |  | 
| [ResetAccountResource](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Resets the account resource in your Amazon Chime account |   |  |  |  | 
| [ResetPersonalPin](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Resets the personal meeting PIN for an Amazon Chime user |   |  |  |  | 
| [RetrieveDataExports](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Downloads the file containing links to all user attachments returned as part of the "Request attachments" action\. |   |  |  |  | 
| [StartDataExport](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) |  Submits the "Request attachments" request\. |   |  |  |  | 
| [SubmitSupportRequest](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Submits a customer service support request |   |  |  |  | 
| [SuspendUsers](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Suspend users from an Amazon Chime enterprise account |   |  |  |  | 
| [UnauthorizeDirectory](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Unauthorize an Active Directory to your Amazon Chime enterprise account |   |  |  |  | 
| [UpdateAccountResource](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Updates the account resource in your Amazon Chime account |   |  |  |  | 
| [UpdateAccountSettings](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Modifies your Amazon Chime account settings |   |  |  |  | 
| [UpdateCDRBucket](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Updates your Call Detail Record S3 bucket |   |  |  |  | 
| [UpdateSupportedLicenses](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Updates the supported license tiers available for users in your Amazon Chime account |   |  |  |  | 
| [UpdateUserLicenses](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Manages the licenses for your Amazon Chime users |   |  |  |  | 
| [ValidateAccountResource](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions) | Validates the account resource in your Amazon Chime account |   |  |  |  | 

## Resources Defined by Chime<a name="amazonchime-resources-for-iam-policies"></a>

Chime has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Chime<a name="amazonchime-policy-keys"></a>

Chime has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.