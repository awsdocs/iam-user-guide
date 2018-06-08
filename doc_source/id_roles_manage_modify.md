# Modifying a Role<a name="id_roles_manage_modify"></a>

You can change or modify a role in the following ways: 
+ To change who can assume a role, modify the role's trust policy\.
**Note**  
If the role is a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*, the role's trust policy cannot be modified\. Service\-linked roles appear with **\(Service\-linked role\)** in the **Trusted entities** column of the table\.
+ To change the permissions allowed by the role, modify the role's permissions policy \(or policies\)\.
**Note**  
If the role is a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*, the role's permissions can be modified only from the service that depends on the role\. Service\-linked roles appear with **\(Service\-linked role\)** in the **Trusted entities** column of the table\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.
+ To change the description of the role, modify the description text\.
+ To specify the maximum session duration setting for roles that are assumed using the AWS CLI or API, modify the maximum session duration setting's value\. This setting can have a value from 1 hour to 12 hours\. If you do not specify a value, the default maximum of 1 hour is applied\. 
**Note**  
Anyone who assumes the role from the AWS CLI or API can use the `duration-seconds` CLI parameter or the `DurationSeconds` API parameter to request a longer session\. The `MaxSessionDuration` setting determines the maximum duration of the role session that can be requested using the `DurationSeconds` parameter\. If users don't specify a value for the `DurationSeconds` parameter, their security credentials are valid for one hour\.

