# Actions, resources, and condition keys for AWS Support<a name="list_awssupport"></a>

AWS Support \(service prefix: `support`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/awssupport/latest/user/getting-started.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/awssupport/latest/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/awssupport/latest/user/access_permissions.html) permission policies\.

**Topics**
+ [Actions defined by AWS Support](#awssupport-actions-as-permissions)
+ [Resource types defined by AWS Support](#awssupport-resources-for-iam-policies)
+ [Condition keys for AWS Support](#awssupport-policy-keys)

## Actions defined by AWS Support<a name="awssupport-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.

**Note**  
AWS Support provides the ability to access, modify and resolve cases, as well as use Trusted Advisor actions\. When you use Support API to call Trusted Advisor\-related actions, none of the "trustedadvisor:\*" actions restrict your access\. The "trustedadvisor:\*" actions apply only to Trusted Advisor in the AWS Console\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddAttachmentsToSet ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddAttachmentsToSet.html)  | Adds one or more attachments to an AWS Support case\. | Write |  |  |  | 
|   [ AddCommunicationToCase ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_AddCommunicationToCase.html)  | Adds a customer communication to an AWS Support case\. | Write |  |  |  | 
|   [ CreateCase ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_CreateCase.html)  | Creates a new AWS Support case\. | Write |  |  |  | 
|   [ DescribeAttachment ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeAttachment.html)  | Returns the description for an attachment\. | Read |  |  |  | 
|   DescribeCaseAttributes  | This is an internally managed function which allows secondary services to read AWS Support case attributes\. | Read |  |  |  | 
|   [ DescribeCases ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeCases.html)  | Returns a list of AWS Support cases that matches the given inputs\. | Read |  |  |  | 
|   [ DescribeCommunications ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeCommunications.html)  | Returns the communications and attachments for one or more AWS Support cases\. | Read |  |  |  | 
|   DescribeIssueTypes  | Returns issue types for AWS Support cases\. | Read |  |  |  | 
|   [ DescribeServices ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeServices.html)  | Returns the current list of AWS services and categories that applies to each service\. | Read |  |  |  | 
|   [ DescribeSeverityLevels ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeSeverityLevels.html)  | Returns the list of severity levels that can be assigned to an AWS Support case\. | Read |  |  |  | 
|   DescribeSupportLevel  | Returns the support level for an AWS Account identifier\. | Read |  |  |  | 
|   [ DescribeTrustedAdvisorCheckRefreshStatuses ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckRefreshStatuses.html)  | Returns the status of a Trusted Advisor refresh check based on a list of check identifiers\. | Read |  |  |  | 
|   [ DescribeTrustedAdvisorCheckResult ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckResult.html)  | Returns the results of the Trusted Advisor check that has the specified check identifier\. | Read |  |  |  | 
|   [ DescribeTrustedAdvisorCheckSummaries ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorCheckSummaries.html)  | Returns the summaries of the results of the Trusted Advisor checks that have the specified check identifiers\. | Read |  |  |  | 
|   [ DescribeTrustedAdvisorChecks ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_DescribeTrustedAdvisorChecks.html)  | Returns a list of all available Trusted Advisor checks, including name, identifier, category and description\. | Read |  |  |  | 
|   InitiateCallForCase  | This is an internally managed function to initiate a call on AWS Support Center\. | Write |  |  |  | 
|   InitiateChatForCase  | This is an internally managed function to initiate a chat on AWS Support Center\. | Write |  |  |  | 
|   PutCaseAttributes  | This is an internally managed function which allows secondary services to attach attributes to AWS Support cases\. | Write |  |  |  | 
|   RateCaseCommunication  | Rate an AWS Support case communication\. | Write |  |  |  | 
|   [ RefreshTrustedAdvisorCheck ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_RefreshTrustedAdvisorCheck.html)  | Requests a refresh of the Trusted Advisor check that has the specified check identifier\. | Write |  |  |  | 
|   [ ResolveCase ](https://docs.aws.amazon.com/awssupport/latest/APIReference/API_ResolveCase.html)  | Resolves an AWS Support case\. | Write |  |  |  | 
|   SearchForCases  | Returns a list of AWS Support cases that matches the given inputs\. | Read |  |  |  | 

## Resource types defined by AWS Support<a name="awssupport-resources-for-iam-policies"></a>

AWS Support does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Support, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS Support<a name="awssupport-policy-keys"></a>

Support has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.