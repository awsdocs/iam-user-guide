# Editing IAM policies<a name="access_policies_manage-edit"></a>

A [policy](access_policies.md) is an entity that, when attached to an identity or resource, defines their permissions\. Policies are stored in AWS as JSON documents and are attached to principals as *identity\-based policies* in IAM\. You can attach an identity\-based policy to a principal \(or identity\), such as an IAM group, user, or role\. Identity\-based policies include AWS managed policies, customer managed policies, and [inline policies](access_policies_managed-vs-inline.md)\. You can edit customer managed policies and inline policies in IAM\. AWS managed policies cannot be edited\. The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\.

**Topics**
+ [View policy access](#manage-edit_prerequisites)
+ [Editing customer managed policies \(console\)](#edit-managed-policy-console)
+ [Editing inline policies \(console\)](#edit-inline-policy-console)
+ [Editing customer managed policies \(AWS CLI\)](#edit-policies-cli-api)
+ [Editing customer managed policies \(AWS API\)](#edit-policies-api)

## View policy access<a name="manage-edit_prerequisites"></a>

Before you change the permissions for a policy, you should review its recent service\-level activity\. This is important because you don't want to remove access from a principal \(person or application\) who is using it\. For more information about viewing last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

## Editing customer managed policies \(console\)<a name="edit-managed-policy-console"></a>

You can edit customer managed policies to change the permissions that are defined in the policy\. A customer managed policy can have up to five versions\. This is important because if you make changes to a managed policy beyond five versions, the AWS Management Console prompts you to decide which version to delete\. You can also change the default version or delete a version of a policy before you edit it to avoid being prompted\. To learn more about versions, see [Versioning IAM policies](access_policies_managed-versioning.md)\.

**To edit a customer managed policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. In the list of policies, choose the policy name of the policy to edit\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose the **Permissions** tab, and then choose **Edit policy**\. 

1. Do one of the following:
   + Choose the **Visual editor** tab to change your policy without understanding JSON syntax\. You can make changes to the service, actions, resources, or optional conditions for each permission block in your policy\. You can also import a policy to add additional permissions to the bottom of your policy\. When you are finished making changes, choose **Review policy** to continue\.
   + Choose the **JSON** tab to modify your policy by typing or pasting text in the JSON text box\. You can also import a policy to add additional permissions to the bottom of your policy\. When you are finished making changes, choose **Review policy** to continue\. [Policy Validator](access_policies_policy-validator.md) reports any syntax errors\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review** page, review the policy **Summary** and then choose **Save changes** to save your work\.

1. If the managed policy already has the maximum of five versions, choosing **Save** displays a dialog box\. To save your new version, you must remove at least one earlier version\. You cannot delete the default version\. Choose from the following options:
   + **Remove oldest non\-default policy version \(version v\# \- created \# days ago\)** – Use this option to see which version will be deleted and when it was created\. You can view the JSON policy document for all nondefault versions by choosing the second option, **Select versions to remove**\. 
   + **Select versions to remove** – Use this option to view the JSON policy document and choose one or more versions to delete\.

   After choosing the versions to remove, choose **Delete version and save** to save your new policy version\.

**To set the default version of a customer managed policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. In the list of policies, choose the policy name of the policy to set the default version of\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose the **Policy versions** tab\. Select the check box next to the version that you want to set as the default version, and then choose **Set as default**\.

**To delete a version of a customer managed policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. Choose the name of the customer managed policy that has a version you want to delete\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose the **Policy versions** tab\. Select the check box next to the version that you want to delete\. Then choose **Delete**\.

1. Confirm that you want to delete the version, and then choose **Delete**\.

## Editing inline policies \(console\)<a name="edit-inline-policy-console"></a>

You can edit an inline policy from the AWS Management Console\.

**To edit an inline policy for a user or role \(console\)**

1. In the navigation pane, choose **Users** or **Roles**\.

1. Choose the name of the user or role with the policy that you want to modify\. Then choose the **Permissions** tab and expand the policy\.

1. To edit an inline policy, choose **Edit Policy**\. 

1. Do one of the following:
   + Choose the **Visual editor** tab to change your policy without understanding JSON syntax\. You can make changes to the service, actions, resources, or optional conditions for each permission block in your policy\. You can also import a policy to add additional permissions to the bottom of your policy\. When you are finished making changes, choose **Review policy** to continue\.
   + Choose the **JSON** tab to modify your policy by typing or pasting text in the JSON text box\. You can also import a policy to add additional permissions to the bottom of your policy\. When you are finished making changes, choose **Review policy** to continue\. [Policy Validator](access_policies_policy-validator.md) reports any syntax errors\. To save your changes without affecting the currently attached entities, clear the check box for **Save as default version**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review** page, review the policy **Summary** and then choose **Save changes** to save your work\.

**To edit an inline policy for a group \(console\)**

1. In the navigation pane, choose **Groups**\.

1. Choose the name of the group with the policy that you want to modify\. Then choose the **Permissions** tab\.

1. To edit an inline policy, choose **Edit Policy**\. 

1. After you have modified your JSON policy, choose **Save** to save your changes\.

## Editing customer managed policies \(AWS CLI\)<a name="edit-policies-cli-api"></a>

You can edit a customer managed policy from the AWS Command Line Interface \(AWS CLI\)\.

**Note**  
A managed policy can have up to five versions\. If you need to make changes to a customer managed policy beyond five versions, you must first delete one or more existing versions\.

**To edit a customer managed policy \(AWS CLI\)**

1. \(Optional\) To view information about a policy, run the following commands:
   + To list managed policies: [list\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)
   + To retrieve detailed information about a managed policy: [get\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html)

1. \(Optional\) To find out about the relationships between the policies and identities, run the following commands:
   + To list the identities \(users, groups, and roles\) to which a managed policy is attached: 
     + [list\-entities\-for\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/list-entities-for-policy.html)
   + To list the managed policies attached to an identity \(a user, group, or role\):
     + [list\-attached\-user\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-user-policies.html)
     + [list\-attached\-group\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html)
     + [list\-attached\-role\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html)

1. To edit a customer managed policy, run the following command:
   + [create\-policy\-version](https://docs.aws.amazon.com/cli/latest/reference/iam/create-policy-version.html)

**To set the default version of a customer managed policy \(AWS CLI\)**

1. \(Optional\) To list managed policies, run the following command:
   + [list\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)

1. To set the default version of a customer managed policy, run the following command:
   + [set\-default\-policy\-version](https://docs.aws.amazon.com/cli/latest/reference/iam/set-default-policy-version.html)

**To delete a version of a customer managed policy \(AWS CLI\)**

1. \(Optional\) To list managed policies, run the following command:
   + [list\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)

1. To delete a customer managed policy, run the following command:
   + [delete\-policy\-version](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-policy-version.html)

## Editing customer managed policies \(AWS API\)<a name="edit-policies-api"></a>

You can edit a customer managed policy using the AWS API\.

**Note**  
A managed policy can have up to five versions\. If you need to make changes to a customer managed policy beyond five versions, you must first delete one or more existing versions\.

**To edit a customer managed policy \(AWS API\)**

1. \(Optional\) To view information about a policy, call the following operations:
   + To list managed policies: [ListPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)
   + To retrieve detailed information about a managed policy: [GetPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html)

1. \(Optional\) To find out about the relationships between the policies and identities, call the following operations:
   + To list the identities \(users, groups, and roles\) to which a managed policy is attached: 
     + [ListEntitiesForPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListEntitiesForPolicy.html)
   + To list the managed policies attached to an identity \(a user, group, or role\):
     + [ListAttachedUserPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html)
     + [ListAttachedGroupPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedGroupPolicies.html)
     + [ListAttachedRolePolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedRolePolicies.html)

1. To edit a customer managed policy, call the following operation:
   + [CreatePolicyVersion](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicyVersion.html)

**To set the default version of a customer managed policy \(AWS API\)**

1. \(Optional\) To list managed policies, call the following operation:
   + [ListPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)

1. To set the default version of a customer managed policy, call the following operation:
   + [SetDefaultPolicyVersion](https://docs.aws.amazon.com/IAM/latest/APIReference/API_SetDefaultPolicyVersion.html)

**To delete a version of a customer managed policy \(AWS API\)**

1. \(Optional\) To list managed policies, call the following operation:
   + [ListPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)

1. To delete a customer managed policy, call the following operation:
   + [DeletePolicyVersion](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeletePolicyVersion.html)