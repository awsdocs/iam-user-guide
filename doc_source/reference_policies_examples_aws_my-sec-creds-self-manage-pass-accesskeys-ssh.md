# AWS: Allows IAM users to manage their own password, access keys, and SSH public keys on the my security credentials page<a name="reference_policies_examples_aws_my-sec-creds-self-manage-pass-accesskeys-ssh"></a>

This example shows how you might create a policy that allows IAM users to manage their own password, access keys, and X\.509 certificates on the **My Security Credentials** page\. This AWS Management Console page displays account information such as the account ID and canonical user ID\. Users can also view and edit their own passwords, access keys, MFA devices, X\.509 certificates, SSH keys, and Git credentials\. This example policy includes the permissions that are required to view and edit only their password, access keys, and X\.509 certificate\. To allow users to manage all of their own credentials with MFA, see [AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage.md)\. To allow users to manage their own credentials without using MFA, see [AWS: Allows IAM users to manage their own credentials on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage-no-mfa.md)\.

To learn how users can access the **My Security Credentials** page, see [How IAM users change their own password \(console\)](id_credentials_passwords_user-change-own.md#ManagingUserPwdSelf-Console)\.

**What does this policy do? **
+ The `AllowViewAccountInfo` statement allows the user to view account\-level information\. These permissions must be in their own statement because they do not support or do not need to specify a resource ARN\. Instead the permissions specify `"Resource" : "*"`\. This statement includes the following actions that allow the user to view specific information: 
  + `GetAccountPasswordPolicy` – View the account password requirements while changing their own IAM user password\.
  + `GetAccountSummary` – View the account ID and the account [canonical user ID](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html#FindingCanonicalId)\.
+ The `AllowManageOwnPasswords` statement allows the user to change their own password\. This statement also includes the `GetUser` action, which is required to view most of the information on the **My Security Credentials** page\.
+ The `AllowManageOwnAccessKeys` statement allows the user to create, update, and delete their own access keys\.
+ The `AllowManageOwnSSHPublicKeys` statement allows the user to upload, update, and delete their own SSH public keys for CodeCommit\.

This policy does not allow users to view or manage their own MFA devices\. They also cannot view the **Users** page in the IAM console or use that page to access their own user information\. To allow this, add the `iam:ListUsers` action to the `AllowViewAccountInfo` statement\. It also does not allow users to change their password on their own user page\. To allow this, add the `iam:CreateLoginProfile`, `iam:DeleteLoginProfile`, `iam:GetLoginProfile`, and `iam:UpdateLoginProfile` actions to the `AllowManageOwnPasswords` statement\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowViewAccountInfo",
            "Effect": "Allow",
            "Action": [
                "iam:GetAccountPasswordPolicy",
                "iam:GetAccountSummary"
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
        }
    ]
}
```