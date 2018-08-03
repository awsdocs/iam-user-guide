# Permissions Boundaries for IAM Identities<a name="access_policies_boundaries"></a>

AWS supports identity\-based policies, resource\-based policies, access control lists \(ACLs\), and AWS Organizations service control policies \(SCPs\)\. Those [policy types](access_policies.md#access_policy-types) can be categorized as *permissions policies* or *permissions boundaries*\. Permissions policies define the permissions for the object to which they’re attached\. These include identity\-based policies \(most common\), resource\-based policies, and ACLs\. A permissions boundary is an advanced feature in which you limit the maximum permissions that a principal can have\. These boundaries can be applied to AWS Organizations organizations or to IAM users or roles\.

You can use an AWS managed policy or a customer managed policy to set the boundary for a user or role\. That policy limits the maximum permissions for the user or role\.

For example, assume that the user named `AnayaIyengar` should be allowed to manage only Amazon S3, Amazon CloudWatch, and Amazon EC2\. To enforce this rule, you can use the following policy to set the permissions boundary for the `AnayaIyengar` user:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:*",
                "cloudwatch:*",
                "ec2:*"
            ],
            "Resource": "*"
        }
    ]
}
```

When you use a policy to set the permissions boundary for a user, it limits the user's permissions but does not provide permissions on its own\. In this example, the `AnayaIyengar` user boundary allows her to perform all operations in Amazon S3, CloudWatch, and Amazon EC2\. However, Anaya can never perform operations in any other service, including IAM, even if she has a permissions policy that allows it\. For example, you can add the following policy to the `AnayaIyengar` user:

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "iam:CreateUser",
    "Resource": "*"
  }
}
```

This policy allows the principal to create a user in IAM\. If you attach this policy to the `AnayaIyengar` user, and Anaya tries to create a user, the operation fails\. It fails because the policy evaluation logic checks the policy used as the permissions boundary, which does not allow the `iam:CreateUser` operation\. To allow Anaya to perform operations in AWS, you must add a permissions policy with actions in Amazon S3, Amazon CloudWatch, or Amazon EC2\. 

## Evaluating Effective Permissions with Boundaries<a name="access_policies_boundaries-eval-logic"></a>

The permissions boundary for a user or role limits the maximum permissions that the entity can have\. This can change the effective permissions for that user or role\. The effective permissions for an entity are the permissions granted when all of the policies that affect the user or role are evaluated\. For more information about how policies are evaluated, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.

AWS evaluates the policies that apply to a request context based on the policy type and category\. If a user or role has a permissions boundary, then operations are allowed only for the intersection of the permissions boundary and the permissions policies\. A permissions boundary limits the maximum permissions, but does not grant access on its own\. Permissions policies alone provide permission but can be limited by the permissions boundary\.

