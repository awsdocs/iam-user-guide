# IAM: Allows and denies access to multiple services programmatically and in the console<a name="reference_policies_examples_iam_multiple-services-console"></a>

This example shows how you might create a policy that allows full access to several services and limited self\-managing access in IAM\. It also denies access to the Amazon S3 `logs` bucket or the Amazon EC2 `i-1234567890abcdef0` instance\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

**Warning**  
This policy allows full access to every action and resource in multiple services\. This policy should be applied only to trusted administrators\.

You can use this policy as a permissions boundary to define the maximum permissions that an identity\-based policy can grant to an IAM user\. For more information, see [Delegating responsibility to others using permissions boundaries](access_policies_boundaries.md#access_policies_boundaries-delegate)\. When the policy is used as a permissions boundary for a user, the statements define the following boundaries:
+ The `AllowServices` statement allows full access to the specified AWS services\. This means that the user's actions in these services are limited only by the permissions policies that are attached to the user\.
+ The `AllowIAMConsoleForCredentials` statement allows access to list all IAM users\. This access is necessary to navigate the **Users** page in the AWS Management Console\. It also allows viewing the password requirements for the account, which is necessary for the user to change their own password\.
+ The `AllowManageOwnPasswordAndAccessKeys` statement allows the users manage only their own console password and programmatic access keys\. This is important because if another policy gives a user full IAM access, that user could then change their own or other users' permissions\. This statement prevents that from happening\.
+ The `DenyS3Logs` statement explicitly denies access to the `logs` bucket\. This policy enforces company restrictions on the user\.
+ The `DenyEC2Production` statement explicitly denies access to the `i-1234567890abcdef0` instance\.

This policy does not allow access to other services or actions\. When the policy is used as a permissions boundary on a user, even if other policies attached to the user allow those actions, AWS denies the request\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowServices",
            "Effect": "Allow",
            "Action": [
                "s3:*",
                "cloudwatch:*",
                "ec2:*"
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
                "iam:*LoginProfile*"
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