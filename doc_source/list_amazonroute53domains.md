# Actions, Resources, and Condition Keys for Amazon Route53 Domains<a name="list_amazonroute53domains"></a>

Amazon Route53 Domains \(service prefix: `route53domains`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/Route53/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/DeveloperGuide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Route53 Domains](#amazonroute53domains-actions-as-permissions)
+ [Resources Defined by Route53 Domains](#amazonroute53domains-resources-for-iam-policies)
+ [Condition Keys for Amazon Route53 Domains](#amazonroute53domains-policy-keys)

## Actions Defined by Amazon Route53 Domains<a name="amazonroute53domains-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_CheckDomainAvailability.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_CheckDomainAvailability.html) | Checks the availability of one domain name | Read |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DeleteTagsForDomain.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DeleteTagsForDomain.html) | Deletes the specified tags for a domain | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainAutoRenew.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainAutoRenew.html) | Configures Amazon Route 53 to automatically renew the specified domain before the domain registration expires\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainTransferLock.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainTransferLock.html) | Removes the transfer lock on the domain \(specifically the clientTransferProhibited status\) to allow domain transfers\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainAutoRenew.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainAutoRenew.html) | Configures Amazon Route 53 to automatically renew the specified domain before the domain registration expires\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_EnableDomainTransferLock.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_EnableDomainTransferLock.html) | Sets the transfer lock on the domain \(specifically the clientTransferProhibited status\) to prevent domain transfers\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetContactReachabilityStatus.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetContactReachabilityStatus.html) | For operations that require confirmation that the email address for the registrant contact is valid, such as registering a new domain, returns information about whether the registrant contact has responded\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetDomainDetail.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetDomainDetail.html) | returns detailed information about the domain\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetDomainSuggestions.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetDomainSuggestions.html) | Returns a list of suggested domain names given a string, which can either be a domain name or simply a word or phrase \(without spaces\)\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetOperationDetail.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetOperationDetail.html) | Returns the current status of an operation that is not completed\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListDomains.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListDomains.html) | Returns all the domain names registered with Amazon Route 53 for the current AWS account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListOperations.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListOperations.html) | Returns the operation IDs of operations that are not yet complete\. | List |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListTagsForDomain.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListTagsForDomain.html) | Returns all of the tags that are associated with the specified domain\. | List |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RegisterDomain.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RegisterDomain.html) | Registers a domain\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RenewDomain.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RenewDomain.html) | Renews a domain for the specified number of years\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ResendContactReachabilityEmail.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ResendContactReachabilityEmail.html) | For operations that require confirmation that the email address for the registrant contact is valid, such as registering a new domain, resends the confirmation email to the current email address for the registrant contact\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RetrieveDomainAuthCode.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RetrieveDomainAuthCode.html) | Returns the AuthCode for the domain\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_TransferDomain.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_TransferDomain.html) | Transfers a domain from another registrar to Amazon Route 53\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainContact.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainContact.html) | Updates the contact information for a particular domain\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainContactPrivacy.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainContactPrivacy.html) | Updates the specified domain contact's privacy setting\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainNameservers.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainNameservers.html) | Replaces the current set of name servers for the domain with the specified set of name servers\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateTagsForDomain.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateTagsForDomain.html) | Adds or updates tags for a specified domain\. | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ViewBilling.html](http://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ViewBilling.html) | Returns all the domain\-related billing records for the current AWS account for a specified period\. | Read |  |  |  | 

## Resources Defined by Route53 Domains<a name="amazonroute53domains-resources-for-iam-policies"></a>

Route53 Domains has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Route53 Domains<a name="amazonroute53domains-policy-keys"></a>

Route53 Domains has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.