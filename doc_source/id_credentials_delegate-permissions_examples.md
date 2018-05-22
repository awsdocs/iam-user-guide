# Example Policies for Administering IAM Resources<a name="id_credentials_delegate-permissions_examples"></a>

Following are examples of IAM policies that allow users to perform tasks associated with managing IAM users, groups, and credentials\. This includes policies that permit users manage their own passwords, access keys, and multi\-factor authentication \(MFA\) devices\.

For examples of policies that let users perform tasks with other AWS services, like Amazon S3, Amazon EC2, and DynamoDB, see [Example Policies](access_policies_examples.md)\. 

**Topics**
+ [Allow Users to Manage Their Own Passwords \(from the My Password Page\)](#creds-policies-password-self)
+ [Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys](#creds-policies-credentials)
+ [Allow a User to List the Account's Groups, Users, Policies, and More for Reporting Purposes](#iampolicy-example-userlistall)
+ [Allow a User to Manage a Group's Membership](#iampolicy-example-usermanagegroups)
+ [Allow a User to Manage IAM Users](#creds-policies-users)
+ [Allow Users to Set Account Password Policy](#creds-policies-set-password-policy)
+ [Allow Users to Generate and Retrieve IAM Credential Reports](#iampolicy-generate-credential-report)
+ [Allow Users to Manage Only Their Own Virtual MFA Devices](#creds-policies-mfa-console)
+ [Allow All IAM Actions \(Admin Access\)](#creds-policies-all-iam)

## Allow Users to Manage Their Own Passwords \(from the My Password Page\)<a name="creds-policies-password-self"></a>

If the account's [password policy](id_credentials_passwords_account-policy.md) is set to allow all users to change their own passwords, you don't need to attach any permissions to individual users or groups\. All users are able to go to the [My Password page](id_credentials_passwords.md#id_credentials_passwords_user-change-own) in the AWS Management Console that lets them change their own password\. 

If the account's password policy is *not* set to allow all users to change their own passwords, you can attach the following policy to selected users or groups to allow those users to change only their own passwords\. This policy only allows users to use the special [My Password page](https://console.aws.amazon.com/iam/home#my_password) in the console; it does not give users permissions to work through the dashboard in the IAM console\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "iam:GetAccountPasswordPolicy",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "iam:ChangePassword",
      "Resource": "arn:aws:iam::account-id-without-hyphens:user/${aws:username}"
    }
  ]
}
```

If users do not use the console to change their own password, they do not need the `iam:GetAccountPasswordPolicy` permission\. They can instead run the [http://docs.aws.amazon.com/cli/latest/reference/iam/change-password.html](http://docs.aws.amazon.com/cli/latest/reference/iam/change-password.html) command from the AWS CLI, or make a request with the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ChangePassword.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ChangePassword.html) action\.

For information about letting selected users manage passwords using the **Users** section of the IAM console, see the next section\. 

## Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys<a name="creds-policies-credentials"></a>

The following policy allows users to perform these actions in the AWS Management Console:
+ Create, change, or remove their own password\. This includes the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateLoginProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateLoginProfile.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteLoginProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteLoginProfile.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetLoginProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetLoginProfile.html), and [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateLoginProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateLoginProfile.html) actions\. 
+ Create or delete their own access key \(access key ID and secret access key\)\. This includes the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccessKeys.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccessKeys.html), and [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html) actions\. 
+ Create or delete their own SSH keys\. This includes the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UploadSSHPublicKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UploadSSHPublicKey.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteSSHPublicKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteSSHPublicKey.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetSSHPublicKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetSSHPublicKey.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListSSHPublicKeys.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListSSHPublicKeys.html), and [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateSSHPublicKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateSSHPublicKey.html) actions\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "iam:*LoginProfile",
        "iam:*AccessKey*",
        "iam:*SSHPublicKey*"
      ],
      "Resource": "arn:aws:iam::account-id-without-hyphens:user/${aws:username}"
    },
    {
      "Effect": "Allow",
      "Action": [
        "iam:ListAccount*",
        "iam:GetAccountSummary",
        "iam:GetAccountPasswordPolicy",
        "iam:ListUsers"
      ],
      "Resource": "*"
    }
  ]
}
```

The actions in the preceding policy include wildcards \(for example, `iam:*LoginProfile`,`iam:*AccessKey*`, and `iam:*SSHPublicKey*`\)\. This is a convenient way to include a set of related actions\. If you want to remove permissions for any one of the related actions, you must instead list each of the individual actions\. For example, if you don't want users to be able to delete a password, you must individually list `iam:CreateLoginProfile`, `iam:GetLoginProfile`, and `iam:UpdateLoginProfile`, and omit `iam:DeleteLoginProfile`\. 

The second element in the Statement array, including `iam:GetAccountSummary`, `iam:GetAccountPasswordPolicy`, `iam:ListAccount*`, and `iam:ListUsers` permissions, allows the user to see certain information on the IAM console dashboard, such as whether a password policy is enabled, how many groups the account has, what the account URL and alias are, etc\. For example, the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountSummary.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountSummary.html) action returns an object that contains a collection of information about the account that is then displayed on the IAM console dashboard\. 

The following policy is like the previous one but excludes the permissions that are needed only for console access\. This policy lets users manage their credentials with the [AWS CLI](http://aws.amazon.com/cli/), Tools for Windows PowerShell, the [AWS SDKs](http://aws.amazon.com/tools/), or the IAM HTTP query API\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:*LoginProfile",
      "iam:*AccessKey*",
      "iam:*SSHPublicKey*"
    ],
    "Resource": "arn:aws:iam::account-id-without-hyphens:user/${aws:username}"
  }
}
```

## Allow a User to List the Account's Groups, Users, Policies, and More for Reporting Purposes<a name="iampolicy-example-userlistall"></a>

The following policy allows the user to call any IAM action that starts with the string `Get` or `List`\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:Get*",
      "iam:List*"
    ],
    "Resource": "*"
  }
}
```

The benefit of using `Get*` and `List*` actions is that if new types of entities are added to IAM in the future, the access granted in the policy to `Get*` and `List*` all actions would automatically allow the user to list those new entities\.

## Allow a User to Manage a Group's Membership<a name="iampolicy-example-usermanagegroups"></a>

The following policy allows the user to update the membership of the group called *MarketingGroup*\. To use the following policy, replace `ACCOUNT-ID-WITHOUT-HYPHENS` with your AWS account ID\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:AddUserToGroup",
      "iam:RemoveUserFromGroup",
      "iam:GetGroup"
    ],
    "Resource": "arn:aws:iam::account-id-without-hyphens:group/MarketingGroup"
  }
}
```

## Allow a User to Manage IAM Users<a name="creds-policies-users"></a>

The following policy allows a user to perform all the tasks associated with managing IAM users but not to perform actions on other entities, such as creating groups or policies\. Allowed actions include these: 
+ Creating the user \(the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateUser.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateUser.html) action\)\. 
+ Deleting the user\. This task requires permissions to perform all of the following actions: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteSigningCertificate.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteSigningCertificate.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteLoginProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteLoginProfile.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html), and [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUser.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUser.html)\. 
+ Listing users in the account and in groups \(the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html) and [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html) actions\)\. 
+ Listing and removing policies for the user \(the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserPolicies.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserPolicies.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachUserPolicy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachUserPolicy.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUserPolicy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUserPolicy.html) actions\) 
+ Renaming or changing the path for the user \(the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateUser.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateUser.html) action\)\. The `Resource` element must include an ARN that covers both the source path and the target path\. For more information on paths, see [Friendly Names and Paths](reference_identifiers.md#identifiers-friendly-names)\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowUsersToPerformUserActions",
      "Effect": "Allow",
      "Action": [
        "iam:CreateUser",
        "iam:ListUsers",
        "iam:GetUser",
        "iam:UpdateUser",
        "iam:DeleteUser",
        "iam:ListGroupsForUser",
        "iam:ListUserPolicies",
        "iam:ListAttachedUserPolicies",
        "iam:DeleteSigningCertificate",
        "iam:DeleteLoginProfile",
        "iam:RemoveUserFromGroup",
        "iam:DetachUserPolicy",
        "iam:DeleteUserPolicy"
      ],
      "Resource": "*"
    },
    {
      "Sid": "AllowUsersToSeeStatsOnIAMConsoleDashboard",
      "Effect": "Allow",
      "Action": [
        "iam:GetAccount*",
        "iam:ListAccount*"
      ],
      "Resource": "*"
    }
  ]
}
```

A number of the permissions included in the preceding policy allow the user to perform tasks in the AWS Management Console\. Users who perform user\-related tasks from the [AWS CLI](http://aws.amazon.com/cli/), the [AWS SDKs](http://aws.amazon.com/tools/), or the IAM HTTP query API only might not need certain permissions\. For example, if users already know the ARN of policies to detach from a user, they do not need the `iam:ListAttachedUserPolicies` permission\. The exact list of permissions that a user requires depends on the tasks that the user must perform while managing other users\. 

The following permissions in the policy allow access to user tasks via the AWS Management Console:
+ `iam:GetAccount*`
+ `iam:ListAccount*`

## Allow Users to Set Account Password Policy<a name="creds-policies-set-password-policy"></a>

You might give some users permissions to get and update your AWS account's [password policy](id_credentials_passwords_account-policy.md)\. The following example policy grants these permissions\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:GetAccountPasswordPolicy",
      "iam:UpdateAccountPasswordPolicy"
    ],
    "Resource": "*"
  }
}
```

## Allow Users to Generate and Retrieve IAM Credential Reports<a name="iampolicy-generate-credential-report"></a>

You can give users permission to generate and download a report that lists all users in your AWS account and the status of their various credentials, including passwords, access keys, MFA devices, and signing certificates\. The following example policy grants these permissions\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:GenerateCredentialReport",
      "iam:GetCredentialReport"
    ],
    "Resource": "*"
  }
}
```

