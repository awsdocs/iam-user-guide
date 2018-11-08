# Tutorial: Enable Your Users to Configure Their Own Credentials and MFA Settings<a name="tutorial_users-self-manage-mfa-and-creds"></a>

You can enable your users to self\-manage their own multi\-factor authentication \(MFA\) devices and credentials\. You can use the AWS Management Console to configure credentials \(access keys, passwords, signing certificates, and SSH public keys\) and MFA devices for your users in small numbers\. But that is a task that could quickly become time consuming as the number of users grows\. Security best practice specifies that users should regularly change their passwords and rotate their access keys\. They should also delete or deactivate credentials that are not needed and use MFA, at the very least, for sensitive operations\. Showing you how to enable these best practices without burdening your administrators is the goal of this tutorial\.

This tutorial shows how to grant users access to AWS services, but **only** when they sign in with MFA\. If they are not signed in with an MFA device, then users cannot access other services\.

This workflow has three basic steps\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

**[Step 1: Create a Policy to Enforce MFA Sign\-In](#tutorial_mfa_step1)**  
Create a customer managed policy that prohibits all actions ***except*** the few IAM API operations that enable changing credentials and managing MFA devices\. Note that MFA permissions are the same for all MFA devices that AWS supports\.

**[Step 2: Attach Policies to Your Test Group](#tutorial_mfa_step2)**  
Create a group whose members have full access to all Amazon EC2 actions if they sign in with MFA\. To create such a group, you attach both the AWS managed policy called `AmazonEC2FullAccess` and the customer managed policy you created in the first step\.

**[Step 3: Test Your User's Access](#tutorial_mfa_step3)**  
Sign in as the test user to verify that access to Amazon EC2 is blocked *until* the user creates an MFA device and then signs in using that device\. 

## Prerequisites<a name="tutorial_mfa_prereqs"></a>

To perform the steps in this tutorial, you must already have the following:
+ An AWS account that you can sign in to as an IAM user with administrative permissions\.
+ Your account ID number, which you type into the policy in Step 1\. 

  To find your account ID number, on the navigation bar at the top of the page, choose **Support** and then choose **Support Center**\. You can find your account ID under this page's **Support** menu\. 
+ A [virtual \(software\-based\) MFA device](id_credentials_mfa_enable_virtual.md), [U2F security key](id_credentials_mfa_enable_u2f.md), or [hardware\-based MFA device](id_credentials_mfa_enable_physical.md)\.
+ A test IAM user who is a member of a group as follows:


****  

| *Create User Account* | *Create and Configure Group Account* | User Name | Other Instructions | Group Name | Add User as a Member | Other Instructions | 
| --- | --- | --- | --- | --- | --- | --- | 
| MFAUser | Choose only the option for AWS Management Console access, and assign a password\. | EC2MFA | MFAUser | Do NOT attach any policies or otherwise grant permissions to this group\. | 

## Step 1: Create a Policy to Enforce MFA Sign\-In<a name="tutorial_mfa_step1"></a>

You begin by creating an IAM customer managed policy that denies all permissions except those required for IAM users to manage their own credentials and MFA devices\.

1. Sign in to the AWS Management Console as a user with administrator credentials\. To adhere to IAM best practices, don’t sign in with your AWS account root user credentials\. For more information, see [Create individual IAM users](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#create-iam-users)\.

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**, and then choose **Create policy**\.

1. Choose the **JSON** tab and copy the text from the following JSON policy document\. Paste this text into the **JSON** text box\.
**Note**  
This example policy does not allow users to reset a password while signing in\. New users and users with an expired password might try to do so\. You can allow this by adding `iam:ChangePassword` and `iam:CreateLoginProfile` to the statement `BlockMostAccessUnlessSignedInWithMFA`\. However, IAM does not recommend this\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Sid": "AllowAllUsersToListAccounts",
               "Effect": "Allow",
               "Action": [
                   "iam:ListAccountAliases",
                   "iam:ListUsers",
                   "iam:ListVirtualMFADevices",
                   "iam:GetAccountPasswordPolicy",
                   "iam:GetAccountSummary"
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
                   "iam:GetLoginProfile",
                   "iam:ListAccessKeys",
                   "iam:UpdateAccessKey",
                   "iam:UpdateLoginProfile",
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
               "Sid": "AllowIndividualUserToViewAndManageTheirOwnMFA",
               "Effect": "Allow",
               "Action": [
                   "iam:CreateVirtualMFADevice",
                   "iam:DeleteVirtualMFADevice",
                   "iam:EnableMFADevice",
                   "iam:ListMFADevices",
                   "iam:ResyncMFADevice"
               ],
               "Resource": [
                   "arn:aws:iam::*:mfa/${aws:username}",
                   "arn:aws:iam::*:u2f/${aws:username}",
                   "arn:aws:iam::*:user/${aws:username}"
               ]
           },
           {
               "Sid": "AllowIndividualUserToDeactivateOnlyTheirOwnMFAOnlyWhenUsingMFA",
               "Effect": "Allow",
               "Action": [
                   "iam:DeactivateMFADevice"
               ],
               "Resource": [
                   "arn:aws:iam::*:mfa/${aws:username}",
                   "arn:aws:iam::*:u2f/${aws:username}",
                   "arn:aws:iam::*:user/${aws:username}"
               ],
               "Condition": {
                   "Bool": {
                       "aws:MultiFactorAuthPresent": "true"
                   }
               }
           },
           {
               "Sid": "BlockMostAccessUnlessSignedInWithMFA",
               "Effect": "Deny",
               "NotAction": [
                   "iam:CreateVirtualMFADevice",
                   "iam:DeleteVirtualMFADevice",
                   "iam:ListVirtualMFADevices",
                   "iam:EnableMFADevice",
                   "iam:ResyncMFADevice",
                   "iam:ListAccountAliases",
                   "iam:ListUsers",
                   "iam:ListSSHPublicKeys",
                   "iam:ListAccessKeys",
                   "iam:ListServiceSpecificCredentials",
                   "iam:ListMFADevices",
                   "iam:GetAccountSummary",
                   "sts:GetSessionToken"
               ],
               "Resource": "*",
               "Condition": {
                   "BoolIfExists": {
                       "aws:MultiFactorAuthPresent": "false"
                   }
               }
           }
       ]
   }
   ```

   What does this policy do? 
   + The `AllowAllUsersToListAccounts` statement enables the user to see basic information about the account and its users in the IAM console\. These permissions must be in their own statement because they do not support or do not need to specify a specific resource ARN, and instead specify `"Resource" : "*"`\.
   + The `AllowIndividualUserToSeeAndManageOnlyTheirOwnAccountInformation` statement enables the user to manage his or her own user, password, access keys, signing certificates, SSH public keys, and MFA information in the IAM console\. It also allows users to sign in for the first time in an administrator requires them to set a first\-time password\. The resource ARN limits the use of these permissions to only the user's own IAM user entity\.
   + The `AllowIndividualUserToViewAndManageTheirOwnMFA` statement enables the user to view or manage his or her own MFA device\. Notice that the resource ARNs in this statement allow access to only an MFA device or user that has the same name as the currently signed\-in user\. Users can't create or alter any MFA device other than their own\.
   + The `AllowIndividualUserToDeactivateOnlyTheirOwnMFAOnlyWhenUsingMFA` statement allows the user to deactivate only his or her own MFA device, and only if the user signed in using MFA\. This prevents others with only the access keys \(and not the MFA device\) from deactivating the MFA device and accessing the account\.
   + The `BlockMostAccessUnlessSignedInWithMFA` statement uses a combination of `"Deny"` and `"NotAction"` to deny access to all but a few actions in IAM and other AWS services ***if*** the user is not signed\-in with MFA\. For more information about the logic for this statement, see [NotAction with Deny](reference_policies_elements_notaction.md)\. If the user is signed\-in with MFA, then the `"Condition"` test fails and the final "deny" statement has no effect and other policies or statements for the user determine the user's permissions\. This statement ensures that when the user is not signed\-in with MFA, they can perform only the listed actions and only if another statement or policy allows access to those actions\.

     The `...IfExists` version of the `Bool` operator ensures that if the `aws:MultiFactorAuthPresent` key is missing, the condition returns true\. This means that a user accessing an API with long\-term credentials, such as an access key, is denied access to the non\-IAM API operations\.

1. When you are finished, choose **Review policy**\. The [Policy Validator](access_policies_policy-validator.md) reports any syntax errors\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, the policy above includes the `NotAction` element, which is not supported in the visual editor\. For this policy, you will see a notification on the **Visual editor** tab\. Return to the **JSON** tab to continue working with this policy\.

1. On the **Review** page, type **Force\_MFA** for the policy name\. For the policy description, type **This policy allows users to manage their own passwords and MFA devices but nothing else unless they authenticate with MFA\.** Review the policy **Summary** to see the permissions granted by your policy, and then choose **Create policy** to save your work\.

   The new policy appears in the list of managed policies and is ready to attach\.

## Step 2: Attach Policies to Your Test Group<a name="tutorial_mfa_step2"></a>

Next you attach two policies to the test IAM group, which will be used to grant the MFA\-protected permissions\.

1. In the navigation pane, choose **Groups**\.

1. In the search box, type **`EC2MFA`**, and then choose the group name \(not the check box\) in the list\. 

1. On the **Permissions** tab, and click **Attach Policy**\.

1. On the **Attach Policy** page, in the search box, type **EC2Full** and then select the check box next to **AmazonEC2FullAccess** in the list\. Don't save your changes yet\.

1. In the search box, type **Force**, and then select the check box next to **Force\_MFA** in the list\. 

1. Choose **Attach Policy**\.

## Step 3: Test Your User's Access<a name="tutorial_mfa_step3"></a>

In this part of the tutorial, you sign in as the test user and verify that the policy works as intended\.

1. Sign in to your AWS account as **MFAUser** with the password you assigned in the previous section\. Use the URL: `https://<alias or account ID number>.signin.aws.amazon.com/console`

1. Choose **EC2** to open the Amazon EC2 console and verify that the user has no permissions to do anything\.

1. On the navigation bar, choose **Services**, and then choose **IAM** to open the IAM console\.

1. In the navigation pane, choose **Users**, and then choose the user \(not the check box\) **MFAUser**\. If the **Groups** tab appears by default, note that it says that you don't have permissions to see your group memberships\.

1. Now add an MFA device\. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose **Manage**\.

1. For this tutorial, we use a virtual \(software\-based\) MFA device, such as the Google Authenticator app on a mobile phone\. Choose **Virtual MFA device**, and then click **Continue**\.

   IAM generates and displays configuration information for the virtual MFA device, including a QR code graphic\. The graphic is a representation of the secret configuration key that is available for manual entry on devices that do not support QR codes\.

1. Open your virtual MFA app\. \(For a list of apps that you can use for hosting virtual MFA devices, see [Virtual MFA Applications](https://aws.amazon.com/iam/details/mfa/#Virtual_MFA_Applications)\.\) If the virtual MFA app supports multiple accounts \(multiple virtual MFA devices\), choose the option to create a new account \(a new virtual MFA device\)\.

1. Determine whether the MFA app supports QR codes, and then do one of the following:
   + From the wizard, choose **Show QR code**\. Then use the app to scan the QR code\. For example, you might choose the camera icon or choose an option similar to **Scan code**, and then use the device's camera to scan the code\.
   + In the **Manage MFA Device** wizard, choose **Show secret key**, and then type the secret key into your MFA app\.

   When you are finished, the virtual MFA device starts generating one\-time passwords\. 

1. In the **Manage MFA Device** wizard, in the **MFA Code 1** box, type the one\-time password that currently appears in the virtual MFA device\. Wait up to 30 seconds for the device to generate a new one\-time password\. Then type the second one\-time password into the **MFA Code 2** box\. Choose **Assign MFA**\. 
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the MFA device is successfully associated with the user\. However, the MFA device is out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\. If this happens, you can [resync the device](id_credentials_mfa_sync.md)\.

   The virtual MFA device is now ready to use with AWS\. 

1. Sign out of the console and then sign in as **MFAUser** again\. This time AWS prompts you for an MFA code from your phone\. When you get it, type the code in the box and then choose **Submit**\.

1. Choose **EC2** to open the Amazon EC2 console again\. Note that this time you can see all the information and perform any actions you want\. If you go to any other console as this user, you see access denied messages because the policies in this tutorial grant access only to Amazon EC2\. 

## Related Resources<a name="tutorial_mfa_related"></a>

For related information found in the *IAM User Guide*, see the following resources:
+ [Using Multi\-Factor Authentication \(MFA\) in AWS](id_credentials_mfa.md)
+ [Enabling MFA Devices](id_credentials_mfa_enable.md)
+ [Using MFA Devices With Your IAM Sign\-in Page](console_sign-in-mfa.md)
