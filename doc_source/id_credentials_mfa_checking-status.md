# Checking MFA Status<a name="id_credentials_mfa_checking-status"></a>

Use the IAM console to check whether an AWS account root user or IAM user has a valid MFA device enabled\.

**To check the MFA status of a root user**

1. Sign in to the AWS Management Console with your root user credentials and then open the IAM console at [https://console.aws.amazon.com/iam/](https://console.aws.amazon.com/iam/)\. 

1. Check under **Security Status** to see whether MFA is enabled or disabled\. If MFA has not been activated, an alert symbol \(![\[Alert icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png)\) is displayed next to **Activate MFA on your root user**\. 

If you want to enable MFA for the account, see [Enable a Virtual MFA Device for Your AWS Account Root User \(Console\)](id_credentials_mfa_enable_virtual.md#enable-virt-mfa-for-root) or [Enable a Hardware MFA Device for the AWS Account Root User \(Console\)](id_credentials_mfa_enable_physical.md#enable-hw-mfa-for-root)\.

**To check the MFA status of IAM users**

1. Open the IAM console at [https://console.aws.amazon.com/iam/](https://console.aws.amazon.com/iam/)\. 

1. In the navigation pane, choose **Users**\.

1. If necessary, add the **MFA** column to the users table by completing the following steps:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage Columns**, select **MFA**\.

   1. \(Optional\) Clear the check box for any column headings that you do not want to appear in the users table\.

   1. Choose **Close** to return to the list of users\.

1. The **MFA** column tells you about the MFA device that is enabled\. If no MFA device is active for the user, the console displays **Not enabled**\. If the user has an MFA device enabled, the **MFA** column shows the type of device that is enabled with a value of **Hardware**, **SMS**, or **Virtual**\.

1. To view additional information about the MFA device for a user, choose the name of the user whose MFA status you want to check\. Then choose the **Security credentials** tab\. 

1. If no MFA device is active for the user, the console displays **No** next to **Assigned MFA device**\. If the user has an MFA device enabled, the **Assigned MFA device** item shows a value for the device:
   + The device serial number of a hardware device \(usually the number from the back of the device\), such as `GAHT12345678`
   + The ARN in AWS for an SMS device, such as `arn:aws:iam::123456789012:sms-mfa/username`
   + The ARN in AWS for a virtual device, such as `arn:aws:iam::123456789012:mfa/username`

If you want to change the current setting, choose the edit icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/pencil_edit_icon.png)\) next to **Assigned MFA Device**\. For hardware device information, see [Enabling a Hardware MFA Device \(Console\)](id_credentials_mfa_enable_physical.md)\. For SMS device information, see [PREVIEW – Enabling SMS Text Message MFA Devices](id_credentials_mfa_enable_sms.md)\. For virtual device information, see [Enabling a Virtual Multi\-factor Authentication \(MFA\) Device](id_credentials_mfa_enable_virtual.md)\.