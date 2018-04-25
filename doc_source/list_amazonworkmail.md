# Actions, Resources, and Condition Keys for Amazon WorkMail<a name="list_amazonworkmail"></a>

Amazon WorkMail \(service prefix: `workmail`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by Amazon WorkMail](#amazonworkmail-actions-as-permissions)
+ [Resources Defined by WorkMail](#amazonworkmail-resources-for-iam-policies)
+ [Condition Keys for Amazon WorkMail](#amazonworkmail-policy-keys)

## Actions Defined by Amazon WorkMail<a name="amazonworkmail-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| AddMembersToGroup | Adds a list of members \(users or groups\) to a group\. |   |  |  |  | 
| CreateGroup | Creates a new group in the directory \(but doesn't enable it for mail\)\. |   |  |  |  | 
| CreateMailDomain | Creates a mail domain\. |   |  |  |  | 
| CreateMailUser | Creates a user in the directory and the WorkMail storage but does not enable the user for mail\. |   |  |  |  | 
| CreateOrganization | Creates an organization, either using an existing directory or creates a new directory on\-the\-fly\. Also creates and enables the complementary mail domain\. Optionally creates KMS key |   |  |  |  | 
| CreateResource | Creates a new resource |   |  |  |  | 
| DeleteMailDomain | Description for DeleteMailDomain |   |  |  |  | 
| DeleteMobileDevice | Description for DeleteMobileDevice |   |  |  |  | 
| DeleteOrganization | Description for DeleteOrganization |   |  |  |  | 
| DescribeDirectories | Description for DescribeDirectories |   |  |  |  | 
| DescribeKmsKeys | Description for DescribeKmsKeys |   |  |  |  | 
| DescribeMailDomains | Description for DescribeMailDomains |   |  |  |  | 
| DescribeMailGroups | Description for DescribeMailGroups |   |  |  |  | 
| DescribeMailUsers | Description for DescribeMailUsers |   |  |  |  | 
| DescribeOrganizations | Description for DescribeOrganizations |   |  |  |  | 
| DisableMailGroups | Description for DisableMailGroups |   |  |  |  | 
| DisableMailUsers | Description for DisableMailUsers |   |  |  |  | 
| EnableMailDomain | Description for EnableMailDomain |   |  |  |  | 
| EnableMailGroups | Description for EnableMailGroups |   |  |  |  | 
| EnableMailUsers | Description for EnableMailUsers |   |  |  |  | 
| GetMailDomainDetails | Description for GetMailDomainDetails |   |  |  |  | 
| GetMailGroupDetails | Description for GetMailGroupDetails |   |  |  |  | 
| GetMailUserDetails | Description for GetMailUserDetails |   |  |  |  | 
| GetMobileDeviceDetails | Description for GetMobileDeviceDetails |   |  |  |  | 
| GetMobileDevicesForUser | Description for GetMobileDevicesForUser |   |  |  |  | 
| GetMobilePolicyDetails | Description for GetMobilePolicyDetails |   |  |  |  | 
| ListMembersInMailGroup | Description for ListMembersInMailGroup |   |  |  |  | 
| RemoveMembersFromGroup | Description for RemoveMembersFromGroup |   |  |  |  | 
| ResetUserPassword | Description for ResetUserPassword |   |  |  |  | 
| SearchMembers | Description for SearchMembers |   |  |  |  | 
| SetAdmin | Description for SetAdmin |   |  |  |  | 
| SetDefaultMailDomain | Description for SetDefaultMailDomain |   |  |  |  | 
| SetMailGroupDetails | Description for SetMailGroupDetails |   |  |  |  | 
| SetMailUserDetails | Description for SetMailUserDetails |   |  |  |  | 
| SetMobilePolicyDetails | Description for SetMobilePolicyDetails |   |  |  |  | 
| WipeMobileDevice | Description for WipeMobileDevice |   |  |  |  | 

## Resources Defined by WorkMail<a name="amazonworkmail-resources-for-iam-policies"></a>

WorkMail has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon WorkMail<a name="amazonworkmail-policy-keys"></a>

WorkMail has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.