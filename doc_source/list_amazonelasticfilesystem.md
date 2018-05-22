# Actions, Resources, and Condition Keys for Amazon Elastic File System<a name="list_amazonelasticfilesystem"></a>

Amazon Elastic File System \(service prefix: `elasticfilesystem`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/efs/latest/ug/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/efs/latest/ug/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/efs/latest/ug/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Elastic File System](#amazonelasticfilesystem-actions-as-permissions)
+ [Resources Defined by EFS](#amazonelasticfilesystem-resources-for-iam-policies)
+ [Condition Keys for Amazon Elastic File System](#amazonelasticfilesystem-policy-keys)

## Actions Defined by Amazon Elastic File System<a name="amazonelasticfilesystem-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_CreateFileSystem.html](http://docs.aws.amazon.com/efs/latest/ug/API_CreateFileSystem.html) | Creates a new, empty file system\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_CreateMountTarget.html](http://docs.aws.amazon.com/efs/latest/ug/API_CreateMountTarget.html) | Creates a mount target for a file system\. | Write | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_CreateTags.html](http://docs.aws.amazon.com/efs/latest/ug/API_CreateTags.html) | Creates or overwrites tags associated with a file system\. | Tagging | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_DeleteFileSystem.html](http://docs.aws.amazon.com/efs/latest/ug/API_DeleteFileSystem.html) | Deletes a file system, permanently severing access to its contents\. | Write | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_DeleteMountTarget.html](http://docs.aws.amazon.com/efs/latest/ug/API_DeleteMountTarget.html) | Deletes the specified mount target\. | Write | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_DeleteTags.html](http://docs.aws.amazon.com/efs/latest/ug/API_DeleteTags.html) | Deletes the specified tags from a file system\. | Tagging | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_DescribeFileSystems.html](http://docs.aws.amazon.com/efs/latest/ug/API_DescribeFileSystems.html) | Returns the description of a specific Amazon EFS file system if either the file system CreationToken or the FileSystemId is provided; otherwise, returns descriptions of all file systems owned by the caller's AWS account in the AWS region of the endpoint that you're calling\. | List | [file\-system](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_DescribeMountTargetSecurityGroups.html](http://docs.aws.amazon.com/efs/latest/ug/API_DescribeMountTargetSecurityGroups.html) | Returns the security groups currently in effect for a mount target\. | Read | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_DescribeMountTargets.html](http://docs.aws.amazon.com/efs/latest/ug/API_DescribeMountTargets.html) | Returns the descriptions of all the current mount targets, or a specific mount target, for a file system\. | Read | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_DescribeTags.html](http://docs.aws.amazon.com/efs/latest/ug/API_DescribeTags.html) | Returns the tags associated with a file system\. | Read | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 
| [http://docs.aws.amazon.com/efs/latest/ug/API_ModifyMountTargetSecurityGroups.html](http://docs.aws.amazon.com/efs/latest/ug/API_ModifyMountTargetSecurityGroups.html) | Modifies the set of security groups in effect for a mount target\. | Write | [file\-system\*](#amazonelasticfilesystem-file-system)  |  |  | 

## Resources Defined by EFS<a name="amazonelasticfilesystem-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonelasticfilesystem-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/efs/latest/ug/access-control-overview.html#access-control-resources](http://docs.aws.amazon.com/efs/latest/ug/access-control-overview.html#access-control-resources) | arn:$\{Partition\}:elasticfilesystem:$\{Region\}:$\{Account\}:file\-system/$\{FileSystemId\} |  | 

## Condition Keys for Amazon Elastic File System<a name="amazonelasticfilesystem-policy-keys"></a>

EFS has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.