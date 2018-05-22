# Actions, Resources, and Condition Keys for AWS Support<a name="list_awssupport"></a>

AWS Support \(service prefix: `support`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/awssupport/latest/user/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/awssupport/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/awssupport/latest/user/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Support](#awssupport-actions-as-permissions)
+ [Resources Defined by Support](#awssupport-resources-for-iam-policies)
+ [Condition Keys for AWS Support](#awssupport-policy-keys)

## Actions Defined by AWS Support<a name="awssupport-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.

AWS Support does not let you allow or deny access to individual actions; therefore your policy must use the `"Action": "support:*"` to use the AWS Support Center or to use the AWS Support API\. In addition, when you use the AWS Support API to call Trusted Advisor\-related actions \(such as `DescribeTrustedAdvisorChecks`\), none of the `trustedadvisor` actions restrict your access\. The `trustedadvisor` actions apply only to Trusted Advisor in the AWS Management Console\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddAttachmentsToSet.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddAttachmentsToSet.html) | Adds one or more attachments to an attachment set\. If an attachmentSetId is not specified, a new attachment set is created\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddCommunicationToCase.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddCommunicationToCase.html) | Adds additional customer communication to an AWS Support case\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html) | Creates a new case in the AWS Support Center\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeAttachment.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeAttachment.html) | Returns a description of an attachment\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeCases.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeCases.html) | Returns a list of cases that matches the given inputs | List |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeCommunications.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeCommunications.html) | Returns the communications \(and attachments\) for one or more support cases | Read |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeServices.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeServices.html) | Returns the current list of AWS services and a list of service categories that applies to each one\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeSeverityLevels.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeSeverityLevels.html) | Returns the list of severity levels that can be assigned to an AWS Support case\. | List |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckRefreshStatuses.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckRefreshStatuses.html) | Returns the refresh status of the Trusted Advisor checks that have the specified check identifiers\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckResult.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckResult.html) | Returns the results of the Trusted Advisor check that has the specified check identifier\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckSummaries.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckSummaries.html) | Returns the summaries of the results of the Trusted Advisor checks that have the specified check identifiers\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorChecks.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorChecks.html) | Returns information about all available Trusted Advisor checks, including name, ID, category, description, and metadata\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_RefreshTrustedAdvisorCheck.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_RefreshTrustedAdvisorCheck.html) | Requests a refresh of the Trusted Advisor check that has the specified check ID\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/awssupport/latest/APIReference/API_ResolveCase.html](http://docs.aws.amazon.com/awssupport/latest/APIReference/API_ResolveCase.html) | Resolves a case\. | Write |  |  |  | 

## Resources Defined by Support<a name="awssupport-resources-for-iam-policies"></a>

Support has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Support<a name="awssupport-policy-keys"></a>

Support has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.