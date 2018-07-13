# Modifying a Role<a name="id_roles_manage_modify"></a>

You can change or modify a role in IAM using the following methods: 
+ To change who can assume a role, modify the role's trust policy\. You cannot modify the trust policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\.
+ To change the permissions allowed by the role, modify the role's permissions policy \(or policies\)\. You cannot modify the permissions policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* in IAM\. You might be able to modify the permissions policy within the service that depends on the role\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.
+ To change the description of the role, modify the description text\.
+ To specify the maximum session duration setting for roles that are assumed using the AWS CLI or API, modify the maximum session duration setting's value\. This setting can have a value from 1 hour to 12 hours\. If you do not specify a value, the default maximum of 1 hour is applied\. 
**Note**  
Anyone who assumes the role from the AWS CLI or API can use the `duration-seconds` CLI parameter or the `DurationSeconds` API parameter to request a longer session\. The `MaxSessionDuration` setting determines the maximum duration of the role session that can be requested using the `DurationSeconds` parameter\. If users don't specify a value for the `DurationSeconds` parameter, their security credentials are valid for one hour\.
+ To change the maximum permissions allowed for a role, modify the [permissions boundary](access_policies_boundaries.md)\.

You can use the AWS Management Console, the [AWS Command Line Tools](https://aws.amazon.com/tools/#Command_Line_Tools), the Tools for Windows PowerShell, or the IAM API to make these changes\.

**Topics**
+ [Modifying a Role \(Console\)](#roles-managingrole-editing-console)
+ [Modifying a Role \(AWS CLI\)](#roles-managingrole-editing-cli)
+ [Modifying a Role \(AWS API\)](#roles-managingrole-editing-api)

## Modifying a Role \(Console\)<a name="roles-managingrole-editing-console"></a>

You can use the AWS Management Console to modify a role\.

**To change who can assume the role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\.

1. In the list of roles in your account, choose the name of the role that you want to modify\.

1. Choose the **Trust relationships** tab, and then choose **Edit trust relationship**\.

1. Edit the trust policy as needed\. To add additional principals that can assume the role, specify them in the `Principal` element\. For example, the following policy snippet shows how to reference two AWS accounts in the `Principal` element:

   ```
   "Principal": {
     "AWS": [
       "arn:aws:iam::111122223333:root",
       "arn:aws:iam::444455556666:root"
     ]
   },
   ```

   Remember that adding an account to the trust policy of a role is only half of establishing the trust relationship\. By default, no users in the trusted accounts can assume the role\. The administrator for the newly trusted account must grant the users the permission to assume the role\. To do that, the administrator must create or edit a policy that is attached to the user to allow the user access to the `sts:AssumeRole` action\. For more information, see the following procedure or [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

   The following policy snippet shows how to reference two AWSservices in the `Principal` element:

   ```
   "Principal": {
     "Service": [
       "opsworks.amazonaws.com",
       "ec2.amazonaws.com"
     ]
   },
   ```

1. When you are finished editing your trust policy, choose **Update Trust Policy** to save your changes\.

   For more information about policy structure and syntax, see [Policies and Permissions](access_policies.md) and the [IAM JSON Policy Elements Reference](reference_policies_elements.md)\.

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
     "Resource": "arn:aws:iam::ACCOUNT-ID-THAT-CONTAINS-ROLE:role/ROLE-NAME"
   }
   ```

   Replace the ARN in the statement with the ARN of the role that the user can assume\.

1. Follow the prompts on screen to finish editing the policy\. 

**To change the permissions allowed by a role \(console\)**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role that you want to modify, and then choose the **Permissions** tab\.

1. Do one of the following:
   + To edit an existing customer managed policy, choose the name of the policy and then choose **Edit policy**\.
**Note**  
You cannot edit an AWS managed policy\. AWS managed policy appear with the AWS icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_icon.png)\)\. For more information about the difference between AWS managed policies and customer managed policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\. 
   + To attach an existing managed policy to the role, choose **Add permissions**\.
   + To edit an existing inline policy, choose the arrow next to the name of the policy and choose **Edit Policy**\.
   + To embed a new inline policy, choose **Add inline policy**\. 

**To change the description of a role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role to modify\.

1. Next to **Role description** and on the far right, choose **Edit**\. 

1. Type a new description in the box and choose **Save**\.<a name="id_roles_modify_max-session"></a>

**To change the maximum session duration setting for roles that are assumed using the AWS CLI or API \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role to modify\.

1. Next to **Maximum CLI/API session duration** choose a value\. Or choose **Custom duration** and type a value \(in seconds\)\.

1. Choose **Save**\.

   Your changes don't take effect until the next time someone assumes this role\. To learn how to revoke existing sessions for this role, see [Revoking IAM Role Temporary Security Credentials](id_roles_use_revoke-sessions.md)\.

**To change the policy used to set the permissions boundary for a role**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles**\.

1. Choose the name of the role whose [permissions boundary](access_policies_boundaries.md) you want to change\. 

1. Choose the **Permissions** tab\. If necessary, open the **Permissions boundary** section and then choose **Change boundary**\.

1. Select the policy that you want to use for the permissions boundary\.

1. Choose **Change boundary**\.

Your changes don't take effect until the next time someone assumes this role\.

## Modifying a Role \(AWS CLI\)<a name="roles-managingrole-editing-cli"></a>

You can use the AWS Command Line Interface to modify a role\.

**To change who can assume the role \(AWS CLI\)**

1. \(Optional\) If you don't know the name of the role that you want to modify, run the following command to list the roles in your account:
   + [aws iam list\-roles](http://docs.aws.amazon.com/cli/latest/reference/iam/list-roles.html)

1. \(Optional\) To view the current trust policy for a role, run the following command:
   + [aws iam get\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

1. To modify the trusted principals that can access the role, create a text file with the updated trust policy\. You can use any text editor to construct the policy\.

   For example, the following trust policy shows how to reference two AWS accounts in the `Principal` element\. This allows users within two separate AWS accounts to assume this role\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": {
           "Effect": "Allow",
           "Principal": {"AWS": [
               "arn:aws:iam::111122223333:root",
               "arn:aws:iam::444455556666:root"
           ]},
           "Action": "sts:AssumeRole"
       }
   }
   ```

   Remember that adding an account to the trust policy of a role is only half of establishing the trust relationship\. By default, no users in the trusted accounts can assume the role\. The administrator for the newly trusted account must grant the users the permission to assume the role\. To do that, the administrator must create or edit a policy that is attached to the user to allow the user access to the `sts:AssumeRole` action\. For more information, see the following procedure or [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. To use the file that you just created to update the trust policy, run the following command:
   + [aws iam update\-assume\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/update-assume-role-policy.html)

**To allow users in a trusted external account to use the role \(AWS CLI\)**

For more information and detail about this procedure, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. Create a JSON file that contains a permissions policy that grants permissions to assume the role\. For example, the following policy contains the minimum necessary permissions:

   ```
   {
     "Version": "2012-10-17",
     "Statement": {
       "Effect": "Allow",
       "Action": "sts:AssumeRole",
       "Resource": "arn:aws:iam::ACCOUNT-ID-THAT-CONTAINS-ROLE:role/ROLE-NAME"
     }
   }
   ```

   Replace the ARN in the statement with the ARN of the role that the user can assume\.

1. Run the following command to upload the JSON file that contains the trust policy to IAM:
   + [aws iam create\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/create-policy.html)

   The output of this command includes the ARN of the policy\. Make a note of this ARN because you will need it in a later step\. 

1. Decide which user or group to attach the policy to\. If you don't know the name of the intended user or group, use one of the following commands to list the users or groups in your account:
   + [aws iam list\-users](http://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html)
   + [aws iam list\-groups](http://docs.aws.amazon.com/cli/latest/reference/iam/list-groups.html)

1. Use one of the following commands to attach the policy that you created in the previous step to the user or group:
   + [aws iam attach\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-user-policy.html)
   + [aws iam attach\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html)

**To change the permissions allowed by a role \(AWS CLI\)**

1. \(Optional\) To view the current permissions associated with a role, run the following commands:

   1. [aws iam list\-role\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-role-policies.html) to list inline policies

   1. [aws iam list\-attached\-role\-policies](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html) to list managed policies

1. The command to update permissions for the role differs depending on whether you are updating a managed policy or an inline policy\.

   To update a managed policy, run the following command to create a new version of the managed policy:
   + [aws iam create\-policy\-version](http://docs.aws.amazon.com/cli/latest/reference/iam/create-policy-version.html)

   To update an inline policy, run the following command:
   + [aws iam put\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)

**To change the managed policy used to set the permissions boundary for a role \(AWS CLI\)**

1. \(Optional\) To view the current [permissions boundary](access_policies_boundaries.md) for a role, run the following command: 
   + [aws iam get\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

1. To use a different managed policy to update the permissions boundary for a role, run the following command: 
   + [aws iam put\-role\-permissions\-boundary](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-permissions-boundary.html)

   A role can have only one managed policy set as a permissions boundary\. If you change the permissions boundary, you change the maximum permissions allowed for a role\.

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

**To change who can assume the role \(AWS API\)**

1. \(Optional\) If you don't know the name of the role that you want to modify, call the following operation to list the roles in your account:
   + [ListRoles](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRoles.html)

1. \(Optional\) To view the current trust policy for a role, call the following operation:
   + [GetRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html)

1. To modify the trusted principals that can access the role, create a text file with the updated trust policy\. You can use any text editor to construct the policy\.

   For example, the following trust policy shows how to reference two AWS accounts in the `Principal` element\. This allows users within two separate AWS accounts to assume this role\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": {
           "Effect": "Allow",
           "Principal": {"AWS": [
               "arn:aws:iam::111122223333:root",
               "arn:aws:iam::444455556666:root"
           ]},
           "Action": "sts:AssumeRole"
       }
   }
   ```

   Remember that adding an account to the trust policy of a role is only half of establishing the trust relationship\. By default, no users in the trusted accounts can assume the role\. The administrator for the newly trusted account must grant the users the permission to assume the role\. To do that, the administrator must create or edit a policy that is attached to the user to allow the user access to the `sts:AssumeRole` action\. For more information, see the following procedure or [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. To use the file that you just created to update the trust policy, call the following operation:
   + [UpdateAssumeRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAssumeRolePolicy.html)

**To allow users in a trusted external account to use the role \(AWS API\)**

For more information and detail about this procedure, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

1. Create a JSON file that contains a permissions policy that grants permissions to assume the role\. For example, the following policy contains the minimum necessary permissions:

   ```
   {
     "Version": "2012-10-17",
     "Statement": {
       "Effect": "Allow",
       "Action": "sts:AssumeRole",
       "Resource": "arn:aws:iam::ACCOUNT-ID-THAT-CONTAINS-ROLE:role/ROLE-NAME"
     }
   }
   ```

   Replace the ARN in the statement with the ARN of the role that the user can assume\.

1. Call the following operation to upload the JSON file that contains the trust policy to IAM:
   + [CreatePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicy.html)

   The output of this operation includes the ARN of the policy\. Make a note of this ARN because you will need it in a later step\. 

1. Decide which user or group to attach the policy to\. If you don't know the name of the intended user or group, call one of the following operations to list the users or groups in your account:
   + [ListUsers](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html)
   + [ListGroups](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroups.html)

1. Call one of the following operations to attach the policy that you created in the previous step to the user or group:
   +  API: [AttachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachUserPolicy.html)
   + [AttachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachGroupPolicy.html)

**To change the permissions allowed by a role \(AWS API\)**

1. \(Optional\) To view the current permissions associated with a role, call the following operations:

   1. [ListRolePolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRolePolicies.html) to list inline policies

   1. [ListAttachedRolePolicies](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedRolePolicies.html) to list managed policies

1. The operation to update permissions for the role differs depending on whether you are updating a managed policy or an inline policy\.

   To update a managed policy, call the following operation to create a new version of the managed policy:
   + [CreatePolicyVersion](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicyVersion.html)

   To update an inline policy, call the following operation:
   + [PutRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)

**To change the managed policy used to set the permissions boundary for a role \(AWS API\)**

1. \(Optional\) To view the current [permissions boundary](access_policies_boundaries.md) for a role, call the following operation: 
   + [GetRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html)

1. To use a different managed policy to update the permissions boundary for a role, call the following operation: 
   + [PutRolePermissionsBoundary](http://alpha-docs-aws.amazon.com/IAM/latest/APIReference/API_PutRolePermissionsBoundary.html)

   A role can have only one managed policy set as a permissions boundary\. If you change the permissions boundary, you change the maximum permissions allowed for a role\.

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