You can use the AWS Management Console, the [AWS Command Line Tools](https://aws.amazon.com/tools/#Command_Line_Tools), the Tools for Windows PowerShell, or the IAM API to make these changes\.

**Topics**
+ [Modifying a Role \(Console\)](#roles-managingrole-editing-console)
+ [Modifying a Role \(AWS CLI\)](#roles-managingrole-editing-cli)
+ [Modifying a Role \(AWS API\)](#roles-managingrole-editing-api)

## Modifying a Role \(Console\)<a name="roles-managingrole-editing-console"></a>

You can use the AWS Management Console to modify a role\.

**To change which trusted principals can access the role \(console\)**

1. In the navigation pane of the IAM console, choose **Roles**\.

1. In the list of roles in your account, choose the name of the role that you want to modify\.

1. Choose the **Trust relationships** tab, and then choose **Edit trust relationship**\.

1. Edit the trust policy as needed\. To add additional trusted principals, specify them in the `Principal` element\. Remember that policies are written in the [JSON](http://www.json.org) format, and JSON arrays are surrounded by square brackets \[ \] and separated by commas\. As an example, the following policy snippet shows how to reference two AWS accounts in the `Principal` element:

   ```
   "Principal": {
     "AWS": [
       "arn:aws:iam::111122223333:root",
       "arn:aws:iam::444455556666:root"
     ]
   },
   ```

   Remember that adding an account to the trust policy of a role is only half of establishing the trust relationship\. By default, no users in the trusted accounts can assume the role until the administrator for that account grants the users the permission to assume the role\. To do that, the administrator adds the Amazon Resource Name \(ARN\) of the role to an `Allow` element for the `sts:AssumeRole` action\. For more information, see the next procedure and the topic [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

   If your role can be used by one or more trusted services rather than AWS accounts, then the policy might contain an element similar to the following:

   ```
   "Principal": {
     "Service": [
       "opsworks.amazonaws.com",
       "ec2.amazonaws.com"
     ]
   },
   ```

1. When you are done editing, choose **Update Trust Policy** to save your changes\.

   For more information about policy structure and syntax, see [IAM Policies](access_policies.md) and the [IAM JSON Policy Elements Reference](reference_policies_elements.md)\.

**To allow users in a trusted external account to use the role \(console\)**

For more information and detail about this procedure, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. Sign in to the trusted external AWS account\. 

1. Decide whether to attach the permissions to a user or to a group\. In the navigation pane of the IAM console, choose **Users** or **Groups** accordingly\.

1. Choose the name of the user or group to which you want to grant access, and then choose the **Permissions** tab\.

1. Do one of the following:
   + To edit a customer managed policy, choose the name of the policy, choose **Edit policy**, and then choose the **JSON** tab\. You cannot edit an AWS managed policy\. AWS managed policies appear with the AWS icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_icon.png)\)\. For more information about the difference between AWS managed policies and customer managed policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\.
   + To edit an inline policy, choose the arrow next to the name of the policy and choose **Edit policy**\.

1. In the policy editor, add a new `Statement` element that specifies the following:

   ```
   {
     "Effect": "Allow",
     "Action": "sts:AssumeRole",
     "Resource": "arn:aws:iam::AWS account ID that contains the role:role/role name"
   }
   ```

   Replace the values in red with the actual values from the ARN of the role in the original account that users in this trusted external account can use\.

   Remember that you can have only one `Statement` keyword\. However, a statement can have several elements in an array, with elements separated by commas in their own curly braces \{ \} and all of the elements surrounded by square brackets \[ \]\. 

1. Follow the prompts on screen to finish editing the policy\. 

   For more information about editing customer managed and inline policies in the AWS Management Console, see [Editing IAM Policies](access_policies_manage-edit.md)\. 

**To change the permissions allowed by a role \(console\)**

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role to modify, and then choose the **Permissions** tab\.

1. Do one of the following:
   + To edit an existing customer managed policy, choose the name of the policy and then choose **Edit policy**\.
**Note**  
You cannot edit an AWS managed policy\. AWS managed policy appear with the AWS icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_icon.png)\)\. For more information about the difference between AWS managed policies and customer managed policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\. 
   + To attach an existing managed policy, choose **Add permissions**\.
   + To edit an existing inline policy, choose the arrow next to the name of the policy and choose **Edit Policy**\.
   + To embed a new inline policy, choose **Add inline policy**\. 

   For example policies that delegate permissions through roles, see [Example Policies](access_policies_examples.md)\.

   For more information about permissions, see [IAM Policies](access_policies.md)\.

**To change the description of a role \(console\)**

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role to modify\.

1. Next to **Role description** and on the far right, choose **Edit**\. 

1. Type a new description in the box and choose **Save**\.<a name="id_roles_modify_max-session"></a>

**To change the maximum session duration setting for roles that are assumed using the AWS CLI or API \(console\)**

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role to modify\.

1. Next to **Maximum CLI/API session duration** choose a value\. Or choose **Custom duration** and type a value \(in seconds\)\.

1. Choose **Save**\.

   Your changes don't take effect until the next time someone assumes this role\. To learn how to revoke existing sessions for this role, see [Revoking IAM Role Temporary Security Credentials](id_roles_use_revoke-sessions.md)\.

## Modifying a Role \(AWS CLI\)<a name="roles-managingrole-editing-cli"></a>

You can use the AWS Command Line Interface to modify a role\.

**To change the trusted principals that can access the role \(AWS CLI\)**

1. If you don't know the name of the role that you want to modify, run the following command to list the roles in your account:
   + [aws iam list\-roles](http://docs.aws.amazon.com/cli/latest/reference/iam/list-roles.html)

1. \(Optional\) To view the current trust policy for a role, run the following command:
   + [aws iam get\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

1. To modify the trusted principals that can access the role, create a text file with the updated trust policy\. You can use any text editor to construct the policy\.

   For example, the following policy snippet shows how to reference two AWS accounts in the `Principal` element:

   ```
   "Principal": {
     "AWS": [
       "arn:aws:iam::111122223333:root",
       "arn:aws:iam::444455556666:root"
     ]
   },
   ```

   Remember that adding an account to the trust policy of a role is only half of establishing the trust relationship\. By default, no users in the trusted accounts can assume the role until the administrator for that account grants the users the permission to assume the role\. To do this, the administrator must add the Amazon Resource Name \(ARN\) of the role to an `Allow` element for the `sts:AssumeRole` action\. For more information, see the next procedure and the topic [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. To update the trust policy, run the following command:
   + [aws iam update\-assume\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/update-assume-role-policy.html)

**To allow users in a trusted external account to use the role \(AWS CLI\)**

For more information and detail about this procedure, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. Begin by creating a policy that grants permissions to assume the role\. For example, the following policy contains the minimum necessary permissions:

   ```
   {
     "Version": "2012-10-17",
     "Statement": {
       "Effect": "Allow",
       "Action": "sts:AssumeRole",
       "Resource": "arn:aws:iam::AWS account ID that contains the role:role/role name"
     }
   }
   ```

   Create a JSON file that contains a policy similar to the preceding example\. Replace the values in red with the actual values from the ARN of the role that users are allowed to assume\. After you have created the policy, run the following command to upload it to IAM:
   + [aws iam create\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/create-policy.html)

   The output of this command contains the ARN of the policy\. Make a note of this ARN because you will need to use it in a later step\. 

1. Decide which user or group to attach the policy to\. If you don't know the name of the intended user or group, use one of these commands to list the users or groups in your account:
   + [aws iam list\-users](http://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html) or [aws iam list\-groups](http://docs.aws.amazon.com/cli/latest/reference/iam/list-groups.html)

1. Use one of the following commands to attach the policy that you created in a previous step to the user or group:
   + [aws iam attach\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-user-policy.html) or [aws iam attach\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html)

**To change the permissions allowed by a role \(AWS CLI\)**

1. \(Optional\) To view the current permissions associated with a role, run the following commands:
   + [aws iam list\-role\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-role-policies.html) \(to list inline policies\) and [aws iam list\-attached\-role\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html) \(to list managed policies\)

1. The command to update permissions for the role differs depending on whether you are updating a managed policy or an inline policy\.

   To update a managed policy, run the following command to create a new version of the managed policy:
   + [aws iam create\-policy\-version](http://docs.aws.amazon.com/cli/latest/reference/iam/create-policy-version.html)

   To update an inline policy, run the following command:
   + [aws iam put\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)

**To change the description of a role \(AWS CLI\)**

1. \(Optional\) To view the current description for a role, run the following command:
   + [aws iam get\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

1. To update a role's description, run the following command with the description parameter:
   + [aws iam update\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/update-role.html)

**To change the maximum session duration setting for roles that are assumed using the AWS CLI \(AWS CLI\)**

1. \(Optional\) To view the current maximum session duration setting for a role, run the following command:
   + [aws iam get\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

1. To update a role's maximum session duration setting, run the following command with the `max-sessionduration` CLI parameter or the `MaxSessionDuration` API parameter:
   + [aws iam update\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/update-role.html)

   Your changes don't take effect until the next time someone assumes this role\. To learn how to revoke existing sessions for this role, see [Revoking IAM Role Temporary Security Credentials](id_roles_use_revoke-sessions.md)\.

## Modifying a Role \(AWS API\)<a name="roles-managingrole-editing-api"></a>

You can use the AWS API to modify a role\.

**To change the trusted principals that can access the role \(AWS API\)**

1. If you don't know the name of the role that you want to modify, call the following operation to list the roles in your account:
   + [ListRoles](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRoles.html)

1. \(Optional\) To view the current trust policy for a role, call the following operation:
   + [GetRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html)

1. To modify the trusted principals that can access the role, create a text file with the updated trust policy\. You can use any text editor to construct the policy\.

   For example, the following policy snippet shows how to reference two AWS accounts in the `Principal` element:

   ```
   "Principal": {
     "AWS": [
       "arn:aws:iam::111122223333:root",
       "arn:aws:iam::444455556666:root"
     ]
   },
   ```

   Remember that adding an account to the trust policy of a role is only half of establishing the trust relationship\. By default, no users in the trusted accounts can assume the role until the administrator for that account grants the users the permission to assume the role\. To do this, the administrator must add the Amazon Resource Name \(ARN\) of the role to an `Allow` element for the `sts:AssumeRole` action\. For more information, see the next procedure and the topic [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. To update the trust policy, call the following operation:
   + [UpdateAssumeRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAssumeRolePolicy.html)

**To allow users in a trusted external account to use the role \(AWS API\)**

For more information and detail about this procedure, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. Begin by creating a policy that grants permissions to assume the role\. For example, the following policy contains the minimum necessary permissions:

   ```
   {
     "Version": "2012-10-17",
     "Statement": {
       "Effect": "Allow",
       "Action": "sts:AssumeRole",
       "Resource": "arn:aws:iam::AWS account ID that contains the role:role/role name"
     }
   }
   ```

   Create a JSON file that contains a policy similar to the preceding example\. Replace the values in red with the actual values from the ARN of the role that users are allowed to assume\. After you have created the policy, call the following operation to upload it to IAM:
   + [CreatePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicy.html)

   The output of this operation contains the ARN of the policy\. Make a note of this ARN because you will need to use it in a later step\. 

1. Decide which user or group to attach the policy to\. If you don't know the name of the intended user or group, call one of these operations to list the users or groups in your account:
   + [ListUsers](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html) or [ListGroups](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroups.html)

1. Call one of the following operations to attach the policy that you created in a previous step to the user or group:
   +  API: [AttachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachUserPolicy.html) or [AttachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachGroupPolicy.html)

**To change the permissions allowed by a role \(AWS API\)**

1. \(Optional\) To view the current permissions associated with a role, call the following operations:
   + [ListRolePolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRolePolicies.html) \(to list inline policies\) and [ListAttachedRolePolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedRolePolicies.html) \(to list managed policies\)

1. The operation to update permissions for the role differs depending on whether you are updating a managed policy or an inline policy\.

   To update a managed policy, call the following operation to create a new version of the managed policy:
   + [CreatePolicyVersion](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicyVersion.html)

   To update an inline policy, call the following operation:
   + [PutRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)

**To change the description of a role \(AWS API\)**

1. \(Optional\) To view the current description for a role, call the following operation:
   + [GetRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html) 

1. To update a role's description, call the following operation with the description parameter:
   + [UpdateRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateRole.html)

**To change the maximum session duration setting for roles that are assumed using the API \(AWS API\)**

1. \(Optional\) To view the current maximum session duration setting for a role, call the following operation:
   + [GetRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html) 

1. To update a role's maximum session duration setting, call the following operation with the `max-sessionduration` CLI parameter or the `MaxSessionDuration` API parameter:
   + [UpdateRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateRole.html)

   Your changes don't take effect until the next time someone assumes this role\. To learn how to revoke existing sessions for this role, see [Revoking IAM Role Temporary Security Credentials](id_roles_use_revoke-sessions.md)\.