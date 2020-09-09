# Switching to an IAM role \(AWS CLI\)<a name="id_roles_use_switch-role-cli"></a>

A *role* specifies a set of permissions that you can use to access AWS resources that you need\. In that sense, it is similar to a [user in AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) \(IAM\)\. When you sign in as a user, you get a specific set of permissions\. However, you don't sign in to a role, but after signing in as a user, you can switch to a role\. This temporarily sets aside your original user permissions and instead gives you the permissions assigned to the role\. The role can be in your own account or any other AWS account\. For more information about roles, their benefits, and how to create and configure them, see [IAM roles](id_roles.md), and [Creating IAM roles](id_roles_create.md)\. To learn about the different methods that you can use to assume a role, see [Using IAM roles](id_roles_use.md)\.

**Important**  
The permissions of your IAM user and any roles that you assume are not cumulative\. Only one set of permissions is active at a time\. When you assume a role, you temporarily give up your previous user or role permissions and work with the permissions that are assigned to the role\. When you exit the role, your user permissions are automatically restored\.

You can use a role to run an AWS CLI command when you are signed in as an IAM user\. You can also use a role to run an AWS CLI command when you are signed in as an [externally authenticated user](id_roles_providers.md) \([SAML](id_roles_providers_saml.md) or [OIDC](id_roles_providers_oidc.md)\) that is already using a role\. In addition, you can use a role to run an AWS CLI command from within an Amazon EC2 instance that is attached to a role through its instance profile\. You can also use [*role chaining*](id_roles_terms-and-concepts.md#iam-term-role-chaining), which is using a role to assume a second role\. You cannot assume a role when you are signed in as the AWS account root user\.

By default, your role session lasts for one hour\. When you assume this role using the `assume-role*` CLI operations, you can specify a value for the `duration-seconds` parameter\. This value can range from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\. 

If you use role chaining, your session duration is limited to a maximum of one hour\. If you then use the `duration-seconds` parameter to provide a value greater than one hour, the operation fails\.

## Example scenario: Switch to a production role<a name="switch-role-cli-scenario-prod-env"></a>

Imagine that you are an IAM user for working in the development environment\. In this scenario, you occasionally need to work with the production environment at the command line with the [AWS CLI](http://aws.amazon.com/cli/)\. You already have an access key credential set available to you\. This can be the access key pair that is assigned to your standard IAM user\. Or, if you signed in as a federated user, it can be the access key pair for the role that was initially assigned to you\. If your current permissions grant you the ability to assume a specific IAM role, then you can identify that role in a "profile" in the AWS CLI configuration files\. That command is then run with the permissions of the specified IAM role, not the original identity\. Note that when you specify that profile in an AWS CLI command, you are using the new role\. In this situation, you cannot make use of your original permissions in the development account at the same time\. The reason is that only one set of permissions can be in effect at a time\.

**Note**  
For security purposes, administrators can [review AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) to learn who performed an action in AWS\. Your administrator might require that you specify your IAM user name as the session name when you assume the role\. For more information, see [`aws:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname)\.

**To switch to a production role \(AWS CLI\)**

1. <a name="step-configure-default"></a>If you have never used the AWS CLI, then you must first configure your default CLI profile\. Open a command prompt and set up your AWS CLI installation to use the access key from your IAM user or from your federated role\. For more information, see [Configuring the AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-quick-configuration) in the *AWS Command Line Interface User Guide*\.

   Run the [aws configure](https://docs.aws.amazon.com/cli/latest/reference/configure/) command as follows:

   ```
   aws configure
   ```

   When prompted, provide the following information:

   ```
   AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
   AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
   Default region name [None]: us-east-2
   Default output format [None]: json
   ```

1. Create a new profile for the role in the `.aws/config` file in Unix or Linux, or the `C:\Users\USERNAME\.aws\config` file in Windows\. The following example creates a profile called `prodaccess` that switches to the role `ProductionAccessRole` in the `123456789012` account\. You get the role ARN from the account administrator who created the role\. When this profile is invoked, the AWS CLI uses the credentials of the `source_profile` to request credentials for the role\. Because of that, the identity referenced as the `source_profile` must have `sts:AssumeRole` permissions to the role that is specified in the `role_arn`\.

   ```
   [profile prodaccess]
       role_arn = arn:aws:iam::123456789012:role/ProductionAccessRole
       source_profile = default
   ```

1. After you create the new profile, any AWS CLI command that specifies the parameter `--profile prodaccess` runs under the permissions that are attached to the IAM role `ProductionAccessRole` instead of the default user\.

   ```
   aws iam list-users --profile prodaccess
   ```

   This command works if the permissions assigned to the `ProductionAccessRole` enable listing the users in the current AWS account\.

1. To return to the permissions granted by your original credentials, run commands without the `--profile` parameter\. The AWS CLI reverts to using the credentials in your default profile, which you configured in [Step 1](#step-configure-default)\.

For more information, see [Assuming a Role](https://docs.aws.amazon.com/cli/latest/userguide/cli-roles.html) in the *AWS Command Line Interface User Guide*\.

## Example scenario: Allow an instance profile role to switch to a role in another account<a name="switch-role-cli-scenario-ec2-instance"></a>

Imagine that you are using two AWS accounts, and you want to allow an application running on an Amazon EC2 instance to run [AWS CLI](http://aws.amazon.com/cli/) commands in both accounts\. Assume that the EC2 instance exists in account `111111111111`\. That instance includes the `abcd` instance profile role that allows the application to perform read\-only Amazon S3 tasks on the `my-bucket-1` bucket within the same `111111111111` account\. However, the application must also be allowed to assume the `efgh` cross\-account role to perform tasks in account `222222222222`\. To do this, the `abcd` EC2 instance profile role must have the following permissions policy:

***Account 111111111111 `abcd` Role Permissions Policy***

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowAccountLevelS3Actions",
            "Effect": "Allow",
            "Action": [
                "s3:ListAllMyBuckets",
                "s3:HeadBucket"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AllowListAndReadS3ActionOnMyBucket",
            "Effect": "Allow",
            "Action": [
                "s3:Get*",
                "s3:List*"
            ],
            "Resource": [
                "arn:aws:s3:::my-bucket-1/*",
                "arn:aws:s3:::my-bucket-1"
            ]
        },
        {
            "Sid": "AllowIPToAssumeCrossAccountRole",
            "Effect": "Allow",
            "Action": "sts:AssumeRole",
            "Resource": "arn:aws:iam::222222222222:role/efgh"
        }
    ]
}
```

Assume that the `efgh` cross\-account role allows read\-only Amazon S3 tasks on the `my-bucket-2` bucket within the same `222222222222` account\. To do this, the `efgh` cross\-account role must have the following permissions policy:

***Account 222222222222 `efgh` Role Permissions Policy***

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowAccountLevelS3Actions",
            "Effect": "Allow",
            "Action": [
                "s3:ListAllMyBuckets",
                "s3:HeadBucket"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AllowListAndReadS3ActionOnMyBucket",
            "Effect": "Allow",
            "Action": [
                "s3:Get*",
                "s3:List*"
            ],
            "Resource": [
                "arn:aws:s3:::my-bucket-2/*",
                "arn:aws:s3:::my-bucket-2"
            ]
        }
    ]
}
```

The `efgh` role must allow the `abcd` instance profile role to assume it\. To do this, the `efgh` role must have the following trust policy:

***Account 222222222222 `efgh` Role Trust Policy***

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "efghTrustPolicy",
            "Effect": "Allow",
            "Action": "sts:AssumeRole",
            "Principal": {"AWS": "arn:aws:iam::111111111111:role/abcd"}
        }
    ]
}
```

To then run AWS CLI commands in account `222222222222`, you must update the CLI configuration file\. Identify the `efgh` role as the "profile" and the `abcd` EC2 instance profile role as the "credential source" in the AWS CLI configuration file\. Then your CLI commands are run with the permissions of the `efgh` role, not the original `abcd` role\.

**Note**  
For security purposes, you can use AWS CloudTrail to audit the use of roles in the account\. To identify a role's actions in CloudTrail logs, you can use the role session name\. When the AWS CLI assumes a role on a user's behalf as described in this topic, a role session name is automatically created as `AWS-CLI-session-nnnnnnnn`\. Here *nnnnnnnn* is an integer that represents the time in [Unix epoch time](http://wikipedia.org/wiki/Unix_time) \(the number of seconds since midnight UTC on January 1, 1970\)\. For more information, see [CloudTrail Event Reference](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/eventreference.html) in the *AWS CloudTrail User Guide*\.

**To allow an EC2 instance profile role to switch to a cross\-account role \(AWS CLI\)**

1. You do not have to configure a default CLI profile\. Instead, you can load credentials from the EC2 instance profile metadata\. Create a new profile for the role in the `.aws/config` file\. The following example creates an `instancecrossaccount` profile that switches to the role `efgh` in the `222222222222` account\. When this profile is invoked, the AWS CLI uses the credentials of the EC2 instance profile metadata to request credentials for the role\. Because of that, the EC2 instance profile role must have `sts:AssumeRole` permissions to the role specified in the `role_arn`\.

   ```
   [profile instancecrossaccount]
   role_arn = arn:aws:iam::222222222222:role/efgh
   credential_source = Ec2InstanceMetadata
   ```

1. After you create the new profile, any AWS CLI command that specifies the parameter `--profile instancecrossaccount` runs under the permissions that are attached to the `efgh` role in account `222222222222`\.

   ```
   aws s3 ls my-bucket-2 --profile instancecrossaccount
   ```

   This command works if the permissions that are assigned to the `efgh` role allow listing the users in the current AWS account\.

1. To return to the original EC2 instance profile permissions in account `111111111111`, run the CLI commands without the `--profile` parameter\.

For more information, see [Assuming a Role](https://docs.aws.amazon.com/cli/latest/userguide/cli-roles.html) in the *AWS Command Line Interface User Guide*\.