# PREVIEW – Enabling SMS text message MFA devices<a name="id_credentials_mfa_enable_sms"></a>

AWS will soon end support for SMS multi\-factor authentication \(MFA\)\. We are not allowing new customers to preview this feature\. We recommend that existing customers switch to one of the following alternative methods of MFA:
+ [A virtual \(software\-based\)](id_credentials_mfa_enable_virtual.md) MFA device
+ [A U2F security key](id_credentials_mfa_enable_u2f.md)
+ [A hardware\-based](id_credentials_mfa_enable_physical.md) MFA device

**Tip**  
You can view users in your account with an assigned SMS MFA device\. In the IAM console, choose **Users** from the navigation pane, and look for users with **SMS** in the **MFA** column of the table\.

An SMS \(short message service\) MFA device can be any mobile device with a phone number that can receive standard [SMS text messages](http://wikipedia.org/wiki/Short_Message_Service)\. When an MFA code is needed, AWS sends it to the phone number that is configured for the IAM user\. 

**Note**  
SMS MFA can be used only with IAM users\. It cannot be used with the AWS account root user\. To protect the root user with MFA, you must use a virtual MFA device, U2F security key, or hardware MFA device\.

## Enable an SMS MFA device for an IAM user \(console\)<a name="enable-sms-mfa-console"></a>

You can use IAM in the AWS Management Console to configure an IAM user with a phone number to enable SMS MFA\.

**Note**  
Currently, you can manage SMS MFA only in the AWS Management Console\.

**To enable SMS MFA for an IAM user \(console\)**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

1. In the navigation pane, choose **Users**\.

1. In the **User Name** list, choose the name \(not the check box\) of the intended MFA user\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose **Manage**\.

1. In the **Manage MFA Device** wizard, choose **An SMS MFA device**, and then choose **Continue**\.

1. Type the phone number to which you want to send MFA codes for this IAM user, and then choose **Continue**\.

1. A six\-digit authentication code is immediately sent to the specified phone number for verification\. Type the six\-digit code and then choose **Continue**\. If the code does not arrive in a reasonable amount of time\), choose **Resend Code**\. Note that SMS is not a service with a guaranteed delivery time\.

1. If AWS successfully verifies the code, the wizard ends\. Otherwise, choose **Finish** to close the wizard\.

## Change the phone number for SMS MFA for an IAM user<a name="change-sms-mfa-phone-number"></a>

To change the phone number of the SMS MFA device assigned to an IAM user, you must delete the current MFA device\. Then create a new device with the new phone number\. To learn how to delete a device, see [Deactivating MFA devices](id_credentials_mfa_disable.md)\. 