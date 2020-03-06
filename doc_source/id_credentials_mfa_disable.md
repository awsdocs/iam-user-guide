# Deactivating MFA Devices<a name="id_credentials_mfa_disable"></a>

If you have having trouble signing in with a multi\-factor authentication \(MFA\) device as an IAM user, contact your administrator for help\. 

As an administrator, you can deactivate the device for another IAM user\. This allows the user to sign in without using MFA\. You might do this as a temporary solution while the MFA device is replaced, or if the device is temporarily unavailable\. However, we recommend that you enable a new device for the user as soon as possible\. To learn how to enable a new MFA device, see [Enabling MFA Devices](id_credentials_mfa_enable.md)\.

**Note**  
If you use the API or AWS CLI to delete a user from your AWS account, you must deactivate or delete the user's MFA device\. You make this change as part of the process of removing the user\. For more information about deleting users, see [Managing IAM Users](id_users_manage.md)\.

**Topics**
+ [Deactivating MFA Devices \(Console\)](#deactive-mfa-console)
+ [Deactivating MFA Devices \(AWS CLI\)](#deactivate-mfa-cli)
+ [Deactivating MFA Devices \(AWS API\)](#deactivate-mfa-api)

## Deactivating MFA Devices \(Console\)<a name="deactive-mfa-console"></a><a name="deactivate-mfa-for-user"></a>

**To deactivate an MFA device for another IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. To deactivate the MFA device for a user, choose the name of the user whose MFA you want to remove\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose **Manage**\.

1. In the **Manage MFA device** wizard, choose **Deactivate MFA device**, and then choose **Continue**\.

   The device is removed from AWS\. It cannot be used to sign in or authenticate requests until it is reactivated and associated with an AWS user or AWS account root user\.<a name="deactivate-mfa-for-root"></a>

**To deactivate the MFA device for your AWS account root user \(console\)**

1. Use your AWS account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the AWS account root user\.
**Note**  
If you see three text boxes, then you previously signed in to the console with *[IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* credentials\. Your browser might remember this preference and open this account\-specific sign\-in page every time that you try to sign in\. You cannot use the IAM user sign\-in page to sign in as the account owner\. If you see the [IAM user sign\-in page](https://docs.aws.amazon.com/IAM/latest/UserGuide/console.html#user-sign-in-page), choose **Sign in using root user email** near the bottom of the page\. This returns you to the main sign\-in page\. From there, you can sign in as the root user using your AWS account email address and password\.

1. On the right side of the navigation bar, choose on your account name, and then choose **My Security Credentials**\. If necessary, choose **Continue to Security Credentials**\.  
![\[Security Credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Expand the **Multi\-factor authentication \(MFA\)** section\.

1. In the row for the MFA device that you want to deactivate, choose **Deactivate**\.

The MFA device is deactivated for the AWS account\.

## Deactivating MFA Devices \(AWS CLI\)<a name="deactivate-mfa-cli"></a>

**To deactivate an MFA device for an IAM user \(AWS CLI\)**
+ Run this command: [https://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html](https://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html)

## Deactivating MFA Devices \(AWS API\)<a name="deactivate-mfa-api"></a>

**To deactivate an MFA device for an IAM user \(AWS API\)**
+ Call this operation: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeactivateMFADevice.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeactivateMFADevice.html)