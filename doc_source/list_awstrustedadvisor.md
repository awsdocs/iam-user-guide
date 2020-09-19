# Actions, resources, and condition keys for AWS Trusted Advisor<a name="list_awstrustedadvisor"></a>

AWS Trusted Advisor \(service prefix: `trustedadvisor`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/awssupport/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/awssupport/latest/user/security.html) permission policies\.

**Topics**
+ [Actions defined by AWS Trusted Advisor](#awstrustedadvisor-actions-as-permissions)
+ [Resource types defined by AWS Trusted Advisor](#awstrustedadvisor-resources-for-iam-policies)
+ [Condition keys for AWS Trusted Advisor](#awstrustedadvisor-policy-keys)

## Actions defined by AWS Trusted Advisor<a name="awstrustedadvisor-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.

**Note**  
Note: The IAM Trusted Advisor policy description details apply only to the Trusted Advisor console\. If you want to manage programmatic access to Trusted Advisor, use the Trusted Advisor operations in the AWS Support API\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DescribeAccount ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to view the AWS Support plan and various AWS Trusted Advisor preferences | Read |  |  |  | 
|   [ DescribeAccountAccess ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to view if the AWS account has enabled or disabled AWS Trusted Advisor | Read |  |  |  | 
|   [ DescribeCheckItems ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations)  | Grants permission to view details for the check items | Read |   [ checks\* ](#awstrustedadvisor-checks)   |  |  | 
|   [ DescribeCheckRefreshStatuses ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations)  | Grants permission to view the refresh statuses for AWS Trusted Advisor checks | Read |   [ checks\* ](#awstrustedadvisor-checks)   |  |  | 
|   [ DescribeCheckSummaries ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations)  | Grants permission to view AWS Trusted Advisor check summaries | Read |   [ checks\* ](#awstrustedadvisor-checks)   |  |  | 
|   [ DescribeChecks ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations)  | Grants permission to view details for AWS Trusted Advisor checks | Read |  |  |  | 
|   [ DescribeNotificationPreferences ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to view the notification preferences for the AWS account | Read |  |  |  | 
|   [ DescribeOrganization ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to view if the AWS account meets the requirements to enable the organizational view feature | Read |  |  |  | 
|   [ DescribeOrganizationAccounts ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to view the linked AWS accounts that are in the organization | Read |  |  |  | 
|   [ DescribeReports ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to view details for organizational view reports, such as the report name, runtime, date created, status, and format | Read |  |  |  | 
|   [ DescribeServiceMetadata ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to view information about organizational view reports, such as the AWS Regions, check categories, check names, and resource statuses | Read |  |  |  | 
|   [ ExcludeCheckItems ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to exclude recommendations for AWS Trusted Advisor checks | Write |   [ checks\* ](#awstrustedadvisor-checks)   |  |  | 
|   [ GenerateReport ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to create a report for AWS Trusted Advisor checks in your organization | Write |  |  |  | 
|   [ IncludeCheckItems ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to include recommendations for AWS Trusted Advisor checks | Write |   [ checks\* ](#awstrustedadvisor-checks)   |  |  | 
|   [ RefreshCheck ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations)  | Grants permission to refresh an AWS Trusted Advisor check | Write |   [ checks\* ](#awstrustedadvisor-checks)   |  |  | 
|   [ SetAccountAccess ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to enable or disable AWS Trusted Advisor for the account | Write |  |  |  | 
|   [ SetOrganizationAccess ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to enable the organizational view feature for AWS Trusted Advisor | Write |  |  |  | 
|   [ UpdateNotificationPreferences ](https://docs.aws.amazon.com/awssupport/latest/user/security-trusted-advisor.html#trusted-advisor-operations) \[permission only\] | Grants permission to update notification preferences for AWS Trusted Advisor | Write |  |  |  | 

## Resource types defined by AWS Trusted Advisor<a name="awstrustedadvisor-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awstrustedadvisor-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ checks ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_TrustedAdvisorCheckDescription.html)  |  arn:$\{Partition\}:trustedadvisor:$\{Region\}:$\{Account\}:checks/$\{CategoryCode\}/$\{CheckId\}  |  | 

## Condition keys for AWS Trusted Advisor<a name="awstrustedadvisor-policy-keys"></a>

Trusted Advisor has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.