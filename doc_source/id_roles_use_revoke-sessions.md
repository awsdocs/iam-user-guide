# Revoking IAM role temporary security credentials<a name="id_roles_use_revoke-sessions"></a>

**Warning**  
If you follow the steps on this page, all users with current sessions created by assuming the role are denied access to all AWS actions and resources\. This can result in users losing unsaved work\. 

When you enable users to access the AWS Management Console with a long session duration time \(such as 12 hours\), their temporary credentials do not expire as quickly\. If users inadvertently expose their credentials to an unauthorized third party, that party has access for the duration of the session\. However, you can immediately revoke all permissions to the role's credentials issued before a certain point in time if you need to\. All temporary credentials for that role issued before the specified time become invalid\. This forces all users to reauthenticate and request new credentials\.

**Note**  
You cannot revoke the session for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\.

When you revoke permissions for a role using the procedure in this topic, AWS attaches a new inline policy to the role that denies all permissions to all actions\. It includes a condition that applies the restrictions only if the user assumed the role *before* the point in time when you revoke the permissions\. If the user assumes the role *after* you revoked the permissions, then the deny policy does not apply to that user\.

**Important**  
This deny policy applies to all users of the specified role, not just those with longer duration console sessions\.

## Minimum permissions to revoke session permissions from a role<a name="revoke-session-permissions"></a>

To successfully revoke session permissions from a role, you must have the `PutRolePolicy` permission for the role\. This allows you to attach the `AWSRevokeOlderSessions` inline policy to the role\.

## Revoking session permissions<a name="revoke-session"></a>

You can revoke the session permissions from a role\.

**To immediately deny all permissions to any current user of role credentials**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the **IAM Dashboard**, choose **Roles**, and then choose the name \(not the check box\) of the role whose permissions you want to revoke\.

1. On the **Summary** page for the selected role, choose the **Revoke sessions** tab\.

1. On the **Revoke sessions** tab, choose **Revoke active sessions**\.

1. AWS asks you to confirm the action\. Choose **Revoke active sessions** on the dialog box\.

   IAM immediately attaches a policy named `AWSRevokeOlderSessions` to the role\. The policy denies all access to users who assumed the role before the moment you chose **Revoke active sessions**\. Any user who assumes the role ***after ***you chose **Revoke active sessions** is **not** affected\.

   When you apply a new policy to a user or a resource, it may take a few minutes for policy updates to take effect\.

**Note**  
Don't worry about remembering to delete the policy\. Any user who assumes the role *after* you revoked sessions is not affected by the policy\. If you choose to **Revoke Sessions** again later, then the date/time stamp in the policy is refreshed and it again denies all permissions to any user who assumed the role before the new specified time\.

Valid users whose sessions are revoked in this way must acquire temporary credentials for a new session to continue working\. Note that the AWS CLI caches credentials until they expire\. To force the CLI to delete and refresh cached credentials that are no longer valid, run one of the following commands:

**Linux, macOS, or Unix**

```
$ rm -r ~/.aws/cli/cache
```

**Windows**

```
C:\> del /s /q %UserProfile%\.aws\cli\cache
```

For more information, see [Disabling permissions for temporary security credentials](id_credentials_temp_control-access_disable-perms.md)\.