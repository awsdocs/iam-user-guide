# Actions, resources, and condition keys for AWS CodeStar Connections<a name="list_awscodestarconnections"></a>

AWS CodeStar Connections \(service prefix: `codestar-connections`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/codestar-connections/latest/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html) permission policies\.

**Topics**
+ [Actions defined by AWS CodeStar Connections](#awscodestarconnections-actions-as-permissions)
+ [Resource types defined by AWS CodeStar Connections](#awscodestarconnections-resources-for-iam-policies)
+ [Condition keys for AWS CodeStar Connections](#awscodestarconnections-policy-keys)

## Actions defined by AWS CodeStar Connections<a name="awscodestarconnections-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscodestarconnections.html)

## Resource types defined by AWS CodeStar Connections<a name="awscodestarconnections-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodestarconnections-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ Connection ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections.html/API_Connection.html)  |  arn:$\{Partition\}:codestar\-connections:$\{Region\}:$\{Account\}:connection/$\{ConnectionId\}  |  | 

## Condition keys for AWS CodeStar Connections<a name="awscodestarconnections-policy-keys"></a>

AWS CodeStar Connections defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the tags that are passed in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on the tags associated with the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the tag keys that are passed in the request | String | 
|   [ codestar\-connections:BranchName ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-use)  | Filters access by the branch name that is passed in the request\. Applies only to UseConnection requests for access to a specific repository branch | String | 
|   [ codestar\-connections:FullRepositoryId ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-use)  | Filters access by the repository that is passed in the request\. Applies only to UseConnection requests for access to a specific repository | String | 
|   [ codestar\-connections:InstallationId ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-permissions-actions-handshake)  | Filters access by the third\-party ID \(such as the Bitbucket App installation ID for CodeStar Connections\) that is used to update a Connection\. Allows you to restrict which third\-party App installations can be used to make a Connection | String | 
|   [ codestar\-connections:OwnerId ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-use)  | Filters access by the owner of the third\-party repository\. Applies only to UseConnection requests for access to repositories owned by a specific user | String | 
|   [ codestar\-connections:PassedToService ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-passconnection)  | Filters access by the service to which the principal is allowed to pass a Connection | String | 
|   [ codestar\-connections:ProviderAction ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-use-provider)  | Filters access by the provider action in a UseConnection request such as ListRepositories\. See documentation for all valid values | String | 
|   [ codestar\-connections:ProviderPermissionsRequired ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-use)  | Filters access by the write permissions of a provider action in a UseConnection request\. Valid types include read\_only and read\_write | String | 
|   [ codestar\-connections:ProviderType ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-permissions-actions)  | Filters access by the type of third\-party provider passed in the request | String | 
|   [ codestar\-connections:ProviderTypeFilter ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-permissions-actions)  | Filters access by the type of third\-party provider used to filter results | String | 
|   [ codestar\-connections:RepositoryName ](https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-permissions.html#connections-use)  | Filters access by the repository name that is passed in the request\. Applies only to UseConnection requests for creating new repositories | String | 