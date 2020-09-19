# Actions, resources, and condition keys for Amazon CodeGuru Reviewer<a name="list_amazoncodegurureviewer"></a>

Amazon CodeGuru Reviewer \(service prefix: `codeguru-reviewer`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/Welcome.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/codeguru/latest/reviewer-api/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](${UserGuideDocPage}) permission policies\.

**Topics**
+ [Actions defined by Amazon CodeGuru Reviewer](#amazoncodegurureviewer-actions-as-permissions)
+ [Resource types defined by Amazon CodeGuru Reviewer](#amazoncodegurureviewer-resources-for-iam-policies)
+ [Condition keys for Amazon CodeGuru Reviewer](#amazoncodegurureviewer-policy-keys)

## Actions defined by Amazon CodeGuru Reviewer<a name="amazoncodegurureviewer-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   AssociateRepository  | Grants permission to associates a repository with Amazon CodeGuru Reviewer\. | Write |   [ repository ](#amazoncodegurureviewer-repository)   |  |   codecommit:ListRepositories   codecommit:TagResource   events:PutRule   events:PutTargets   iam:CreateServiceLinkedRole   | 
|   CreateConnectionToken \[permission only\] | Grants permission to perform webbased oauth handshake for 3rd party providers\. | Read |  |  |  | 
|   DescribeCodeReview  | Grants permission to describe a code review\. | Read |   [ codereview\* ](#amazoncodegurureviewer-codereview)   |  |  | 
|   DescribeRecommendationFeedback  | Grants permission to describe a recommendation feedback on a code review\. | Read |   [ codereview\* ](#amazoncodegurureviewer-codereview)   |  |  | 
|   DescribeRepositoryAssociation  | Grants permission to describe a repository association\. | Read |   [ association\* ](#amazoncodegurureviewer-association)   |  |  | 
|   DisassociateRepository  | Grants permission to disassociate a repository with Amazon CodeGuru Reviewer\. | Write |   [ association\* ](#amazoncodegurureviewer-association)   |  |   codecommit:UntagResource   events:DeleteRule   events:RemoveTargets   | 
|   GetMetricsData \[permission only\] | Grants permission to view pull request metrics in console\. | Read |  |  |  | 
|   ListCodeReviews  | Grants permission to list summary of code reviews\. | List |  |  |  | 
|   ListRecommendationFeedback  | Grants permission to list summary of recommendation feedback on a code review\. | List |   [ codereview\* ](#amazoncodegurureviewer-codereview)   |  |  | 
|   ListRecommendations  | Grants permission to list summary of recommendations on a code review | List |   [ codereview\* ](#amazoncodegurureviewer-codereview)   |  |  | 
|   ListRepositoryAssociations  | Grants permission to list summary of repository associations\. | List |  |  |  | 
|   ListThirdPartyRepositories \[permission only\] | Grants permission to list 3rd party providers repositories in console\. | Read |  |  |  | 
|   PutRecommendationFeedback  | Grants permission to put feedback for a recommendation on a code review\. | Write |   [ codereview\* ](#amazoncodegurureviewer-codereview)   |  |  | 

## Resource types defined by Amazon CodeGuru Reviewer<a name="amazoncodegurureviewer-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncodegurureviewer-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   association  |  arn:$\{Partition\}:codeguru\-reviewer::$\{Account\}:association:$\{ResourceId\}  |  | 
|   codereview  |  arn:$\{Partition\}:codeguru\-reviewer::$\{Account\}:\.\+:\.\+  |  | 
|   [ repository ](https://docs.aws.amazon.com/codeguru/latest/reviewer-ug/auth-and-access-control-iam-access-control-identity-based.html#arn-formats)  |  arn:$\{Partition\}:codecommit:$\{Region\}:$\{Account\}:$\{RepositoryName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazoncodegurureviewer-aws_ResourceTag___TagKey_)   | 

## Condition keys for Amazon CodeGuru Reviewer<a name="amazoncodegurureviewer-policy-keys"></a>

Amazon CodeGuru Reviewer defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag key\-value pairs attached to the resource | String | 