# What If an MFA Device Is Lost or Stops Working?<a name="id_credentials_mfa_lost-or-broken"></a>

If your AWS account root user multi\-factor authentication \(MFA\) device is lost, damaged, or not working, you can sign in using alternative methods of authentication\. This means that if you can't sign in with your MFA device, you can sign in by verifying your identity using the email and phone that are registered with your account\. 

If the device appears to be functioning properly, but you cannot use it to access your AWS resources, then it might be out of synchronization with the AWS system\. For information about synchronizing an MFA device, see [Resynchronize MFA Devices](id_credentials_mfa_sync.md)\.

If the MFA device associated with an IAM user is lost or stops working, the user can't recover it\. IAM users must contact an administrator to deactivate the device\.

Before you sign in as a root user using alternative factors of authentication, make sure that you have access to the email and phone number that are associated with your account\.

**To sign in using alternative factors of authentication as an AWS account root user**

1. On the **Amazon Web Services Sign In With Authentication Device** page, choose **Having problems with your authentication device? Click here**\.
**Note**  
If you are using an AWS account created after September 14, 2017, you might see the following console text: **Sign in with authentication device**, **Troubleshoot your authentication device**\. However, the same features are provided\. In either case, if you cannot verify your account email address and phone number using alternative factors of authentication, contact [AWS Support](https://aws.amazon.com/forms/aws-mfa-support) to deactivate your MFA setting\.

1. If required, type your password again and choose **Sign in**\.

1. In the **Sign In Using Alternative Factors of Authentication** section, choose **Sign in using alternative factors**\.

1. To authenticate your account by verifying the email address, choose **Send verification email**\. 

1. Check the email that is associated with your AWS account for a message from Amazon Web Services \(no\-reply\-aws@amazon\.com\)\. Follow the directions in the email\.

   If you don't see the email in your account, check your spam folder, or return to your browser and choose **Resend the email**\.

1. After you verify your email address, you can continue authenticating your account\. To verify your phone number, choose **Call me now**\.

1. Answer the call from AWS and, when prompted, enter the 6\-digit number from the AWS website on your phone keypad\. 

   If you don't receive a call from AWS, choose **Sign in **to sign in to the console again and start over\. Or choose **AWS Support** to contact support for help\.

1. After you verify your phone number, you can sign in to your account by choosing **Sign in to the console**\.

1. If you are using a hardware MFA device, contact the third\-party provider for help fixing or replacing the device\. You can continue to sign in using alternative factors of authentication until you receive your new device\. After you have the new physical MFA device, go to the [AWS Security Credentials](https://console.aws.amazon.com/iam/home?#security_credential) page and delete the old MFA hardware device entity before you create a new one\.

   If you are using a virtual MFA device, remove the account from your device\. Then go to the [AWS Security Credentials](https://console.aws.amazon.com/iam/home?#security_credential) page and delete the old MFA virtual device entity before you create a new one\.

1. If your MFA device is missing or stolen, also [change your AWS password](id_credentials_passwords_change-root.md) in case an attacker has stolen the authentication device and might also have your current password\.

**To get help for an MFA device as an IAM user**

1. Contact the AWS administrator or other person who gave you the user name and password for the IAM user\. The administrator must deactivate the MFA device as described in [Deactivating MFA Devices](id_credentials_mfa_disable.md) so that you can sign in\.

1. If you are using a hardware MFA device, contact the third\-party provider for help fixing or replacing the device\. After you have the new physical MFA device, enable the device as described in [Enabling a Hardware MFA Device \(Console\)](id_credentials_mfa_enable_physical.md)\.

   If you are using a virtual MFA device, remove the account from your device\. Then enable the virtual device as described in [Enabling a Virtual Multi\-factor Authentication \(MFA\) Device](id_credentials_mfa_enable_virtual.md)\.

1. If your MFA device is missing or stolen, also [change your password](id_credentials_passwords.md#id_credentials_passwords_user-change-own) in case an attacker has stolen the authentication device and might also have your current password\.