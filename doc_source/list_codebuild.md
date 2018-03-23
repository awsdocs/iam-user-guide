# Actions and Condition Context Keys for AWS CodeBuild<a name="list_codebuild"></a>

AWS CodeBuild \(service prefix: codebuild\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS CodeBuild**

For information about using the following AWS CodeBuild API actions in an IAM policy, see [Using Identity\-Based Policies \(IAM Policies\) for AWS CodeBuild](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html) in the *AWS CodeBuild User Guide*\.
+ `[codebuild:BatchDeleteBuilds](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchDeleteBuilds.html)`
+ `[codebuild:BatchGetBuilds](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchGetBuilds.html)`
+ `[codebuild:BatchGetProjects](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_BatchGetProjects.html)`
+ `[codebuild:CreateProject](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_CreateProject.html)`
+ `[codebuild:DeleteProject](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_DeleteProject.html)`
+ `[codebuild:ListBuilds](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListBuilds.html)`
+ `[codebuild:ListBuildsForProject](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListBuildsForProject.html)`
+ `[codebuild:ListConnectedOAuthAccounts](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[codebuild:ListCuratedEnvironmentImages](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListCuratedEnvironmentImages.html)`
+ `[codebuild:ListProjects](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_ListProjects.html)`
+ `[codebuild:ListRepositories](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[codebuild:PersistOAuthToken](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#console-policies)` \- this is an IAM policy permission only, not an API action that can be called\.
+ `[codebuild:StartBuild](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_StartBuild.html)`
+ `[codebuild:StopBuild](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_StopBuild.html)`
+ `[codebuild:UpdateProject](http://docs.aws.amazon.com/codebuild/latest/APIReference/API_UpdateProject.html)`

**Condition context keys for AWS CodeBuild**

AWS CodeBuild has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.