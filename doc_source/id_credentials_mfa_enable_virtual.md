# Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)<a name="id_credentials_mfa_enable_virtual"></a>

You can use a phone or other device as a virtual multi\-factor authentication \(MFA\) device\. To do this, install a mobile app that is compliant with [RFC 6238, a standards\-based TOTP \(time\-based one\-time password\) algorithm](https://tools.ietf.org/html/rfc6238)\. These apps generates a six\-digit authentication code\. Because they can run on unsecured mobile devices, virtual MFA might not provide the same level of security as U2F devices or hardware MFA devices\. We do recommend that you use a virtual MFA device while waiting for hardware purchase approval or while you wait for your hardware to arrive\. 

Most virtual MFA apps support creating multiple virtual devices, allowing you to use the same app for multiple AWS accounts or users\. However, you can enable only one MFA device per user\.

For a list of virtual MFA apps that you can use, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\. Note that AWS requires a virtual MFA app that produces a six\-digit OTP\.

**Topics**
+ [Permissions required](#mfa_enable_virtual_permissions-required)
+ [Enable a virtual MFA device for an IAM user \(console\)](#enable-virt-mfa-for-iam-user)
+ [Enable a virtual MFA device for your AWS account root user \(console\)](#enable-virt-mfa-for-root)
+ [Replace or "rotate" a virtual MFA device](#replace-virt-mfa)

## Permissions required<a name="mfa_enable_virtual_permissions-required"></a>

To manage virtual MFA devices for your IAM user, you must have the permissions from the following policy: [AWS: Allows MFA\-authenticated IAM users to manage their own MFA device on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage-mfa-only.md)\.

## Enable a virtual MFA device for an IAM user \(console\)<a name="enable-virt-mfa-for-iam-user"></a>

You can use IAM in the AWS Management Console to enable and manage a virtual MFA device for an IAM user in your account\. To enable and manage an MFA device using the AWS CLI or AWS API, see [Enabling and managing virtual MFA devices \(AWS CLI or AWS API\)](id_credentials_mfa_enable_cliapi.md)\.

**Note**  
You must have physical access to the hardware that will host the user's virtual MFA device in order to configure MFA\. For example, you might configure MFA for a user who will use a virtual MFA device running on a smartphone\. In that case, you must have the smartphone available in order to finish the wizard\. Because of this, you might want to let users configure and manage their own virtual MFA devices\. In that case, you must grant users the permissions to perform the necessary IAM actions\. For more information and for an example of an IAM policy that grants these permissions, see [AWS: Allows MFA\-authenticated IAM users to manage their own MFA device on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage-mfa-only.md)\. 

**To enable a virtual MFA device for an IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. In the **User Name** list, choose the name of the intended MFA user\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose **Manage**\.

1. In the **Manage MFA Device** wizard, choose **Virtual MFA device**, and then choose **Continue**\.

   IAM generates and displays configuration information for the virtual MFA device, including a QR code graphic\. The graphic is a representation of the "secret configuration key" that is available for manual entry on devices that do not support QR codes\.

1. Open your virtual MFA app\. For a list of apps that you can use for hosting virtual MFA devices, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\. 

   If the virtual MFA app supports multiple virtual MFA devices or accounts, choose the option to create a new virtual MFA device or account\.

1. Determine whether the MFA app supports QR codes, and then do one of the following:
   + From the wizard, choose **Show QR code**, and then use the app to scan the QR code\. For example, you might choose the camera icon or choose an option similar to **Scan code**, and then use the device's camera to scan the code\.
   + In the **Manage MFA Device** wizard, choose **Show secret key**, and then type the secret key into your MFA app\.

   When you are finished, the virtual MFA device starts generating one\-time passwords\. 

1. In the **Manage MFA Device** wizard, in the **MFA code 1** box, type the one\-time password that currently appears in the virtual MFA device\. Wait up to 30 seconds for the device to generate a new one\-time password\. Then type the second one\-time password into the **MFA code 2** box\. Choose **Assign MFA**\. 
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the MFA device successfully associates with the user but the MFA device is out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\. If this happens, you can [resync the device](id_credentials_mfa_sync.md)\.

The virtual MFA device is now ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\.

## Enable a virtual MFA device for your AWS account root user \(console\)<a name="enable-virt-mfa-for-root"></a>

You can use the AWS Management Console to configure and enable a virtual MFA device for your root user\. To enable MFA devices for the AWS account, you must be signed in to AWS using your root user credentials\. 

Before you enable MFA for your root user, review your account settings and contact information to make sure that you have access to the email and phone number\. If your MFA device is lost, stolen, or not working, you can still sign in as the root user by verifying your identity using that email and phone number\. To learn about signing in using these alternative factors of authentication, see [What if an MFA device is lost or stops working?](id_credentials_mfa_lost-or-broken.md)\. 

**To configure and enable a virtual MFA device for use with your root user \(console\)**

1. Sign in to the AWS Management Console\.

1. On the right side of the navigation bar, choose your account name, and choose **My Security Credentials**\. If necessary, choose **Continue to Security Credentials**\. Then expand the **Multi\-Factor Authentication \(MFA\)** section on the page\.  
![\[My Security Credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Choose **Activate MFA**\.

1. In the wizard, choose **Virtual MFA device**, and then choose **Continue**\.

   IAM generates and displays configuration information for the virtual MFA device, including a QR code graphic\. The graphic is a representation of the secret configuration key that is available for manual entry on devices that do not support QR codes\.

1. Open the virtual MFA app on the device\. 

   If the virtual MFA app supports multiple virtual MFA devices or accounts, choose the option to create a new virtual MFA device or account\.

1. The easiest way to configure the app is to use the app to scan the QR code\. If you cannot scan the code, you can type the configuration information manually\. The QR code and secret configuration key generated by IAM are tied to your AWS account and cannot be used with a different account\. They can, however, be reused to configure a new MFA device for your account in case you lose access to the original MFA device\.
   + To use the QR code to configure the virtual MFA device, from the wizard, choose **Show QR code**\. Then follow the app instructions for scanning the code\. For example, you might need to choose the camera icon or choose a command like **Scan account barcode**, and then use the device's camera to scan the QR code\.
   +  In the **Manage MFA Device** wizard, choose **Show secret key**, and then type the secret key into your MFA app\.
**Important**  
Make a secure backup of the QR code or secret configuration key, or make sure that you enable multiple virtual MFA devices for your account\. A virtual MFA device might become unavailable, for example, if you lose the smartphone where the virtual MFA device is hosted\)\. If that happens, you will not be able to sign in to your account and you will have to contact customer service to remove MFA protection for the account\. 

   The device starts generating six\-digit numbers\. 

1. In the **Manage MFA Device** wizard, in the **MFA Code 1** box, enter the six\-digit number that's currently displayed by the MFA device\. Wait up to 30 seconds for the device to generate a new number, and then type the new six\-digit number into the **MFA Code 2** box\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the MFA device successfully associates with the user but the MFA device is out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\. If this happens, you can [resync the device](id_credentials_mfa_sync.md)\.

1. Choose **Assign MFA**, and then choose **Finish**\.

The device is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\.

## Replace or "rotate" a virtual MFA device<a name="replace-virt-mfa"></a>

You can have only one MFA device assigned to a user at a time\. If the user loses a device or needs to replace it for any reason, you must first deactivate the old device\. Then you can add the new device for the user\.
+ To deactivate the device currently associated with another IAM user, see [Deactivating MFA devices](id_credentials_mfa_disable.md)\.
+ To add a replacement virtual MFA device for another IAM user, follow the steps in the procedure [Enable a virtual MFA device for an IAM user \(console\)](#enable-virt-mfa-for-iam-user) above\.
+ To add a replacement virtual MFA device for the AWS account root user, follow the steps in the procedure [Enable a virtual MFA device for your AWS account root user \(console\)](#enable-virt-mfa-for-root) earlier in this topic\.