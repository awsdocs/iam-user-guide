# Disabling permissions for temporary security credentials<a name="id_credentials_temp_control-access_disable-perms"></a>

Temporary security credentials are valid until they expire, and they cannot be revoked\. However, because permissions are evaluated each time an AWS request is made using the credentials, you can achieve the effect of revoking the credentials by changing the permissions for the credentials even after they have been issued\. If you remove all permissions from the temporary security credentials, subsequent AWS requests that use those credentials will fail\. The mechanisms for changing or removing the permissions assigned to temporary security credentials are explained in the following sections\. 

**Note**  
When you update existing policy permissions, or when you apply a new policy to a user or a resource, it may take a few minutes for policy updates to take effect\.

**Topics**
+ [Denying access to the creator of the temporary security credentials](#denying-access-to-credentials-creator)
+ [Denying access to temporary security credentials by name](#denying-access-to-credentials-by-name)
+ [Denying access to temporary security credentials issued before a specific time](#denying-access-to-credentials-by-issue-time)

## Denying access to the creator of the temporary security credentials<a name="denying-access-to-credentials-creator"></a>

To change or remove the permissions assigned to temporary security credentials, you can change or remove the permissions that are associated with the creator of the credentials\. The creator of the credentials is determined by the AWS STS API that was used to obtain the credentials\. The mechanisms for changing or removing the permissions associated with this creator are explained in the following sections\. 

### Denying access to credentials created by AssumeRole, AssumeRoleWithSAML, or AssumeRoleWithWebIdentity<a name="denying-access-to-credentials-creator-roles"></a>

To change or remove the permissions assigned to the temporary security credentials obtained by calling the `AssumeRole`, `AssumeRoleWithSAML`, or `AssumeRoleWithWebIdentity` API operations, you edit or delete the role permission policy that defines the permissions for the assumed role\. The temporary security credentials obtained by assuming a role can never have more permissions than those defined in the permissions policy of the assumed role, and the permissions assigned to temporary security credentials are evaluated each time they are used to make an AWS request\. When you edit or delete the permission policy of a role, the changes affect the permissions of ***all*** temporary security credentials associated with that role, including credentials that were issued before you changed the role's permissions policy\. You can immediately revoke all permissions to a session by following the steps at [Revoking IAM role temporary security credentials](id_roles_use_revoke-sessions.md)\.

For more information about editing a role permission policy, see [Modifying a role](id_roles_manage_modify.md)\. 

### Denying access to credentials created by GetFederationToken or GetSessionToken<a name="denying-access-to-credentials-creator-federation-and-session-tokens"></a>

To change or remove the permissions assigned to the temporary security credentials obtained by calling the `GetFederationToken` or `GetSessionToken` API operations, you edit or delete the policies that are attached to the IAM user whose credentials were used to call `GetFederationToken` or `GetSessionToken`\. The temporary security credentials that were obtained by calling `GetFederationToken` or `GetSessionToken` can never have more permissions than the IAM user whose credentials were used to obtain them\. In addition the permissions assigned to temporary security credentials are evaluated each time they are used to make an AWS request\. It is important to note that when you edit or delete the permissions of an IAM user, the changes affect the IAM user as well as all temporary security credentials created by that user\.

**Important**  
You cannot change the permissions for an AWS account root user\. Likewise, you cannot change the permissions for the temporary security credentials that were created by calling `GetFederationToken` or `GetSessionToken` while signed in as the root user\. For this reason, we recommend that you do not call `GetFederationToken` or `GetSessionToken` as a root user\.

For information about how to change or remove the policies associated with the IAM user whose credentials were used to call `GetFederationToken` or `GetSessionToken`, see[Managing IAM policies](access_policies_manage.md)\.

## Denying access to temporary security credentials by name<a name="denying-access-to-credentials-by-name"></a>

You can deny access to temporary security credentials without affecting the permissions of the IAM user or role that created the credentials\. You do this by specifying the Amazon Resource Name \(ARN\) of the temporary security credentials in the `Principal` element of a resource\-based policy\. \(Only some AWS services support resource\-based policies\.\)

### Denying access to federated users<a name="denying-access-by-name-get-federation-token"></a>

For example, imagine you have an IAM user named `token-app` whose credentials are used to call `GetFederationToken`\. The `GetFederationToken` API call resulted in temporary security credentials associated with a federated user named Bob \(the federated user's name is taken from the `Name` parameter of the API call\)\. To deny federated user Bob's access to an S3 bucket called EXAMPLE\-BUCKET, you attach the following example bucket policy to EXAMPLE\-BUCKET\. It is important to note that this affects the federated user's Amazon S3 permissions only—any other permissions granted to the federated user remain intact\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Principal": {"AWS": "arn:aws:sts::ACCOUNT-ID-WITHOUT-HYPHENS:federated-user/Bob"},
    "Effect": "Deny",
    "Action": "s3:*",
    "Resource": "arn:aws:s3:::EXAMPLE-BUCKET"
  }
}
```

You can specify the ARN of the IAM user whose credentials were used to call `GetFederationToken` in the `Principal` element of the bucket policy, instead of specifying the federated user\. In that case, the `Principal` element of the preceding policy would look like this:

```
"Principal": {"AWS": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:user/token-app"}
```

It is important to note that specifying the ARN of IAM user `token-app` in the policy will result in denying access to ***all*** federated users created by `token-app`, not only the federated user named Bob\. 

### Denying access to assumed role users<a name="denying-access-by-name-assume-role"></a>

It is also possible to specify the ARN of the temporary security credentials that were created by assuming a role\. The difference is the syntax used in the `Principal` element of the resource\-based policy\. For example, a user assumes a role called `Accounting-Role` and specifies a `RoleSessionName` of `Mary` \(`RoleSessionName` is a parameter of the `AssumeRole` API call\)\. To deny access to the temporary security credentials that resulted from this API call, the `Principal` element of the resource\-based policy would look like this:

```
"Principal": {"AWS": "arn:aws:sts::ACCOUNT-ID-WITHOUT-HYPHENS:assumed-role/Accounting-Role/Mary"}
```

You can also specify the ARN of the IAM role in the `Principal` element of a resourced\-based policy, as in the following example\. In this case, the policy will result in denying access to ***all*** temporary security credentials associated with the role named `Accounting-Role`\. 

```
"Principal": {"AWS": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:role/Accounting-Role"}
```

## Denying access to temporary security credentials issued before a specific time<a name="denying-access-to-credentials-by-issue-time"></a>

It is possible to deny access only to temporary security credentials that were created before a specific time and date\. You do this by specifying a value for the `aws:TokenIssueTime` key in the `Condition` element of a policy\. The following policy shows an example\. You attach a policy similar to the following example to the IAM user that created the temporary security credentials\. The policy denies all permissions but only when the value of `aws:TokenIssueTime` is earlier than the specified date and time\. The value of `aws:TokenIssueTime` corresponds to the exact time at which the temporary security credentials were created\. The `aws:TokenIssueTime` value is only present in the context of AWS requests that are signed with temporary security credentials, so the `Deny` statement in the policy will not affect requests that are signed with the long\-term credentials of the IAM user\. 

The following policy can also be attached to a role\. In that case, the policy affects only the temporary security credentials that were created by the role before the specified date and time\. If the credentials were created by the role after the specified date and time, the `Condition` element in the policy is evaluated to false, so the `Deny` statement has no effect\.

**Example policy that denies all permissions to temporary credentials by issue time**  

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Deny",
    "Action": "*",
    "Resource": "*",
    "Condition": {"DateLessThan": {"aws:TokenIssueTime": "2014-05-07T23:47:00Z"}}
  }
}
```

Valid users whose sessions are revoked in this way must acquire temporary credentials for a new session to continue working\. Note that the AWS CLI caches credentials until they expire\. To force the CLI to delete and refresh cached credentials that are no longer valid, run one of the following commands:

**Linux, MacOS, or Unix**

```
$ rm -r ~/.aws/cli/cache
```

**Windows**

```
C:\> del /s /q %UserProfile%\.aws\cli\cache
```