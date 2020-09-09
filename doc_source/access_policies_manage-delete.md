# Deleting IAM policies<a name="access_policies_manage-delete"></a>

You can delete IAM policies using the AWS Management Console, the AWS Command Line Interface \(AWS CLI\), or the IAM API\.

For more information about the difference between managed and inline policies, see [Managed policies and inline policies](access_policies_managed-vs-inline.md)\. 

For general information about IAM policies, see [Policies and permissions in IAM](access_policies.md)\.

The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\.

**Topics**
+ [View policy access](#manage-delete_prerequisites)
+ [Deleting IAM policies \(console\)](#delete-managed-policy)
+ [Deleting IAM policies \(AWS CLI\)](#delete-policies-cli-api)
+ [Deleting IAM policies \(AWS API\)](#delete-policies-api)

## View policy access<a name="manage-delete_prerequisites"></a>

Before you delete a policy, you should review its recent service\-level activity\. This is important because you don't want to remove access from a principal \(person or application\) who is using it\. For more information about viewing last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

## Deleting IAM policies \(console\)<a name="delete-managed-policy"></a>

You can delete a customer managed policy to remove it from your AWS account\. You cannot delete AWS managed policies\.

**To delete a customer managed policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. Select the check box next to the customer managed policy to delete\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose **Policy actions**, and then choose **Delete**\.

1. Confirm that you want to delete the policy, and then choose **Delete**\.

**To delete an inline policy for a group, user, or role \(console\)**

1. In the navigation pane, choose **Groups**, **Users**, or **Roles**\.

1. Choose the name of the group, user, or role with the policy that you want to delete\. Then choose the **Permissions** tab\. If you chose **Users** or **Roles**, expand the policy\.

1. To delete an inline policy in **Groups**, choose **Remove Policy**\. To delete an inline policy in **Users** or **Roles**, choose **X**\. 

## Deleting IAM policies \(AWS CLI\)<a name="delete-policies-cli-api"></a>

You can delete a customer managed policy from the AWS Command Line Interface\.

**To delete a customer managed policy \(AWS CLI\)**

1. \(Optional\) To view information about a policy, run the following commands:
   + To list managed policies: [list\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)
   + To retrieve detailed information about a managed policy: [get\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html)

1. \(Optional\) To find out about the relationships between the policies and identities, run the following commands:
   + To list the identities \(users, groups, and roles\) to which a managed policy is attached, run the following command: 
     + [list\-entities\-for\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/list-entities-for-policy.html)
   + To list the managed policies attached to an identity \(a user, group, or role\), run one of the following commands:
     + [list\-attached\-user\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-user-policies.html)
     + [list\-attached\-group\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html)
     + [list\-attached\-role\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html)

1. To delete a customer managed policy, run the following command:
   + [delete\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-policy.html)

**To delete an inline policy \(AWS CLI\)**

1. \(Optional\) To list all inline policies that are attached to an identity \(user, group, role\), use one of the following commands:
   + [aws iam list\-user\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-user-policies.html)
   + [aws iam list\-group\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-group-policies.html)
   + [aws iam list\-role\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-role-policies.html)

1. \(Optional\) To retrieve an inline policy document that is embedded in an identity \(user, group, or role\), use one of the following commands:
   + [aws iam get\-user\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/get-user-policy.html)
   + [aws iam get\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/get-group-policy.html)
   + [aws iam get\-role\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role-policy.html)

1. To delete an inline policy from an identity \(user, group, or role that is not a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\), use one of the following commands:
   + [aws iam delete\-user\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-user-policy.html)
   + [aws iam delete\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-group-policy.html)
   + [aws iam delete\-role\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-role-policy.html)

## Deleting IAM policies \(AWS API\)<a name="delete-policies-api"></a>

You can delete a customer managed policy using the AWS API\.

**To delete a customer managed policy \(AWS API\)**

1. \(Optional\) To view information about a policy, call the following operations:
   + To list managed policies: [ListPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)
   + To retrieve detailed information about a managed policy: [GetPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html)

1. \(Optional\) To find out about the relationships between the policies and identities, call the following operations:
   + To list the identities \(users, groups, and roles\) to which a managed policy is attached, call the following operation: 
     + [ListEntitiesForPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListEntitiesForPolicy.html)
   + To list the managed policies attached to an identity \(a user, group, or role\), call one of the following operations:
     + [ListAttachedUserPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html)
     + [ListAttachedGroupPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedGroupPolicies.html)
     + [ListAttachedRolePolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedRolePolicies.html)

1. To delete a customer managed policy, call the following operation:
   + [DeletePolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeletePolicy.html)

**To delete an inline policy \(AWS API\)**

1. \(Optional\) To list all inline policies that are attached to an identity \(user, group, role\), call one of the following operations:
   + [ListUserPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserPolicies.html)
   + [ListGroupPolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupPolicies.html)
   + [ListRolePolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRolePolicies.html)

1. \(Optional\) To retrieve an inline policy document that is embedded in an identity \(user, group, or role\), call one of the following operations:
   + [GetUserPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUserPolicy.html)
   + [GetGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroupPolicy.html)
   + [GetRolePolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRolePolicy.html)

1. To delete an inline policy from an identity \(user, group, or role that is not a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\), call one of the following operations:
   + [DeleteUserPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUserPolicy.html)
   + [DeleteGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteGroupPolicy.html)
   + [DeleteRolePolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteRolePolicy.html)