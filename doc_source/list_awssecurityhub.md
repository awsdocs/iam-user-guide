# Actions, Resources, and Condition Keys for AWS Security Hub<a name="list_awssecurityhub"></a>

AWS Security Hub \(service prefix: `securityhub`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/securityhub/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/securityhub/1.0/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Security Hub](#awssecurityhub-actions-as-permissions)
+ [Resource Types Defined by AWS Security Hub](#awssecurityhub-resources-for-iam-policies)
+ [Condition Keys for AWS Security Hub](#awssecurityhub-policy-keys)

## Actions Defined by AWS Security Hub<a name="awssecurityhub-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AcceptInvitation ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_AcceptInvitation.html)  | Grants permission to accept Security Hub invitations to become a member account\. | Write |  |  |  | 
|   [ BatchDisableStandards ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_BatchDisableStandards.html)  | Grants permission to disable standards in Security Hub\. | Write |   [ standards\-subscription\* ](#awssecurityhub-standards-subscription)   |  |  | 
|   [ BatchEnableStandards ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_BatchEnableStandards.html)  | Grants permission to enable standards in Security Hub\. | Write |   [ standard\* ](#awssecurityhub-standard)   |  |  | 
|   [ BatchImportFindings ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_BatchImportFindings.html)  | Grants permission to import findings into Security Hub from an integrated product\. | Write |  |   [ securityhub:TargetAccount ](#awssecurityhub-securityhub_TargetAccount)   |  | 
|   [ CreateActionTarget ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_CreateActionTarget.html)  | Grants permission to create custom actions in Security Hub\. | Write |  |  |  | 
|   [ CreateInsight ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_CreateInsight.html)  | Grants permission to create insights in Security Hub\. Insights are collections of related findings\. | Write |  |  |  | 
|   [ CreateMembers ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_CreateMembers.html)  | Grants permission to create member accounts in Security Hub\. | Write |  |  |  | 
|   [ DeclineInvitations ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DeclineInvitations.html)  | Grants permission to decline Security Hub invitations to become a member account\. | Write |  |  |  | 
|   [ DeleteActionTarget ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DeleteActionTarget.html)  | Grants permission to delete custom actions in Security Hub\. | Write |   [ action\-target\* ](#awssecurityhub-action-target)   |  |  | 
|   [ DeleteInsight ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DeleteInsight.html)  | Grants permission to delete insights from Security Hub\. | Write |   [ insight\* ](#awssecurityhub-insight)   |  |  | 
|   [ DeleteInvitations ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DeleteInvitations.html)  | Grants permission to delete Security Hub invitations to become a member account\. | Write |  |  |  | 
|   [ DeleteMembers ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DeleteMembers.html)  | Grants permission to delete Security Hub member accounts\. | Write |  |  |  | 
|   [ DescribeActionTargets ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DescribeActionTargets.html)  | Grants permission to retrieve a list of custom actions using the API\. | Read |  |  |  | 
|   [ DescribeHub ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DescribeHub.html)  | Grants permission to retrieve information about the hub resource in your account\. | Read |  |  |  | 
|   [ DescribeProducts ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DescribeProducts.html)  | Grants permission to retrieve information about the available Security Hub product integrations\. | Read |  |  |  | 
|   [ DescribeStandards ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DescribeStandards.html)  | Grants permission to retrieve information about Security Hub standards\. | Read |   [ hub\* ](#awssecurityhub-hub)   |  |  | 
|   [ DescribeStandardsControls ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DescribeStandardsControls.html)  | Grants permission to retrieve information about Security Hub standards controls\. | Read |   [ hub\* ](#awssecurityhub-hub)   |  |  | 
|   [ DisableImportFindingsForProduct ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DisableImportFindingsForProduct.html)  | Grants permission to disable the findings importing for a Security Hub integrated product\. | Write |   [ product\* ](#awssecurityhub-product)   |  |  | 
|   [ DisableSecurityHub ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DisableSecurityHub.html)  | Grants permission to disable Security Hub\. | Write |  |  |  | 
|   [ DisassociateFromMasterAccount ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DisassociateFromMasterAccount.html)  | Grants permission to a Security Hub member account to disassociate from the associated master account\. | Write |  |  |  | 
|   [ DisassociateMembers ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_DisassociateMembers.html)  | Grants permission to disassociate Security Hub member accounts from the associated master account\. | Write |  |  |  | 
|   [ EnableImportFindingsForProduct ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_EnableImportFindingsForProduct.html)  | Grants permission to enable the findings importing for a Security Hub integrated product\. | Write |   [ product\* ](#awssecurityhub-product)   |  |  | 
|   [ EnableSecurityHub ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_EnableSecurityHub.html)  | Grants permission to enable Security Hub\. | Write |  |   [ aws:RequestTag/$\{TagKey\} ](#awssecurityhub-aws_RequestTag___TagKey_)   [ aws:TagKeys ](#awssecurityhub-aws_TagKeys)   |  | 
|   [ GetEnabledStandards ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_GetEnabledStandards.html)  | Grants permission to retrieve a list of the standards that are enabled in Security Hub\. | List |  |  |  | 
|   [ GetFindings ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_GetFindings.html)  | Grants permission to retrieve a list of findings from Security Hub\. | Read |  |  |  | 
|   [ GetInsightResults ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_GetInsightResults.html)  | Grants permission to retrieve insight results from Security Hub\. | Read |   [ insight\* ](#awssecurityhub-insight)   |  |  | 
|   [ GetInsights ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_GetInsights.html)  | Grants permission to retrieve Security Hub insights\. | List |   [ insight\* ](#awssecurityhub-insight)   |  |  | 
|   [ GetInvitationsCount ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_GetInvitationsCount.html)  | Grants permission to retrieve the count of Security Hub membership invitations sent to the account\. | Read |  |  |  | 
|   [ GetMasterAccount ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_GetMasterAccount.html)  | Grants permission to retrieve details about the Security Hub master account\. | Read |  |  |  | 
|   [ GetMembers ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_GetMembers.html)  | Grants permission to retrieve the details of Security Hub member accounts\. | Read |  |  |  | 
|   [ InviteMembers ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_InviteMembers.html)  | Grants permission to invite other AWS accounts to become Security Hub member accounts\. | Write |  |  |  | 
|   [ ListEnabledProductsForImport ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_ListEnabledProductsForImport.html)  | Grants permission to retrieve the Security Hub integrated products that are currently enabled\. | List |  |  |  | 
|   [ ListInvitations ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_ListInvitations.html)  | Grants permission to retrieve the Security Hub invitations sent to the account\. | List |  |  |  | 
|   [ ListMembers ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_ListMembers.html)  | Grants permission to retrieve details about Security Hub member accounts associated with the master account\.  | List |  |  |  | 
|   [ ListTagsForResource ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_ListTagsForResource.html)  | Grants permission to list of tags associated with a resource\. | List |   [ hub\* ](#awssecurityhub-hub)   |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_TagResource.html)  | Grants permission to add tags to a Security Hub resource\. | Write |   [ hub\* ](#awssecurityhub-hub)   |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_UntagResource.html)  | Grants permission to remove tags from a Security Hub resource\. | Write |   [ hub\* ](#awssecurityhub-hub)   |  |  | 
|   [ UpdateActionTarget ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_UpdateActionTarget.html)  | Grants permission to update custom actions in Security Hub\. | Write |   [ action\-target\* ](#awssecurityhub-action-target)   |  |  | 
|   [ UpdateFindings ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_UpdateFindings.html)  | Grants permission to update Security Hub findings\. | Write |  |  |  | 
|   [ UpdateInsight ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_UpdateInsight.html)  | Grants permission to update insights in Security Hub\. | Write |   [ insight\* ](#awssecurityhub-insight)   |  |  | 
|   [ UpdateStandardsControl ](https://docs.aws.amazon.com/securityhub/1.0/APIReference/API_UpdateStandardsControl.html)  | Grants permission to update Security Hub standards controls\. | Write |   [ hub\* ](#awssecurityhub-hub)   |  |  | 

## Resource Types Defined by AWS Security Hub<a name="awssecurityhub-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awssecurityhub-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ insight ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:$\{Region\}:$\{Account\}:insight/$\{CompanyId\}/$\{ProductId\}/$\{UniqueId\}  |  | 
|   [ standard ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:::ruleset/$\{StandardsName\}/v/$\{StandardsVersion\}  |  | 
|   [ standards\-subscription ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:$\{Region\}:$\{Account\}:subscription/$\{StandardsName\}/v/$\{StandardsVersion\}  |  | 
|   [ product\-subscription ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:$\{Region\}:$\{Account\}:product\-subscription/$\{Company\}/$\{ProductId\}  |  | 
|   [ product ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:$\{Region\}:$\{Account\}:product/$\{Company\}/$\{ProductId\}  |  | 
|   [ hub ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:$\{Region\}:$\{Account\}:hub/default  |   [ aws:ResourceTag/$\{TagKey\} ](#awssecurityhub-aws_ResourceTag___TagKey_)   | 
|   [ action\-target ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#resources)  |  arn:$\{Partition\}:securityhub:$\{Region\}:$\{Account\}:action/custom/$\{Id\}  |  | 

## Condition Keys for AWS Security Hub<a name="awssecurityhub-policy-keys"></a>

AWS Security Hub defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of tag keys in the request | String | 
|   [ securityhub:TargetAccount ](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-access.html#conditions)  | The ID of the AWS account into which you want to import findings\. In the AWS Security Finding format, this field is called AwsAccountId | String | 