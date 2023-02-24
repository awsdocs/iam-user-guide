# Creating an IAM user in your AWS account<a name="id_users_create"></a>

**Important**  
The IAM best practices have been updated\. As a [best practice](best-practices.md), require human users to use federation with an identity provider to access AWS using temporary credentials\. An additional best practice recommendation is to require workloads to use temporary credentials with IAM roles to access AWS\. IAM users are to be used only in very limited scenarios where an IAM role cannot be assumed\. To learn about using AWS IAM Identity Center \(successor to AWS Single Sign\-On\) to create users with temporary credentials, see [Getting started](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\. 

**Note**  
If you found this page because you are looking for information about the Product Advertising API to sell Amazon products on your website, see the [Product Advertising API 5\.0 Documentation](https://webservices.amazon.com/paapi5/documentation/)\.  
If you arrived at this page from the IAM console, it is possible that your account does not include IAM users, even though you are signed in\. You could be signed in as the AWS account root user, using a role, or signed in with temporary credentials\. To learn more about these IAM identities, see [IAM Identities \(users, user groups, and roles\)](id.md)\.

The process of creating a user and enabling that user to perform work tasks consists of the following steps:

1. Create the user in the AWS Management Console, the AWS CLI, Tools for Windows PowerShell, or using an AWS API operation\. If you create the user in the AWS Management Console, then steps 1–4 are handled automatically, based on your choices\. If you create the users programmatically, then you must perform each of those steps individually\.

1. Create credentials for the user, depending on the type of access the user requires:
   + **Enable console access – *optional***: If the user needs to access the AWS Management Console, [create a password for the user](id_credentials_passwords_admin-change-user.md)\. Disabling console access for a user prevents them from signing in to the AWS Management Console using their user name and password\. It does not change their permissions or prevent them from accessing the console using an assumed role\.
**Tip**  
Create only the credentials that the user needs\. For example, for a user who requires access only through the AWS Management Console, do not create access keys\.

1. Give the user permissions to perform the required tasks by adding the user to one or more groups\. You can also grant permissions by attaching permissions policies directly to the user\. However, we recommend instead that you put your users in groups and manage permissions through policies that are attached to those groups\. You can also use a [permissions boundary](access_policies_boundaries.md) to limit the permissions that a user can have, though this is not common\.

1. \(Optional\) Add metadata to the user by attaching tags\. For more information about using tags in IAM, see [Tagging IAM resources](id_tags.md)\.

1. Provide the user with the necessary sign\-in information\. This includes the password and the console URL for the account sign\-in page where the user provides those credentials\. For more information, see [How IAM users sign in to AWS](id_users_sign-in.md)\.

1. \(Optional\) Configure [multi\-factor authentication \(MFA\)](id_credentials_mfa.md) for the user\. MFA requires the user to provide a one\-time\-use code each time he or she signs into the AWS Management Console\.

1. \(Optional\) Give users permissions to manage their own security credentials\. \(By default, users do not have permissions to manage their own credentials\.\) For more information, see [Permitting IAM users to change their own passwords](id_credentials_passwords_enable-user-change.md)\.

For information about the permissions that you need in order to create a user, see [Permissions required to access IAM resources](access_permissions-required.md)\.

**Topics**
+ [Creating IAM users \(console\)](#id_users_create_console)
+ [Creating IAM users \(AWS CLI\)](#id_users_create_cliwpsapi)
+ [Creating IAM users \(AWS API\)](#id_users_create_api)

## Creating IAM users \(console\)<a name="id_users_create_console"></a>

You can use the AWS Management Console to create IAM users\.

**To create an IAM user \(console\)**

1. Follow the sign\-in procedure appropriate to your user type as described in the topic [How to sign in to AWS](https://docs.aws.amazon.com/signin/latest/userguide/how-to-sign-in.html) in the *AWS Sign\-In User Guide*\.

1. On the **Console Home** page, select the IAM service\.

1. In the navigation pane, select **Users** and then select **Add users**\.

1. On the **Specify user details** page, under **User details**, in **User name**, enter the name for the new user\. This is their sign\-in name for AWS\.
**Note**  
The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and AWS STS quotas, name requirements, and character limits](reference_iam-quotas.md)\. User names can be a combination of up to 64 letters, digits, and these characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at sign \(@\), underscore \(\_\), and hyphen \(\-\)\. Names must be unique within an account\. They are not distinguished by case\. For example, you cannot create two users named *TESTUSER* and *testuser*\.

1. Select **Provide user access to the – AWS Management Console *optional*** This produces AWS Management Console sign\-in credentials for the new user\.

   You are asked whether you are providing console access to a person\. We recommend that you create users in IAM Identity Center rather than IAM\.
   + To switch to creating the user in IAM Identity Center, select **Specify a user in Identity Center**\.

     If you have not enabled IAM Identity Center, selecting this option takes you to the service page in the console so that you can enable the service\. For details on this procedure, see [https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html](https://docs.aws.amazon.com/singlesignon/latest/userguide/getting-started.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide* 

     If you have enabled IAM Identity Center, selecting this option takes you to the **Specify user details** page in IAM Identity Center\. For details on this procedure, see [https://docs.aws.amazon.com/singlesignon/latest/userguide/addusers.html](https://docs.aws.amazon.com/singlesignon/latest/userguide/addusers.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*
   + If you cannot use IAM Identity Center, select **I want to create an IAM user** and continue following this procedure\.

   1. For **Console password**, select one of the following:
      + **Autogenerated password** – The user gets a randomly generated password that meets the [account password policy](id_credentials_passwords_account-policy.md)\. You can view or download the password when you get to the **Retrieve password** page\.
      + **Custom password** – The user is assigned the password that you enter in the box\.

   1. \(Optional\) **Users must create a new password at next sign\-in \(recommended\)** is selected by default to ensure that the user is forced to change their password the first time they sign in\.
**Note**  
If an administrator has enabled the [**Allow users to change their own password** account password policy setting](https://console.aws.amazon.com/iam/home?#/account_settings), then this check box does nothing\. Otherwise, it automatically attaches an AWS managed policy named [https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMUserChangePassword](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMUserChangePassword) to the new users\. The policy grants them permission to change their own passwords\.

1. Select **Next**\.

1. On the **Set permissions** page, specify how you want to assign permissions for this user\. Select one of the following three options:
   + **Add user to group** – Select this option if you want to assign the user to one or more groups that already have permissions policies\. IAM displays a list of the groups in your account, along with their attached policies\. You can select one or more existing groups, or select **Create group** to create a new group\. For more information, see [Changing permissions for an IAM user](id_users_change-permissions.md)\.
   + **Copy permissions** – Select this option to copy all of the group memberships, attached managed policies, embedded inline policies, and any existing [permissions boundaries](access_policies_boundaries.md) from an existing user to the new user\. IAM displays a list of the users in your account\. Select the one whose permissions most closely match the needs of your new user\.
   + **Attach policies directly** – Select this option to see a list of the AWS managed and customer managed policies in your account\. Select the policies that you want to attach to the user or select **Create policy** to open a new browser tab and create a new policy\. For more information, see step 4 in the procedure [Creating IAM policies](access_policies_create-console.md#access_policies_create-start)\. After you create the policy, close that tab and return to your original tab to add the policy to the user\.
**Tip**  
Whenever possible, attach your policies to a group and then make users members of the appropriate groups\.

1. \(Optional\) Set a [permissions boundary](access_policies_boundaries.md)\. This is an advanced feature\. 

   Open the **Permissions boundary** section and select **Use a permissions boundary to control the maximum permissions**\. IAM displays a list of the AWS managed and customer managed policies in your account\. Select the policy to use for the permissions boundary or select **Create policy** to open a new browser tab and create a new policy\. For more information, see step 4 in the procedure [Creating IAM policies](access_policies_create-console.md#access_policies_create-start)\. After you create the policy, close that tab and return to your original tab to select the policy to use for the permissions boundary\.

1. Select **Next**\.

1. \(Optional\) On the **Review and create** page, under **Tags**, select **Add new tag** to add metadata to the user by attaching tags as key\-value pairs\. For more information about using tags in IAM, see [Tagging IAM resources](id_tags.md)\.

1. Review all of the choices you made up to this point\. When you are ready to proceed, select **Create user**\.

1. On the **Retrieve password** page, get the password assigned to the user:
   + Select **Show** next to the password to view the user's password so that you can record it manually\. 
   + Select **Download \.csv** to download the user's sign in credentials as a \.csv file that you can save to a safe location\. 

1. Select **Email sign\-in instructions**\. Your local mail client opens with a draft that you can customize and send to the user\. The email template includes the following details to each user:
   + User name
   + URL to the account sign\-in page\. Use the following example, substituting the correct account ID number or account alias:

     ```
     https://AWS-account-ID or alias.signin.aws.amazon.com/console
     ```
**Important**  
The user's password is ***not*** included in the generated email\. You must provide the password to the user in a way that complies with your organization's security guidelines\.

1. If the user also requires access keys, refer to [Managing access keys for IAM users](id_credentials_access-keys.md)\.

## Creating IAM users \(AWS CLI\)<a name="id_users_create_cliwpsapi"></a>

You can use the AWS CLI to create an IAM user\.

**To create an IAM user \(AWS CLI\)**

1. Create a user\.
   + [aws iam create\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/create-user.html)

1. \(Optional\) Give the user access to the AWS Management Console\. This requires a password\. You must also give the user the [URL of your account's sign\-in page\.](id_users_sign-in.md)
   +  [aws iam create\-login\-profile](https://docs.aws.amazon.com/cli/latest/reference/iam/create-login-profile.html)

1. \(Optional\) Give the user programmatic access\. This requires access keys\. 
   + [aws iam create\-access\-key](https://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html)
   + Tools for Windows PowerShell: [New\-IAMAccessKey](https://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMAccessKey.html&tocid=New-IAMAccessKey)
   + IAM API: [CreateAccessKey](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html)
**Important**  
This is your only opportunity to view or download the secret access keys, and you must provide this information to your users before they can use the AWS API\. Save the user's new access key ID and secret access key in a safe and secure place\. **You will not have access to the secret keys again after this step\.** 

1. Add the user to one or more groups\. The groups that you specify should have attached policies that grant the appropriate permissions for the user\. 
   + [aws iam add\-user\-to\-group](https://docs.aws.amazon.com/cli/latest/reference/iam/add-user-to-group.html) 

1. \(Optional\) Attach a policy to the user that defines the user's permissions\. **Note:** We recommend that you manage user permissions by adding the user to a group and attaching a policy to the group instead of attaching directly to a user\.
   + [aws iam attach\-user\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/attach-user-policy.html)

1. \(Optional\) Add custom attributes to the user by attaching tags\. For more information, see [Managing tags on IAM users \(AWS CLI or AWS API\)](id_tags_users.md#id_tags_users_procs-cli-api)\.

1. \(Optional\) Give the user permission to manage their own security credentials\. For more information, see [AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the My security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage.md)\. 

## Creating IAM users \(AWS API\)<a name="id_users_create_api"></a>

You can use the AWS API to create an IAM user\.

**To create an IAM user from the \(AWS API\)**

1. Create a user\.
   + [CreateUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateUser.html)

1. \(Optional\) Give the user access to the AWS Management Console\. This requires a password\. You must also give the user the [URL of your account's sign\-in page\.](id_users_sign-in.md)
   + [CreateLoginProfile](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateLoginProfile.html)

1. \(Optional\) Give the user programmatic access\. This requires access keys\. 
   + [CreateAccessKey](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html)
**Important**  
This is your only opportunity to view or download the secret access keys, and you must provide this information to your users before they can use the AWS API\. Save the user's new access key ID and secret access key in a safe and secure place\. **You will not have access to the secret keys again after this step\.** 

1. Add the user to one or more groups\. The groups that you specify should have attached policies that grant the appropriate permissions for the user\. 
   + [AddUserToGroup](https://docs.aws.amazon.com/IAM/latest/APIReference/API_AddUserToGroup.html) 

1. \(Optional\) Attach a policy to the user that defines the user's permissions\. **Note:** We recommend that you manage user permissions by adding the user to a group and attaching a policy to the group instead of attaching directly to a user\.
   + [AttachUserPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachUserPolicy.html)

1. \(Optional\) Add custom attributes to the user by attaching tags\. For more information, see [Managing tags on IAM users \(AWS CLI or AWS API\)](id_tags_users.md#id_tags_users_procs-cli-api)\.

1. \(Optional\) Give the user permission to manage their own security credentials\. For more information, see [AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the My security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage.md)\.