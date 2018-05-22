# Attaching and Detaching IAM Policies<a name="access_policies_manage-attach-detach"></a>

You can attach and detach managed policies and embed and delete inline policies using the AWS Management Console, the AWS Command Line Interface \(AWS CLI\), or the AWS API\.

For more information about the difference between managed and inline policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\. 

For general information about IAM policies, see [IAM Policies](access_policies.md)\.

For information about policy size limitations and other quotas, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.

**Topics**
+ [Attaching IAM Policies \(Console\)](#attach-managed-policy-console)
+ [Embedding Inline Policies \(Console\)](#embed-inline-policy-console)
+ [Detaching IAM Policies \(Console\)](#detach-managed-policy-console)
+ [Attaching or Detaching IAM Policies \(AWS CLI or AWS API\)](#attach-detach-managed-policy-cli-api)

## Attaching IAM Policies \(Console\)<a name="attach-managed-policy-console"></a>

You can use the AWS Management Console to attach a managed policy to an identity \(a user, group, or role\)\. Attaching a policy applies the permissions in the policy to the identity\.

**To attach a managed policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\. 

1. In the list of policies, select the check box next to the name of the policy to attach\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose **Policy actions**, and then choose **Attach**\.

1. Select one or more identities to attach the policy to\. You can use the **Filter** menu and the search box to filter the list of principal entities\. After selecting the identities, choose **Attach policy**\.

## Embedding Inline Policies \(Console\)<a name="embed-inline-policy-console"></a>

You can use the AWS Management Console to embed an inline policy in an identity \(a user, group, or role\)\. Embedding a policy applies the permissions in the policy to the identity\. Because an inline policy is stored in the identity, it is embedded rather than attached, though the concept is similar\.

**To embed an inline policy for a user or role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users** or **Roles**\.

1. In the list, choose the name of the user or role to embed a policy in\.

1. Choose the **Permissions** tab\. 

1. Scroll to the bottom of the page and choose **Add inline policy**\.
**Note**  
You cannot embed an inline policy in a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* in IAM\. Because the linked service defines whether you can modify the permissions of the role, you might be able to add additional policies from the service console, API, or AWS CLI\. To view the service\-linked role documentation for a service, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and choose **Yes** in the **Service\-Linked Role** column for your service\.

1. Choose from the following methods to view the steps required to create your policy:
   + [Import an Existing Managed Policy](access_policies_create.md#access_policies_create-copy) – You can import a managed policy within your account and then edit the policy to customize it to your specific requirements\. A managed policy can be an AWS managed policy or a customer managed policy that you created previously\.
   + [Create a Policy with the Visual Editor](access_policies_create.md#access_policies_create-visual-editor) – You can construct a new policy from scratch in the visual editor\. If you use the visual editor, you do not have to understand JSON syntax\.
   + [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor) – In the **JSON** tab, you can use JSON syntax to create a policy\. You can type a new JSON policy document or paste an [example policy](access_policies_examples.md)\.

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
+ AWS CLI: [list\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-policies.html)
+ AWS API: [ListPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPolicies.html)

**To retrieve detailed information about a managed policy \(AWS CLI or API\)**
+ AWS CLI: [get\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html)
+ AWS API: [GetPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html)

**To list the identities \(users, groups, and roles\) to which a managed policy is attached \(AWS CLI or API\)**
+ AWS CLI: [list\-entities\-for\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/list-entities-for-policy.html)
+ AWS API: [ListEntitiesForPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListEntitiesForPolicy.html)

**To list the managed policies attached to an identity \(a user, group, or role\) \(AWS CLI or API\)**
+ AWS CLI: 
  + [list\-attached\-group\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html)
  + [list\-attached\-role\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html)
  + [list\-attached\-user\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-user-policies.html)
+ AWS API: 
  + [ListAttachedGroupPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedGroupPolicies.html)
  + [ListAttachedRolePolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedRolePolicies.html)
  + [ListAttachedUserPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html)

**To list all inline policies that are attached to an identity \(user, group, or role\) \(AWS CLI or API\)**
+ AWS CLI: 
  + [list\-group\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-group-policies.html)
  + [list\-role\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-role-policies.html)
  + [list\-user\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-user-policies.html)
+ AWS API:
  + [ListGroupPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupPolicies.html)
  + [ListRolePolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRolePolicies.html)
  + [ListUserPolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserPolicies.html)

**To retrieve an inline policy document that is embedded in an identity \(user, group, or role\) \(AWS CLI or API\)**
+ AWS CLI:
  + [get\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-group-policy.html)
  + [get\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role-policy.html)
  + [get\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-user-policy.html)
+ AWS API:
  + [GetGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroupPolicy.html)
  + [GetRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRolePolicy.html)
  + [GetUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUserPolicy.html)

**To attach a managed policy to an identity \(user, group, or role\) \(AWS CLI or API\)**
+ AWS CLI: 
  + [attach\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html)
  + [attach\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-role-policy.html)
  + [attach\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-user-policy.html)
+ AWS API: 
  + [AttachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachGroupPolicy.html)
  + [AttachRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html)
  + [AttachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachUserPolicy.html)

**To detach a managed policy from an identity \(user, group, or role\) \(AWS CLI or API\)**
+ AWS CLI: 
  + [detach\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-group-policy.html)
  + [detach\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-role-policy.html)
  + [detach\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/detach-user-policy.html)
+ AWS API: 
  + [DetachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachGroupPolicy.html)
  + [DetachRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachRolePolicy.html)
  + [DetachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachUserPolicy.html)

**To embed an inline policy in an identity \(user, group, or role\) \(AWS CLI or API\)**
+ AWS CLI:
  + [put\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-group-policy.html)
  + [put\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)
  + [put\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-user-policy.html)
+ AWS API:
  + [PutGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutGroupPolicy.html)
  + [PutRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)
  + [PutUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutUserPolicy.html)

**Note**  
You can embed an inline policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* only in the service that depends on the role\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.

**To detach and delete an inline policy from an identity \(user, group, or role\)**
+ AWS CLI:
  + [delete\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-group-policy.html)
  + [delete\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-role-policy.html)
  + [delete\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-user-policy.html)

**Note**  
You can delete an inline policy from a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* only in the service that depends on the role\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.