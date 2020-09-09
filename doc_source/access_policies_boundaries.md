# Permissions boundaries for IAM entities<a name="access_policies_boundaries"></a>

AWS supports *permissions boundaries* for IAM entities \(users or roles\)\. A permissions boundary is an advanced feature for using a managed policy to set the maximum permissions that an identity\-based policy can grant to an IAM entity\. An entity's permissions boundary allows it to perform only the actions that are allowed by both its identity\-based policies and its permissions boundaries\.

For more information about policy types, see [Policy types](access_policies.md#access_policy-types)\.

You can use an AWS managed policy or a customer managed policy to set the boundary for an IAM entity \(user or role\)\. That policy limits the maximum permissions for the user or role\.

For example, assume that the IAM user named `ShirleyRodriguez` should be allowed to manage only Amazon S3, Amazon CloudWatch, and Amazon EC2\. To enforce this rule, you can use the following policy to set the permissions boundary for the `ShirleyRodriguez` user:

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

When you use a policy to set the permissions boundary for a user, it limits the user's permissions but does not provide permissions on its own\. In this example, the policy sets the maximum permissions of `ShirleyRodriguez` as all operations in Amazon S3, CloudWatch, and Amazon EC2\. Shirley can never perform operations in any other service, including IAM, even if she has a permissions policy that allows it\. For example, you can add the following policy to the `ShirleyRodriguez` user:

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

This policy allows creating a user in IAM\. If you attach this permissions policy to the `ShirleyRodriguez` user, and Shirley tries to create a user, the operation fails\. It fails because the permissions boundary does not allow the `iam:CreateUser` operation\. Given these two policies, Shirley does not have permission to perform any operations in AWS\. You must add a different permissions policy to allow actions in other services, such as Amazon S3\. Alternatively, you could update the permissions boundary to allow her to create a user in IAM\.

## Evaluating effective permissions with boundaries<a name="access_policies_boundaries-eval-logic"></a>

The permissions boundary for an IAM entity \(user or role\) sets the maximum permissions that the entity can have\. This can change the effective permissions for that user or role\. The effective permissions for an entity are the permissions that are granted by all the policies that affect the user or role\. Within an account, the permissions for an entity can be affected by identity\-based policies, resource\-based policies, permissions boundaries, Organizations SCPs, or session policies\. For more information about the different types of policies, see [Policies and permissions in IAM](access_policies.md)\.

If any one of these policy types explicitly denies access for an operation, then the request is denied\. The permissions granted to an entity by multiple permissions types are more complex\. For more details about how AWS evaluates policies, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.

**Identity\-based policies with boundaries** – Identity\-based policies are inline or managed policies that are attached to a user, group of users, or role\. Identity\-based policies grant permission to the entity, and permissions boundaries limit those permissions\. The effective permissions are the intersection of both policy types\. An explicit deny in either of these policies overrides the allow\.

![\[Evaluation of identity-based policies and permissions boundaries\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/permissions_boundary.png)

**Resource\-based policies** – Resource\-based policies control how the specified principal can access the resource to which the policy is attached\. Within an account, an implicit deny in a permissions boundary does not limit the permissions granted by a resource\-based policy\. Permissions boundaries reduce permissions that are granted to an entity by identity\-based policies, and then resource\-based policies provide additional permissions to the entity\. In this case, the effective permissions are everything that is allowed by the resource\-based policy *and* the intersection of the permissions boundary and the identity\-based policy\. An explicit deny in any of these policies overrides the allow\.

![\[Evaluation of a resource-based policy, permissions boundary, and identity-based policy\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/EffectivePermissions-rbp-boundary-id.png)

**Organizations SCPs** – SCPs are applied to an entire AWS account\. They limit permissions for every request made by a principal within the account\. An IAM entity \(user or role\) can make a request that is affected by an SCP, a permissions boundary, and an identity\-based policy\. In this case, the request is allowed only if all three policy types allow it\. The effective permissions are the intersection of all three policy types\. An explicit deny in any of these policies overrides the allow\.

![\[Evaluation of an SCP, permissions boundary, and identity-based policy\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/EffectivePermissions-scp-boundary-id.png)

You can learn [whether your account is a member of an organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_details.html#orgs_view_account) in AWS Organizations\. Organization members might be affected by an SCP\. To view this data using the AWS CLI command or AWS API operation, you must have permissions for the `organizations:DescribeOrganization` action for your Organizations entity\. You must have additional permissions to perform the operation in the Organizations console\. To learn whether an SCP is denying access to a specific request, or to change your effective permissions, contact your AWS Organizations administrator\.

**Session policies** – Session policies are advanced policies that you pass as a parameter when you programmatically create a temporary session for a role or federated user\. The permissions for a session come from the IAM entity \(user or role\) used to create the session and from the session policy\. The entity's identity\-based policy permissions are limited by the session policy and the permissions boundary\. The effective permissions for this set of policy types are the intersection of all three policy types\. An explicit deny in any of these policies overrides the allow\. For more information about session policies, see [Session Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#policies_session)\.

![\[Evaluation of a session policy, permissions boundary, and identity-based policy\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/EffectivePermissions-session-boundary-id.png)

## Delegating responsibility to others using permissions boundaries<a name="access_policies_boundaries-delegate"></a>

You can use permissions boundaries to delegate permissions management tasks, such as user creation, to IAM users in your account\. This permits others to perform tasks on your behalf within a specific boundary of permissions\.

For example, assume that María is the administrator of the X\-Company AWS account\. She wants to delegate user creation duties to Zhang\. However, she must ensure that Zhang creates users that adhere to the following company rules:
+ Users cannot use IAM to create or manage users, groups, roles, or policies\.
+ Users are denied access to the Amazon S3 `logs` bucket and cannot access the `i-1234567890abcdef0` Amazon EC2 instance\.
+ Users cannot remove their own boundary policies\.

To enforce these rules, María completes the following tasks, for which details are included below:

1. María creates the `XCompanyBoundaries` managed policy to use as a permissions boundary for all new users in the account\.

1. María creates the `DelegatedUserBoundary` managed policy and assigns it as the permissions boundary for Zhang\. Maria makes a note of her admin IAM user's ARN and uses it in the policy to prevent Zhang from accessing it\.

1. María creates the `DelegatedUserPermissions` managed policy and attaches it as a permissions policy for Zhang\.

1. María tells Zhang about his new responsibilities and limitations\.

**Task 1:** María must first create a managed policy to define the boundary for the new users\. María will allow Zhang to give users the permissions policies they need, but she wants those users to be restricted\. To do this, she creates the following customer managed policy with the name `XCompanyBoundaries`\. This policy does the following:
+ Allows users full access to several services
+ Allows limited self\-managing access in the IAM console\. This means they can change their password after signing into the console\. They can't set their initial password\. To allow this, add the `"*LoginProfile"` action to the `AllowManageOwnPasswordAndAccessKeys` statement\.
+ Denies users access to the Amazon S3 logs bucket or the `i-1234567890abcdef0` Amazon EC2 instance

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
                "dynamodb:*"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AllowIAMConsoleForCredentials",
            "Effect": "Allow",
            "Action": [
                "iam:ListUsers",
                "iam:GetAccountPasswordPolicy"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AllowManageOwnPasswordAndAccessKeys",
            "Effect": "Allow",
            "Action": [
                "iam:*AccessKey*",
                "iam:ChangePassword",
                "iam:GetUser",
                "iam:*ServiceSpecificCredential*",
                "iam:*SigningCertificate*"
            ],
            "Resource": ["arn:aws:iam::*:user/${aws:username}"]
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

1. The `ServiceBoundaries` statement of this policy allows full access to the specified AWS services\. This means that a new user's actions in these services are limited only by the permissions policies that are attached to the user\.

1. The `AllowIAMConsoleForCredentials` statement allows access to list all IAM users\. This access is necessary to navigate the **Users** page in the AWS Management Console\. It also allows viewing the password requirements for the account, which is necessary when changing your own password\.

1. The `AllowManageOwnPasswordAndAccessKeys` statement allows the users manage only their own console password and programmatic access keys\. This is important if Zhang or another administrator gives a new user a permissions policy with full IAM access\. In that case, that user could then change their own or other users' permissions\. This statement prevents that from happening\.

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
                "iam:PutUserPermissionsBoundary",
                "iam:PutUserPolicy"
            ],
            "Resource": "*",
            "Condition": {"StringEquals": 
                {"iam:PermissionsBoundary": "arn:aws:iam::123456789012:policy/XCompanyBoundaries"}}
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
                "iam:CreateAccessKey",
                "iam:CreateLoginProfile",
                "iam:GetAccountPasswordPolicy",
                "iam:GetLoginProfile",
                "iam:ListGroups",
                "iam:ListGroupsForUser",
                "iam:CreateGroup",
                "iam:GetGroup",
                "iam:DeleteGroup",
                "iam:UpdateGroup",
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
                "iam:SetDefaultPolicyVersion",
                "iam:SimulatePrincipalPolicy",
                "iam:SimulateCustomPolicy" 
            ],
            "NotResource": "arn:aws:iam::123456789012:user/Maria"
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

1. The `CloudWatchAndOtherIAMTasks` statement allows Zhang to complete other user, group, and policy management tasks\. He has permissions to reset passwords and create access keys for any IAM user not listed in the condition key\. This allows him to help users with sign\-in issues\.

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

1. The `S3BucketContents` statement allows Zhang to list the `ZhangBucket` Amazon S3 bucket\. However, his permissions boundary does not allow any Amazon S3 action, so he cannot perform any S3 operations, regardless of his permissions policy\.
**Note**  
Zhang's policies allow him to create a user that can then access Amazon S3 resources that he can't access\. By delegating these administrative actions, Maria effectively trusts Zhang with access to Amazon S3\. 

María then attaches the `DelegatedUserPermissions` policy as the permissions policy for the `Zhang` user\. 

**Task 4:** She gives Zhang instructions to create a new user\. She tells him that he can create new users with any permissions that they need, but he must assign them the `XCompanyBoundaries` policy as a permissions boundary\.

Zhang completes the following tasks:

1. Zhang [creates a user](id_users_create.md#id_users_create_console) with the AWS Management Console\. He types the user name `Nikhil` and enables console access for the user\. He clears the checkbox next to **Requires password reset**, because the policies above allow users to change their passwords only after they are signed in to the IAM console\.

1. On the **Set permissions** page, Zhang chooses the **IAMFullAccess** and ** AmazonS3ReadOnlyAccess** permissions policies that allow Nikhil to do his work\. 

1. Zhang skips the **Set permissions boundary** section, forgetting María's instructions\.

1. Zhang reviews the user details and chooses **Create user**\.

   The operation fails and access is denied\. Zhang's `DelegatedUserBoundary` permissions boundary requires that any user he creates have the `XCompanyBoundaries` policy used as a permissions boundary\.

1. Zhang returns to the previous page\. In the **Set permissions boundary** section, he chooses the `XCompanyBoundaries` policy\. 

1. Zhang reviews the user details and chooses **Create user**\.

   The user is created\. 

When Nikhil signs in, he has access to IAM and Amazon S3, except those operations that are denied by the permissions boundary\. For example, he can change his own password in IAM but can't create another user or edit his policies\. Nikhil has read\-only access to Amazon S3\.

If someone adds a resource\-based policy to the `logs` bucket that allows Nikhil to put an object in the bucket, he still cannot access the bucket\. The reason is that any actions on the `logs` bucket are explicitly denied by his permissions boundary\. An explicit deny in any policy type results in a request being denied\. However, if a resource\-based policy attached to a Secrets Manager secret allows Nikhil to perform the `secretsmanager:GetSecretValue` action, then Nikhil can retrieve and decrypt the secret\. The reason is that Secrets Manager operations are not explicitly denied by his permissions boundary, and implicit denies in permissions boundaries do not limit resource\-based policies\.