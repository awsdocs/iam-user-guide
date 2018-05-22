# Actions, Resources, and Condition Keys for AWS Trusted Advisor<a name="list_awstrustedadvisor"></a>

AWS Trusted Advisor \(service prefix: `trustedadvisor`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/awssupport/latest/user/getting-started.html#trusted-advisor)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/trustedadvisor/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/awssupport/latest/user/getting-started.html#trusted-advisoraccess_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Trusted Advisor](#awstrustedadvisor-actions-as-permissions)
+ [Resources Defined by Trusted Advisor](#awstrustedadvisor-resources-for-iam-policies)
+ [Condition Keys for AWS Trusted Advisor](#awstrustedadvisor-policy-keys)

## Actions Defined by AWS Trusted Advisor<a name="awstrustedadvisor-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| DescribeCheckItems | View details for the check items | List | [checks\*](#awstrustedadvisor-checks)  |  |  | 
| DescribeCheckRefreshStatuses | Describe check refresh statuses | List | [checks\*](#awstrustedadvisor-checks)  |  |  | 
| DescribeCheckSummaries | Describes the check's summaries | List | [checks\*](#awstrustedadvisor-checks)  |  |  | 
| DescribeNotificationPreferences | Describes the notification preferences for the account | List |  |  |  | 
| ExcludeCheckItems | Exclude recommendations for checks for a given customer | Write | [checks\*](#awstrustedadvisor-checks)  |  |  | 
| IncludeCheckItems | Include recommendations for checks for a given customer | Write | [checks\*](#awstrustedadvisor-checks)  |  |  | 
| RefreshCheck | Enqueue a refresh for the specified check | Write | [checks\*](#awstrustedadvisor-checks)  |  |  | 
| UpdateNotificationPreferences | Update notification preferences  | Write |  |  |  | 

## Resources Defined by Trusted Advisor<a name="awstrustedadvisor-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awstrustedadvisor-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/trustedadvisor/latest/APIReference/API_TrustedAdvisorCheckDescription.html](http://docs.aws.amazon.com/trustedadvisor/latest/APIReference/API_TrustedAdvisorCheckDescription.html) | arn:$\{Partition\}:trustedadvisor:$\{Region\}:$\{Account\}:checks/$\{CategoryCode\}/$\{CheckId\} |  | 

## Condition Keys for AWS Trusted Advisor<a name="awstrustedadvisor-policy-keys"></a>

Trusted Advisor has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.