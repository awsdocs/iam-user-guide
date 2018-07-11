# Actions, Resources, and Condition Keys for Amazon WorkDocs<a name="list_amazonworkdocs"></a>

Amazon WorkDocs \(service prefix: `workdocs`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/workdocs/latest/adminguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/workdocs/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/workdocs/latest/adminguide/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon WorkDocs](#amazonworkdocs-actions-as-permissions)
+ [Resources Defined by WorkDocs](#amazonworkdocs-resources-for-iam-policies)
+ [Condition Keys for Amazon WorkDocs](#amazonworkdocs-policy-keys)

## Actions Defined by Amazon WorkDocs<a name="amazonworkdocs-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AbortDocumentVersionUpload ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_AbortDocumentVersionUpload.html)  | Aborts the upload of the specified document version that was previously initiated by InitiateDocumentVersionUpload\. | Write |  |  |  | 
|   [ ActivateUser ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_ActivateUser.html)  | Activates the specified user\. Only active users can access Amazon WorkDocs\. | Write |  |  |  | 
|   [ AddResourcePermissions ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_AddResourcePermissions.html)  | Creates a set of permissions for the specified folder or document\. | Write |  |  |  | 
|   AddUserToGroup  |  | Write |  |  |  | 
|   CheckAlias  |  | Read |  |  |  | 
|   [ CreateFolder ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateFolder.html)  | Creates a folder with the specified name and parent folder\. | Write |  |  |  | 
|   CreateInstance  |  | Write |  |  |  | 
|   [ CreateNotificationSubscription ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateNotificationSubscription.html)  | Configure WorkDocs to use Amazon SNS notifications\. | Write |  |  |  | 
|   [ CreateUser ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_CreateUser.html)  | Creates a user in a Simple AD or Microsoft AD directory\. | Write |  |  |  | 
|   [ DeactivateUser ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeactivateUser.html)  | Deactivates the specified user, which revokes the user's access to Amazon WorkDocs\. | Write |  |  |  | 
|   [ DeleteDocument ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteDocument.html)  | Permanently deletes the specified document and its associated metadata\. | Write |  |  |  | 
|   [ DeleteFolder ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteFolder.html)  | Permanently deletes the specified folder and its contents\. | Write |  |  |  | 
|   [ DeleteFolderContents ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteFolderContents.html)  | Deletes the contents of the specified folder\. | Write |  |  |  | 
|   DeleteInstance  |  | Write |  |  |  | 
|   [ DeleteNotificationSubscription ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteNotificationSubscription.html)  | Deletes the specified subscription from the specified organization\. | Write |  |  |  | 
|   [ DeleteUser ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DeleteUser.html)  | Deletes the specified user from a Simple AD or Microsoft AD directory\. | Write |  |  |  | 
|   DeregisterDirectory  |  | Write |  |  |  | 
|   DescribeAvailableDirectories  |  | List |  |  |  | 
|   [ DescribeDocumentVersions ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeDocumentVersions.html)  | Retrieves the document versions for the specified document\. | List |  |  |  | 
|   [ DescribeFolderContents ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeFolderContents.html)  | Describes the contents of the specified folder, including its documents and sub\-folders\. | List |  |  |  | 
|   DescribeInstances  |  | List |  |  |  | 
|   [ DescribeNotificationSubscriptions ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeNotificationSubscriptions.html)  | Lists the specified notification subscriptions\. | List |  |  |  | 
|   [ DescribeResourcePermissions ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeResourcePermissions.html)  | Describes the permissions of a specified resource\. | List |  |  |  | 
|   [ DescribeUsers ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_DescribeUsers.html)  | Describes the specified users\. You can describe all users or filter the results \(for example, by status or organization\)\. | List |  |  |  | 
|   [ GetDocument ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetDocument.html)  | Retrieves the specified document object\. | Read |  |  |  | 
|   [ GetDocumentPath ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetDocumentPath.html)  | Retrieves the path information \(the hierarchy from the root folder\) for the requested document\. | Read |  |  |  | 
|   [ GetDocumentVersion ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetDocumentVersion.html)  | Retrieves version metadata for the specified document\. | Read |  |  |  | 
|   [ GetFolder ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetFolder.html)  | Retrieves the metadata of the specified folder\. | Read |  |  |  | 
|   [ GetFolderPath ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_GetFolderPath.html)  | Retrieves the path information \(the hierarchy from the root folder\) for the specified folder\. | Read |  |  |  | 
|   [ InitiateDocumentVersionUpload ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_InitiateDocumentVersionUpload.html)  | Creates a new document object and version object\. | Write |  |  |  | 
|   RegisterDirectory  |  | Write |  |  |  | 
|   [ RemoveAllResourcePermissions ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_RemoveAllResourcePermissions.html)  | Removes all the permissions from the specified resource\. | Write |  |  |  | 
|   [ RemoveResourcePermission ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_RemoveResourcePermission.html)  | Removes the permission for the specified principal from the specified resource\. | Write |  |  |  | 
|   RemoveUserFromGroup  |  | Write |  |  |  | 
|   [ UpdateDocument ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_UpdateDocument.html)  | Updates the specified attributes of the specified document\. | Write |  |  |  | 
|   [ UpdateDocumentVersion ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_UpdateDocumentVersion.html)  | Changes the status of the document version to ACTIVE\. | Write |  |  |  | 
|   [ UpdateFolder ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_UpdateFolder.html)  | Updates the specified attributes of the specified folder\. | Write |  |  |  | 
|   UpdateInstanceAlias  |  | Write |  |  |  | 
|   [ UpdateUser ](http://docs.aws.amazon.com/workdocs/latest/APIReference/API_UpdateUser.html)  | Updates the specified attributes of the specified user, and grants or revokes administrative privileges to the Amazon WorkDocs site\. | Write |  |  |  | 

## Resources Defined by WorkDocs<a name="amazonworkdocs-resources-for-iam-policies"></a>

Amazon WorkDocs has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon WorkDocs<a name="amazonworkdocs-policy-keys"></a>

WorkDocs has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.