![\[effective_permissions_policy-types_Diagram\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/permissions_boundary.png)

Assume that the `people-admin` user has one permissions policy that allows only Amazon S3 operations\. Also assume that the policy used to set the permissions boundary allows only IAM operations\. In this case, the effective permissions of both policies implicitly deny access for all operations\. To provide the expected effective permissions to access IAM, you must attach the following permissions policy to the user\. This policy allows all IAM operations\.

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

When this policy is evaluated, it allows all IAM operations except those that are explicitly denied by the policy that is set as the permissions boundary\.

## Delegating Responsibility to Others Using Permissions Boundaries<a name="access_policies_boundaries-delegate"></a>

You can use permissions boundaries to delegate permissions management tasks, such as user creation, to IAM users in your account\. This permits others to perform tasks on your behalf within a specific boundary of permissions\.

For example, assume that María is the administrator of the X\-Company AWS account\. She wants to delegate user creation duties to Zhang\. However, she must ensure that Zhang creates users that adhere to the following company rules:
+ Users cannot use IAM to create or manage users, groups, roles, or policies\.
+ Users are denied access to the Amazon S3 `logs` bucket and cannot access the `i-1234567890abcdef0` Amazon EC2 instance\.
+ Users cannot remove their own boundary policies\.

To enforce these rules, María completes the following tasks, for which details are included below:

1. María creates the `XCompanyBoundaries` managed policy to use as a permissions boundary for all new users in the account\.

1. María creates the `DelegatedUserBoundary` managed policy and assigns it as the permissions boundary for Zhang\.

1. María creates the `DelegatedUserPermissions` managed policy and attaches it as a permissions policy for Zhang\.

1. María tells Zhang about his new responsibilities and limitations\.

**Task 1:** María must first create a managed policy to define the boundary for the new users\. María will allow Zhang to give users the permissions policies they need, but she wants those users to be restricted\. To do this, she creates the following customer managed policy with the name `XCompanyBoundaries`\. This policy allows users full access to several services, limited self\-managing access in IAM, and denies users access to the Amazon S3 logs bucket or the `i-1234567890abcdef0` Amazon EC2 instance\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ServiceBoundaries",
            "Effect": "Allow",
            "Action": [
                "s3:*",
                "cloudwatch:*",
                "ec2:*",
                "dynamodb:*",
                "iam:ListUsers"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AllowIndividualUserToSeeAndManageOnlyTheirOwnAccountInformation",
            "Effect": "Allow",
            "Action": [
                "iam:ChangePassword",
                "iam:CreateAccessKey",
                "iam:CreateLoginProfile",
                "iam:DeleteAccessKey",
                "iam:DeleteLoginProfile",
                "iam:GetAccessKeyLastUsed",
                "iam:GetLoginProfile",
                "iam:GetUser",
                "iam:GetUserPolicy",
                "iam:ListAccessKeys",
                "iam:ListAttachedUserPolicies",
                "iam:ListGroupsForUser",
                "iam:ListUserPolicies",
                "iam:UpdateAccessKey",
                "iam:UpdateLoginProfile",
                "iam:DeactivateMFADevice",
                "iam:EnableMFADevice",
                "iam:ListMFADevices",
                "iam:ResyncMFADevice",
                "iam:ListSigningCertificates",
                "iam:DeleteSigningCertificate",
                "iam:UpdateSigningCertificate",
                "iam:UploadSigningCertificate",
                "iam:ListSSHPublicKeys",
                "iam:GetSSHPublicKey",
                "iam:DeleteSSHPublicKey",
                "iam:UpdateSSHPublicKey",
                "iam:UploadSSHPublicKey"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "DenyS3Logs",
            "Effect": "Deny",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::logs",
                "arn:aws:s3:::logs/*"
            ]
        },
        {
            "Sid": "DenyEC2Production",
            "Effect": "Deny",
            "Action": "ec2:*",
            "Resource": "arn:aws:ec2:*:*:instance/i-1234567890abcdef0"
        }
    ]
}
```

Each statement serves a different purpose:

1. The `ServiceBoundaries` statement of this policy allows full access to the specified AWS services\. This means that a new user's actions in these services are limited only by the permissions policies that are attached to the user\. It also provides access to list all IAM users, which is necessary to navigate the **Users** page in the AWS Management Console\.

1. The `AllowIndividualUserToSeeAndManageOnlyTheirOwnAccountInformation` statement lets the users [manage only their own credentials](tutorial_users-self-manage-mfa-and-creds.md)\. This is important because if Zhang or another administrator gives a new user a permissions policy with full IAM access, that user could then change their own or other users' permissions\. This statement prevents that from happening\.

1. The `DenyS3Logs` statement explicitly denies access to the `logs` bucket\.

1. The `DenyEC2Production` statement explicitly denies access to the `i-1234567890abcdef0` instance\.

**Task 2:** María wants to allow Zhang to create all X\-Company users, but only with the `XCompanyBoundaries` permissions boundary\. She creates the following customer managed policy named `DelegatedUserBoundary`\. This policy defines the maximum permissions that Zhang can have\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "CreateOrChangeOnlyWithBoundary",
            "Effect": "Allow",
            "Action": [
                "iam:CreateUser",
                "iam:DeleteUserPolicy",
                "iam:AttachUserPolicy",
                "iam:DetachUserPolicy",
                "iam:PutUserPermissionsBoundary"
            ],
            "Resource": "*",
            "Condition": {"StringEquals": 
                {"iam:PermissionsBoundary": "arn:aws:iam::111122223333:policy/XCompanyBoundaries"}}
        },
        {
            "Sid": "CloudWatchAndOtherIAMTasks",
            "Effect": "Allow",
            "Action": [
                "cloudwatch:*",
                "iam:GetUser",
                "iam:ListUsers",
                "iam:DeleteUser",
                "iam:UpdateUser",
                "iam:CreateAccessKeys",
                "iam:CreateLoginProfile",
                "iam:GetAccountPasswordPolicy",
                "iam:GetLoginProfile",
                "iam:*Group*",
                "iam:CreatePolicy",
                "iam:DeletePolicy",
                "iam:DeletePolicyVersion",
                "iam:GetPolicy",
                "iam:GetPolicyVersion",
                "iam:GetUserPolicy",
                "iam:GetRolePolicy",
                "iam:ListPolicies",
                "iam:ListPolicyVersions",
                "iam:ListEntitiesForPolicy",
                "iam:ListUserPolicies",
                "iam:ListAttachedUserPolicies",
                "iam:ListRolePolicies",
                "iam:ListAttachedRolePolicies",
                "iam:PutUserPolicy",
                "iam:SetDefaultPolicyVersion",
                "iam:SimulatePrincipalPolicy",
                "iam:SimulateCustomPolicy" 
            ],
            "Resource": "*"
        },
        {
            "Sid": "NoBoundaryPolicyEdit",
            "Effect": "Deny",
            "Action": [
                "iam:CreatePolicyVersion",
                "iam:DeletePolicy",
                "iam:DeletePolicyVersion",
                "iam:SetDefaultPolicyVersion"
            ],
            "Resource": [
                "arn:aws:iam::123456789012:policy/XCompanyBoundaries",
                "arn:aws:iam::123456789012:policy/DelegatedUserBoundary"
            ]
        },
        {
            "Sid": "NoBoundaryUserDelete",
            "Effect": "Deny",
            "Action": "iam:DeleteUserPermissionsBoundary",
            "Resource": "*"
        }
    ]
}
```

