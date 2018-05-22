# Creating an IAM User in Your AWS Account<a name="id_users_create"></a>

You can create one or more IAM users in your AWS account\. You might create an IAM user when someone joins your organization, or when you have a new application that needs to make API calls to AWS\. 

**Important**  
If you arrived at this page trying to enable Amazon Advertising for your application or website, see [Becoming a Product Advertising API Developer](http://docs.aws.amazon.com/AWSECommerceService/latest/DG/becomingDev.html)\.  
If you arrived at this page from the IAM console, it is possible that your account does not include IAM users, even though you are logged in\. You could be signed in as the AWS account root user, using a role, or signed in with temporary credentials\. To learn more about these IAM identities, see [Identities \(Users, Groups, and Roles\)](id.md)\.

**Topics**
+ [Creating IAM Users \(Console\)](#id_users_create_console)
+ [Creating IAM Users \(AWS CLI, Tools for Windows PowerShell, or IAM HTTP API\)](#id_users_create_cliwpsapi)

In outline, the process of creating a user and making it usable for work tasks consists of these steps:

1. Create the user in the AWS Management Console or from an AWS CLI, Tools for Windows PowerShell, or IAM API command\. If you create the user in the AWS Management Console, then steps 1–4 are handled automatically\. If you create the users programmatically, then you must perform each of those steps individually\.

1. Create credentials for the user, depending on the type of access the user requires:
   + **Programmatic access:** The IAM user might need to make API calls or use the AWS CLI or the Tools for Windows PowerShell\. In that case, create an access key \(an access key ID and a secret access key\) for that user\.

     **AWS Management Console access**: If the user needs to access AWS resources from the AWS Management Console, [create a password for the user](id_credentials_passwords_admin-change-user.md)\.

   As a best practice, do not create credentials of a certain type for a user who will never need that kind of access\. For example, for a user who requires access through the AWS Management Console only, do not create access keys\.

1. Give the user permissions to perform the required tasks by adding the user to one or more groups\. You can grant permissions by attaching IAM permission policies directly to the user\. However, we recommend instead that you put your users in groups and manage permissions through policies that are attached to those groups\. 

1. Provide the user with the necessary sign\-in information\. This includes the password and the URL for the account sign\-in webpage where the user enters those credentials\. For more information, see [How IAM Users Sign In to AWS](id_users_sign-in.md)\.

1. \(Optional\) Configure [multi\-factor authentication \(MFA\)](id_credentials_mfa.md) for the user\. MFA requires the user to provide a one\-time\-use code each time he or she signs into the AWS Management Console\. 

1. \(Optional\) Give users permissions to manage their own security credentials\. \(By default, users do not have permissions to manage their own credentials\.\) For more information, see [Permitting IAM Users to Change Their Own Passwords](id_credentials_passwords_enable-user-change.md)\. 

For information about the permissions that you need in order to create a user, see [Permissions Required to Access IAM Resources](access_permissions-required.md)\. 

## Creating IAM Users \(Console\)<a name="id_users_create_console"></a>

**To create one or more IAM users from the AWS Management Console**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users** and then choose **Add user**\.

1. Type the user name for the new user\. This is the sign\-in name for AWS\. If you want to add more than one user at the same time, choose **Add another user** for each additional user and type their user names\. You can add up to 10 users at one time\.
**Note**  
User names can be a combination of up to 64 letters, digits, and these characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at sign \(@\), and hyphen \(\-\)\. Names must be unique within an account\. They are not distinguished by case\. For example, you cannot create two users named *TESTUSER* and *testuser*\. For more information about limitations on IAM entities, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\. 

1. Select the type of access this set of users will have\. You can select programmatic access, access to the AWS Management Console, or both\.
   + Select **Programmatic access** if the users require access to the API, AWS CLI, or Tools for Windows PowerShell\. This creates an access key for each new user\. You can view or download the access keys when you get to the **Final** page\.

      
   + Select **AWS Management Console access** if the users require access to the AWS Management Console\. This creates a password for each new user\.

      

     1. For **Console password type**, choose one of the following:

         
        + **Autogenerated password**\. Each user gets a randomly generated password that meets the current password policy in effect \(if any\)\. You can view or download the passwords when you get to the **Final** page\.

           
        + **Custom password**\. Each user is assigned the password that you type in the box\.

           

     1. \(Optional\) We recommend that you choose **Require password reset** to ensure that users are forced to change their password the first time they sign in\.
**Note**  
If you have *not* enabled [the account\-wide password policy setting **Allow users to change their own password**](https://console.aws.amazon.com/iam/home?#/account_settings), then selecting **Require password reset** automatically attaches an AWS managed policy named [https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMUserChangePassword](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMUserChangePassword) to the new users that grants them permission to change their own passwords\.

1. Choose **Next: Permissions**\.

1. On the **Set permissions** page, specify how you want to assign permissions to this set of new users\. Choose one of the following three options:
   + **Add user to group**\. Choose this option if you have groups with appropriate permission policies already created and want to assign the users to those groups\. IAM displays a list of all currently defined groups, along with their attached policies\. You can select one or more existing groups, or choose **Create group** to create a new group\. For more information, see [Changing Permissions for an IAM User](id_users_change-permissions.md)\.
   + **Copy permissions from existing user**\. Choose this option to copy all of the group memberships, attached managed policies, and embedded inline policies from an existing user to the new users\. IAM displays a list of currently defined users\. Select the one whose permissions most closely match the needs of your new users\. Each new user gets the same group memberships and attached policies as the selected user\.
   + **Attach existing policies to user directly**\. Choose this option to select from existing managed policies or to create new managed policies that are attached to the new users\. IAM displays a list of currently defined managed policies, both AWS and customer\-defined\. Select the policies that you want to attach to the new users or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see step 4 in the procedure [Create an IAM Policy \(Console\)](access_policies_create.md#access_policies_create-start)\. After you create the policy, close that tab and return to your original tab to add the policy to the new user\.

1. Choose **Next: Review** to see all of the choices you made up to this point\. When you are ready to proceed, choose **Create user**\.

1. To view the users' access keys \(access key IDs and secret access keys\), choose **Show** next to each password and secret access key that you want to see\. To save the access keys, choose **Download \.csv** and then save the file to a safe location\. 
**Important**  
This is your only opportunity to view or download the secret access keys, and you must provide this information to your users before they can use the AWS API\. Save the user's new access key ID and secret access key in a safe and secure place\. **You will not have access to the secret keys again after this step\.** 

1. Provide each user with his or her credentials\. On the final page you can choose **Send email** next to each user\. Your local mail client opens with a draft that you can customize and send\. The email template includes the following details to each user:
   + User name

      
   + URL to the account sign\-in webpage\. Use the following example, substituting the correct account ID number or account alias:

     ```
     https://AWS-account-ID or alias.signin.aws.amazon.com/console
     ```

   For more information, see [How IAM Users Sign In to AWS](id_users_sign-in.md)\.
**Important**  
The user's password is ***not*** included in the generated email\. You must provide them to the customer in a way that complies with your organization's security guidelines\.

1. \(Optional\) Grant the users permission to manage their own security credentials\. For more information, see [Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys](id_credentials_delegate-permissions_examples.md#creds-policies-credentials)\. 

## Creating IAM Users \(AWS CLI, Tools for Windows PowerShell, or IAM HTTP API\)<a name="id_users_create_cliwpsapi"></a>

**To create an IAM user from the AWS CLI, Tools for Windows PowerShell, or IAM HTTP API**

1. **Create a user\.**
   + AWS CLI: [aws iam create\-user](http://docs.aws.amazon.com/cli/latest/reference/iam/create-user.html)
   + Tools for Windows PowerShell: [New\-IAMUser](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMUser.html&tocid=New-IAMUser)
   + IAM API: [CreateUser](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateUser.html)

1. \(Optional\) **Give the user access to the AWS Management Console**\. This requires a password\. You must also give the user the [URL of your account's sign\-in page\.](id_users_sign-in.md)
   + AWS CLI: [aws iam create\-login\-profile](http://docs.aws.amazon.com/cli/latest/reference/iam/create-login-profile.html)
   + Tools for Windows PowerShell: [New\-IAMLoginProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMLoginProfile.html&tocid=New-IAMLoginProfile)
   + IAM API: [CreateLoginProfile](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateLoginProfile.html)

1. \(Optional\) **Give the user programmatic access**\. This requires access keys\. 
   + AWS CLI: [aws iam create\-access\-key](http://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html)
   + Tools for Windows PowerShell: [New\-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMAccessKey.html&tocid=New-IAMAccessKey)
   + IAM API: [CreateAccessKey](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html)
**Important**  
This is your only opportunity to view or download the secret access keys, and you must provide this information to your users before they can use the AWS API\. Save the user's new access key ID and secret access key in a safe and secure place\. **You will not have access to the secret keys again after this step\.** 

1. **Add the user to one or more groups\.** The groups that you specify should have attached policies that grant the appropriate permissions for the user\. 
   + AWS CLI: [aws iam add\-user\-to\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/add-user-to-group.html) 
   + Tools for Windows PowerShell: [Add\-IAMUserToGroup](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Add-IAMUserToGroup.html&tocid=Add-IAMUserToGroup)
   + IAM API: [AddUserToGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AddUserToGroup.html) 

1. \(Optional\) **Attach a policy to the user** Attach a policy that defines the user's permissions\. **Note:** We recommend that you manage user permissions by adding the user to a group and attaching a policy to the group instead of attaching directly to a user\.
   + AWS CLI: [aws iam attach\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-user-policy.html)
   + Tools for Windows PowerShell: [Register\-IAMUserPolicy](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Register-IAMUserPolicy.html&tocid=Register-IAMUserPolicy)
   + IAM API: [AttachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachUserPolicy.html)

1. \(Optional\) **Give the user permission to manage his or her own security credentials**\. For more information, see [Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys](id_credentials_delegate-permissions_examples.md#creds-policies-credentials)\. 