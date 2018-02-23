# Switching to an IAM Role \(AWS Command Line Interface\)<a name="id_roles_use_switch-role-cli"></a>

A *role* specifies a set of permissions that you can use to access AWS resources that you need\. In that sense, it is similar to a [user in AWS Identity and Access Management](http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) \(IAM\)\. When you sign in as a user, you get a specific set of permissions\. However, you don't sign in to a role, but once signed in as a user you can switch to a role\. This temporarily sets aside your original user permissions and instead gives you the permissions assigned to the role\. The role can be in your own account or any other AWS account\. For more information about roles, their benefits, and how to create and configure them, see [IAM Roles](id_roles.md), and [Creating IAM Roles](id_roles_create.md)\.

**Important**  
The permissions of your IAM user and any roles that you switch to are not cumulative\. Only one set of permissions is active at a time\. When you switch to a role, you temporarily give up your user permissions and work with the permissions that are assigned to the role\. When you exit the role, your user permissions are automatically restored\.

You can run an AWS CLI command using a role only when you are signed in as an IAM user, as an [externally authenticated user](id_roles_providers.md) \([SAML](id_roles_providers_saml.md) or [OIDC](id_roles_providers_oidc.md)\) already using a role, or when run from within an Amazon EC2 instance that is attached to a role through its instance profile\. You cannot switch to a role when you are signed in as the AWS account root user\.

This section describes how to switch roles when you work at the command line with the AWS Command Line Interface\.

Imagine that you have an IAM user for working in the development environment and you occasionally need to work with the production environment at the command line with the [AWS CLI](http://aws.amazon.com/cli/)\. You already have an access key credential set available to you\. This can be the access key pair assigned to your standard IAM user; or, if you signed\-in as a federated user, it can be the access key pair for the role initially assigned to you\. If your current permissions grant you the ability to assume a specific role, then you can identify that role in a "profile" in the AWS CLI configuration files\. That command is then run with the permissions of the specified role, not the original identity\. Note that when you specify that profile, and thus use the new role, in an AWS CLI command, you cannot make use of your original permissions in the development account at the same time because only one set of permissions can be in effect at a time\.

**Note**  
For security purposes, you can use AWS CloudTrail to audit the use of roles in the account\. To identify a role's actions in CloudTrail logs, you can use the role session name\. When the AWS CLI assumes a role on a user's behalf as described in this topic, a role session name is automatically created as `AWS-CLI-session-nnnnnnnn`, where *nnnnnnnn* is an integer that represents the time in [Unix epoch time](http://wikipedia.org/wiki/Unix_time) \(the number of seconds since midnight UTC on January 1, 1970\)\. For more information, see [CloudTrail Event Reference](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/eventreference.html) in the *AWS CloudTrail User Guide*\.

**To switch to a role using the AWS CLI**

1. <a name="step-configure-default"></a>If you have never used the AWS CLI, then you must first configure your default CLI profile\. Open a command prompt and set up your AWS CLI installation to use the access key from your IAM user or from your federated role\. For more information, see [Configuring the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-quick-configuration) in the *AWS Command Line Interface User Guide*\.

   ```
   $ aws configure
   AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
   AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
   Default region name [None]: us-east-2
   Default output format [None]: json
   ```

1. Create a new profile for the role in the \.aws/config file\. The following example creates a profile called "prodaccess" that switches to the role `ProductionAccessRole` in the 123456789012 account\. You get the role ARN from the account administrator who created the role\. When this profile is invoked, the AWS CLI uses the credentials of the `source_profile` to request credentials for the role\. Because of that, the identity referenced as the `source_profile` must have `sts:AssumeRole` permissions to the role specified in the `role_arn`\.

   ```
   [profile prodaccess]
   role_arn = arn:aws:iam::123456789012:role/ProductionAccessRole
   source_profile = default
   ```

1. After you create the new profile, any AWS CLI command that specifies the parameter `--profile prodaccess` runs under the permissions attached to the IAM role ProductionAccessRole instead of the default user\.

   ```
   $ aws iam list-users --profile prodaccess
   ```

   This command works if the permissions assigned to the `ProductionAccessRole` enable listing the users in the current AWS account\.

1. To return to the permissions granted by your original credentials, run commands without the `--profile` parameter\. The AWS CLI reverts to using the credentials in your default profile, which you configured in [Step 1](#step-configure-default)\.

For more information, see [Assuming a Role](http://docs.aws.amazon.com/cli/latest/userguide/cli-roles.html) in the *AWS Command Line Interface User Guide*\.