# Enabling a FIDO security key \(console\)<a name="id_credentials_mfa_enable_fido"></a>

FIDO security keys are a type of [multi\-factor authentication \(MFA\) device](id_credentials_mfa.md) that you can use to protect your AWS resources\. You plug your FIDO security key into a USB port on your computer and enable it using the instructions that follow\. After you enable it, you tap it when prompted to securely complete the sign\-in process\. If you already use a FIDO security key with other services, and it has an [AWS supported configuration](id_credentials_mfa_fido_supported_configurations.md) \(for example, the YubiKey 5 Series from Yubico\), you can also use it with AWS\. Otherwise, you need to purchase a FIDO security key if you want to use WebAuthn for MFA in AWS\. For specifications and purchase information, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.

FIDO2 is an open authentication standard and an extension of FIDO U2F, offering the same high level of security based on public key cryptography\. FIDO2 consists of the W3C Web Authentication specification \(WebAuthn API\) and the FIDO Alliance Client\-to\-Authenticator Protocol \(CTAP\), an application layer protocol\. CTAP enables communication between client or platform, like a browser or operating system, with an external authenticator\. When you enable a FIDO Certified authenticator in AWS, the FIDO security key creates a new key pair for use with only AWS\. First, you enter your credentials\. When prompted, you tap the FIDO security key, which responds to the authentication challenge issued by AWS\. To learn more about the FIDO2 standard, see the [FIDO2 Project](https://en.wikipedia.org/wiki/FIDO2_Project)\.

You can register up to **eight** MFA devices of any combination of the [currently supported MFA types](https://aws.amazon.com/iam/features/mfa/) with your AWS account root user and IAM users\. With multiple MFA devices, you only need one MFA device to sign in to the AWS Management Console or create a session through the AWS CLI as that user\.

**Note**  
We recommend that you require your human users to use temporary credentials when accessing AWS\. Your users can federate into AWS with an identity provider where they authenticate with their corporate credentials and MFA configurations\. To manage access to AWS and business applications, we recommend that you use IAM Identity Center\. For more information, see the [The IAM Identity Center User Guide](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)\. 

**Topics**
+ [Permissions required](#enable-fido-mfa-for-iam-user-permissions-required)
+ [Enable a FIDO security key for your own IAM user \(console\)](#enable-fido-mfa-for-own-iam-user)
+ [Enable a FIDO security key for another IAM user \(console\)](#enable-fido-mfa-for-iam-user)
+ [Enable a FIDO security key for the AWS account root user \(console\)](#enable-fido-mfa-for-root)
+ [Replace a FIDO security key](#replace-fido-mfa)
+ [Supported configurations for using FIDO security keys](id_credentials_mfa_fido_supported_configurations.md)

## Permissions required<a name="enable-fido-mfa-for-iam-user-permissions-required"></a>

To manage a FIDO security key for your own IAM user while protecting sensitive MFA\-related actions, you must have the permissions from the following policy:

**Note**  
The ARN values are static values and are not an indicator of what protocol was used to register the authenticator\. We have deprecated U2F, so all new implementations use WebAuthn\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowManageOwnUserMFA",
            "Effect": "Allow",
            "Action": [
                "iam:DeactivateMFADevice",
                "iam:EnableMFADevice",
                "iam:GetUser",
                "iam:ListMFADevices",
                "iam:ResyncMFADevice"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "DenyAllExceptListedIfNoMFA",
            "Effect": "Deny",
            "NotAction": [
                "iam:EnableMFADevice",
                "iam:GetUser",
                "iam:ListMFADevices",
                "iam:ResyncMFADevice"
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

## Enable a FIDO security key for your own IAM user \(console\)<a name="enable-fido-mfa-for-own-iam-user"></a>

You can enable a FIDO security key for your own IAM user from the AWS Management Console only, not from the AWS CLI or AWS API\.

**Note**  
Before you can enable a FIDO security key, you must have physical access to the device\.

**Note**  
You should not choose any of the available options on the Google Chrome pop\-up that asks to **Verify your identity with amazon\.com**\. You only need to tap on the security key\.

**To enable a FIDO security key for your own IAM user \(console\)**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

   To get your AWS account ID, contact your administrator\.

1. In the navigation bar on the upper right, choose your user name, and then choose **Security credentials**\.   
![\[AWS Management Console Security credentials link\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-user.shared.console.png)

1. On the **AWS IAM credentials** tab, in the **Multi\-factor authentication \(MFA\)** section, choose **Assign MFA device**\.

1. In the wizard, type a **Device name**, choose **Security Key**, and then choose **Next**\.

1. Insert the FIDO security key into your computer's USB port\.  
![\[FIDO security key inserted into a USB port\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the FIDO security key\. 

The FIDO security key is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\. 

## Enable a FIDO security key for another IAM user \(console\)<a name="enable-fido-mfa-for-iam-user"></a>

You can enable a FIDO security key for another IAM user from the AWS Management Console only, not from the AWS CLI or AWS API\.

**To enable a FIDO security key for another IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user for whom you want to enable MFA\.

1. Choose the **Security Credentials** tab\. Under **Multi\-factor authentication \(MFA\)**, choose **Assign MFA device**\.

1. In the wizard, type a **Device name**, choose **Security Key**, and then choose **Next**\.

1. Insert the FIDO security key into your computer's USB port\.  
![\[FIDO security key inserted into a USB port\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the FIDO security key\. 

The FIDO security key is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\.

## Enable a FIDO security key for the AWS account root user \(console\)<a name="enable-fido-mfa-for-root"></a>

You can configure and enable a virtual MFA device for your root user from the AWS Management Console only, not from the AWS CLI or AWS API\. 

If your FIDO security key is lost, stolen, or not working, you can still sign in using another MFA device registered to the same AWS account root user\. If you only have a single MFA device registered, you can sign in using alternate factors of identification\. To learn about signing in using alternative factors of authentication, see [What if an MFA device is lost or stops working?](id_credentials_mfa_lost-or-broken.md)\. To disable this feature, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.<a name="enable_fido_root"></a>

**To enable the FIDO key for your root user \(console\)**

1. Sign in to the [IAM console](https://console.aws.amazon.com/iam/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.
**Note**  
As the root user, you can't sign in to the **Sign in as IAM user** page\. If you see the **Sign in as IAM user** page, choose **Sign in using root user email** near the bottom of the page\. For help signing in as the root user, see [Signing in to the AWS Management Console as the root user](https://docs.aws.amazon.com/signin/latest/userguide/introduction-to-          root-user-sign-in-tutorial.html) in the *AWS Sign\-In User Guide*\.

1. On the right side of the navigation bar, choose your account name, and then choose **Security credentials**\. If necessary, choose **Continue to Security credentials**\.  
![\[Security credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Expand the **Multi\-factor authentication \(MFA\)** section\.

1. Choose **Assign MFA device**\.

1. In the wizard, type a **Device name**, choose **Security Key**, and then choose **Next**\.

1. Insert the FIDO security key into your computer's USB port\.  
![\[FIDO security key inserted into a USB port\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the FIDO security key\. 

The FIDO security key is ready for use with AWS\. The next time you use your root user credentials to sign in, you must tap your FIDO security key to complete the sign\-in process\.

## Replace a FIDO security key<a name="replace-fido-mfa"></a>

You can have up to eight MFA devices of any combination of the [ currently supported MFA types](https://aws.amazon.com/iam/features/mfa/) assigned to a use at a time with your AWS account root user and IAM users\. If the user loses a FIDO authenticator or needs to replace it for any reason, you must first deactivate the old FIDO authenticator\. Then you can add a new MFA device for the user\.
+ To deactivate the device currently associated with an IAM user, see [Deactivating MFA devices](id_credentials_mfa_disable.md)\.
+ To add a new FIDO security key for an IAM user, see [Enable a FIDO security key for your own IAM user \(console\)](#enable-fido-mfa-for-own-iam-user)\.

If you don't have access to a new FIDO security key, you can enable a new virtual MFA device or hardware TOTP token\. See one of the following for instructions:
+ [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md) 
+ [Enabling a hardware TOTP token \(console\)](id_credentials_mfa_enable_physical.md) 