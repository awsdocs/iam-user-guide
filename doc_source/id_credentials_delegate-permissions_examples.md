# Example Policies for Administering IAM Resources<a name="id_credentials_delegate-permissions_examples"></a>

Following are examples of IAM policies that allow users to perform tasks associated with managing IAM users, groups, and credentials\. This includes policies that permit users manage their own passwords, access keys, and multi\-factor authentication \(MFA\) devices\.

For examples of policies that let users perform tasks with other AWS services, like Amazon S3, Amazon EC2, and DynamoDB, see [Example IAM Identity\-Based Policies](access_policies_examples.md)\. 

**Topics**
+ [Allow a User to List the Account's Groups, Users, Policies, and More for Reporting Purposes](#iampolicy-example-userlistall)
+ [Allow a User to Manage a Group's Membership](#iampolicy-example-usermanagegroups)
+ [Allow a User to Manage IAM Users](#creds-policies-users)
+ [Allow Users to Set Account Password Policy](#creds-policies-set-password-policy)
+ [Allow Users to Generate and Retrieve IAM Credential Reports](#iampolicy-generate-credential-report)
+ [Allow All IAM Actions \(Admin Access\)](#creds-policies-all-iam)

## Allow a User to List the Account's Groups, Users, Policies, and More for Reporting Purposes<a name="iampolicy-example-userlistall"></a>

The following policy allows the user to call any IAM action that starts with the string `Get` or `List`, and to generate reports\. To view the example policy, see [IAM: Allows Read\-Only Access to the IAM Console](reference_policies_examples_iam_read-only-console.md)\. 

## Allow a User to Manage a Group's Membership<a name="iampolicy-example-usermanagegroups"></a>

The following policy allows the user to update the membership of the group called *MarketingGroup*\. To view the example policy, see [IAM: Allows Managing a Group's Membership Programmatically and in the Console](reference_policies_examples_iam_manage-group-membership.md)\. 

## Allow a User to Manage IAM Users<a name="creds-policies-users"></a>

The following policy allows a user to perform all the tasks associated with managing IAM users but not to perform actions on other entities, such as creating groups or policies\. Allowed actions include these: 
+ Creating the user \(the [https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateUser.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateUser.html) action\)\. 
+ Deleting the user\. This task requires permissions to perform all of the following actions: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteSigningCertificate.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteSigningCertificate.html), [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteLoginProfile.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteLoginProfile.html), [https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveUserFromGroup.html), and [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUser.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUser.html)\. 
+ Listing users in the account and in groups \(the [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html), [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html) and [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListGroupsForUser.html) actions\)\. 
+ Listing and removing policies for the user \(the [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserPolicies.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserPolicies.html), [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAttachedUserPolicies.html), [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachUserPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachUserPolicy.html), [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUserPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteUserPolicy.html) actions\) 
+ Renaming or changing the path for the user \(the [https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateUser.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateUser.html) action\)\. The `Resource` element must include an ARN that covers both the source path and the target path\. For more information on paths, see [Friendly Names and Paths](reference_identifiers.md#identifiers-friendly-names)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowUsersToPerformUserActions",
            "Effect": "Allow",
            "Action": [
                "iam:ListPolicies",
                "iam:GetPolicy",
                "iam:UpdateUser",
                "iam:AttachUserPolicy",
                "iam:ListEntitiesForPolicy",
                "iam:DeleteUserPolicy",
                "iam:DeleteUser",
                "iam:ListUserPolicies",
                "iam:CreateUser",
                "iam:RemoveUserFromGroup",
                "iam:AddUserToGroup",
                "iam:GetUserPolicy",
                "iam:ListGroupsForUser",
                "iam:PutUserPolicy",
                "iam:ListAttachedUserPolicies",
                "iam:ListUsers",
                "iam:GetUser",
                "iam:DetachUserPolicy"
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

You might give some users permissions to get and update your AWS account's [password policy](id_credentials_passwords_account-policy.md)\. To view the example policy, see [IAM: Allows Setting the Account Password Requirements Programmatically and in the Console](reference_policies_examples_iam_set-account-pass-policy.md)\. 

## Allow Users to Generate and Retrieve IAM Credential Reports<a name="iampolicy-generate-credential-report"></a>

You can give users permission to generate and download a report that lists all users in your AWS account\. The report also lists the status of various user credentials, including passwords, access keys, MFA devices, and signing certificates\. For more information about credential reports, see [Getting Credential Reports for Your AWS Account](id_credentials_getting-report.md)\. To view the example policy, see [IAM: Generate and Retrieve IAM Credential Reports](reference_policies_examples_iam-credential-report.md)\. 

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