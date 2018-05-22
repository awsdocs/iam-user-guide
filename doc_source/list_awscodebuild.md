# Actions, Resources, and Condition Keys for AWS CodeBuild<a name="list_awscodebuild"></a>

AWS CodeBuild \(service prefix: `codebuild`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/codebuild/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/codebuild/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CodeBuild](#awscodebuild-actions-as-permissions)
+ [Resources Defined by CodeBuild](#awscodebuild-resources-for-iam-policies)
+ [Condition Keys for AWS CodeBuild](#awscodebuild-policy-keys)

## Actions Defined by AWS CodeBuild<a name="awscodebuild-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchDeleteBuilds.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchDeleteBuilds.html) | Deletes one or more builds\. | Write | [project\*](#awscodebuild-project)  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchGetBuilds.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchGetBuilds.html) | Gets information about one or more builds\. | Read | [project\*](#awscodebuild-project)  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchGetProjects.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchGetProjects.html) | Gets information about one or more build projects\. | Read | [project\*](#awscodebuild-project)  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_CreateProject.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_CreateProject.html) | Creates a build project\. | Write | [project\*](#awscodebuild-project)  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_DeleteProject.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_DeleteProject.html) | Deletes a build project\. | Write | [project\*](#awscodebuild-project)  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListBuilds.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListBuilds.html) | Gets a list of build IDs, with each build ID representing a single build\. | List |  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListBuildsForProject.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListBuildsForProject.html) | Gets a list of build IDs for the specified build project, with each build ID representing a single build\. | List | [project\*](#awscodebuild-project)  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies) | Lists connected third\-party OAuth providers\. Only used in the AWS CodeBuild console\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListCuratedEnvironmentImages.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListCuratedEnvironmentImages.html) | Gets information about Docker images that are managed by AWS CodeBuild\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListProjects.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListProjects.html) | Gets a list of build project names, with each build project name representing a single build project\. | List |  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies) | Lists source code repositories from a connected third\-party OAuth provider\. Only used in the AWS CodeBuild console\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies) | Saves an OAuth token from a connected third\-party OAuth provider\. Only used in the AWS CodeBuild console\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_StartBuild.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_StartBuild.html) | Starts running a build\. | Write | [project\*](#awscodebuild-project)  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_StopBuild.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_StopBuild.html) | Attempts to stop running a build\. | Write | [project\*](#awscodebuild-project)  |  |  | 
| [http://docs.aws.amazon.com/codebuild/latest/APIReference/API_UpdateProject.html](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_UpdateProject.html) | Changes the settings of an existing build project\. | Write | [project\*](#awscodebuild-project)  |  |  | 

## Resources Defined by CodeBuild<a name="awscodebuild-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodebuild-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#arn-formats](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#arn-formats) | arn:$\{Partition\}:codebuild:$\{Region\}:$\{Account\}:build/$\{BuildId\} |  | 
| [http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#arn-formats](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#arn-formats) | arn:$\{Partition\}:codebuild:$\{Region\}:$\{Account\}:project/$\{ProjectName\} |  | 

## Condition Keys for AWS CodeBuild<a name="awscodebuild-policy-keys"></a>

CodeBuild has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.