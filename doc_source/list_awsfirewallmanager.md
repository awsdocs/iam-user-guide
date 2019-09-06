# Actions, Resources, and Condition Keys for AWS Firewall Manager<a name="list_awsfirewallmanager"></a>

AWS Firewall Manager \(service prefix: `fms`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/)\.

**Topics**
+ [Actions Defined by AWS Firewall Manager](#awsfirewallmanager-actions-as-permissions)
+ [Resources Defined by AWS Firewall Manager](#awsfirewallmanager-resources-for-iam-policies)
+ [Condition Keys for AWS Firewall Manager](#awsfirewallmanager-policy-keys)

## Actions Defined by AWS Firewall Manager<a name="awsfirewallmanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateAdminAccount ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_AssociateAdminAccount.html)  | Sets the AWS Firewall Manager administrator account and enables the service in all organization accounts | Write |  |  |  | 
|   [ DeleteNotificationChannel ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_DeleteNotificationChannel.html)  | Deletes an AWS Firewall Manager association with the IAM role and the Amazon Simple Notification Service \(SNS\) topic that is used to notify the FM administrator about major FM events and errors across the organization\. | Write |  |  |  | 
|   [ DeletePolicy ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_DeletePolicy.html)  | Permanently deletes an AWS Firewall Manager policy\. | Write |   [ policy\* ](#awsfirewallmanager-policy)   |  |  | 
|   [ DisassociateAdminAccount ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_DisassociateAdminAccount.html)  | Disassociates the account that has been set as the AWS Firewall Manager administrator account and and disables the service in all organization accounts | Write |  |  |  | 
|   [ GetAdminAccount ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_GetAdminAccount.html)  | Returns the AWS Organizations master account that is associated with AWS Firewall Manager as the AWS Firewall Manager administrator\. | Read |  |  |  | 
|   [ GetComplianceDetail ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_GetComplianceDetail.html)  | Returns detailed compliance information about the specified member account\. Details include resources that are in and out of compliance with the specified policy\. | Read |   [ policy\* ](#awsfirewallmanager-policy)   |  |  | 
|   [ GetNotificationChannel ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_GetNotificationChannel.html)  | Returns information about the Amazon Simple Notification Service \(SNS\) topic that is used to record AWS Firewall Manager SNS logs\. | Read |  |  |  | 
|   [ GetPolicy ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_GetPolicy.html)  | Returns information about the specified AWS Firewall Manager policy\. | Read |   [ policy\* ](#awsfirewallmanager-policy)   |  |  | 
|   [ GetProtectionStatus ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_GetProtectionStatus.html)  | Returns policy\-level attack summary information in the event of a potential DDoS attack\. | Read |   [ policy\* ](#awsfirewallmanager-policy)   |  |  | 
|   [ ListComplianceStatus ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_ListComplianceStatus.html)  | Returns an array of PolicyComplianceStatus objects in the response\. Use PolicyComplianceStatus to get a summary of which member accounts are protected by the specified policy\. | List |   [ policy\* ](#awsfirewallmanager-policy)   |  |  | 
|   [ ListMemberAccounts ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_ListMemberAccounts.html)  | Returns an array of member account ids if the caller is FMS admin account\. | List |  |  |  | 
|   [ ListPolicies ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_ListPolicies.html)  | Returns an array of PolicySummary objects in the response\. | List |  |  |  | 
|   [ PutNotificationChannel ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_PutNotificationChannel.html)  | Designates the IAM role and Amazon Simple Notification Service \(SNS\) topic that AWS Firewall Manager \(FM\) could use to notify the FM administrator about major FM events and errors across the organization\. | Write |  |  |  | 
|   [ PutPolicy ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_PutPolicy.html)  | Creates an AWS Firewall Manager policy\. | Write |   [ policy\* ](#awsfirewallmanager-policy)   |  |  | 

## Resources Defined by AWS Firewall Manager<a name="awsfirewallmanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsfirewallmanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ policy ](https://docs.aws.amazon.com/fms/2018-01-01/APIReference/API_Policy.html)  |  arn:$\{Partition\}:fms:$\{Region\}:$\{Account\}:policy/$\{Id\}  |  | 

## Condition Keys for AWS Firewall Manager<a name="awsfirewallmanager-policy-keys"></a>

Firewall Manager has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.