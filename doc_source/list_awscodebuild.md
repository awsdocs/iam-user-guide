# Actions, Resources, and Condition Keys for AWS CodeBuild<a name="list_awscodebuild"></a>

AWS CodeBuild \(service prefix: `codebuild`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/codebuild/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/codebuild/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CodeBuild](#awscodebuild-actions-as-permissions)
+ [Resources Defined by AWS CodeBuild](#awscodebuild-resources-for-iam-policies)
+ [Condition Keys for AWS CodeBuild](#awscodebuild-policy-keys)

## Actions Defined by AWS CodeBuild<a name="awscodebuild-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchDeleteBuilds ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchDeleteBuilds.html)  | Deletes one or more builds\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ BatchGetBuilds ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchGetBuilds.html)  | Gets information about one or more builds\. | Read |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ BatchGetProjects ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchGetProjects.html)  | Gets information about one or more build projects\. | Read |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ CreateProject ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_CreateProject.html)  | Creates a build project\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ CreateWebhook ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_CreateWebhook.html)  | For an existing AWS CodeBuild build project that has its source code stored in a GitHub or Bitbucket repository, enables AWS CodeBuild to start rebuilding the source code every time a code change is pushed to the repository\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ DeleteOAuthToken ](https://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies) \[permission only\] | Deletes an OAuth token from a connected third\-party OAuth provider\. Only used in the AWS CodeBuild console\. | Write |  |  |  | 
|   [ DeleteProject ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_DeleteProject.html)  | Deletes a build project\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ DeleteSourceCredentials ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_DeleteSourceCredentials.html)  | Deletes a set of GitHub, GitHub Enterprise, or Bitbucket source credentials\. | Write |  |  |  | 
|   [ DeleteWebhook ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_DeleteWebhook.html)  | For an existing AWS CodeBuild build project that has its source code stored in a GitHub or Bitbucket repository, stops AWS CodeBuild from rebuilding the source code every time a code change is pushed to the repository\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ ImportSourceCredentials ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_ImportSourceCredentials.html)  | Imports the source repository credentials for an AWS CodeBuild project that has its source code stored in a GitHub, GitHub Enterprise, or Bitbucket repository\. | Write |  |  |  | 
|   [ InvalidateProjectCache ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_InvalidateProjectCache.html)  | Resets the cache for a project\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ ListBuilds ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListBuilds.html)  | Gets a list of build IDs, with each build ID representing a single build\. | List |  |  |  | 
|   [ ListBuildsForProject ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListBuildsForProject.html)  | Gets a list of build IDs for the specified build project, with each build ID representing a single build\. | List |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ ListConnectedOAuthAccounts ](https://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies) \[permission only\] | Lists connected third\-party OAuth providers\. Only used in the AWS CodeBuild console\. | List |  |  |  | 
|   [ ListCuratedEnvironmentImages ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListCuratedEnvironmentImages.html)  | Gets information about Docker images that are managed by AWS CodeBuild\. | List |  |  |  | 
|   [ ListProjects ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListProjects.html)  | Gets a list of build project names, with each build project name representing a single build project\. | List |  |  |  | 
|   [ ListRepositories ](https://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies) \[permission only\] | Lists source code repositories from a connected third\-party OAuth provider\. Only used in the AWS CodeBuild console\. | List |  |  |  | 
|   [ ListSourceCredentials ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListSourceCredentials.html)  | Returns a list of SourceCredentialsInfo objects\. | List |  |  |  | 
|   [ PersistOAuthToken ](https://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies) \[permission only\] | Saves an OAuth token from a connected third\-party OAuth provider\. Only used in the AWS CodeBuild console\. | Write |  |  |  | 
|   [ StartBuild ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_StartBuild.html)  | Starts running a build\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ StopBuild ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_StopBuild.html)  | Attempts to stop running a build\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ UpdateProject ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_UpdateProject.html)  | Changes the settings of an existing build project\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 
|   [ UpdateWebhook ](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_UpdateWebhook.html)  | Updates the webhook associated with an AWS CodeBuild build project\. | Write |   [ project\* ](#awscodebuild-project)   |  |  | 

## Resources Defined by AWS CodeBuild<a name="awscodebuild-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodebuild-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ build ](https://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#arn-formats)  |  arn:$\{Partition\}:codebuild:$\{Region\}:$\{Account\}:build/$\{BuildId\}  |  | 
|   [ project ](https://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#arn-formats)  |  arn:$\{Partition\}:codebuild:$\{Region\}:$\{Account\}:project/$\{ProjectName\}  |  | 

## Condition Keys for AWS CodeBuild<a name="awscodebuild-policy-keys"></a>

CodeBuild has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.