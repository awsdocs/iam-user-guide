# Enabling a U2F Security Key \(Console\)<a name="id_credentials_mfa_enable_u2f"></a>

Universal 2nd Factor \(U2F\) security keys are a type of [MFA device](id_credentials_mfa.md) that you can use to protect your AWS resources\. You plug your U2F security key into a USB port on your computer and enable it using the instructions that follow\. After you enable it, you tap it when prompted to securely complete the sign\-in process\. If you already use a U2F security key with other services, and it has an [AWS supported configuration](id_credentials_mfa_u2f_supported_configurations.md) \(for example, the Yubikey 4 or 5 from Yubico\), you can also use it with AWS\. Otherwise, you need to purchase a U2F security key if you want to use U2F for MFA in AWS\. For specifications and purchase information, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.

U2F is an open authentication standard hosted by the [FIDO Alliance](https://fidoalliance.org)\. When you enable a U2F key in AWS, the U2F security key creates a new key pair for use with only AWS\. First, you enter your credentials\. When prompted, you tap the U2F security key, which responds to the authentication challenge issued by AWS\. To learn more about the U2F standard, see [Universal 2nd Factor](https://en.wikipedia.org/wiki/Universal_2nd_Factor)\.

You can enable **one** MFA device \(of any kind\) per root user or IAM user\. 

**Topics**
+ [Enable a U2F Security Key for an IAM User \(Console\)](#enable-u2f-mfa-for-iam-user)
+ [Enable a U2F Security Key for the AWS Account Root User \(Console\)](#enable-u2f-mfa-for-root)
+ [Replace a U2F Security Key](#replace-u2f-mfa)
+ [Supported Configurations for Using U2F Security Keys](id_credentials_mfa_u2f_supported_configurations.md)

## Enable a U2F Security Key for an IAM User \(Console\)<a name="enable-u2f-mfa-for-iam-user"></a>

You can enable a U2F security key for an IAM user from the AWS Management Console only, not from the AWS CLI or AWS API\. To enable a U2F security key for your AWS account root user, see [Enable a U2F Security Key for the AWS Account Root User \(Console\)](#enable-u2f-mfa-for-root)\.

**To enable a U2F security key for an IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user for whom you want to enable MFA, and then choose the **Security Credentials** tab\.

1. Next to **Assigned MFA device**, choose **Manage**\.

1. In the **Manage MFA Device** wizard, choose **U2F security key**, and then choose **Continue**\.

1. Insert the U2F security key into your computer's USB port\.  
![\[U2F Security Key\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the U2F security key, and then choose **Close** when U2F setup is complete\. 

The U2F security key is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA Devices With Your IAM Sign\-in Page](console_sign-in-mfa.md)\.

## Enable a U2F Security Key for the AWS Account Root User \(Console\)<a name="enable-u2f-mfa-for-root"></a>

You can use IAM in the AWS Management Console to configure and enable a U2F security key for your AWS account root user\. To enable MFA devices for the AWS account, you must be signed in to AWS using your root user credentials\. 

If your U2F security key is lost, stolen, or not working, you can still sign in using alternative factors of authentication\. If you can't sign in with your U2F security key, you can sign in by verifying your identity using the email and phone that are registered with your account\. Before you enable a U2F security key for your root user, review your account settings and contact information to make sure that you have access to the email and phone number\. To learn about signing in using alternative factors of authentication, see [What If an MFA Device Is Lost or Stops Working?](id_credentials_mfa_lost-or-broken.md)\. To disable this feature, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.

**Note**  
You might see different text, such as **Sign in using MFA** and **Troubleshoot your authentication device**\. However, the same features are provided\. In either case, if you cannot verify your account email address and phone number using alternative factors of authentication, contact [AWS Support](https://aws.amazon.com/forms/aws-mfa-support) to deactivate your MFA setting\.<a name="enable_u2f_root"></a>

**To enable the U2F key for your root user \(console\)**

1. Sign in to the AWS Management Console\.
**Important**  
To manage MFA devices for the AWS account, you must use your root user credentials to sign in to AWS\. You cannot manage MFA devices for the root user while signed in with other credentials\.

1. Do one of the following:
   + **Option 1**: Choose **Dashboard**, and under **Security Status**, expand **Activate MFA on your root account**\. 
   + **Option 2**: On the right side of the navigation bar, choose on your account name, and then choose **My Security Credentials**\. If necessary, choose **Continue to Security Credentials**\. Then expand the **Multi\-Factor Authentication \(MFA\)** section on the page\.  
![\[My Security Credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Choose **Manage MFA** or **Activate MFA**, depending on which option you chose in the preceding step\.

1. In the wizard, choose **U2F security key** and then choose **Continue**\.

1. Insert the U2F security key into your computer's USB port\.  
![\[U2F Security Key\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the U2F security key, and then choose **Close** when U2F setup is complete\. 

The U2F security key is ready for use with AWS\. The next time you use your root user credentials to sign in, you must tap your U2F security key to complete the sign\-in process\.

## Replace a U2F Security Key<a name="replace-u2f-mfa"></a>

You can have only one MFA device \(virtual, U2F security key, or hardware\) assigned to a user at a time\. If the user loses a U2F key or needs to replace it for any reason, you must first deactivate the old U2F key\. Then you can add a new MFA device for the user\.
+ To deactivate the device currently associated with a user, see [Deactivating MFA Devices](id_credentials_mfa_disable.md)\.
+ To add a new U2F security for an IAM user, see [Enabling a U2F Security Key \(Console\)](#id_credentials_mfa_enable_u2f)\.

If you don't have access to a new U2F security key, you can enable a new virtual MFA device or hardware MFA device\. See one of the following for instructions:
+ [Enabling a Virtual Multi\-factor Authentication \(MFA\) Device \(Console\)](id_credentials_mfa_enable_virtual.md) 
+ [Enabling a Hardware MFA Device \(Console\)](id_credentials_mfa_enable_physical.md) 