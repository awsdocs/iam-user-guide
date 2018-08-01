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
|   [ AcceptDelegate ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Accepts the delegate invitation to share management of an Amazon Chime account with another AWS Account | Write |  |  |  | 
|   [ ActivateUsers ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Activates users in an Amazon Chime enterprise account | Write |  |  |  | 
|   [ AddDomain ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Adds a domain to your Amazon Chime account | Write |  |  |  | 
|   [ AddOrUpdateGroups ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Adds new or updates existing Active Directory or Okta user groups associated with your Amazon Chime enterprise account | Write |  |  |  | 
|   [ AuthorizeDirectory ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Authorize an Active Directory to your Amazon Chime enterprise account | Write |  |  |  | 
|   [ ConnectDirectory ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Connects an Active Directory to your Amazon Chime enterprise account | Write |  |  |   ds:ConnectDirectory   | 
|   [ CreateAccount ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Creates a new Amazon Chime account | Write |  |  |  | 
|   [ CreateApiKey ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Generates a new SCIM access key for your Amazon Chime account and Okta configuration | Write |  |  |  | 
|   [ CreateCDRBucket ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Creates a new Call Detail Record S3 bucket | Write |  |  |   s3:CreateBucket   s3:ListAllMyBuckets   | 
|   [ DeleteAccount ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Deletes an Amazon Chime account | Write |  |  |  | 
|   [ DeleteAccountOpenIdConfig ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Deletes the OpenIdConfig attributes from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteApiKey ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Deletes the specified SCIM access key associated with your Amazon Chime account and Okta configuration | Write |  |  |  | 
|   [ DeleteCDRBucket ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Deletes a Call Detail Record S3 bucket from your Amazon Chime account | Write |  |  |   s3:DeleteBucket   | 
|   [ DeleteDelegate ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Deletes delegated AWS account management from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteDomain ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Deletes a domain from your Amazon Chime account | Write |  |  |  | 
|   [ DeleteGroups ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Deletes Active Directory or Okta user groups from your Amazon Chime enterprise account | Write |  |  |  | 
|   [ DisconnectDirectory ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Disconnects the Active Directory from your Amazon Chime enterprise account | Write |  |  |  | 
|   [ GetAccount ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Gets the account details for an Amazon Chime account | Read |  |  |  | 
|   [ GetAccountResource ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Shows the details of the account resource associated with your Amazon Chime account | Read |  |  |  | 
|   [ GetAccountSettings ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Shows your Amazon Chime account settings | Read |  |  |  | 
|   [ GetAccountWithOpenIdConfig ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Gets the account details and OpenIdConfig attributes for your Amazon Chime account | Read |  |  |  | 
|   [ GetCDRBucket ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Gets the details of a Call Detail Record S3 bucket associated with your Amazon Chime account | Read |  |  |   s3:GetBucketAcl   s3:GetBucketLocation   s3:GetBucketLogging   s3:GetBucketVersioning   s3:GetBucketWebsite   | 
|   [ GetDomain ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Shows domain details for a domain associated with your Amazon Chime account | Read |  |  |  | 
|   [ GetMeetingDetail ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Shows attendee, connection and other details for a meeting\. | Read |  |  |  | 
|   [ GetUser ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Gets the user details for an Amazon Chime user | Read |  |  |  | 
|   [ GetUserActivityReportData ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Shows summary of user activity on the user details page | Read |  |  |  | 
|   [ GetUserByEmail ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Gets user details for an Amazon Chime user based on the email address in an Amazon Chime enterprise or team account | Read |  |  |  | 
|   [ InviteDelegate ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Sends an invitation to accept a request for AWS account delegation for an Amazon Chime account | Write |  |  |  | 
|   [ InviteUsers ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Invites new users to an Amazon Chime account | Write |  |  |  | 
|   [ ListAccountUsageReportData ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists Amazon Chime account usage reporting data | List |  |  |  | 
|   [ ListAccounts ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists the Amazon Chime accounts associated with your AWS account | List |  |  |  | 
|   [ ListApiKeys ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists the SCIM access keys defined for your Amazon Chime account and Okta configuration | List |  |  |  | 
|   [ ListCDRBucket ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists Call Detail Record S3 buckets | List |  |  |   s3:ListAllMyBuckets   s3:ListBucket   | 
|   [ ListDelegates ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists account delegate information associated with your Amazon Chime account | List |  |  |  | 
|   [ ListDirectories ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists active Active Directories hosted in the Directory Service of your AWS account | List |  |  |  | 
|   [ ListDomains ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists domains associated with your Amazon Chime account | List |  |  |  | 
|   [ ListGroups ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists Active Directory or Okta user groups associated with your Amazon Chime enterprise account | List |  |  |  | 
|   [ ListMeetingEvents ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists all events that occurred for a meeting | List |  |  |  | 
|   [ ListMeetingsReportData ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists meetings ended during the date range | List |  |  |  | 
|   [ ListUsers ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Lists the users in an Amazon Chime account | List |  |  |  | 
|   [ LogoutUser ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Spike an Amazon Chime user device | Write |  |  |  | 
|   [ RenameAccount ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Modifies the account name for your Amazon Chime enterprise or team account | Write |  |  |  | 
|   [ RenewDelegate ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Renews the delegation request associated with an Amazon Chime account | Write |  |  |  | 
|   [ ResetAccountResource ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Resets the account resource in your Amazon Chime account | Write |  |  |  | 
|   [ ResetPersonalPin ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Resets the personal meeting PIN for an Amazon Chime user | Write |  |  |  | 
|   [ RetrieveDataExports ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Downloads the file containing links to all user attachments returned as part of the "Request attachments" action\. | List |  |  |  | 
|   [ StartDataExport ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  |  Submits the "Request attachments" request\. | Write |  |  |  | 
|   [ SubmitSupportRequest ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Submits a customer service support request | Write |  |  |  | 
|   [ SuspendUsers ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Suspend users from an Amazon Chime enterprise account | Write |  |  |  | 
|   [ UnauthorizeDirectory ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Unauthorize an Active Directory to your Amazon Chime enterprise account | Write |  |  |  | 
|   [ UpdateAccountOpenIdConfig ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Updates the OpenIdConfig attributes for your Amazon Chime account | Write |  |  |  | 
|   [ UpdateAccountResource ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Updates the account resource in your Amazon Chime account | Write |  |  |  | 
|   [ UpdateAccountSettings ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Modifies your Amazon Chime account settings | Write |  |  |  | 
|   [ UpdateCDRBucket ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Updates your Call Detail Record S3 bucket | Write |  |  |   s3:CreateBucket   s3:DeleteBucket   s3:ListAllMyBuckets   | 
|   [ UpdateSupportedLicenses ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Updates the supported license tiers available for users in your Amazon Chime account | Write |  |  |  | 
|   [ UpdateUserLicenses ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Manages the licenses for your Amazon Chime users | Write |  |  |  | 
|   [ ValidateAccountResource ](http://docs.aws.amazon.com/chime/latest/ag/working-users.html#available-actions)  | Validates the account resource in your Amazon Chime account | Read |  |  |  | 

## Resources Defined by Chime<a name="amazonchime-resources-for-iam-policies"></a>

Amazon Chime has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Chime<a name="amazonchime-policy-keys"></a>

Chime has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.