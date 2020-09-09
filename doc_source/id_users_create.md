# Creating an IAM user in your AWS account<a name="id_users_create"></a>

You can create one or more IAM users in your AWS account\. You might create an IAM user when someone joins your team, or when you create a new application that needs to make API calls to AWS\. 

**Important**  
If you arrived at this page while trying to enable Amazon Advertising for your application or website, see [Becoming a Product Advertising API Developer](https://docs.aws.amazon.com/AWSECommerceService/latest/DG/becomingDev.html)\.  
If you arrived at this page from the IAM console, it is possible that your account does not include IAM users, even though you are signed in\. You could be signed in as the AWS account root user, using a role, or signed in with temporary credentials\. To learn more about these IAM identities, see [IAM Identities \(users, groups, and roles\)](id.md)\.

**Topics**
+ [Creating IAM users \(console\)](#id_users_create_console)
+ [Creating IAM users \(AWS CLI\)](#id_users_create_cliwpsapi)
+ [Creating IAM users \(AWS API\)](#id_users_create_api)

The process of creating a user and enabling that user to perform work tasks consists of the following steps:

1. Create the user in the AWS Management Console, the AWS CLI, Tools for Windows PowerShell, or using an AWS API operation\. If you create the user in the AWS Management Console, then steps 1–4 are handled automatically, based on your choices\. If you create the users programmatically, then you must perform each of those steps individually\.

1. Create credentials for the user, depending on the type of access the user requires:
   + **Programmatic access:** The IAM user might need to make API calls, use the AWS CLI, or use the Tools for Windows PowerShell\. In that case, create an access key \(access key ID and a secret access key\) for that user\.
   + **AWS Management Console access**: If the user needs to access the AWS Management Console, [create a password for the user](id_credentials_passwords_admin-change-user.md)\.

   As a best practice, create only the credentials that the user needs\. For example, for a user who requires access only through the AWS Management Console, do not create access keys\.

1. Give the user permissions to perform the required tasks by adding the user to one or more groups\. You can also grant permissions by attaching permission policies directly to the user\. However, we recommend instead that you put your users in groups and manage permissions through policies that are attached to those groups\. You can also use a [permissions boundary](access_policies_boundaries.md) to limit the permissions that a user can have, though this is not common\. 

1. \(Optional\) Add metadata to the user by attaching tags\. For more information about using tags in IAM, see [Tagging IAM users and roles](id_tags.md)\.

1. Provide the user with the necessary sign\-in information\. This includes the password and the console URL for the account sign\-in page where the user provides those credentials\. For more information, see [How IAM users sign in to AWS](id_users_sign-in.md)\.

1. \(Optional\) Configure [multi\-factor authentication \(MFA\)](id_credentials_mfa.md) for the user\. MFA requires the user to provide a one\-time\-use code each time he or she signs into the AWS Management Console\. 

1. \(Optional\) Give users permissions to manage their own security credentials\. \(By default, users do not have permissions to manage their own credentials\.\) For more information, see [Permitting IAM users to change their own passwords](id_credentials_passwords_enable-user-change.md)\. 

For information about the permissions that you need in order to create a user, see [Permissions required to access IAM resources](access_permissions-required.md)\. 

## Creating IAM users \(console\)<a name="id_users_create_console"></a>

You can use the AWS Management Console to create IAM users\.

**To create one or more IAM users \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users** and then choose **Add user**\.

1. Type the user name for the new user\. This is the sign\-in name for AWS\. If you want to add more than one user at the same time, choose **Add another user** for each additional user and type their user names\. You can add up to 10 users at one time\.
**Note**  
The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\. User names can be a combination of up to 64 letters, digits, and these characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at sign \(@\), underscore \(\_\), and hyphen \(\-\)\. Names must be unique within an account\. They are not distinguished by case\. For example, you cannot create two users named *TESTUSER* and *testuser*\.

1. Select the type of access this set of users will have\. You can select programmatic access, access to the AWS Management Console, or both\.
   + Select **Programmatic access** if the users require access to the API, AWS CLI, or Tools for Windows PowerShell\. This creates an access key for each new user\. You can view or download the access keys when you get to the **Final** page\.
   + Select **AWS Management Console access** if the users require access to the AWS Management Console\. This creates a password for each new user\.

   1. For **Console password**, choose one of the following:
      + **Autogenerated password**\. Each user gets a randomly generated password that meets the account password policy in effect \(if any\)\. You can view or download the passwords when you get to the **Final** page\.
      + **Custom password**\. Each user is assigned the password that you type in the box\.

   1. \(Optional\) We recommend that you select **Require password reset** to ensure that users are forced to change their password the first time they sign in\.
**Note**  
If you have *not* enabled [the account\-wide password policy setting **Allow users to change their own password**](https://console.aws.amazon.com/iam/home?#/account_settings), then selecting **Require password reset** automatically attaches an AWS managed policy named [https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMUserChangePassword](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMUserChangePassword) to the new users that grants them permission to change their own passwords\.

1. Choose **Next: Permissions**\.

1. On the **Set permissions** page, specify how you want to assign permissions to this set of new users\. Choose one of the following three options:
   + **Add user to group**\. Choose this option if you want to assign the users to one or more groups that already have permissions policies\. IAM displays a list of the groups in your account, along with their attached policies\. You can select one or more existing groups, or choose **Create group** to create a new group\. For more information, see [Changing permissions for an IAM user](id_users_change-permissions.md)\.
   + **Copy permissions from existing user**\. Choose this option to copy all of the group memberships, attached managed policies, embedded inline policies, and any existing [permissions boundaries](access_policies_boundaries.md) from an existing user to the new users\. IAM displays a list of the users in your account\. Select the one whose permissions most closely match the needs of your new users\.
   + **Attach existing policies to user directly**\. Choose this option to see a list of the AWS managed and customer managed policies in your account\. Select the policies that you want to attach to the new users or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see step 4 in the procedure [Creating IAM policies \(console\)](access_policies_create-console.md#access_policies_create-start)\. After you create the policy, close that tab and return to your original tab to add the policy to the new user\. As a [best practice](best-practices.md#use-groups-for-permissions), we recommend that you instead attach your policies to a group and then make users members of the appropriate groups\.

1. \(Optional\) Set a [permissions boundary](access_policies_boundaries.md)\. This is an advanced feature\. 

   Open the **Set permissions boundary** section and choose **Use a permissions boundary to control the maximum user permissions**\. IAM displays a list of the AWS managed and customer managed policies in your account\. Select the policy to use for the permissions boundary or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see step 4 in the procedure [Creating IAM policies \(console\)](access_policies_create-console.md#access_policies_create-start)\. After you create the policy, close that tab and return to your original tab to select the policy to use for the permissions boundary\.

1. Choose **Next: Tags**\.

1. \(Optional\) Add metadata to the user by attaching tags as key\-value pairs\. For more information about using tags in IAM, see [Tagging IAM users and roles](id_tags.md)\.

1. Choose **Next: Review** to see all of the choices you made up to this point\. When you are ready to proceed, choose **Create user**\.

1. To view the users' access keys \(access key IDs and secret access keys\), choose **Show** next to each password and access key that you want to see\. To save the access keys, choose **Download \.csv** and then save the file to a safe location\. 
**Important**  
This is your only opportunity to view or download the secret access keys, and you must provide this information to your users before they can use the AWS API\. Save the user's new access key ID and secret access key in a safe and secure place\. **You will not have access to the secret keys again after this step\.** 

1. Provide each user with his or her credentials\. On the final page you can choose **Send email** next to each user\. Your local mail client opens with a draft that you can customize and send\. The email template includes the following details to each user:
   + User name
   + URL to the account sign\-in page\. Use the following example, substituting the correct account ID number or account alias:

     ```
     https://AWS-account-ID or alias.signin.aws.amazon.com/console
     ```

   For more information, see [How IAM users sign in to AWS](id_users_sign-in.md)\.
**Important**  
The user's password is ***not*** included in the generated email\. You must provide them to the customer in a way that complies with your organization's security guidelines\.

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

1. \(Optional\) Add custom attributes to the user by attaching tags\. For more information, see [Managing tags on IAM entities \(AWS CLI or AWS API\)](id_tags.md#id_tags_procs-cli-api)\.

1. \(Optional\) Give the user permission to manage their own security credentials\. For more information, see [AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage.md)\. 

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

1. \(Optional\) Add custom attributes to the user by attaching tags\. For more information, see [Managing tags on IAM entities \(AWS CLI or AWS API\)](id_tags.md#id_tags_procs-cli-api)\.

1. \(Optional\) Give the user permission to manage their own security credentials\. For more information, see [AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage.md)\.