Each statement serves a different purpose:

1. The `CreateOrChangeOnlyWithBoundary` statement allows Zhang to create IAM users but only if he uses the `XCompanyBoundaries` policy to set the permissions boundary\. This statement also allows him to set the permissions boundary for existing users but only using that same policy\. Finally, this statement allows Zhang to manage permissions policies for users with this permissions boundary set\.

1. The `CloudWatchAndOtherIAMTasks` statement allows Zhang to complete other user, group, and policy management tasks\. Note that Zhang does not have the permission to delete the permissions boundary from himself or any other user\.

1. The `NoBoundaryPolicyEdit` statement denies Zhang access to update the `XCompanyBoundaries` policy\. He is not allowed to change any policy that is used to set the permissions boundary for himself or other users\.

1. The `NoBoundaryUserDelete` statement denies Zhang access to delete the permissions boundary for himself or other users\.

María then assigns the `DelegatedUserBoundary` policy [as the permissions boundary](id_users_change-permissions.md#users_change_permissions-set-boundary-console) for the `Zhang` user\. 

**Task 3:** Because the permissions boundary limits the maximum permissions, but does not grant access on its own, Maria must create a permissions policy for Zhang\. She creates the following policy named `DelegatedUserPermissions`\. This policy defines the operations that Zhang can perform, within the defined boundary\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "IAM",
            "Effect": "Allow",
            "Action": "iam:*",
            "Resource": "*"
        },
        {
            "Sid": "CloudWatchLimited",
            "Effect": "Allow",
            "Action": [
                "cloudwatch:GetDashboard",
                "cloudwatch:GetMetricData",
                "cloudwatch:ListDashboards",
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:ListMetrics"
            ],
            "Resource": "*"
        },
        {
            "Sid": "S3BucketContents",
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::ZhangBucket"
        }
    ]
}
```

Each statement serves a different purpose:

1. The `IAM` statement of the policy allows Zhang full access to IAM\. However, because his permissions boundary allows only some IAM operations, his effective IAM permissions are limited only by his permissions boundary\.

1. The `CloudWatchLimited` statement allows Zhang to perform five actions in CloudWatch\. His permissions boundary allows all actions in CloudWatch, so his effective CloudWatch permissions are limited only by his permissions policy\.

1. The `S3BucketContents` statement allows Zhang to list the `ZhangBucket` Amazon S3 bucket\. However, his permissions boundary does not allow any Amazon S3 action, he cannot perform any S3 operations, regardless of his permissions policy\.

María then attaches the `DelegatedUserPermissions` policy as the permissions policy for the `Zhang` user\. 

**Task 4:** She gives Zhang instructions to create a new user\. She tells him that he can create new users with any permissions that they need, but he must assign them the `XCompanyBoundaries` policy as a permissions boundary\.

Zhang completes the following tasks:

1. Zhang [creates a user](id_users_create.md#id_users_create_console) with the AWS Management Console\. He types the user name `Nikhil` and enables console access for the user\. 

1. On the **Set permissions** page, Zhang chooses the **IAMFullAccess** and ** AmazonS3ReadOnlyAccess** permissions policies that allow Nikhil to do his work\. 

1. Zhang skips the **Set permissions boundary** section, forgetting María's instructions\.

1. Zhang reviews the user details and chooses **Create user**\.

   The operation fails and access is denied\. Zhang's `DelegatedUserBoundary` permissions boundary requires that any user he creates have the `XCompanyBoundaries` policy used as a permissions boundary\.

1. Zhang returns to the previous page\. In the **Set permissions boundary** section, he chooses the `XCompanyBoundaries` policy\. 

1. Zhang reviews the user details and chooses **Create user**\.

   The user is created\. 

When Nikhil signs in, he has access to IAM and Amazon S3, except those operations that denied by the permissions boundary\. For example, he can change his own password in IAM but can't create another user or edit his policies\. He can view and manage all the buckets in Amazon S3 except the `logs` bucket\.