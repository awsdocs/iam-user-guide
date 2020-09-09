# Modifying a role \(AWS CLI\)<a name="roles-managingrole-editing-cli"></a>

You can use the AWS Command Line Interface to modify a role\. To change the set of tags on a role, see [Managing tags on IAM entities \(console\)](id_tags.md#id_tags_procs-console)\.

**Topics**
+ [Modifying a role trust policy \(AWS CLI\)](#roles-managingrole_edit-trust-policy-cli)
+ [Modifying a role permissions policy \(AWS CLI\)](#roles-modify_permissions-policy-cli)
+ [Modifying a role description \(AWS CLI\)](#roles-modify_description-cli)
+ [Modifying a role maximum session duration \(AWS CLI\)](#roles-modify_max-session-duration-cli)
+ [Modifying a role permissions boundary \(AWS CLI\)](#roles-modify_permissions-boundary-cli)

## Modifying a role trust policy \(AWS CLI\)<a name="roles-managingrole_edit-trust-policy-cli"></a>

To change who can assume a role, you must modify the role's trust policy\. You cannot modify the trust policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\.

**Note**  
If a user is listed as the principal in a role's trust policy but cannot assume the role, check the user's [permissions boundary](access_policies_boundaries.md)\. If a permissions boundary is set for the user, then it must allow the `sts:AssumeRole` action\.

**To modify a role trust policy \(AWS CLI\)**

1. \(Optional\) If you don't know the name of the role that you want to modify, run the following command to list the roles in your account:
   + [aws iam list\-roles](https://docs.aws.amazon.com/cli/latest/reference/iam/list-roles.html)

1. \(Optional\) To view the current trust policy for a role, run the following command:
   + [aws iam get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

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

   If you specify a principal in another account, adding an account to the trust policy of a role is only half of establishing the cross\-account trust relationship\. By default, no users in the trusted accounts can assume the role\. The administrator for the newly trusted account must grant the users the permission to assume the role\. To do that, the administrator must create or edit a policy that is attached to the user to allow the user access to the `sts:AssumeRole` action\. For more information, see the following procedure or [Granting a user permissions to switch roles](id_roles_use_permissions-to-switch.md)\.

1. To use the file that you just created to update the trust policy, run the following command:
   + [aws iam update\-assume\-role\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/update-assume-role-policy.html)

**To allow users in a trusted external account to use the role \(AWS CLI\)**

For more information and detail about this procedure, see [Granting a user permissions to switch roles](id_roles_use_permissions-to-switch.md)\.

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
   + [aws iam create\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/create-policy.html)

   The output of this command includes the ARN of the policy\. Make a note of this ARN because you will need it in a later step\. 

1. Decide which user or group to attach the policy to\. If you don't know the name of the intended user or group, use one of the following commands to list the users or groups in your account:
   + [aws iam list\-users](https://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html)
   + [aws iam list\-groups](https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups.html)

1. Use one of the following commands to attach the policy that you created in the previous step to the user or group:
   + [aws iam attach\-user\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/attach-user-policy.html)
   + [aws iam attach\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html)

## Modifying a role permissions policy \(AWS CLI\)<a name="roles-modify_permissions-policy-cli"></a>

To change the permissions allowed by the role, modify the role's permissions policy \(or policies\)\. You cannot modify the permissions policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* in IAM\. You might be able to modify the permissions policy within the service that depends on the role\. To check whether a service supports this feature, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-linked roles** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

**To change the permissions allowed by a role \(AWS CLI\)**

1. \(Optional\) To view the current permissions associated with a role, run the following commands:

   1. [aws iam list\-role\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-role-policies.html) to list inline policies

   1. [aws iam list\-attached\-role\-policies](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-role-policies.html) to list managed policies

1. The command to update permissions for the role differs depending on whether you are updating a managed policy or an inline policy\.

   To update a managed policy, run the following command to create a new version of the managed policy:
   + [aws iam create\-policy\-version](https://docs.aws.amazon.com/cli/latest/reference/iam/create-policy-version.html)

   To update an inline policy, run the following command:
   + [aws iam put\-role\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)

## Modifying a role description \(AWS CLI\)<a name="roles-modify_description-cli"></a>

To change the description of the role, modify the description text\.

**To change the description of a role \(AWS CLI\)**

1. \(Optional\) To view the current description for a role, run the following command:
   + [aws iam get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

1. To update a role's description, run the following command with the description parameter:
   + [aws iam update\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/update-role.html)

## Modifying a role maximum session duration \(AWS CLI\)<a name="roles-modify_max-session-duration-cli"></a>

To specify the maximum session duration setting for roles that are assumed using the AWS CLI or API, modify the maximum session duration setting's value\. This setting can have a value from 1 hour to 12 hours\. If you do not specify a value, the default maximum of 1 hour is applied\. This setting does not limit sessions assumed by AWS services\.

**Note**  
Anyone who assumes the role from the AWS CLI or API can use the `duration-seconds` CLI parameter or the `DurationSeconds` API parameter to request a longer session\. The `MaxSessionDuration` setting determines the maximum duration of the role session that can be requested using the `DurationSeconds` parameter\. If users don't specify a value for the `DurationSeconds` parameter, their security credentials are valid for one hour\.

**To change the maximum session duration setting for roles that are assumed using the AWS CLI \(AWS CLI\)**

1. \(Optional\) To view the current maximum session duration setting for a role, run the following command:
   + [aws iam get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

1. To update a role's maximum session duration setting, run the following command with the `max-sessionduration` CLI parameter or the `MaxSessionDuration` API parameter:
   + [aws iam update\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/update-role.html)

   Your changes don't take effect until the next time someone assumes this role\. To learn how to revoke existing sessions for this role, see [Revoking IAM role temporary security credentials](id_roles_use_revoke-sessions.md)\.

## Modifying a role permissions boundary \(AWS CLI\)<a name="roles-modify_permissions-boundary-cli"></a>

To change the maximum permissions allowed for a role, modify the role's [permissions boundary](access_policies_boundaries.md)\.

**To change the managed policy used to set the permissions boundary for a role \(AWS CLI\)**

1. \(Optional\) To view the current [permissions boundary](access_policies_boundaries.md) for a role, run the following command: 
   + [aws iam get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)

1. To use a different managed policy to update the permissions boundary for a role, run the following command: 
   + [aws iam put\-role\-permissions\-boundary](https://docs.aws.amazon.com/cli/latest/reference/iam/put-role-permissions-boundary.html)

   A role can have only one managed policy set as a permissions boundary\. If you change the permissions boundary, you change the maximum permissions allowed for a role\.