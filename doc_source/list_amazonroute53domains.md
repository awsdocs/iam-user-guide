# Actions, resources, and condition keys for Amazon Route53 Domains<a name="list_amazonroute53domains"></a>

Amazon Route53 Domains \(service prefix: `route53domains`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/Route53/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Route53 Domains](#amazonroute53domains-actions-as-permissions)
+ [Resource types defined by Amazon Route53 Domains](#amazonroute53domains-resources-for-iam-policies)
+ [Condition keys for Amazon Route53 Domains](#amazonroute53domains-policy-keys)

## Actions defined by Amazon Route53 Domains<a name="amazonroute53domains-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CheckDomainAvailability ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_CheckDomainAvailability.html)  | Grants permission to check the availability of one domain name | Read |  |  |  | 
|   [ DeleteTagsForDomain ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DeleteTagsForDomain.html)  | Grants permission to delete the specified tags for a domain | Tagging |  |  |  | 
|   [ DisableDomainAutoRenew ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainAutoRenew.html)  | Grants permission to configure Amazon Route 53 to automatically renew the specified domain before the domain registration expires | Write |  |  |  | 
|   [ DisableDomainTransferLock ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainTransferLock.html)  | Grants permission to remove the transfer lock on the domain \(specifically the clientTransferProhibited status\) to allow domain transfers | Write |  |  |  | 
|   [ EnableDomainAutoRenew ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_DisableDomainAutoRenew.html)  | Grants permission to configure Amazon Route 53 to automatically renew the specified domain before the domain registration expires | Write |  |  |  | 
|   [ EnableDomainTransferLock ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_EnableDomainTransferLock.html)  | Grants permission to set the transfer lock on the domain \(specifically the clientTransferProhibited status\) to prevent domain transfers | Write |  |  |  | 
|   [ GetContactReachabilityStatus ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetContactReachabilityStatus.html)  | For operations that require confirmation that the email address for the registrant contact is valid, such as registering a new domain, grants permission to get information about whether the registrant contact has responded | Read |  |  |  | 
|   [ GetDomainDetail ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetDomainDetail.html)  | Grants permission to get detailed information about a domain | Read |  |  |  | 
|   [ GetDomainSuggestions ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetDomainSuggestions.html)  | Grants permission to get a list of suggested domain names given a string, which can either be a domain name or simply a word or phrase \(without spaces\) | Read |  |  |  | 
|   [ GetOperationDetail ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_GetOperationDetail.html)  | Grants permission to get the current status of an operation that is not completed | Read |  |  |  | 
|   [ ListDomains ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListDomains.html)  | Grants permission to list all the domain names registered with Amazon Route 53 for the current AWS account | List |  |  |  | 
|   [ ListOperations ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListOperations.html)  | Grants permission to list the operation IDs of operations that are not yet complete | List |  |  |  | 
|   [ ListTagsForDomain ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ListTagsForDomain.html)  | Grants permission to list all the tags that are associated with the specified domain | List |  |  |  | 
|   [ RegisterDomain ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RegisterDomain.html)  | Grants permission to register domains | Write |  |  |  | 
|   [ RenewDomain ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RenewDomain.html)  | Grants permission to renew domains for the specified number of years | Write |  |  |  | 
|   [ ResendContactReachabilityEmail ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ResendContactReachabilityEmail.html)  | For operations that require confirmation that the email address for the registrant contact is valid, such as registering a new domain, grants permission to resend the confirmation email to the current email address for the registrant contact | Write |  |  |  | 
|   [ RetrieveDomainAuthCode ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_RetrieveDomainAuthCode.html)  | Grants permission to get the AuthCode for the domain | Write |  |  |  | 
|   [ TransferDomain ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_TransferDomain.html)  | Grants permission to transfer a domain from another registrar to Amazon Route 53 | Write |  |  |  | 
|   [ UpdateDomainContact ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainContact.html)  | Grants permission to update the contact information for domain | Write |  |  |  | 
|   [ UpdateDomainContactPrivacy ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainContactPrivacy.html)  | Grants permission to update the domain contact privacy setting | Write |  |  |  | 
|   [ UpdateDomainNameservers ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateDomainNameservers.html)  | Grants permission to replace the current set of name servers for a domain with the specified set of name servers | Write |  |  |  | 
|   [ UpdateTagsForDomain ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_UpdateTagsForDomain.html)  | Grants permission to add or update tags for a specified domain | Tagging |  |  |  | 
|   [ ViewBilling ](https://docs.aws.amazon.com/Route53/latest/APIReference/API_domains_ViewBilling.html)  | Grants permission to get all the domain\-related billing records for the current AWS account for a specified period | Read |  |  |  | 

## Resource types defined by Amazon Route53 Domains<a name="amazonroute53domains-resources-for-iam-policies"></a>

Amazon Route53 Domains does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Route53 Domains, specify `“Resource”: “*”` in your policy\.

## Condition keys for Amazon Route53 Domains<a name="amazonroute53domains-policy-keys"></a>

Route53 Domains has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.