# Troubleshooting IAM roles<a name="troubleshoot_roles"></a>

Use the information here to help you diagnose and fix common issues that you might encounter when working with IAM roles\.

**Topics**
+ [I can't assume a role](#troubleshoot_roles_cant-assume-role)
+ [A new role appeared in my AWS account](#troubleshoot_roles_new-role-appeared)
+ [I can't edit or delete a role in my AWS account](#troubleshoot_roles_cant-edit-delete-role)
+ [I'm not authorized to perform: iam:PassRole](#troubleshoot_roles_not-auth-passrole)
+ [Why can't I assume a role with a 12\-hour session? \(AWS CLI, AWS API\)](#troubleshoot_roles_cant-set-session)
+ [I receive an error when I try to switch roles in the IAM console](#troubleshoot_roles_cant-switch-role-console)
+ [My role has a policy that allows me to perform an action, but I get "access denied"](#troubleshoot_roles_session-policy)
+ [The service did not create the role's default policy version](#troubleshoot_serviceroles_edited-policy)

## I can't assume a role<a name="troubleshoot_roles_cant-assume-role"></a>

Check the following:
+ Make sure to use the exact name of your role, because role names are case sensitive\.
+ Verify that your IAM policy grants you permission to call `sts:AssumeRole` for the role that you want to assume\. The `Action` element of your IAM policy must allow you to call the `AssumeRole` action\. In addition, the `Resource` element of your IAM policy must specify the role that you want to assume\. For example, the `Resource` element can specify a role by its Amazon Resource Name \(ARN\) or by a wildcard \(\*\)\. For example, at least one policy applicable to you must grant permissions similar to the following:

  ```
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Resource": "arn:aws:iam::account_id_number:role/role-name-you-want-to-assume"
  ```
+ Verify that your IAM identity is tagged with any tags that the IAM policy requires\. For example, in the following policy permissions, the `Condition` element requires that you, as the principal requesting to assume the role, must have a specific tag\. You must be tagged with `department = HR` or `department = CS`\. Otherwise, you cannot assume the role\. To learn about tagging IAM users and roles, see [Tagging IAM users and roles](id_tags.md)\.

  ```
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Resource": "*",
      "Condition": {"StringEquals": {"aws:PrincipalTag/department": [
              "HR",
              "CS"
          ]}}
  ```
+ Verify that you meet all the conditions that are specified in the role's trust policy\. A `Condition` can specify an expiration date, an external ID, or that a request must come only from specific IP addresses\. Consider the following example: If the current date is any time after the specified date, then the policy never matches and cannot grant you the permission to assume the role\.

  ```
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Resource": "arn:aws:iam::account_id_number:role/role-name-you-want-to-assume"
      "Condition": {
          "DateLessThan" : {
              "aws:CurrentTime" : "2016-05-01T12:00:00Z"
          }
      }
  ```
+ Verify that the AWS account from which you are calling `AssumeRole` is a trusted entity for the role that you are assuming\. Trusted entities are defined as a `Principal` in a role's trust policy\. The following example is a trust policy that is attached to the role that you want to assume\. In this example, the account ID with the IAM user that you signed in with must be 123456789012\. If your account number is not listed in the `Principal` element of the role's trust policy, then you cannot assume the role\. It does not matter what permissions are granted to you in access policies\. Note that the example policy limits permissions to actions that occur between July 1, 2017 and December 31, 2017 \(UTC\), inclusive\. If you log in before or after those dates, then the policy does not match, and you cannot assume the role\. 

  ```
      "Effect": "Allow",
      "Principal": { "AWS": "arn:aws:iam::123456789012:root" },
      "Action": "sts:AssumeRole",
      "Condition": {
        "DateGreaterThan": {"aws:CurrentTime": "2017-07-01T00:00:00Z"},
        "DateLessThan": {"aws:CurrentTime": "2017-12-31T23:59:59Z"}
      }
  ```

## A new role appeared in my AWS account<a name="troubleshoot_roles_new-role-appeared"></a>

Some AWS services require that you use a unique type of service role that is linked directly to the service\. This [service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role) is predefined by the service and includes all the permissions that the service requires\. This makes setting up a service easier because you don't have to manually add the necessary permissions\. For general information about service\-linked roles, see [Using service\-linked roles](using-service-linked-roles.md)\.

You might already be using a service when it begins supporting service\-linked roles\. If so, you might receive an email telling you about a new role in your account\. This role includes all the permissions that the service needs to perform actions on your behalf\. You don't need to take any action to support this role\. However, you should not delete the role from your account\. Doing so could remove permissions that the service needs to access AWS resources\. You can view the service\-linked roles in your account by going to the IAM **Roles** page of the IAM console\. Service\-linked roles appear with **\(Service\-linked role\)** in the **Trusted entities** column of the table\.

For information about which services support service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. For information about using the service\-linked role for a service, choose the **Yes** link\.

## I can't edit or delete a role in my AWS account<a name="troubleshoot_roles_cant-edit-delete-role"></a>

You cannot delete or edit the permissions for a [service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role) in IAM\. These roles include predefined trusts and permissions that are required by the service in order to perform actions on your behalf\. You can use the IAM console, AWS CLI, or API to edit only the description of a service\-linked role\. You can view the service\-linked roles in your account by going to the IAM **Roles** page in the console\. Service\-linked roles appear with **\(Service\-linked role\)** in the **Trusted entities** column of the table\. A banner on the role's **Summary** page also indicates that the role is a service\-linked role\. You can manage and delete these roles only through the linked service, if that service supports the action\. Be careful when modifying or deleting a service\-linked role because doing so could remove permissions that the service needs to access AWS resources\. 

For information about which services support service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. 

## I'm not authorized to perform: iam:PassRole<a name="troubleshoot_roles_not-auth-passrole"></a>

When you create a service\-linked role, you must have permission to pass that role to the service\. Some services automatically create a service\-linked role in your account when you perform an action in that service\. For example, Amazon EC2 Auto Scaling creates the `AWSServiceRoleForAutoScaling` service\-linked role for you the first time that you create an Auto Scaling group\. If you try to create an Auto Scaling group without the `PassRole` permission, you receive the following error:

`ClientError: An error occurred (AccessDenied) when calling the PutLifecycleHook operation: User: arn:aws:sts::111122223333:assumed-role/Testrole/Diego is not authorized to perform: iam:PassRole on resource: arn:aws:iam::111122223333:role/aws-service-role/autoscaling.amazonaws.com/AWSServiceRoleForAutoScaling`

To fix this error, ask your administrator to add the `iam:PassRole` permission for you\.

To learn which services support service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. To learn whether a service automatically creates a service\-linked role for you, choose the **Yes** link to view the service\-linked role documentation for the service\.

## Why can't I assume a role with a 12\-hour session? \(AWS CLI, AWS API\)<a name="troubleshoot_roles_cant-set-session"></a>

When you use the AWS STS `AssumeRole*` API or `assume-role*` CLI operations to assume a role, you can specify a value for the `DurationSeconds` parameter\. You can specify a value from 900 seconds \(15 minutes\) up to the **Maximum session duration** setting for the role\. If you specify a value higher than this setting, the operation fails\. This setting can have a maximum value of 12 hours\. For example, if you specify a session duration of 12 hours, but your administrator set the maximum session duration to 6 hours, your operation fails\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\. 

If you use [*role chaining*](id_roles_terms-and-concepts.md#iam-term-role-chaining) \(using a role to assume a second role\), your session is limited to a maximum of one hour\. If you then use the `DurationSeconds` parameter to provide a value greater than one hour, the operation fails\. 

## I receive an error when I try to switch roles in the IAM console<a name="troubleshoot_roles_cant-switch-role-console"></a>

The information you enter on the **Switch Role** page must match the information for the role\. Otherwise, the operation fails and you receive the following error:

`Invalid information in one or more fields. Check your information or contact your administrator.`

If you receive this error, confirm that the following information is correct:
+ **Account ID or alias** – The AWS account ID is a 12\-digit number\. Your account might have an alias, which is a friendly identifier such as your company name that can be used instead of your AWS account ID\. You can use either the account ID or the alias in this field\.
+ **Role name** – Role names are case sensitive\. The account ID and role name must match what is configured for the role\.

If you continue to receive an error message, contact your administrator to verify the previous information\. The role trust policy or the IAM user policy might limit your access\. Your administrator can verify the permissions for these policies\.

## My role has a policy that allows me to perform an action, but I get "access denied"<a name="troubleshoot_roles_session-policy"></a>

Your role session might be limited by session policies\. When you [request temporary security credentials](id_credentials_temp_request.md) programmatically using AWS STS, you can optionally pass inline or managed [session policies](access_policies.md#policies_session)\. Session policies are advanced policies that you pass as a parameter when you programmatically create a temporary credential session for a role\. You can pass a single JSON inline session policy document using the `Policy` parameter\. You can use the `PolicyArns` parameter to specify up to 10 managed session policies\. The resulting session's permissions are the intersection of the role's identity\-based policies and the session policies\. Alternatively, if your administrator or a custom program provides you with temporary credentials, they might have included a session policy to limit your access\.

## The service did not create the role's default policy version<a name="troubleshoot_serviceroles_edited-policy"></a>

A service role is a role that a service assumes to perform actions in your account on your behalf\. When you set up some AWS service environments, you must define a role for the service to assume\. In some cases, the service creates the service role and its policy in IAM for you\. Although you can modify or delete the service role and its policy from within IAM, AWS does not recommend this\. The role and policy are intended for use only by that service\. If you edit the policy and set up another environment, when the service tries to use the same role and policy, the operation can fail\.

For example, when you use AWS CodeBuild for the first time, the service creates a role named `codebuild-RWBCore-service-role`\. That service role uses the policy named `codebuild-RWBCore-managed-policy`\. If you edit the policy, it creates a new version and saves that version as the default version\. If you perform a subsequent operation in AWS CodeBuild, the service might try to update the policy\. If it does, you receive the following error:

```
codebuild.amazon.com did not create the default version (V2) of the codebuild-RWBCore-managed-policy policy that is attached to the codebuild-RWBCore-service-role role. To continue, detach the policy from any other identities and then delete the policy and the role.
```

If you receive this error, you must make changes in IAM before you can continue with your service operation\. First, set the default policy version to V1 and try the operation again\. If V1 was previously deleted, or if choosing V1 doesn't work, then clean up and delete the existing policy and role\.

For more information on editing managed policies, see [Editing customer managed policies \(console\)](access_policies_manage-edit.md#edit-managed-policy-console)\. For more information about policy versions, see [Versioning IAM policies](access_policies_managed-versioning.md)\. 

**To delete a service role and its policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. In the list of policies, choose the name of the policy that you want to delete\.

1. Choose the **Policy usage** tab to view which IAM users, groups, or roles use this policy\. If any of these identities use the policy, complete the following tasks:

   1. Create a new managed policy with the necessary permissions\. To ensure that the identities have the same permissions before and after your actions, copy the JSON policy document from the existing policy\. Then create the new managed policy and paste the JSON document as described in [Creating Policies on the JSON Tab](access_policies_create-console.md#access_policies_create-json-editor)\.

   1. For each affected identity, attach the new policy and then detach the old one\. For more information, see [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md)\.

1. In the navigation pane, choose **Roles**\.

1. In the list of roles, choose the name of the role that you want to delete\.

1. Choose the **Trust relationships** tab to view which entities can assume the role\. If any entity other than the service is listed, complete the following tasks:

   1. [Create a new role](id_roles_create_for-user.md#roles-creatingrole-user-console) that trusts those entities\.

   1. The policy that you created in the previous step\. If you skipped that step, create the new managed policy now\.

   1. Notify anyone who was assuming the role that they can no longer do so\. Provide them with information about how to assume the new role and have the same permissions\.

1. [Delete the policy](access_policies_manage-delete.md#delete-managed-policy)\.

1. [Delete the role](id_roles_manage_delete.md#roles-managingrole-deleting-console)\.