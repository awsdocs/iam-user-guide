# Actions, resources, and condition keys for Amazon WorkDocs<a name="list_amazonworkdocs"></a>

Amazon WorkDocs \(service prefix: `workdocs`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/workdocs/latest/adminguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/workdocs/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/workdocs/latest/adminguide/prereqs.html) permission policies\.

**Topics**
+ [Actions defined by Amazon WorkDocs](#amazonworkdocs-actions-as-permissions)
+ [Resource types defined by Amazon WorkDocs](#amazonworkdocs-resources-for-iam-policies)
+ [Condition keys for Amazon WorkDocs](#amazonworkdocs-policy-keys)

## Actions defined by Amazon WorkDocs<a name="amazonworkdocs-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AbortDocumentVersionUpload ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_AbortDocumentVersionUpload.html)  | Grants permission to abort the upload of the specified document version that was previously initiated by InitiateDocumentVersionUpload\. | Write |  |  |  | 
|   [ ActivateUser ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_ActivateUser.html)  | Grants permission to activate the specified user\. Only active users can access Amazon WorkDocs\. | Write |  |  |  | 
|   [ AddResourcePermissions ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_AddResourcePermissions.html)  | Grants permission to create a set of permissions for the specified folder or document\. | Write |  |  |  | 
|   [ AddUserToGroup ](https://docs.aws.amazon.com/workdocs/latest/adminguide/manage_set_admin.html) \[permission only\] | Grants permission to add a user to a group\. | Write |  |  |  | 
|   [ CheckAlias ](https://docs.aws.amazon.com/workdocs/latest/adminguide/cloud_quick_start.html) \[permission only\] | Grants permission to check an alias\. | Read |  |  |  | 
|   [ CreateComment ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateComment.html)  | Grants permission to add a new comment to the specified document version\. | Write |  |  |  | 
|   [ CreateCustomMetadata ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateCustomMetadata.html)  | Grants permission to add one or more custom properties to the specified resource\. | Write |  |  |  | 
|   [ CreateFolder ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateFolder.html)  | Grants permission to create a folder with the specified name and parent folder\. | Write |  |  |  | 
|   [ CreateInstance ](https://docs.aws.amazon.com/workdocs/latest/adminguide/getting_started.html) \[permission only\] | Grants permission to create an instance\. | Write |  |  |  | 
|   [ CreateLabels ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateLabels.html)  | Grants permission to add labels to the given resource\. | Write |  |  |  | 
|   [ CreateNotificationSubscription ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateNotificationSubscription.html)  | Grants permission to configure WorkDocs to use Amazon SNS notifications\. | Write |  |  |  | 
|   [ CreateUser ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateUser.html)  | Grants permission to create a user in a Simple AD or Microsoft AD directory\. | Write |  |  |  | 
|   [ DeactivateUser ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeactivateUser.html)  | Grants permission to deactivate the specified user, which revokes the user's access to Amazon WorkDocs\. | Write |  |  |  | 
|   [ DeleteComment ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteComment.html)  | Grants permission to delete the specified comment from the document version\. | Write |  |  |  | 
|   [ DeleteCustomMetadata ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteCustomMetadata.html)  | Grants permission to delete custom metadata from the specified resource\. | Write |  |  |  | 
|   [ DeleteDocument ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteDocument.html)  | Grants permission to permanently delete the specified document and its associated metadata\. | Write |  |  |  | 
|   [ DeleteFolder ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteFolder.html)  | Grants permission to permanently delete the specified folder and its contents\. | Write |  |  |  | 
|   [ DeleteFolderContents ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteFolderContents.html)  | Grants permission to delete the contents of the specified folder\. | Write |  |  |  | 
|   [ DeleteInstance ](https://docs.aws.amazon.com/workdocs/latest/adminguide/manage-sites.html#delete_site) \[permission only\] | Grants permission to delete an instance\. | Write |  |  |  | 
|   [ DeleteLabels ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteLabels.html)  | Grants permission to delete one or more labels from a resource\. | Write |  |  |  | 
|   [ DeleteNotificationSubscription ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteNotificationSubscription.html)  | Grants permission to delete the specified subscription from the specified organization\. | Write |  |  |  | 
|   [ DeleteUser ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteUser.html)  | Grants permission to delete the specified user from a Simple AD or Microsoft AD directory\. | Write |  |  |  | 
|   [ DeregisterDirectory ](https://docs.aws.amazon.com/workdocs/latest/adminguide/manage-sites.html#delete_site) \[permission only\] | Grants permission to deregister a directory\. | Write |  |  |  | 
|   [ DescribeActivities ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeActivities.html)  | Grants permission to fetch user activities in a specified time period\. | List |  |  |  | 
|   [ DescribeAvailableDirectories ](https://docs.aws.amazon.com/workdocs/latest/adminguide/getting_started.html) \[permission only\] | Grants permission to describe available directories\. | List |  |  |  | 
|   [ DescribeComments ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeComments.html)  | Grants permission to list all the comments for the specified document version\. | List |  |  |  | 
|   [ DescribeDocumentVersions ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeDocumentVersions.html)  | Grants permission to retrieve the document versions for the specified document\. | List |  |  |  | 
|   [ DescribeFolderContents ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeFolderContents.html)  | Grants permission to describe the contents of the specified folder, including its documents and sub\-folders\. | List |  |  |  | 
|   [ DescribeGroups ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeGroups.html)  | Grants permission to describe the user groups\. | List |  |  |  | 
|   [ DescribeInstances ](https://docs.aws.amazon.com/workdocs/latest/adminguide/getting_started.html) \[permission only\] | Grants permission to describe instances\. | List |  |  |  | 
|   [ DescribeNotificationSubscriptions ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeNotificationSubscriptions.html)  | Grants permission to list the specified notification subscriptions\. | List |  |  |  | 
|   [ DescribeResourcePermissions ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeResourcePermissions.html)  | Grants permission to view a description of a specified resource's permissions\. | List |  |  |  | 
|   [ DescribeRootFolders ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeRootFolders.html)  | Grants permission to describe the root folders\. | List |  |  |  | 
|   [ DescribeUsers ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeUsers.html)  | Grants permission to view a description of the specified users\. You can describe all users or filter the results \(for example, by status or organization\)\. | List |  |  |  | 
|   [ DownloadDocumentVersion ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetDocumentVersion.html) \[permission only\] | Grants permission to download a specified document version\. | Read |  |  |  | 
|   [ GetCurrentUser ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetCurrentUser.html)  | Grants permission to retrieve the details of the current user\. | Read |  |  |  | 
|   [ GetDocument ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetDocument.html)  | Grants permission to retrieve the specified document object\. | Read |  |  |  | 
|   [ GetDocumentPath ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetDocumentPath.html)  | Grants permission to retrieve the path information \(the hierarchy from the root folder\) for the requested document\. | Read |  |  |  | 
|   [ GetDocumentVersion ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetDocumentVersion.html)  | Grants permission to retrieve version metadata for the specified document\. | Read |  |  |  | 
|   [ GetFolder ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetFolder.html)  | Grants permission to retrieve the metadata of the specified folder\. | Read |  |  |  | 
|   [ GetFolderPath ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetFolderPath.html)  | Grants permission to retrieve the path information \(the hierarchy from the root folder\) for the specified folder\. | Read |  |  |  | 
|   [ GetResources ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetResources.html)  | Grants permission to get a collection of resources\. | Read |  |  |  | 
|   [ InitiateDocumentVersionUpload ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_InitiateDocumentVersionUpload.html)  | Grants permission to create a new document object and version object\. | Write |  |  |  | 
|   [ RegisterDirectory ](https://docs.aws.amazon.com/workdocs/latest/adminguide/existing-dir-setup.html) \[permission only\] | Grants permission to register a directory\. | Write |  |  |  | 
|   [ RemoveAllResourcePermissions ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_RemoveAllResourcePermissions.html)  | Grants permission to remove all the permissions from the specified resource\. | Write |  |  |  | 
|   [ RemoveResourcePermission ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_RemoveResourcePermission.html)  | Grants permission to remove the permission for the specified principal from the specified resource\. | Write |  |  |  | 
|   [ UpdateDocument ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_UpdateDocument.html)  | Grants permission to update the specified attributes of the specified document\. | Write |  |  |  | 
|   [ UpdateDocumentVersion ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_UpdateDocumentVersion.html)  | Grants permission to change the status of the document version to ACTIVE\. | Write |  |  |  | 
|   [ UpdateFolder ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_UpdateFolder.html)  | Grants permission to update the specified attributes of the specified folder\. | Write |  |  |  | 
|   [ UpdateInstanceAlias ](https://docs.aws.amazon.com/workdocs/latest/adminguide/getting_started.html) \[permission only\] | Grants permission to update an instance alias\. | Write |  |  |  | 
|   [ UpdateUser ](https://docs.aws.amazon.com/workdocs/latest/APIReference/API_UpdateUser.html)  | Grants permission to update the specified attributes of the specified user, and grants or revokes administrative privileges to the Amazon WorkDocs site\. | Write |  |  |  | 

## Resource types defined by Amazon WorkDocs<a name="amazonworkdocs-resources-for-iam-policies"></a>

Amazon WorkDocs does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon WorkDocs, specify `“Resource”: “*”` in your policy\.

## Condition keys for Amazon WorkDocs<a name="amazonworkdocs-policy-keys"></a>

WorkDocs has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.