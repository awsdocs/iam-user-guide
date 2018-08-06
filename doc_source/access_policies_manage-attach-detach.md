# Adding and Removing IAM Policies<a name="access_policies_manage-attach-detach"></a>

You can use policies as permissions policies for users, groups, and roles using the AWS Management Console, the AWS Command Line Interface \(AWS CLI\), or the AWS API\. You can use policies to set [permissions boundaries](access_policies_boundaries.md) for users and roles only, using the same methods\. Use a policy to set a permissions boundary to control the maximum permissions that a principal can have\. Permissions boundaries are an advanced AWS feature\.

**Topics**
+ [Terminology](#attach-detach-etc-terminology)
+ [Adding and Removing IAM Policies \(Console\)](#add-remove-policies-console)
+ [Adding and Removing IAM Policies \(AWS CLI\)](#attach-detaching-policy-cli)
+ [Adding and Removing IAM Policies \(AWS API\)](#attach-detaching-policy-api)

## Terminology<a name="attach-detach-etc-terminology"></a>

When you associate permissions policies with identities \(users, groups, and roles\), you might notice that terminology and procedures vary depending on whether you are working with a managed or inline policy:
+ **Attach** – Used with managed policies\. You attach a managed policy to an identity \(a user, group, or role\)\. Attaching a policy applies the permissions in the policy to the identity\.
+ **Detach** – Used with managed policies\. You detach a managed policy from a principal entity \(a user, group, or role\)\. Detaching a policy removes its permissions from the principal entity\.
+ **Embed** – Used with inline policies\. You embed an inline policy in an identity \(a user, group, or role\)\. Embedding a policy applies the permissions in the policy to the identity\. Because an inline policy is stored in the identity, it is embedded rather than attached, though the results are similar\.
**Note**  
You can embed an inline policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* only in the service that depends on the role\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.
+ **Delete** – Used with inline policies\. You delete an inline policy from a principal entity \(a user, group, or role\)\. Deleting a policy removes its permissions from the principal entity\.
**Note**  
You can delete an inline policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* only in the service that depends on the role\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.

You can use the console, AWS CLI, or AWS API to perform any of these actions\.

### More Information<a name="terminology-more-info-roles-policies"></a>
+ For more information about the difference between managed and inline policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\. 
+ For more information about permissions boundaries, see [Permissions Boundaries for IAM Identities](access_policies_boundaries.md)\.
+ For general information about IAM policies, see [Policies and Permissions](access_policies.md)\.
+ For information about policy size limitations and other quotas, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.

## Adding and Removing IAM Policies \(Console\)<a name="add-remove-policies-console"></a>

You can use the AWS Management Console to attach or detach managed policies used as a permissions policy, or to set, change, or remove a policy used for a [permissions boundary](access_policies_boundaries.md)\. You can also embed or delete an inline policy\.

### <a name="access_policies_manage-attach-detach-console"></a>

**To use a managed policy as a permissions policy for a principal \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\. 

1. In the list of policies, select the check box next to the name of the policy to attach\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose **Policy actions**, and then choose **Attach**\.

1. Select one or more identities to attach the policy to\. You can use the **Filter** menu and the search box to filter the list of principal entities\. After selecting the identities, choose **Attach policy**\.

### <a name="set-managed-policy-boundary-console"></a>

**To use a managed policy to set a permissions boundary \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\. 

1. In the list of policies, choose the name of the policy to set\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. On the policy summary page, choose the **Policy usage tab**, and then, if necessary, open the **Permissions boundaries** section and choose **Set boundary**\.

1. Select one or more users or roles on which to use the policy for a permissions boundary\. You can use the **Filter** menu and the search box to filter the list of principal entities\. After selecting the principals, choose **Set boundaries**\.

### <a name="embed-inline-policy-console"></a>

**To embed an inline policy for a user or role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users** or **Roles**\.

1. In the list, choose the name of the user or role to embed a policy in\.

1. Choose the **Permissions** tab\. 

1. Scroll to the bottom of the page and choose **Add inline policy**\.
**Note**  
You cannot embed an inline policy in a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* in IAM\. Because the linked service defines whether you can modify the permissions of the role, you might be able to add additional policies from the service console, API, or AWS CLI\. To view the service\-linked role documentation for a service, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and choose **Yes** in the **Service\-Linked Role** column for your service\.

1. Choose from the following methods to view the steps required to create your policy:
   + [Importing Existing Managed Policies](access_policies_create.md#access_policies_create-copy) – You can import a managed policy within your account and then edit the policy to customize it to your specific requirements\. A managed policy can be an AWS managed policy or a customer managed policy that you created previously\.
   + [Creating Policies with the Visual Editor](access_policies_create.md#access_policies_create-visual-editor) – You can construct a new policy from scratch in the visual editor\. If you use the visual editor, you do not have to understand JSON syntax\.
   + [Creating Policies on the JSON Tab](access_policies_create.md#access_policies_create-json-editor) – In the **JSON** tab, you can use JSON syntax to create a policy\. You can type a new JSON policy document or paste an [example policy](access_policies_examples.md)\.

1. After you create an inline policy, it is automatically embedded in your user or role\.

**To embed an inline policy for a group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups**\.

1. In the list, choose the name of the group to embed a policy in\.

1. Choose the **Permissions** tab and expand the **Inline Policies** section if necessary\.

1. Choose **Create Group Policy**\. If there are no existing policies in **Groups**, instead choose **click here** to create your first inline policy\.

1. Choose **Policy Generator** or **Custom Policy**, and then choose **Select**\. 

1. Do one of the following:
   + If you chose **Custom Policy**, specify a name for the policy and create your policy document\.[ Policy Validator](access_policies_policy-validator.md) reports any syntax errors\.
   + If you are using the policy generator to create your policy, choose the appropriate **Effect**, **AWS Service**, and **Actions** options\. Type the Amazon Resource Name \(ARN\) \(if applicable\), and add any conditions that you want to include\. Then choose **Add Statement**\. You can add as many statements as you want to the policy\. When you are finished adding statements, choose **Next Step**\. 

1. When you are satisfied with the policy, choose **Apply Policy**\.

### <a name="replace-managed-policy-boundary-console"></a>

**To change the permissions boundary for one or more principals \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\. 

1. In the list of policies, choose the name of the policy to set\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. On the policy summary page, choose the **Policy usage tab**, and then, if necessary, open the **Permissions boundaries** section\. Select the check box next to the users or roles whose boundaries you want to change and then choose **Change boundary**\.

1. Select a new policy to use for a permissions boundary\. You can use the **Filter** menu and the search box to filter the list of policies\. After selecting the policy, choose **Change boundary**\.

### <a name="detach-managed-policy-console"></a>

**To detach a managed policy used as a permissions policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\. 

1. In the list of policies, select the check box next to the name of the policy to detach\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose **Policy actions**, and then choose **Detach**\.

1. Select the identities to detach the policy from\. You can use the **Filter** menu and the search box to filter the list of identities\. After selecting the identities, choose **Detach policy**\.

### <a name="remove-managed-policy-boundary-console"></a>

**To remove a permissions boundary \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\. 

1. In the list of policies, choose the name of the policy to set\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. On the policy summary page, choose the **Policy usage tab**, and then, if necessary, open the **Permissions boundaries** section and choose **Remove boundary**\.

1. Confirm that you want to remove the boundary and choose **Remove**\.

### <a name="delete-inline-policy-console"></a>

**To delete an inline policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups**, **Users**, or **Roles**\.

1. In the list, choose the name of the group, user, or role that has the policy you want to remove\.

1. Choose the **Permissions** tab\. If you chose **Groups**, expand the **Inline Policies** section if necessary\.

1. If in **Groups**, choose **Remove Policy**\. If in **Users** or **Roles**, choose **X**\.

## Adding and Removing IAM Policies \(AWS CLI\)<a name="attach-detaching-policy-cli"></a>

You can use the AWS CLI to attach or detach managed policies used for permissions, or to set, change, or remove a policy used for a [permissions boundary](access_policies_boundaries.md)\. You can also embed or delete an inline policy\.

**To use a managed policy as a permissions policy for a principal \(AWS CLI\)**

1. \(Optional\) To view information about a managed policy, run the following commands: 
   + To list managed policies: [aws iam list\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)
   + To retrieve detailed information about a managed policy: [get\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html)

1. To attach a managed policy to an identity \(user, group, or role\), use one of the following commands: 
   + [aws iam attach\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-user-policy.html)
   + [aws iam attach\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html)
   + [aws iam attach\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-role-policy.html)

**To use a managed policy to set a permissions boundary \(AWS CLI\)**

1. \(Optional\) To view information about a managed policy, run the following commands: 
   + To list managed policies: [aws iam list\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)
   + To retrieve detailed information about a managed policy: [aws iam get\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html)

1. To use a managed policy to set the permissions boundary for a principal \(user or role\), use one of the following commands: 
   + [aws iam put\-user\-permissions\-boundary](http://docs.aws.amazon.com/cli/latest/reference/iam/put-user-permissions-boundary.html)
   + [aws iam put\-role\-permissions\-boundary](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-permissions-boundary.html)

**To embed an inline policy \(AWS CLI\)**  
To embed an inline policy to an identity \(user, group, or role that is not a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\), use one of the following commands: 
+ [aws iam put\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-user-policy.html)
+ [aws iam put\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-group-policy.html)
+ [aws iam put\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)

**To detach a managed policy used as a permissions policy \(AWS CLI\)**

1. \(Optional\) To view information about a policy, run the following commands:
   + To list managed policies: [aws iam list\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)
   + To retrieve detailed information about a managed policy: [aws iam get\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html) 

1. \(Optional\) To find out about the relationships between the policies and identities, run the following commands:
   + To list the identities \(users, groups, and roles\) to which a managed policy is attached: 
     + [aws iam list\-entities\-for\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/list-entities-for-policy.html)
   + To list the managed policies attached to an identity \(a user, group, or role\), use one of the following commands:
     + [aws iam list\-attached\-user\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-user-policies.html)
     + [aws iam list\-attached\-group\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html)
     + [aws iam list\-attached\-role\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html)

1. To detach a managed policy from an identity \(user, group, or role\), use one of the following commands:
   + [aws iam detach\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-user-policy.html)
   + [aws iam detach\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-group-policy.html)
   + [aws iam detach\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-role-policy.html)

**To remove a permissions boundary \(AWS CLI\)**

1. \(Optional\) To view which managed policy is currently used to set the permissions boundary for a user or role, run the following commands:
   + [aws iam get\-user](http://docs.aws.amazon.com/cli/latest/reference/iam/get-user.html)
   +  [aws iam get\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html) 

1. \(Optional\) To view the users or roles on which a managed policy is used for a permissions boundary, run the following command:
   + [aws iam list\-entities\-for\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/list-entities-for-policy.html)

1. \(Optional\) To view information about a managed policy, run the following commands:
   + To list managed policies: [aws iam list\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)
   + To retrieve detailed information about a managed policy: [aws iam get\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html) 

1. To remove a permissions boundary from a user or role, use one of the following commands:
   + [aws iam delete\-user\-permissions\-boundary](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-user-policy.html)
   + [aws iam delete\-role\-permissions\-boundary](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-role-permissions-boundary.html)

**To delete an inline policy \(AWS CLI\)**

1. \(Optional\) To list all inline policies that are attached to an identity \(user, group, role\), use one of the following commands:
   + [aws iam list\-user\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-user-policies.html)
   + [aws iam list\-group\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-group-policies.html)
   + [aws iam list\-role\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-role-policies.html)

1. \(Optional\) To retrieve an inline policy document that is embedded in an identity \(user, group, or role\), use one of the following commands:
   + [aws iam get\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-user-policy.html)
   + [aws iam get\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-group-policy.html)
   + [aws iam get\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role-policy.html)

1. To delete an inline policy from an identity \(user, group, or role that is not a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\), use one of the following commands:
   + [aws iam delete\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-user-policy.html)
   + [aws iam delete\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-group-policy.html)
   + [aws iam delete\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-role-policy.html)

## Adding and Removing IAM Policies \(AWS API\)<a name="attach-detaching-policy-api"></a>

You can use the AWS API to attach or detach managed policies used for permissions, or to set, change, or remove a policy used for a [permissions boundary](access_policies_boundaries.md)\. You can also embed or delete an inline policy\.

**To use a managed policy as a permissions policy for a principal \(AWS API\)**

1. \(Optional\) To view information about a policy, call the following operations: 
   + To list managed policies: [ListPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html) 
   + To retrieve detailed information about a managed policy: [GetPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html)

1. To attach a managed policy to an identity \(user, group, or role\), call one of the following operations:
   + [AttachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachUserPolicy.html)
   + [AttachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachGroupPolicy.html)
   + [AttachRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html)

**To use a managed policy to set a permissions boundary \(AWS API\)**

1. \(Optional\) To view information about a managed policy, call the following operations: 
   + To list managed policies: [ListPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)
   + To retrieve detailed information about a managed policy: [GetPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html)

1. To use a managed policy to set the permissions boundary for a principal \(user or role\), call one of the following operations: 
   + [PutUserPermissionsBoundary](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutUserPermissionsBoundary.html)
   + [PutRolePermissionsBoundary](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePermissionsBoundary.html)

**To embed an inline policy \(AWS API\)**  
To embed an inline policy in an identity \(user, group, or role that is not a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\), call one of the following operations:
+ [PutUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutUserPolicy.html)
+ [PutGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutGroupPolicy.html)
+ [PutRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)

**To detach a managed policy used as a permissions policy \(AWS API\)**

1. \(Optional\) To view information about a policy, call the following operations:
   + To list managed policies: [ListPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)
   + To retrieve detailed information about a managed policy: [GetPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html)

1. \(Optional\) To find out about the relationships between the policies and identities, call the following operations:
   + To list the identities \(users, groups, and roles\) to which a managed policy is attached:
     + [ListEntitiesForPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListEntitiesForPolicy.html)
   + To list the managed policies attached to an identity \(a user, group, or role\), call one of the following operations:
     + [ListAttachedUserPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html)
     + [ListAttachedGroupPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedGroupPolicies.html)
     + [ListAttachedRolePolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedRolePolicies.html)

1. To detach a managed policy from an identity \(user, group, or role\), call one of the following operations:
   + [DetachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachUserPolicy.html)
   + [DetachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachGroupPolicy.html)
   + [DetachRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachRolePolicy.html)

**To remove a permissions boundary \(AWS API\)**

1. \(Optional\) To view which managed policy is currently used to set the permissions boundary for a user or role, call the following operations:
   + [GetUser](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html)
   + [GetRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html)

1. \(Optional\) To view the users or roles on which a managed policy is used for a permissions boundary, call the following operation:
   + [ListEntitiesForPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListEntitiesForPolicy.html)

1. \(Optional\) To view information about a managed policy, call the following operations:
   + To list managed policies: [ListPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)
   + To retrieve detailed information about a managed policy: [GetPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html)

1. To remove a permissions boundary from a user or role, call one of the following operations:
   + [DeleteUserPermissionsBoundary](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUserPermissionsBoundary.html)
   + [DeleteRolePermissionsBoundary](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteRolePermissionsBoundary.html)

**To delete an inline policy \(AWS API\)**

1. \(Optional\) To list all inline policies that are attached to an identity \(user, group, role\), call one of the following operations:
   + [ListUserPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserPolicies.html)
   + [ListGroupPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupPolicies.html)
   + [ListRolePolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRolePolicies.html)

1. \(Optional\) To retrieve an inline policy document that is embedded in an identity \(user, group, or role\), call one of the following operations:
   + [GetUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUserPolicy.html)
   + [GetGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroupPolicy.html)
   + [GetRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRolePolicy.html)

1. To delete an inline policy from an identity \(user, group, or role that is not a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\), call one of the following operations:
   + [DeleteUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUserPolicy.html)
   + [DeleteGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteGroupPolicy.html)
   + [DeleteRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteRolePolicy.html)