# Deleting IAM Policies<a name="access_policies_manage-delete"></a>

You can delete IAM policies using the AWS Management Console, the AWS Command Line Interface \(AWS CLI\), or the IAM API\.

For more information about the difference between managed and inline policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\. 

For general information about IAM policies, see [Policies and Permissions](access_policies.md)\.

For information about policy size limitations and other quotas, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.

**Topics**
+ [Deleting Customer Managed Policies \(Console\)](#delete-managed-policy)
+ [Deleting IAM Policies \(AWS CLI\)](#delete-policies-cli-api)
+ [Deleting IAM Policies \(AWS API\)](#delete-policies-api)

## Deleting Customer Managed Policies \(Console\)<a name="delete-managed-policy"></a>

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

## Deleting IAM Policies \(AWS CLI\)<a name="delete-policies-cli-api"></a>

You can edit a customer managed policy from the AWS Command Line Interface\.

**To edit a customer managed policy \(AWS CLI\)**

1. \(Optional\) To view information about a policy, run the following commands:
   + To list managed policies: [list\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)
   + To retrieve detailed information about a managed policy: [get\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html)

1. \(Optional\) To find out about the relationships between the policies and identities, run the following commands:
   + To list the identities \(users, groups, and roles\) to which a managed policy is attached: 
     + [list\-entities\-for\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-entities-for-policy.html)
   + To list the managed policies attached to an identity \(a user, group, or role\), use one of the following commands:
     + [list\-attached\-user\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-attached-user-policies.html)
     + [list\-attached\-group\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html)
     + [list\-attached\-role\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html)

1. To delete a customer managed policy, run the following command:
   + [delete\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-policy.html)

## Deleting IAM Policies \(AWS API\)<a name="delete-policies-api"></a>

You can delete a customer managed policy using the AWS API\.

**To edit a customer managed policy \(AWS API\)**

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

1. To delete a customer managed policy, call the following operation:
   + [DeletePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeletePolicy.html)