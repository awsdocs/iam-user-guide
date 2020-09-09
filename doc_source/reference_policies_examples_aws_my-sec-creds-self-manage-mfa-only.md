# AWS: Allows MFA\-authenticated IAM users to manage their own MFA device on the my security credentials page<a name="reference_policies_examples_aws_my-sec-creds-self-manage-mfa-only"></a>

This example shows how you might create a policy that allows IAM users that are authenticated through [multi\-factor authentication \(MFA\)](id_credentials_mfa.md) to manage their own MFA device on the **My Security Credentials** page\. This AWS Management Console page displays account and user information, but the user can only view and edit their own MFA device\. To allow users to manage all of their own credentials with MFA, see [AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage.md)\.

**Note**  
If an IAM user with this policy is not MFA\-authenticated, this policy denies access to all AWS actions except those necessary to authenticate using MFA\. To use the AWS CLI and AWS API, IAM users must first retrieve their MFA token using the AWS STS [GetSessionToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html) operation and then use that token to authenticate the desired operation\. Other policies, such as resource\-based policies or other identity\-based policies can allow actions in other services, This policy will deny that access if the IAM user is not MFA\-authenticated\.

To learn how users can access the **My Security Credentials** page, see [How IAM users change their own password \(console\)](id_credentials_passwords_user-change-own.md#ManagingUserPwdSelf-Console)\.

**What does this policy do? **
+ The `AllowViewAccountInfo` statement allows the user to view details about a virtual MFA device that is enabled for the user\. This permission must be in its own statement because it does not support specifying a resource ARN\. Instead you must specify `"Resource" : "*"`\.
+ The `AllowManageOwnVirtualMFADevice` statement allows the user to create and delete their own virtual MFA device\. The resource ARN in this statement allows access to only an MFA device that has the same name as the currently signed\-in user\. Users can't create or delete any virtual MFA device other than their own\.
+ The `AllowManageOwnUserMFA` statement allows the user to view or manage their own virtual, U2F, or hardware MFA device\. The resource ARN in this statement allows access to only the user's own IAM user\. Users can't view or manage the MFA device for other users\.
+ The `DenyAllExceptListedIfNoMFA` statement denies access to every action in all AWS services, except a few listed actions, but ***only if*** the user is not signed in with MFA\. The statement uses a combination of `"Deny"` and `"NotAction"` to explicitly deny access to every action that is not listed\. The items listed are not denied or allowed by this statement\. However, the actions are allowed by other statements in the policy\. For more information about the logic for this statement, see [NotAction with Deny](reference_policies_elements_notaction.md)\. If the user is signed in with MFA, then the `Condition` test fails and this statement does not deny any actions\. In this case, other policies or statements for the user determine the user's permissions\.

  This statement ensures that when the user is not signed in with MFA, they can perform only the listed actions\. In addition, they can perform the listed actions only if another statement or policy allows access to those actions\.

  The `...IfExists` version of the `Bool` operator ensures that if the `aws:MultiFactorAuthPresent` key is missing, the condition returns true\. This means that a user accessing an API operation with long\-term credentials, such as an access key, is denied access to the non\-IAM API operations\.

This policy does not allow users to view the **Users** page in the IAM console or use that page to access their own user information\. To allow this, add the `iam:ListUsers` action to the `AllowViewAccountInfo` statement and the `DenyAllExceptListedIfNoMFA` statement\.

**Warning**  
Do not allow add permission to delete an MFA device without MFA authentication\. Users with this policy might attempt to assign themselves an MFA device and receive an error that they are not authorized to perform `iam:DeleteVirtualMFADevice`\. If this happens, **do not** add that permission to the `DenyAllExceptListedIfNoMFA` statement\. Users that are not authenticated using MFA should never be allowed to delete their MFA device\. Users might see this error if they previously began assigning a virtual MFA device to their user and cancelled the process\. To resolve this issue, you or another administrator must delete the user's existing MFA device using the AWS CLI or AWS API\. For more information, see [I Am not authorized to perform: iam:DeleteVirtualMFADevice](troubleshoot_general.md#troubleshoot_general_access-denied-delete-mfa)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowViewAccountInfo",
            "Effect": "Allow",
            "Action": "iam:ListVirtualMFADevices",
            "Resource": "*"
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
                "iam:GetUser",
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
                "BoolIfExists": {"aws:MultiFactorAuthPresent": "false"}
            }
        }
    ]
}
```