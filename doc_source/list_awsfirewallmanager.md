# Actions, Resources, and Condition Keys for AWS Firewall Manager<a name="list_awsfirewallmanager"></a>

AWS Firewall Manager \(service prefix: `fms`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by AWS Firewall Manager](#awsfirewallmanager-actions-as-permissions)
+ [Resources Defined by Firewall Manager](#awsfirewallmanager-resources-for-iam-policies)
+ [Condition Keys for AWS Firewall Manager](#awsfirewallmanager-policy-keys)

## Actions Defined by AWS Firewall Manager<a name="awsfirewallmanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| AssociateAdminAccount | Sets the AWS Firewall Manager administrator account and enables the service in all organization accounts | Write |  |  |  | 
| DeleteNotificationChannel | Deletes an AWS Firewall Manager association with the IAM role and the Amazon Simple Notification Service \(SNS\) topic that is used to notify the FM administrator about major FM events and errors across the organization\. | Write |  |  |  | 
| DeletePolicy | Permanently deletes an AWS Firewall Manager policy\. | Write | [policy\*](#awsfirewallmanager-policy)  |  |  | 
| DisassociateAdminAccount | Disassociates the account that has been set as the AWS Firewall Manager administrator account and and disables the service in all organization accounts | Write |  |  |  | 
| GetAdminAccount | Returns the AWS Organizations master account that is associated with AWS Firewall Manager as the AWS Firewall Manager administrator\. | Read |  |  |  | 
| GetComplianceDetail | Returns detailed compliance information about the specified member account\. Details include resources that are in and out of compliance with the specified policy\. | Write | [policy\*](#awsfirewallmanager-policy)  |  |  | 
| GetNotificationChannel | Returns information about the Amazon Simple Notification Service \(SNS\) topic that is used to record AWS Firewall Manager SNS logs\. | Read |  |  |  | 
| GetPolicy | Returns information about the specified AWS Firewall Manager policy\. | Read | [policy\*](#awsfirewallmanager-policy)  |  |  | 
| ListComplianceStatus | Returns an array of PolicyComplianceStatus objects in the response\. Use PolicyComplianceStatus to get a summary of which member accounts are protected by the specified policy\. | List | [policy\*](#awsfirewallmanager-policy)  |  |  | 
| ListPolicies | Returns an array of PolicySummary objects in the response\. | List |  |  |  | 
| PutNotificationChannel | Designates the IAM role and Amazon Simple Notification Service \(SNS\) topic that AWS Firewall Manager \(FM\) could use to notify the FM administrator about major FM events and errors across the organization\. | Write |  |  |  | 
| PutPolicy | Creates an AWS Firewall Manager policy\. | Write | [policy\*](#awsfirewallmanager-policy)  |  |  | 

## Resources Defined by Firewall Manager<a name="awsfirewallmanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsfirewallmanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| policy | arn:$\{Partition\}:fms:$\{Region\}:$\{Account\}:policy/$\{Id\} |  | 

## Condition Keys for AWS Firewall Manager<a name="awsfirewallmanager-policy-keys"></a>

Firewall Manager has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.