# Actions, Resources, and Condition Keys for AWS Directory Service<a name="list_awsdirectoryservice"></a>

AWS Directory Service \(service prefix: `ds`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/directoryservice/latest/devguide/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/UsingWithDS_IAM_AuthNAccess.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Directory Service](#awsdirectoryservice-actions-as-permissions)
+ [Resources Defined by Directory Service](#awsdirectoryservice-resources-for-iam-policies)
+ [Condition Keys for AWS Directory Service](#awsdirectoryservice-policy-keys)

## Actions Defined by AWS Directory Service<a name="awsdirectoryservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_AddIpRoutes.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_AddIpRoutes.html) | Adds a CIDR address block to correctly route traffic to and from your Microsoft AD on Amazon Web Services | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_AddTagsToResource.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_AddTagsToResource.html) | Adds or overwrites one or more tags for the specified Amazon Directory Services directory\. | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CancelSchemaExtension.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CancelSchemaExtension.html) | Cancels an in\-progress schema extension to a Microsoft AD directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_ConnectDirectory.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_ConnectDirectory.html) | Creates an AD Connector to connect to an on\-premises directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateAlias.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateAlias.html) | Creates an alias for a directory and assigns the alias to the directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateComputer.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateComputer.html) | Creates a computer account in the specified directory, and joins the computer to the directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateConditionalForwarder.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateConditionalForwarder.html) | Creates a conditional forwarder associated with your AWS directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateDirectory.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateDirectory.html) | Creates a Simple AD directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateMicrosoftAD.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateMicrosoftAD.html) | Creates a Microsoft AD in the AWS cloud\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateSnapshot.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateSnapshot.html) | Creates a snapshot of a Simple AD or Microsoft AD directory in the AWS cloud\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateTrust.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_CreateTrust.html) | Initiates the creation of the AWS side of a trust relationship between a Microsoft AD in the AWS cloud and an external domain\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DeleteConditionalForwarder.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DeleteConditionalForwarder.html) | Deletes a conditional forwarder that has been set up for your AWS directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DeleteDirectory.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DeleteDirectory.html) | Deletes an AWS Directory Service directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DeleteSnapshot.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DeleteSnapshot.html) | Deletes a directory snapshot\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/DeleteTrust.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/DeleteTrust.html) | Deletes an existing trust relationship between your Microsoft AD in the AWS cloud and an external domain\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DeregisterEventTopic.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DeregisterEventTopic.html) | Removes the specified directory as a publisher to the specified SNS topic\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeConditionalForwarders.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeConditionalForwarders.html) | Obtains information about the conditional forwarders for this account\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeDirectories.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeDirectories.html) | Obtains information about the directories that belong to this account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeEventTopics.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeEventTopics.html) | Obtains information about which SNS topics receive status messages from the specified directory\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeSnapshots.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeSnapshots.html) | Obtains information about the directory snapshots that belong to this account\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeTrusts.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DescribeTrusts.html) | Obtains information about the trust relationships for this account\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DisableRadius.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DisableRadius.html) | Disables multi\-factor authentication \(MFA\) with the Remote Authentication Dial In User Service \(RADIUS\) server for an AD Connector directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DisableSso.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_DisableSso.html) | Disables single\-sign on for a directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_EnableRadius.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_EnableRadius.html) | Enables multi\-factor authentication \(MFA\) with the Remote Authentication Dial In User Service \(RADIUS\) server for an AD Connector directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_EnableSso.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_EnableSso.html) | Enables single\-sign on for a directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_GetDirectoryLimits.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_GetDirectoryLimits.html) | Obtains directory limit information for the current region\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_GetSnapshotLimits.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_GetSnapshotLimits.html) | Obtains the manual snapshot limits for a directory\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_ListIpRoutes.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_ListIpRoutes.html) | Lists the address blocks that you have added to a directory\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_ListSchemaExtensions.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_ListSchemaExtensions.html) | Lists all schema extensions applied to a Microsoft AD Directory\. | List |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_ListTagsForResource.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_ListTagsForResource.html) | Lists all tags on an Amazon Directory Services directory\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_RegisterEventTopic.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_RegisterEventTopic.html) | Associates a directory with an SNS topic\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_RemoveIpRoutes.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_RemoveIpRoutes.html) | Removes IP address blocks from a directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_RemoveTagsFromResource.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_RemoveTagsFromResource.html) | Removes tags from an Amazon Directory Services directory\. | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_RestoreFromSnapshot.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_RestoreFromSnapshot.html) | Restores a directory using an existing directory snapshot\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_StartSchemaExtension.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_StartSchemaExtension.html) | Applies a schema extension to a Microsoft AD directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_UpdateConditionalForwarder.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_UpdateConditionalForwarder.html) | Updates a conditional forwarder that has been set up for your AWS directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_UpdateRadius.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_UpdateRadius.html) | Updates the Remote Authentication Dial In User Service \(RADIUS\) server information for an AD Connector directory\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/directoryservice/latest/devguide/API_VerifyTrust.html](http://docs.aws.amazon.com/directoryservice/latest/devguide/API_VerifyTrust.html) | Verifies a trust relationship between your Microsoft AD in the AWS cloud and an external domain\. | Read |  |  |  | 

## Resources Defined by Directory Service<a name="awsdirectoryservice-resources-for-iam-policies"></a>

Directory Service has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Directory Service<a name="awsdirectoryservice-policy-keys"></a>

Directory Service has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.