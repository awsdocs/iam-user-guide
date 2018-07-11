# Actions, Resources, and Condition Keys for AWS CodeCommit<a name="list_awscodecommit"></a>

AWS CodeCommit \(service prefix: `codecommit`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/codecommit/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/codecommit/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/codecommit/latest/userguide/access-permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CodeCommit](#awscodecommit-actions-as-permissions)
+ [Resources Defined by CodeCommit](#awscodecommit-resources-for-iam-policies)
+ [Condition Keys for AWS CodeCommit](#awscodecommit-policy-keys)

## Actions Defined by AWS CodeCommit<a name="awscodecommit-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchGetPullRequests ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-pr) \[permission only\] | Returns information about one or more pull requests in an AWS CodeCommit repository\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ BatchGetRepositories ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_BatchGetRepositories.html)  | Get information about multiple repositories\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ CancelUploadArchive ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-acp) \[permission only\] | Required to cancel the uploading of an archive to a pipeline\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ CreateBranch ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_CreateBranch.html)  | Create a branch in an AWS CodeCommit repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ CreatePullRequest ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_CreatePullRequest.html)  | Creates a pull request in the specified repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ CreateRepository ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_CreateRepository.html)  | Create a new AWS CodeCommit repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ DeleteBranch ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_DeleteBranch.html)  | Delete a branch in an AWS CodeCommit repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ DeleteCommentContent ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_DeleteCommentContent.html)  | Deletes the content of a comment made on a change, file, or commit in a repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ DeleteRepository ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_DeleteRepository.html)  | Delete an AWS CodeCommit repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ DescribePullRequestEvents ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_DescribePullRequestEvents.html)  | Returns information about one or more pull request events\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetBlob ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetBlob.html)  | View the encoded content of an individual file in an AWS CodeCommit repository from the AWS CodeCommit console\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetBranch ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetBranch.html)  | Get details about a branch in an AWS CodeCommit repository\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetComment ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetComment.html)  | Returns the content of a comment made on a change, file, or commit in a repository\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetCommentsForComparedCommit ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetCommentsForComparedCommit.html)  | Returns information about comments made on the comparison between two commits\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetCommentsForPullRequest ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetCommentsForPullRequest.html)  | Returns comments made on a pull request\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetCommit ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetCommit.html)  | Returns information about a commit, including commit message and committer information\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetCommitHistory ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-code) \[permission only\] | Returns information about the history of commits in a repository\.  | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetCommitsFromMergeBase ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-pr) \[permission only\] | Returns information about the difference between commits in the context of a potential merge\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetDifferences ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetDifferences.html)  | Enables the user to view information about the differences in a valid commit specifier \(such as a branch, tag, HEAD, commit ID or other fully qualified reference\)\. Results can be limited to a specified path\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetMergeConflicts ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetMergeConflicts.html)  | Returns information about merge conflicts between the before and after commit IDs for a pull request in a repository\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetObjectIdentifier ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-code) \[permission only\] | Resolve blobs, trees, and commits to their identifier\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetPullRequest ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetPullRequest.html)  | Gets information about a pull request in a specified repository\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetReferences ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-code) \[permission only\] | Get details about references in an AWS CodeCommit repository\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetRepository ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetRepository.html)  | Get information about a single AWS CodeCommit repository\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetRepositoryTriggers ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_GetRepositoryTriggers.html)  | Gets information about triggers configured for a repository\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetTree ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-code) \[permission only\] | View the contents of a specified tree in an AWS CodeCommit repository from the AWS CodeCommit console\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GetUploadArchiveStatus ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-acp) \[permission only\] | Required to determine the status of an archive upload: whether it is in progress, complete, cancelled, or if an error occurred\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GitPull ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-git) \[permission only\] | Pull information from an AWS CodeCommit repository to a local repo\. | Read |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ GitPush ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-git) \[permission only\] | Push information from a local repo to an AWS CodeCommit repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ ListBranches ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_ListBranches.html)  | Get a list of branches in an AWS CodeCommit repository\. | List |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ ListPullRequests ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_ListPullRequests.html)  | Returns a list of pull requests for a specified repository\. The return list can be refined by pull request status or pull request author ARN\. | List |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ ListRepositories ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_ListRepositories.html)  | Gets information about one or more repositories\. | List |  |  |  | 
|   [ MergePullRequestByFastForward ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_MergePullRequestByFastForward.html)  | Closes a pull request and attempts to merge the source commit of a pull request into the specified destination branch for that pull request at the specified commit using the fast\-forward merge option\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ PostCommentForComparedCommit ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_PostCommentForComparedCommit.html)  | Posts a comment on the comparison between two commits\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ PostCommentForPullRequest ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_PostCommentForPullRequest.html)  | Posts a comment on a pull request\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ PostCommentReply ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_PostCommentReply.html)  | Posts a comment in reply to an existing comment on a comparison between commits or a pull request\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ PutFile ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_PutFile.html)  | Enables the user to add or update a file in a branch in an AWS CodeCommit repository, and generate a commit for the addition in the specified branch\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ PutRepositoryTriggers ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_PutRepositoryTriggers.html)  | Replaces all triggers for a repository\. This can be used to create or delete triggers\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ TestRepositoryTriggers ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_TestRepositoryTriggers.html)  | Tests the functionality of repository triggers by sending information to the trigger target\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ UpdateComment ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_UpdateComment.html)  | Replaces the contents of a comment\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ UpdateDefaultBranch ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_UpdateDefaultBranch.html)  | Change the default branch in an AWS CodeCommit repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ UpdatePullRequestDescription ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_UpdatePullRequestDescription.html)  | Replaces the contents of the description of a pull request\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ UpdatePullRequestStatus ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_UpdatePullRequestStatus.html)  | Updates the status of a pull request\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ UpdatePullRequestTitle ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_UpdatePullRequestTitle.html)  | Replaces the title of a pull request\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ UpdateRepositoryDescription ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_UpdateRepositoryDescription.html)  | Change the description of an AWS CodeCommit repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ UpdateRepositoryName ](http://docs.aws.amazon.com/codecommit/latest/APIReference/API_UpdateRepositoryName.html)  | Change the name of an AWS CodeCommit repository\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 
|   [ UploadArchive ](http://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-permissions-reference.html#aa-acp) \[permission only\] | Allows the service role for AWS CodePipeline to upload repository changes into a pipeline\. | Write |   [ repository\* ](#awscodecommit-repository)   |  |  | 

## Resources Defined by CodeCommit<a name="awscodecommit-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodecommit-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ repository ](http://docs.aws.amazon.com/codecommit/latest/userguide/access-permissions.html#access-permissions-syntax)  |  arn:$\{Partition\}:codecommit:$\{Region\}:$\{Account\}:$\{RepositoryName\}  |  | 

## Condition Keys for AWS CodeCommit<a name="awscodecommit-policy-keys"></a>

CodeCommit has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.