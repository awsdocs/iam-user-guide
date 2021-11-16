# Enabling a U2F security key \(console\)<a name="id_credentials_mfa_enable_u2f"></a>

Universal 2nd Factor \(U2F\) security keys are a type of [MFA device](id_credentials_mfa.md) that you can use to protect your AWS resources\. You plug your U2F security key into a USB port on your computer and enable it using the instructions that follow\. After you enable it, you tap it when prompted to securely complete the sign\-in process\. If you already use a U2F security key with other services, and it has an [AWS supported configuration](id_credentials_mfa_u2f_supported_configurations.md) \(for example, the Yubikey 4 or 5 from Yubico\), you can also use it with AWS\. Otherwise, you need to purchase a U2F security key if you want to use U2F for MFA in AWS\. For specifications and purchase information, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.

U2F is an open authentication standard hosted by the [FIDO Alliance](https://fidoalliance.org)\. When you enable a U2F key in AWS, the U2F security key creates a new key pair for use with only AWS\. First, you enter your credentials\. When prompted, you tap the U2F security key, which responds to the authentication challenge issued by AWS\. To learn more about the U2F standard, see [Universal 2nd Factor](https://en.wikipedia.org/wiki/Universal_2nd_Factor)\.

You can enable **one** MFA device \(of any kind\) per root user or IAM user\. 

**Topics**
+ [Permissions required](#enable-u2f-mfa-for-iam-user-permissions-required)
+ [Enable a U2F security key for your own IAM user \(console\)](#enable-u2f-mfa-for-own-iam-user)
+ [Enable a U2F security key for another IAM user \(console\)](#enable-u2f-mfa-for-iam-user)
+ [Enable a U2F security key for the AWS account root user \(console\)](#enable-u2f-mfa-for-root)
+ [Replace a U2F security key](#replace-u2f-mfa)
+ [Supported configurations for using U2F security keys](id_credentials_mfa_u2f_supported_configurations.md)

## Permissions required<a name="enable-u2f-mfa-for-iam-user-permissions-required"></a>

To manage a U2F security key for your own IAM user while protecting sensitive MFA\-related actions, you must have the permissions from the following policy:

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

## Enable a U2F security key for your own IAM user \(console\)<a name="enable-u2f-mfa-for-own-iam-user"></a>

You can enable a U2F security key for your own IAM user from the AWS Management Console only, not from the AWS CLI or AWS API\.

**Note**  
Before you can enable a U2F security key, you must have physical access to the device\.

**To enable a U2F security key for your own IAM user \(console\)**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

   To get your AWS account ID, contact your administrator\.

1. In the navigation bar on the upper right, choose your user name, and then choose **My Security Credentials**\.   
![\[AWS Management Console My Security Credentials link\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-user.shared.console.png)

1. On the **AWS IAM credentials** tab, in the **Multi\-factor authentication** section, choose **Manage MFA device**\.

1. In the **Manage MFA device** wizard, choose **U2F security key**, and then choose **Continue**\.

1. Insert the U2F security key into your computer's USB port\.  
![\[U2F Security Key\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the U2F security key, and then choose **Close** when U2F setup is complete\. 

The U2F security key is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\.

## Enable a U2F security key for another IAM user \(console\)<a name="enable-u2f-mfa-for-iam-user"></a>

You can enable a U2F security key for another IAM user from the AWS Management Console only, not from the AWS CLI or AWS API\.

**To enable a U2F security key for another IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user for whom you want to enable MFA, and then choose the **Security credentials** tab\.

1. Next to **Assigned MFA device**, choose **Manage**\.

1. In the **Manage MFA device** wizard, choose **U2F security key**, and then choose **Continue**\.

1. Insert the U2F security key into your computer's USB port\.  
![\[U2F Security Key\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the U2F security key, and then choose **Close** when U2F setup is complete\. 

The U2F security key is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\.

## Enable a U2F security key for the AWS account root user \(console\)<a name="enable-u2f-mfa-for-root"></a>

You can configure and enable a virtual MFA device for your root user from the AWS Management Console only, not from the AWS CLI or AWS API\. 

If your U2F security key is lost, stolen, or not working, you can still sign in using alternative factors of authentication\. To learn about signing in using alternative factors of authentication, see [What if an MFA device is lost or stops working?](id_credentials_mfa_lost-or-broken.md)\. To disable this feature, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.<a name="enable_u2f_root"></a>

**To enable the U2F key for your root user \(console\)**

1. Sign in to the [IAM console](https://console.aws.amazon.com/iam/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.
**Note**  
If you see three text boxes, then you previously signed in to the console with *[IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* credentials\. Your browser might remember this preference and open this account\-specific sign\-in page every time that you try to sign in\. You cannot use the IAM user sign\-in page to sign in as the account owner\. If you see the [IAM user sign\-in page](https://docs.aws.amazon.com/IAM/latest/UserGuide/console.html#user-sign-in-page), choose **Sign in using root user email** near the bottom of the page\. This returns you to the main sign\-in page\. From there, you can sign in as the root user using your AWS account email address and password\.

1. On the right side of the navigation bar, choose on your account name, and then choose **My Security Credentials**\. If necessary, choose **Continue to Security Credentials**\.  
![\[My Security Credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Expand the **Multi\-factor authentication \(MFA\)** section\.

1. Choose **Manage MFA** or **Activate MFA**, depending on which option you chose in the preceding step\.

1. In the wizard, choose **U2F security key** and then choose **Continue**\.

1. Insert the U2F security key into your computer's USB port\.  
![\[U2F Security Key\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/u2f-key.png)

1. Tap the U2F security key, and then choose **Close** when U2F setup is complete\. 

The U2F security key is ready for use with AWS\. The next time you use your root user credentials to sign in, you must tap your U2F security key to complete the sign\-in process\.

## Replace a U2F security key<a name="replace-u2f-mfa"></a>

You can have only one MFA device \(virtual, U2F security key, or hardware\) assigned to a user at a time\. If the user loses a U2F key or needs to replace it for any reason, you must first deactivate the old U2F key\. Then you can add a new MFA device for the user\.
+ To deactivate the device currently associated with a user, see [Deactivating MFA devices](id_credentials_mfa_disable.md)\.
+ To add a new U2F security for an IAM user, see [Enabling a U2F security key \(console\)](#id_credentials_mfa_enable_u2f)\.

If you don't have access to a new U2F security key, you can enable a new virtual MFA device or hardware MFA device\. See one of the following for instructions:
+ [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md) 
+ [Enabling a hardware MFA device \(console\)](id_credentials_mfa_enable_physical.md) 