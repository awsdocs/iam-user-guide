# What if an MFA device is lost or stops working?<a name="id_credentials_mfa_lost-or-broken"></a>

If your [virtual MFA device](id_credentials_mfa_enable_virtual.md) or [hardware TOTP token](id_credentials_mfa_enable_physical.md) appears to be functioning properly, but you can't use it to access your AWS resources, it might be out of synchronization with AWS\. For information about synchronizing a virtual MFA device or hardware MFA device, see [Resynchronizing virtual and hardware MFA devices](id_credentials_mfa_sync.md)\. [FIDO security keys](id_credentials_mfa_enable_fido.md) do not go out of sync\.

If your AWS account root user [multi\-factor authentication \(MFA\) device](id_credentials_mfa.md) is lost, damaged, or not working, you can recover access to your account\. IAM users must contact an administrator to deactivate the device\.

**Important**  
We recommend that you enable multiple MFA devices for your IAM users to ensure continued access to your account in case of lost or inaccessible MFA device\. You can register up to eight MFA devices of any combination of the currently supported MFA types with your AWS account root user and IAM users\.

## Recovering a root user MFA device<a name="root-mfa-lost-or-broken"></a>

If your AWS account root user [multi\-factor authentication \(MFA\) device](id_credentials_mfa.md) is lost, damaged, or not working, you can sign in using another MFA device registered to the same AWS account root user\. If the root user only has one MFA device enabled, you can use alternative methods of authentication\. This means that if you can't sign in with your MFA device, you can sign in by verifying your identity using the email and the primary contact phone number registered with your account\.

Before you use alternative factors of authentication to sign in as a root user, you must be able to access the email and primary contact phone number that are associated with your account\. If you need to update the primary contact phone number, you can sign in as an IAM user with *Administrator* access instead of the root user\. For additional instructions on updating the account contact information, see [https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-account-payment.html#contact-info](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-account-payment.html#contact-info)\. If you do not have access to an email and primary contact phone number, you must contact [AWS Support](https://aws.amazon.com/forms/aws-mfa-support)\.

**Important**  
We recommend that you keep the email address and contact phone number linked to your root user up to date for a successful account recovery\.

**To sign in using alternative factors of authentication as an AWS account root user**

1.  Sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.

1. On the **Amazon Web Services Sign In With Authentication Device** page, choose **Having problems with your authentication device? Click here**\.
**Note**  
You might see alternative text, such as **Sign in using MFA**, **Troubleshoot your authentication device**, or **Troubleshoot MFA**, but the functionality is the same\. If you can't use alternative factors of authentication to verify your account email address and primary contact phone number, contact [AWS Support](https://aws.amazon.com/forms/aws-mfa-support) to deactivate your MFA device\.

1. If required, type your password again and choose **Sign in**\.

1. In the **Sign In Using Alternative Factors of Authentication** section, choose **Sign in using alternative factors**\.

1. To authenticate your account by verifying the email address, choose **Send verification email**\. 

1. Check the email that is associated with your AWS account for a message from Amazon Web Services \(no\-reply\-aws@amazon\.com\)\. Follow the directions in the email\.

   If you don't see the email in your account, check your spam folder, or return to your browser and choose **Resend the email**\.

1. After you verify your email address, you can continue authenticating your account\. To verify your primary contact phone number, choose **Call me now**\.

1. Answer the call from AWS and, when prompted, enter the 6\-digit number from the AWS website on your phone keypad\. 

   If you don't receive a call from AWS, choose **Sign in **to sign in to the console again and start over\. Or see [Lost or unusable Multi\-Factor Authentication \(MFA\) device](https://support.aws.amazon.com/#/contacts/aws-mfa-support) to contact support for help\.

1. After you verify your phone number, you can sign in to your account by choosing **Sign in to the console**\.

1. The next step varies depending on the type of MFA you are using:
   + For a virtual MFA device, remove the account from your device\. Then go to the [AWS Security Credentials](https://console.aws.amazon.com/iam/home?#security_credential) page and delete the old MFA virtual device entity before you create a new one\.
   + For a FIDO security key, go to the [AWS Security Credentials](https://console.aws.amazon.com/iam/home?#security_credential) page and deactivate the old FIDO security key before enabling a new one\.
   + For a hardware TOTP token, contact the third\-party provider for help fixing or replacing the device\. You can continue to sign in using alternative factors of authentication until you receive your new device\. After you have the new hardware MFA device, go to the [AWS Security Credentials](https://console.aws.amazon.com/iam/home?#security_credential) page and delete the old MFA hardware device entity before you create a new one\.
**Note**  
You don't have to replace a lost or stolen MFA device with the same type of device\. For example, if you break your FIDO security key and order a new one, you can use virtual MFA or a hardware TOTP token until you receive a new FIDO security key\.

1. If your MFA device is missing or stolen, also [change your AWS password](id_credentials_passwords_change-root.md) in case an attacker has stolen the authentication device and might also have your current password\.

## Recovering an IAM user MFA device<a name="iam-user-mfa-lost-or-broken"></a>

If you are an IAM user and your device is lost or stops working, you can't recover it by yourself\. You must contact an administrator to deactivate the device\. Then you can enable a new device\.

**To get help for an MFA device as an IAM user**

1. Contact the AWS administrator or other person who gave you the user name and password for the IAM user\. The administrator must deactivate the MFA device as described in [Deactivating MFA devices](id_credentials_mfa_disable.md) so that you can sign in\.

1. The next step varies depending on the type of MFA you are using:
   + For a virtual MFA device, remove the account from your device\. Then enable the virtual device as described in [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md)\.
   + For a FIDO security key, contact the third\-party provider for help replacing the device\. When you receive the new FIDO security key, enable it as described in [Enabling a FIDO security key \(console\)](id_credentials_mfa_enable_fido.md)\.
   + For a hardware TOTP token, contact the third\-party provider for help fixing or replacing the device\. After you have the new physical MFA device, enable the device as described in [Enabling a hardware TOTP token \(console\)](id_credentials_mfa_enable_physical.md)\.
**Note**  
You don't have to replace a lost or stolen MFA device with the same type of device\. You can have up to eight MFA devices of any combination\. For example, if you break your FIDO security key and order a new one, you can use virtual MFA or a hardware TOTP token until you receive a new FIDO security key\.

1. If your MFA device is missing or stolen, also [change your password](id_credentials_passwords_user-change-own.md) in case an attacker has stolen the authentication device and might also have your current password\.