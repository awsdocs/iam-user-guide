# PREVIEW – Enabling SMS Text Message MFA Devices<a name="id_credentials_mfa_enable_sms"></a>


|  | 
| --- |
|   AWS will stop supporting SMS MFA on February 1, 2019\. If your account is already participating in the SMS MFA Preview program, you can continue using this feature until then\. We encourage you to use MFA through either a [hardware\-based](id_credentials_mfa_enable_physical.md) or [virtual \(software\-based\)](id_credentials_mfa_enable_virtual.md) MFA device\.  Tip You can view users in your account with an assigned SMS MFA device\. To do so, go to the IAM console, choose **Users** from the navigation pane, and look for users with **SMS** in the **MFA** column of the table\.   | 

An SMS \(Short Message Service\) MFA device can be any mobile device with a phone number that can receive standard [SMS text messages](http://wikipedia.org/wiki/Short_Message_Service)\. When an MFA code is needed, AWS sends it to the phone number that is configured for the IAM user\. 

**Note**  
SMS MFA can be used only with IAM users\. It cannot be used with the AWS account root user\. To protect the root user with MFA, you must use either a [hardware\-based](id_credentials_mfa_enable_physical.md) or [virtual \(software\-based\)](id_credentials_mfa_enable_virtual.md) MFA token device\.

## Enable an SMS MFA Device for an IAM User \(AWS Management Console\)<a name="enable-sms-mfa-console"></a>

You can use IAM in the AWS Management Console to configure an IAM user with a phone number to enable SMS MFA\.

**Note**  
Currently, you can manage SMS MFA only in the AWS Management Console\.

**To enable SMS MFA for an IAM user \(console\)**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

1. In the navigation pane, choose **Users**\.

1. In the **User Name** list, choose the name \(not the check box\) of the intended MFA user\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose the pencil icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/pencil_edit_icon.png)\)\.

1. In the **Manage MFA Device** wizard, choose **An SMS MFA device**, and then choose **Next Step**\.

1. Type the phone number to which you want to send MFA codes for this IAM user, and then choose **Next Step**\.

1. A six\-digit authentication code is immediately sent to the specified phone number for verification\. Type the six\-digit code and then choose **Next Step**\. If the code does not arrive in a reasonable amount of time\), choose **Resend Code**\. Note that SMS is not a service with a guaranteed delivery time\.

1. If AWS successfully verifies the code, the wizard ends\. Otherwise, choose **Finish** to close the wizard\.

## Change the Phone Number for SMS MFA for an IAM User<a name="change-sms-mfa-phone-number"></a>

To change the phone number of the SMS MFA device assigned to an IAM user, you must delete the current MFA device\. Then create a new device with the new phone number\. To learn how to delete a device, see [Deactivating MFA Devices](id_credentials_mfa_disable.md)\. To create a new device, see the previous procedures in this topic\.