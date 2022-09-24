# Enabling a FIDO security key \(console\)<a name="id_credentials_mfa_enable_fido"></a>

FIDO security keys are a type of [MFA device](id_credentials_mfa.md) that you can use to protect your AWS resources\. You plug your FIDO security key into a USB port on your computer and enable it using the instructions that follow\. After you enable it, you tap it when prompted to securely complete the sign\-in process\. If you already use a FIDO security key with other services, and it has an [AWS supported configuration](id_credentials_mfa_fido_supported_configurations.md) \(for example, the Yubikey 5 Series from Yubico\), you can also use it with AWS\. Otherwise, you need to purchase a FIDO2 security key if you want to use Webauthn for MFA in AWS\. For specifications and purchase information, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.

FIDO2 is an open authentication standard and an extension of FIDO U2F, offering the same high level of security based on public key cryptography\. FIDO2 consists of the W3C Web Authentication specification \(WebAuthn API\) and the Client to Authentication Protocol \(CTAP\), an application layer protocol\. CTAP enables communication between client or platform, like a browser or operating system, with an external authenticator\. You can continue to use FIDO\-compliant devices, such as FIDO U2F security keys\. When you enable a FIDO\-compliant authenticator in AWS, the FIDO security key creates a new key pair for use with only AWS\. First, you enter your credentials\. When prompted, you tap the FIDO security key, which responds to the authentication challenge issued by AWS\. To learn more about the FIDO2 standard, see the [FIDO2 Project](https://en.wikipedia.org/wiki/FIDO2_Project)\.

You can enable **one** MFA device \(of any kind\) per root user or IAM user\. 

**Topics**
+ [Permissions required](#enable-fido-mfa-for-iam-user-permissions-required)
+ [Enable a FIDO security key for your own IAM user \(console\)](#enable-fido-mfa-for-own-iam-user)
+ [Enable a FIDO security key for another IAM user \(console\)](#enable-fido-mfa-for-iam-user)
+ [Enable a FIDO security key for the AWS account root user \(console\)](#enable-fido-mfa-for-root)
+ [Replace a FIDO security key](#replace-fido-mfa)
+ [Supported configurations for using FIDO security keys](id_credentials_mfa_fido_supported_configurations.md)

## Permissions required<a name="enable-fido-mfa-for-iam-user-permissions-required"></a>

To manage a FIDO security key for your own IAM user while protecting sensitive MFA\-related actions, you must have the permissions from the following policy:

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
            "Resource": "arn:aws:iam::*:user/${aws:username}",
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

1. In the navigation bar on the upper right, choose your user name, and then choose **My Security Credentials**\.   
![\[AWS Management Console My Security Credentials link\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-user.shared.console.png)

1. On the **AWS IAM credentials** tab, in the **Multi\-factor authentication** section, choose **Manage MFA device**\.

1. In the **Manage MFA device** wizard, choose **FIDO security key**, and then choose **Continue**\.

1. Insert the FIDO security key into your computer's USB port\.  
![\[FIDO Security Key\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the FIDO2 security key, and then choose **Close** when setup is complete\. 

The FIDO2 security key is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\.

## Enable a FIDO security key for another IAM user \(console\)<a name="enable-fido-mfa-for-iam-user"></a>

You can enable a FIDO security key for another IAM user from the AWS Management Console only, not from the AWS CLI or AWS API\.

**To enable a FIDO security key for another IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user for whom you want to enable MFA, and then choose the **Security credentials** tab\.

1. Next to **Assigned MFA device**, choose **Manage**\.

1. In the **Manage MFA device** wizard, choose **FIDO security key**, and then choose **Continue**\.

1. Insert the FIDO security key into your computer's USB port\.  
![\[FIDO Security Key\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the FIDO security key, and then choose **Close** when setup is complete\. 

The FIDO security key is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\.

## Enable a FIDO security key for the AWS account root user \(console\)<a name="enable-fido-mfa-for-root"></a>

You can configure and enable a virtual MFA device for your root user from the AWS Management Console only, not from the AWS CLI or AWS API\. 

If your FIDO security key is lost, stolen, or not working, you can still sign in using alternative factors of authentication\. To learn about signing in using alternative factors of authentication, see [What if an MFA device is lost or stops working?](id_credentials_mfa_lost-or-broken.md)\. To disable this feature, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.<a name="enable_fido_root"></a>

**To enable the FIDO key for your root user \(console\)**

1. Sign in to the [IAM console](https://console.aws.amazon.com/iam/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.
**Note**  
If you see three text boxes, then you previously signed in to the console with *[IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* credentials\. Your browser might remember this preference and open this account\-specific sign\-in page every time that you try to sign in\. You cannot use the IAM user sign\-in page to sign in as the account owner\. If you see the [IAM user sign\-in page](https://docs.aws.amazon.com/IAM/latest/UserGuide/console.html#user-sign-in-page), choose **Sign in using root user email** near the bottom of the page\. This returns you to the main sign\-in page\. From there, you can sign in as the root user using your AWS account email address and password\.

1. On the right side of the navigation bar, choose on your account name, and then choose **My Security Credentials**\. If necessary, choose **Continue to Security Credentials**\.  
![\[My Security Credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Expand the **Multi\-factor authentication \(MFA\)** section\.

1. Choose **Manage MFA** or **Activate MFA**, depending on which option you chose in the preceding step\.

1. In the wizard, choose **FIDO security key** and then choose **Continue**\.

1. Insert the FIDO security key into your computer's USB port\.  
![\[FIDO Security Key\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the FIDO security key, and then choose **Close** when setup is complete\. 

The FIDO security key is ready for use with AWS\. The next time you use your root user credentials to sign in, you must tap your FIDO security key to complete the sign\-in process\.

## Replace a FIDO security key<a name="replace-fido-mfa"></a>

You can have only one MFA device \(virtual, FIDO security key, or hardware\) assigned to a user at a time\. If the user loses a FIDO\-compliant authenticator or needs to replace it for any reason, you must first deactivate the old FIDO\-compliant authenticator\. Then you can add a new MFA device for the user\.
+ To deactivate the device currently associated with a user, see [Deactivating MFA devices](id_credentials_mfa_disable.md)\.
+ To add a new FIDO security key for an IAM user, see [Enabling a FIDO security key \(console\)](#id_credentials_mfa_enable_fido)\.

If you don't have access to a new FIDO security key, you can enable a new virtual MFA device or hardware MFA device\. See one of the following for instructions:
+ [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md) 
+ [Enabling a hardware MFA device \(console\)](id_credentials_mfa_enable_physical.md) 