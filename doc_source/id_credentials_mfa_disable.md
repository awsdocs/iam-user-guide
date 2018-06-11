# Deactivating MFA Devices<a name="id_credentials_mfa_disable"></a>

If an IAM user in your account is having trouble signing in with a multi\-factor authentication \(MFA\) device, you can deactivate the device\. This allows the user to sign in without using MFA\. You might do this as a temporary solution while the MFA device is replaced, or if the device is temporarily unavailable\. However, we recommend that you enable a new device for the user as soon as possible\. To learn how to enable a new MFA device, see [Enabling MFA Devices](id_credentials_mfa_enable.md)\.

**Note**  
If you use the API or AWS CLI to delete a user from your AWS account, you must deactivate or delete the user's MFA device\. You make this change as part of the process of removing the user\. For more information about deleting users, see [Managing IAM Users](id_users_manage.md)\.

**Topics**
+ [Deactivating MFA Devices \(Console\)](#deactive-mfa-console)
+ [Deactivating MFA Devices \(AWS CLI\)](#deactivate-mfa-cli)
+ [Deactivating MFA Devices \(AWS API\)](#deactivate-mfa-api)

## Deactivating MFA Devices \(Console\)<a name="deactive-mfa-console"></a><a name="deactivate-mfa-for-user"></a>

**To deactivate an MFA device for an IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. To deactivate the MFA device for a user, choose the name of the user whose MFA you want to remove\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose the pencil icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/pencil_edit_icon.png)\)\.

1. In the **Manage MFA Device** wizard, choose **Deactivate MFA device**, and then choose **Next Step**\.

   The device is removed from AWS\. It cannot be used to sign in or authenticate requests until it is reactivated and associated with an AWS user or AWS account root user\.<a name="deactivate-mfa-for-root"></a>

**To deactivate the MFA device for your AWS account root user \(console\)**

1. Use your AWS account root user credentials to sign in to the [AWS Management Console](https://console.aws.amazon.com//iam/home)\.
**Important**  
To manage MFA devices for the AWS account, you must sign in to AWS with your AWS account root user credentials\. You cannot manage MFA devices for the root user with other credentials\.

1. On the navigation bar, choose your account name, and then choose **My Security Credentials**\. If a prompt appears, choose **Continue to Security Credentials**\.  
![\[Security Credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Expand the **Multi\-Factor Authentication \(MFA\)** section\.

1. In the row for the MFA device that you want to deactivate, choose **Deactivate**\.

The MFA device is deactivated for the AWS account\.

## Deactivating MFA Devices \(AWS CLI\)<a name="deactivate-mfa-cli"></a>

**To deactivate an MFA device for an IAM user \(AWS CLI\)**
+ Run this command: [http://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html](http://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html)

## Deactivating MFA Devices \(AWS API\)<a name="deactivate-mfa-api"></a>

**To deactivate an MFA device for an IAM user \(AWS API\)**
+ Call this operation: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeactivateMFADevice.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeactivateMFADevice.html)