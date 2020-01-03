# Actions, Resources, and Condition Keys for Amazon WorkLink<a name="list_amazonworklink"></a>

Amazon WorkLink \(service prefix: `worklink`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/worklink/latest/ag/what-is.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/worklink/latest/api/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/worklink/latest/ag/configure-network.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon WorkLink](#amazonworklink-actions-as-permissions)
+ [Resource Types Defined by Amazon WorkLink](#amazonworklink-resources-for-iam-policies)
+ [Condition Keys for Amazon WorkLink](#amazonworklink-policy-keys)

## Actions Defined by Amazon WorkLink<a name="amazonworklink-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateDomain ](https://docs.aws.amazon.com/worklink/latest/api/API_AssociateDomain.html)  | Grants permission to associate a domain with an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ AssociateWebsiteAuthorizationProvider ](https://docs.aws.amazon.com/worklink/latest/api/API_AssociateWebsiteAuthorizationProvider.html)  | Grants permission to associate a website authorization provider with an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ AssociateWebsiteCertificateAuthority ](https://docs.aws.amazon.com/worklink/latest/api/API_AssociateWebsiteCertificateAuthority.html)  | Grants permission to associate a website certificate authority with an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ CreateFleet ](https://docs.aws.amazon.com/worklink/latest/api/API_CreateFleet.html)  | Grants permission to create an Amazon WorkLink fleet | Write |  |  |  | 
|   [ DeleteFleet ](https://docs.aws.amazon.com/worklink/latest/api/API_DeleteFleet.html)  | Grants permission to delete an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeAuditStreamConfiguration ](https://docs.aws.amazon.com/worklink/latest/api/API_DescribeAuditStreamConfiguration.html)  | Grants permission to describe the audit stream configuration for an Amazon WorkLink fleet | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeCompanyNetworkConfiguration ](https://docs.aws.amazon.com/worklink/latest/api/API_DescribeCompanyNetworkConfiguration.html)  | Grants permission to describe the company network configuration for an Amazon WorkLink fleet | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeDevice ](https://docs.aws.amazon.com/worklink/latest/api/API_DescribeDevice.html)  | Grants permission to describe details of a device associated with an Amazon WorkLink fleet | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeDevicePolicyConfiguration ](https://docs.aws.amazon.com/worklink/latest/api/API_DescribeDevicePolicyConfiguration.html)  | Grants permission to describe the device policy configuration for an Amazon WorkLink fleet | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeDomain ](https://docs.aws.amazon.com/worklink/latest/api/API_DescribeDomain.html)  | Grants permission to describe details about a domain associated with an Amazon WorkLink fleet | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeFleetMetadata ](https://docs.aws.amazon.com/worklink/latest/api/API_DescribeFleetMetadata.html)  | Grants permission to describe metadata of an Amazon WorkLink fleet | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeIdentityProviderConfiguration ](https://docs.aws.amazon.com/worklink/latest/api/API_DescribeIdentityProviderConfiguration.html)  | Grants permission to describe the identity provider configuration for an Amazon WorkLink fleet | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeWebsiteCertificateAuthority ](https://docs.aws.amazon.com/worklink/latest/api/API_DescribeWebsiteCertificateAuthority.html)  | Grants permission to describe a website certificate authority associated with an Amazon WorkLink fleet | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DisassociateDomain ](https://docs.aws.amazon.com/worklink/latest/api/API_DisassociateDomain.html)  | Grants permission to disassociate a domain from an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DisassociateWebsiteAuthorizationProvider ](https://docs.aws.amazon.com/worklink/latest/api/API_DisassociateWebsiteAuthorizationProvider.html)  | Grants permission to disassociate a website authorization provider from an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DisassociateWebsiteCertificateAuthority ](https://docs.aws.amazon.com/worklink/latest/api/API_DisassociateWebsiteCertificateAuthority.html)  | Grants permission to disassociate a website certificate authority from an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ ListDevices ](https://docs.aws.amazon.com/worklink/latest/api/API_ListDevices.html)  | Grants permission to list the devices associated with an Amazon WorkLink fleet | List |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ ListDomains ](https://docs.aws.amazon.com/worklink/latest/api/API_ListDomains.html)  | Grants permission to list the associated domains for an Amazon WorkLink fleet | List |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ ListFleets ](https://docs.aws.amazon.com/worklink/latest/api/API_ListFleets.html)  | Grants permission to list the Amazon WorkLink fleets associated with the account | List |  |  |  | 
|   [ ListWebsiteAuthorizationProviders ](https://docs.aws.amazon.com/worklink/latest/api/API_ListWebsiteAuthorizationProviders.html)  | Grants permission to list the website authorization providers for an Amazon WorkLink fleet | List |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ ListWebsiteCertificateAuthorities ](https://docs.aws.amazon.com/worklink/latest/api/API_ListWebsiteCertificateAuthorities.html)  | Grants permission to list the website certificate authorities associated with an Amazon WorkLink fleet | List |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ RestoreDomainAccess ](https://docs.aws.amazon.com/worklink/latest/api/API_RestoreDomainAccess.html)  | Grants permission to restore access to a domain associated with an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ RevokeDomainAccess ](https://docs.aws.amazon.com/worklink/latest/api/API_RevokeDomainAccess.html)  | Grants permission to revoke access to a domain associated with an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ SignOutUser ](https://docs.aws.amazon.com/worklink/latest/api/API_SignOutUser.html)  | Grants permission to sign out a user from an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateAuditStreamConfiguration ](https://docs.aws.amazon.com/worklink/latest/api/API_UpdateAuditStreamConfiguration.html)  | Grants permission to update the audit stream configuration for an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateCompanyNetworkConfiguration ](https://docs.aws.amazon.com/worklink/latest/api/API_UpdateCompanyNetworkConfiguration.html)  | Grants permission to update the company network configuration for an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateDevicePolicyConfiguration ](https://docs.aws.amazon.com/worklink/latest/api/API_UpdateDevicePolicyConfiguration.html)  | Grants permission to update the device policy configuration for an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateDomainMetadata ](https://docs.aws.amazon.com/worklink/latest/api/API_UpdateDomainMetadata.html)  | Grants permission to update the metadata for a domain associated with an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateFleetMetadata ](https://docs.aws.amazon.com/worklink/latest/api/API_UpdateFleetMetadata.html)  | Grants permission to update the metadata of an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateIdentityProviderConfiguration ](https://docs.aws.amazon.com/worklink/latest/api/API_UpdateIdentityProviderConfiguration.html)  | Grants permission to update the identity provider configuration for an Amazon WorkLink fleet | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 

## Resource Types Defined by Amazon WorkLink<a name="amazonworklink-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonworklink-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ fleet ](https://docs.aws.amazon.com/worklink/latest/api/worklink-resources.html#Fleet)  |  arn:$\{Partition\}:worklink::$\{Account\}:fleet/$\{fleetName\}  |  | 

## Condition Keys for Amazon WorkLink<a name="amazonworklink-policy-keys"></a>

WorkLink has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.