For more information about credential reports, see [Getting Credential Reports for Your AWS Account](id_credentials_getting-report.md)\.

## Allow Users to Manage Only Their Own Virtual MFA Devices<a name="creds-policies-mfa-console"></a>

A [virtual MFA device](id_credentials_mfa_enable_virtual.md) is a software implementation of a device that provides one\-time passwords\. Virtual MFA devices are hosted on a physical hardware device \(typically a smartphone\)\. In order to configure a virtual MFA device, you must have access to the physical device where the virtual MFA device is hosted\. If your users create virtual MFA devices inside a smartphone app on their own smartphone, you might want to let them configure the devices themselves\. For more about using virtual MFA devices with IAM, see [Enabling a Virtual Multi\-factor Authentication \(MFA\) Device](id_credentials_mfa_enable_virtual.md)\.

The following policy allows a user to configure and manage his or her own virtual MFA device from the AWS Management Console or using any of the command\-line tools\. The policy allows only MFA\-authenticated users to deactivate and delete their own virtual MFA devices\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowUsersToCreateEnableResyncDeleteTheirOwnVirtualMFADevice",
      "Effect": "Allow",
      "Action": [
        "iam:CreateVirtualMFADevice",
        "iam:EnableMFADevice",
        "iam:ResyncMFADevice",
        "iam:DeleteVirtualMFADevice"
      ],
      "Resource": [
        "arn:aws:iam::account-id-without-hyphens:mfa/${aws:username}",
        "arn:aws:iam::account-id-without-hyphens:user/${aws:username}"
      ]
    },
    {
      "Sid": "AllowUsersToDeactivateTheirOwnVirtualMFADevice",
      "Effect": "Allow",
      "Action": [
        "iam:DeactivateMFADevice"
      ],
      "Resource": [
        "arn:aws:iam::account-id-without-hyphens:mfa/${aws:username}",
        "arn:aws:iam::account-id-without-hyphens:user/${aws:username}"
      ],
      "Condition": {
        "Bool": {
          "aws:MultiFactorAuthPresent": true
        }
      }
    },
    {
      "Sid": "AllowUsersToListMFADevicesandUsersForConsole",
      "Effect": "Allow",
      "Action": [
        "iam:ListMFADevices",
        "iam:ListVirtualMFADevices",
        "iam:ListUsers"
      ],
      "Resource": "*"
    }
  ]
}
```

**Note**  
The action `iam:DeleteVirtualMFADevice` is *not* subject to the MFA condition check because it is included in the first statement instead of the second\. This isn't a security concern because you can only delete an MFA device after you deactivate it, which the user can do only if they are MFA authenticated\. This prevents a situation that can occur if you cancel the **Create MFA Device** wizard after it creates the device but before it validates the two codes and associates it with the user\. Because the user is not yet MFA authenticated at this point, the wizard \(which operates with the user's permissions\) fails to clean up the device if the policy requires MFA authentication to delete the device\.

## Allow All IAM Actions \(Admin Access\)<a name="creds-policies-all-iam"></a>

You might give some users administrative permissions to perform all actions in IAM, including managing passwords, access keys, MFA devices, and user certificates\. The following example policy grants these permissions\. 

**Warning**  
When you give a user full access to IAM, there is no limit to the permissions that user can grant to him/herself or others\. The user can create new IAM entities \(users or roles\) and grant those entities full access to all resources in your AWS account\. When you give a user full access to IAM, you are effectively giving them full access to all resources in your AWS account\. This includes access to delete all resources\. You should grant these permissions to only trusted administrators, and you should enforce multi\-factor authentication \(MFA\) for these administrators\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "iam:*",
    "Resource": "*"
  }
}
```