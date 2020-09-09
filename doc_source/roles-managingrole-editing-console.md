# Modifying a role \(console\)<a name="roles-managingrole-editing-console"></a>

You can use the AWS Management Console to modify a role\. To change the set of tags on a role, see [Managing tags on IAM entities \(console\)](id_tags.md#id_tags_procs-console)\.

**Topics**
+ [Modifying a role trust policy \(console\)](#roles-managingrole_edit-trust-policy)
+ [Modifying a role permissions policy \(console\)](#roles-modify_permissions-policy)
+ [Modifying a role description \(console\)](#roles-modify_description)
+ [Modifying a role maximum session duration \(console\)](#roles-modify_max-session-duration)
+ [Modifying a role permissions boundary \(console\)](#roles-modify_permissions-boundary)

## Modifying a role trust policy \(console\)<a name="roles-managingrole_edit-trust-policy"></a>

To change who can assume a role, you must modify the role's trust policy\. You cannot modify the trust policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\.

**Note**  
If a user is listed as the principal in a role's trust policy but cannot assume the role, check the user's [permissions boundary](access_policies_boundaries.md)\. If a permissions boundary is set for the user, then it must allow the `sts:AssumeRole` action\.

**To modify a role trust policy \(console\)**

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

   If you specify a principal in another account, adding an account to the trust policy of a role is only half of establishing the cross\-account trust relationship\. By default, no users in the trusted accounts can assume the role\. The administrator for the newly trusted account must grant the users the permission to assume the role\. To do that, the administrator must create or edit a policy that is attached to the user to allow the user access to the `sts:AssumeRole` action\. For more information, see the following procedure or [Granting a user permissions to switch roles](id_roles_use_permissions-to-switch.md)\.

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

   For more information about policy structure and syntax, see [Policies and permissions in IAM](access_policies.md) and the [IAM JSON policy elements reference](reference_policies_elements.md)\.

**To allow users in a trusted external account to use the role \(console\)**

For more information and detail about this procedure, see [Granting a user permissions to switch roles](id_roles_use_permissions-to-switch.md)\.

1. Sign in to the trusted external AWS account\. 

1. Decide whether to attach the permissions to a user or to a group\. In the navigation pane of the IAM console, choose **Users** or **Groups** accordingly\.

1. Choose the name of the user or group to which you want to grant access, and then choose the **Permissions** tab\.

1. Do one of the following:
   + To edit a customer managed policy, choose the name of the policy, choose **Edit policy**, and then choose the **JSON** tab\. You cannot edit an AWS managed policy\. AWS managed policies appear with the AWS icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_icon.png)\)\. For more information about the difference between AWS managed policies and customer managed policies, see [Managed policies and inline policies](access_policies_managed-vs-inline.md)\.
   + To edit an inline policy, choose the arrow next to the name of the policy and choose **Edit policy**\.

1. In the policy editor, add a new `Statement` element that specifies the following:

   ```
   {
     "Effect": "Allow",
     "Action": "sts:AssumeRole",
     "Resource": "arn:aws:iam::ACCOUNT-ID:role/ROLE-NAME"
   }
   ```

   Replace the ARN in the statement with the ARN of the role that the user can assume\.

1. Follow the prompts on screen to finish editing the policy\. 

## Modifying a role permissions policy \(console\)<a name="roles-modify_permissions-policy"></a>

To change the permissions allowed by the role, modify the role's permissions policy \(or policies\)\. You cannot modify the permissions policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* in IAM\. You might be able to modify the permissions policy within the service that depends on the role\. To check whether a service supports this feature, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-linked roles** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

**To change the permissions allowed by a role \(console\)**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role that you want to modify, and then choose the **Permissions** tab\.

1. Do one of the following:
   + To edit an existing customer managed policy, choose the name of the policy and then choose **Edit policy**\.
**Note**  
You cannot edit an AWS managed policy\. AWS managed policy appear with the AWS icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_icon.png)\)\. For more information about the difference between AWS managed policies and customer managed policies, see [Managed policies and inline policies](access_policies_managed-vs-inline.md)\. 
   + To attach an existing managed policy to the role, choose **Add permissions**\.
   + To edit an existing inline policy, choose the arrow next to the name of the policy and choose **Edit Policy**\.
   + To embed a new inline policy, choose **Add inline policy**\. 

## Modifying a role description \(console\)<a name="roles-modify_description"></a>

To change the description of the role, modify the description text\.

**To change the description of a role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role to modify\.

1. Next to **Role description** and on the far right, choose **Edit**\. 

1. Type a new description in the box and choose **Save**\.

## Modifying a role maximum session duration \(console\)<a name="roles-modify_max-session-duration"></a>

To specify the maximum session duration setting for roles that are assumed using the console, the AWS CLI, or AWS API, modify the maximum session duration setting value\. This setting can have a value from 1 hour to 12 hours\. If you do not specify a value, the default maximum of 1 hour is applied\. This setting does not limit sessions assumed by AWS services\.<a name="id_roles_modify_max-session"></a>

**To change the maximum session duration setting for roles that are assumed using the console, AWS CLI, or AWS API \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role to modify\.

1. Next to **Maximum session duration**, choose a value\. Or choose **Custom duration** and type a value \(in seconds\)\.

1. Choose **Save**\.

   Your changes don't take effect until the next time someone assumes this role\. To learn how to revoke existing sessions for this role, see [Revoking IAM role temporary security credentials](id_roles_use_revoke-sessions.md)\.

In the AWS Management Console, IAM user sessions are 12 hours by default\. IAM users who switch roles in the console are granted the role maximum session duration, or the remaining time in the IAM user's session, whichever is less\.

Anyone who assumes the role from the AWS CLI or AWS API can request a longer session, up to this maximum\. The `MaxSessionDuration` setting determines the maximum duration of the role session that can be requested\.
+ To specify a session duration using the AWS CLI use the `duration-seconds` parameter\. To learn more, see [Switching to an IAM role \(AWS CLI\)](id_roles_use_switch-role-cli.md)\.
+ To specify a session duration using the AWS API, use the `DurationSeconds` parameter\. To learn more, see [Switching to an IAM role \(AWS API\)](id_roles_use_switch-role-api.md)\. 

## Modifying a role permissions boundary \(console\)<a name="roles-modify_permissions-boundary"></a>

To change the maximum permissions allowed for a role, modify the role's [permissions boundary](access_policies_boundaries.md)\.

**To change the policy used to set the permissions boundary for a role**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles**\.

1. Choose the name of the role whose [permissions boundary](access_policies_boundaries.md) you want to change\. 

1. Choose the **Permissions** tab\. If necessary, open the **Permissions boundary** section and then choose **Change boundary**\.

1. Select the policy that you want to use for the permissions boundary\.

1. Choose **Change boundary**\.

   Your changes don't take effect until the next time someone assumes this role\.