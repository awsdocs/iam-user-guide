# AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the my security credentials page<a name="reference_policies_examples_aws_my-sec-creds-self-manage"></a>

This example shows how you might create a policy that allows IAM users that are authenticated using [multi\-factor authentication \(MFA\)](id_credentials_mfa.md) to manage their own credentials on the **My Security Credentials** page\. This AWS Management Console page displays account information such as the account ID and canonical user ID\. Users can also view and edit their own passwords, access keys, MFA devices, X\.509 certificates, and SSH keys and Git credentials\. This example policy includes the permissions required to view and edit all of the information on the page\. It also requires the user to set up and authenticate using MFA before performing any other operations in AWS\. To allow users to manage their own credentials without using MFA, see [AWS: Allows IAM users to manage their own credentials on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage-no-mfa.md)\.

To learn how users can access the **My Security Credentials** page, see [How IAM users change their own password \(console\)](id_credentials_passwords_user-change-own.md#ManagingUserPwdSelf-Console)\.

**Note**  
This example policy does not allow users to reset a password while signing in\. New users and users with an expired password might try to do so\. You can allow this by adding `iam:ChangePassword` and `iam:GetAccountPasswordPolicy` to the statement `DenyAllExceptListedIfNoMFA`\. However, IAM does not recommend this\. Allowing users to change their password without MFA can be a security risk\.

**What does this policy do?**
+ The `AllowViewAccountInfo` statement allows the user to view account\-level information\. These permissions must be in their own statement because they do not support or do not need to specify a resource ARN\. Instead the permissions specify `"Resource" : "*"`\. This statement includes the following actions that allow the user to view specific information: 
  + `GetAccountSummary` – View the account ID and the account [canonical user ID](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html#FindingCanonicalId)\.
  + `GetAccountPasswordPolicy` – View the account password requirements while changing their own IAM user password\.
  + `ListVirtualMFADevices` – View details about a virtual MFA device that is enabled for the user\.
+ The `AllowManageOwnPasswords` statement allows the user to change their own password\. This statement also includes the `GetUser` action, which is required to view most of the information on the **My Security Credentials** page\.
+ The `AllowManageOwnAccessKeys` statement allows the user to create, update, and delete their own access keys\.
+ The `AllowManageOwnSigningCertificates` statement allows the user to upload, update, and delete their own signing certificates\.
+ The `AllowManageOwnSSHPublicKeys` statement allows the user to upload, update, and delete their own SSH public keys for CodeCommit\.
+ The `AllowManageOwnGitCredentials` statement allows the user to create, update, and delete their own Git credentials for CodeCommit\.
+ The `AllowManageOwnVirtualMFADevice` statement allows the user to create and delete their own virtual MFA device\. The resource ARN in this statement allows access to only an MFA device that has the same name as the currently signed\-in user\. Users can't create or delete any virtual MFA device other than their own\.
+ The `AllowManageOwnUserMFA` statement allows the user to view or manage the virtual, U2F, or hardware MFA device for their own user\. The resource ARN in this statement allows access to only the user's own IAM user\. Users can't view or manage the MFA device for other users\.
+ The `DenyAllExceptListedIfNoMFA` statement denies access to every action in all AWS services, except a few listed actions, but ***only if*** the user is not signed in with MFA\. The statement uses a combination of `"Deny"` and `"NotAction"` to explicitly deny access to every action that is not listed\. The items listed are not denied or allowed by this statement\. However, the actions are allowed by other statements in the policy\. For more information about the logic for this statement, see [NotAction with Deny](reference_policies_elements_notaction.md)\. If the user is signed in with MFA, then the `Condition` test fails and this statement does not deny any actions\. In this case, other policies or statements for the user determine the user's permissions\.

  This statement ensures that when the user is not signed in with MFA that they can perform only the listed actions\. In addition, they can perform the listed actions only if another statement or policy allows access to those actions\. This does not allow a user to create a password at sign\-in, because `iam:ChangePassword` action should not be allowed without MFA authorization\.

  The `...IfExists` version of the `Bool` operator ensures that if the `aws:MultiFactorAuthPresent` key is missing, the condition returns true\. This means that a user accessing an API with long\-term credentials, such as an access key, is denied access to the non\-IAM API operations\.

This policy does not allow users to view the **Users** page in the IAM console or use that page to access their own user information\. To allow this, add the `iam:ListUsers` action to the `AllowViewAccountInfo` statement and the `DenyAllExceptListedIfNoMFA` statement\. It also does not allow users to change their password on their own user page\. To allow this, add the `iam:CreateLoginProfile`, `iam:DeleteLoginProfile`, `iam:GetLoginProfile`, and `iam:UpdateLoginProfile` actions to the `AllowManageOwnPasswords` statement\. To also allow a user to change their password from their own user page without signing in using MFA, add the `iam:CreateLoginProfile` action to the `DenyAllExceptListedIfNoMFA` statement\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowViewAccountInfo",
            "Effect": "Allow",
            "Action": [
                "iam:GetAccountPasswordPolicy",
                "iam:GetAccountSummary",       
                "iam:ListVirtualMFADevices"
            ],
            "Resource": "*"
        },       
        {
            "Sid": "AllowManageOwnPasswords",
            "Effect": "Allow",
            "Action": [
                "iam:ChangePassword",
                "iam:GetUser"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "AllowManageOwnAccessKeys",
            "Effect": "Allow",
            "Action": [
                "iam:CreateAccessKey",
                "iam:DeleteAccessKey",
                "iam:ListAccessKeys",
                "iam:UpdateAccessKey"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "AllowManageOwnSigningCertificates",
            "Effect": "Allow",
            "Action": [
                "iam:DeleteSigningCertificate",
                "iam:ListSigningCertificates",
                "iam:UpdateSigningCertificate",
                "iam:UploadSigningCertificate"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "AllowManageOwnSSHPublicKeys",
            "Effect": "Allow",
            "Action": [
                "iam:DeleteSSHPublicKey",
                "iam:GetSSHPublicKey",
                "iam:ListSSHPublicKeys",
                "iam:UpdateSSHPublicKey",
                "iam:UploadSSHPublicKey"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "AllowManageOwnGitCredentials",
            "Effect": "Allow",
            "Action": [
                "iam:CreateServiceSpecificCredential",
                "iam:DeleteServiceSpecificCredential",
                "iam:ListServiceSpecificCredentials",
                "iam:ResetServiceSpecificCredential",
                "iam:UpdateServiceSpecificCredential"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "AllowManageOwnVirtualMFADevice",
            "Effect": "Allow",
            "Action": [
                "iam:CreateVirtualMFADevice",
                "iam:DeleteVirtualMFADevice"
            ],
            "Resource": "arn:aws:iam::*:mfa/${aws:username}"
        },
        {
            "Sid": "AllowManageOwnUserMFA",
            "Effect": "Allow",
            "Action": [
                "iam:DeactivateMFADevice",
                "iam:EnableMFADevice",
                "iam:ListMFADevices",
                "iam:ResyncMFADevice"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "DenyAllExceptListedIfNoMFA",
            "Effect": "Deny",
            "NotAction": [
                "iam:CreateVirtualMFADevice",
                "iam:EnableMFADevice",
                "iam:GetUser",
                "iam:ListMFADevices",
                "iam:ListVirtualMFADevices",
                "iam:ResyncMFADevice",
                "sts:GetSessionToken"
            ],
            "Resource": "*",
            "Condition": {
                "BoolIfExists": {
                    "aws:MultiFactorAuthPresent": "false"
                }
            }
        }
    ]
}
```