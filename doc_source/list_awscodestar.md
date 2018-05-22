# Actions, Resources, and Condition Keys for AWS CodeStar<a name="list_awscodestar"></a>

AWS CodeStar \(service prefix: `codestar`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/codestar/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/codestar/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/codestar/latest/userguide/access-permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CodeStar](#awscodestar-actions-as-permissions)
+ [Resources Defined by CodeStar](#awscodestar-resources-for-iam-policies)
+ [Condition Keys for AWS CodeStar](#awscodestar-policy-keys)

## Actions Defined by AWS CodeStar<a name="awscodestar-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_AssociateTeamMember.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_AssociateTeamMember.html) | Adds a user to the team for an AWS CodeStar project\. | Permissions management | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_CreateProject.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_CreateProject.html) | Creates a project with minimal structure, customer policies, and no resources\. | Permissions management |  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_CreateUserProfile.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_CreateUserProfile.html) | Creates a profile for a user that includes user preferences, display name, and email\. | Write |  |  |  | 
| DeleteExtendedAccess \[permission only\] | Grants access to extended delete APIs\. | Write | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_DeleteProject.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_DeleteProject.html) | Deletes a project, including project resources\. Does not delete users associated with the project, but does delete the IAM roles that allowed access to the project\. | Permissions management | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_DeleteUserProfile.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_DeleteUserProfile.html) | Deletes a user profile in AWS CodeStar, including all personal preference data associated with that profile, such as display name and email address\. It does not delete the history of that user, for example the history of commits made by that user\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_DescribeProject.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_DescribeProject.html) | Describes a project and its resources\. | Read | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_DescribeUserProfile.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_DescribeUserProfile.html) | Describes a user in AWS CodeStar and the user attributes across all projects\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_DisassociateTeamMember.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_DisassociateTeamMember.html) | Removes a user from a project\. Removing a user from a project also removes the IAM policies from that user that allowed access to the project and its resources\. | Permissions management | [project\*](#awscodestar-project)  |  |  | 
| GetExtendedAccess \[permission only\] | Grants access to extended read APIs\. | Read | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_ListProjects.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_ListProjects.html) | Lists all projects in CodeStar associated with your AWS account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_ListResources.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_ListResources.html) | Lists all resources associated with a project in CodeStar\. | List | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_ListTeamMembers.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_ListTeamMembers.html) | Lists all team members associated with a project\. | List | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_ListUserProfiles.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_ListUserProfiles.html) | Lists user profiles in AWS CodeStar\. | List |  |  |  | 
| PutExtendedAccess \[permission only\] | Grants access to extended write APIs\. | Write | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_UpdateProject.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_UpdateProject.html) | Updates a project in CodeStar\. | Write | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_UpdateTeamMember.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_UpdateTeamMember.html) | Updates team member attributes within a CodeStar project\. | Permissions management | [project\*](#awscodestar-project)  |  |  | 
| [http://docs.aws.amazon.com/codestar/latest/APIReference/API_UpdateUserProfile.html](http://docs.aws.amazon.com/codestar/latest/APIReference/API_UpdateUserProfile.html) | Updates a profile for a user that includes user preferences, display name, and email\. | Write |  |  |  | 
| VerifyServiceRole | Verifies whether the AWS CodeStar service role exists in the customer's account\. | List |  |  |  | 

## Resources Defined by CodeStar<a name="awscodestar-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodestar-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/codestar/latest/userguide/working-with-projects.html](http://docs.aws.amazon.com/codestar/latest/userguide/working-with-projects.html) | arn:$\{Partition\}:codestar:$\{Region\}:$\{Account\}:project/$\{ProjectId\} |  | 

## Condition Keys for AWS CodeStar<a name="awscodestar-policy-keys"></a>

CodeStar has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.