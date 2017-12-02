# Attaching and Detaching IAM Policies<a name="access_policies_manage-attach-detach"></a>

You can attach and detach managed policies and embed and delete inline policies using the AWS Management Console, the AWS Command Line Interface \(AWS CLI\), or the AWS API\.

For more information about the difference between managed and inline policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\. 

For general information about IAM policies, see [IAM Policies](access_policies.md)\.

For information about policy size limitations and other quotas, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.


+ [Attaching IAM Policies \(Console\)](#attach-managed-policy-console)
+ [Detaching IAM Policies \(Console\)](#detach-managed-policy-console)
+ [Attaching or Detaching IAM Policies \(AWS CLI or AWS API\)](#attach-detach-managed-policy-cli-api)

## Attaching IAM Policies \(Console\)<a name="attach-managed-policy-console"></a>

You can use the AWS Management Console to attach a managed policy to an identity \(a user, group, or role\)\. Attaching a policy applies its permissions in the policy to the identity\. Because an inline policy is stored on the identity, it is embedded rather than attached, though it is a similar concept\.

**To attach a managed policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\. 

1. In the list of policies, select the check box next to the name of the policy to attach\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose **Policy actions**, and then choose **Attach**\.

1. Select one or more identities to attach the policy to\. You can use the **Filter** menu and the search box to filter the list of principal entities\. After selecting the identities, choose **Attach policy**\.

**To embed an inline policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups**, **Users**, or **Roles**\.

1. In the list, choose the name of the group, user, or role to embed a policy in\.

1. Choose the **Permissions** tab\. If you chose **Groups**, expand the **Inline Policies** section if necessary\.

1. If in **Groups**, choose **Create Group Policy**\. If in **Users** or **Roles**, scroll to the bottom of the page and choose **Add inline policy**\. If there are no existing policies in **Groups**, instead choose **click here** to create your first inline policy\.
**Note**  
You cannot embed an inline policy in a *service\-linked role* in IAM\. Because the linked service defines whether you can modify the permissions of the role, you might be able to add additional policies from the service console, API, or CLI\. To view the service\-linked role documentation for a service, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and choose **Yes** in the **Service\-Linked Role** column for your service\.

1. Choose **Policy Generator** or **Custom Policy**, and then choose **Select**\. 

1. Do one of the following:

   + If you chose **Custom Policy**, specify a name for the policy and create your policy document\. Policy Validator reports any syntax errors\.

   + If you are using the policy generator to create your policy, select the appropriate **Effect**, **AWS Service**, and **Actions** options\. Type the Amazon Resource Name \(ARN\) \(if applicable\), and add any conditions that you want to include\. Then choose **Add Statement**\. You can add as many statements as you want to the policy\. When you are finished adding statements, choose **Next Step**\. 

1. When you are satisfied with the policy, choose **Apply Policy**\.

## Detaching IAM Policies \(Console\)<a name="detach-managed-policy-console"></a>

You can use the AWS Management Console to detach a managed policy from a principal entity \(a user, group, or role\)\. Detaching a policy removes its permissions from the principal entity\.

**To detach a managed policy \(Console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\. 

1. In the list of policies, select the check box next to the name of the policy to detach\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose **Policy actions**, and then choose **Detach**\.

1. Select the identities to detach the policy from\. You can use the **Filter** menu and the search box to filter the list of identities\. After selecting the identities, choose **Detach policy**\.

**To detach and delete an inline policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups**, **Users**, or **Roles**\.

1. In the list, choose the name of the group, user, or role that has the policy you want to remove\.

1. Choose the **Permissions** tab\. If you chose **Groups**, expand the **Inline Policies** section if necessary\.

1. If in **Groups**, choose **Remove Policy**\. If in **Users** or **Roles**, choose **X**\.

## Attaching or Detaching IAM Policies \(AWS CLI or AWS API\)<a name="attach-detach-managed-policy-cli-api"></a>

You can attach or detach managed policies and embed or delete inline policies using the AWS Command Line Interface \(AWS CLI\) or the AWS API\. The following information applies to both managed and inline policies\.

**To list managed policies \(AWS CLI or API\)**

+ AWS CLI: [list\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-policies.html)

+ AWS API: [ListPolicies](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)

**To retrieve detailed information about a managed policy \(AWS CLI or API\)**

+ AWS CLI: [get\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/get-policy.html)

+ AWS API: [GetPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html)

**To list the identities \(users, groups, and roles\) to which a managed policy is attached \(AWS CLI or API\)**

+ AWS CLI: [list\-entities\-for\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-entities-for-policy.html)

+ AWS API: [ListEntitiesForPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListEntitiesForPolicy.html)

**To list the managed policies attached to an identity \(a user, group, or role\) \(AWS CLI or API\)**

+ AWS CLI: 

  + [list\-attached\-group\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html)

  + [list\-attached\-role\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html)

  + [list\-attached\-user\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-attached-user-policies.html)

+ AWS API: 

  + [ListAttachedGroupPolicies](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListAttachedGroupPolicies.html)

  + [ListAttachedRolePolicies](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListAttachedRolePolicies.html)

  + [ListAttachedUserPolicies](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html)

**To list all inline policies that are attached to an identity \(user, group, or role\) \(AWS CLI or API\)**

+ AWS CLI: 

  + [list\-group\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-group-policies.html)

  + [list\-role\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-role-policies.html)

  + [list\-user\-policies](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/list-user-policies.html)

+ AWS API:

  + [ListGroupPolicies](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListGroupPolicies.html)

  + [ListRolePolicies](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListRolePolicies.html)

  + [ListUserPolicies](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_ListUserPolicies.html)

**To retrieve an inline policy document that is embedded in an identity \(user, group, or role\) \(AWS CLI or API\)**

+ AWS CLI:

  + [get\-group\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/get-group-policy.html)

  + [get\-role\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/get-role-policy.html)

  + [get\-user\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/get-user-policy.html)

+ AWS API:

  + [GetGroupPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_GetGroupPolicy.html)

  + [GetRolePolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_GetRolePolicy.html)

  + [GetUserPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_GetUserPolicy.html)

**To attach a managed policy to an identity \(user, group, or role\) \(AWS CLI or API\)**

+ AWS CLI: 

  + [attach\-group\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html)

  + [attach\-role\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/attach-role-policy.html)

  + [attach\-user\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/attach-user-policy.html)

+ AWS API: 

  + [AttachGroupPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_AttachGroupPolicy.html)

  + [AttachRolePolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html)

  + [AttachUserPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_AttachUserPolicy.html)

**To detach a managed policy from an identity \(user, group, or role\) \(AWS CLI or API\)**

+ AWS CLI: 

  + [detach\-group\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/detach-group-policy.html)

  + [detach\-role\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/detach-role-policy.html)

  + [detach\-user\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/detach-user-policy.html)

+ AWS API: 

  + [DetachGroupPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_DetachGroupPolicy.html)

  + [DetachRolePolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_DetachRolePolicy.html)

  + [DetachUserPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_DetachUserPolicy.html)

**To embed an inline policy in an identity \(user, group, or role\) \(AWS CLI or API\)**

+ AWS CLI:

  + [put\-group\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/put-group-policy.html)

  + [put\-role\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)

  + [put\-user\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/put-user-policy.html)

+ AWS API:

  + [PutGroupPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_PutGroupPolicy.html)

  + [PutRolePolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)

  + [PutUserPolicy](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_PutUserPolicy.html)

**Note**  
You can embed an inline policy for a *service\-linked role* only in the service that depends on the role\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.

**To detach and delete an inline policy from an identity \(user, group, or role\)**

+ AWS CLI:

  + [delete\-group\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/delete-group-policy.html)

  + [delete\-role\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/delete-role-policy.html)

  + [delete\-user\-policy](http://alpha-docs-aws.amazon.com/cli/latest/reference/iam/delete-user-policy.html)

**Note**  
You can delete an inline policy from a *service\-linked role* only in the service that depends on the role\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.