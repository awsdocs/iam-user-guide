# Enabling a Virtual Multi\-factor Authentication \(MFA\) Device<a name="id_credentials_mfa_enable_virtual"></a>

A virtual MFA device uses a software application to generate a six\-digit authentication code that is compatible with the time\-based one\-time password \(TOTP\) standard, as described in [RFC 6238](http://tools.ietf.org/html/rfc6238)\. The app can run on mobile hardware devices, including smartphones\. With most virtual MFA apps, you can host more than one virtual MFA device, which makes them more convenient than hardware MFA devices\. However, be aware that a virtual MFA might be run on a less secure device such as a smartphone\. Consequently, a virtual MFA might not provide the same level of security as a hardware MFA device\. 

You can enable only one MFA device per AWS account root user or IAM user, and the device can only be used by the specified user\. Keep in mind that although some virtual MFA software apps appear to support multiple accounts, each account you add represents a single virtual MFA device\. In addition, that one virtual device can still associate with only one user\.

For a list of virtual MFA apps that you can use on smartphones and tablets \(including Google Android, Apple iPhone and iPad, and Windows Phone\), go to the **Virtual MFA Applications** section at [http://aws.amazon.com/iam/details/mfa/](http://aws.amazon.com/iam/details/mfa/)\. Note that AWS requires a virtual MFA app that produces a six\-digit OTP\.

Use the following steps to enable and manage MFA devices from the AWS Management Console\. To enable and manage MFA devices at the command line, or to use the API, see [Enable and manage virtual MFA devices \(AWS CLI, Tools for Windows PowerShell, or AWS API\)](id_credentials_mfa_enable_cliapi.md)\.

**Important**  
We recommend that when you configure a virtual MFA device to use with AWS that you save a copy of the QR code or the secret key ***in a secure place***\. That way, if you lose the phone or have to reinstall the MFA software app for any reason, you can reconfigure the app to use the same virtual MFA\. This avoids the need to create a new virtual MFA in AWS for the user or root user\.

## Enable a Virtual MFA Device for an IAM User \(AWS Management Console\)<a name="enable-virt-mfa-for-iam-user"></a>

You can use IAM in the AWS Management Console to enable a virtual MFA device for an IAM user in your account\. 

**Note**  
You must have physical access to the hardware that will host the user's virtual MFA device in order to configure MFA\. For example, you might configure MFA for a user who will use a virtual MFA device running on a smartphone\. In that case, you must have the smartphone available in order to finish the wizard\. Because of this, you might want to let users configure and manage their own virtual MFA devices\. In that case you must grant users the permissions to perform the necessary IAM actions\. For more information and for an example of an IAM policy that grants these permissions, see [Allow Users to Manage Only Their Own Virtual MFA Devices](id_credentials_delegate-permissions_examples.md#creds-policies-mfa-console)\. 

**To enable a virtual MFA device for a user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. In the **User Name** list, choose the name of the intended MFA user\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose the edit icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/pencil_edit_icon.png)\)\.

1. In the **Manage MFA Device** wizard, choose **A virtual MFA device**, and then choose **Next Step**\.

   IAM generates and displays configuration information for the virtual MFA device, including a QR code graphic\. The graphic is a representation of the 'secret configuration key' that is available for manual entry on devices that do not support QR codes\.

1. Open your virtual MFA app\. \(For a list of apps that you can use for hosting virtual MFA devices, see [Virtual MFA Applications](https://aws.amazon.com/iam/details/mfa/#Virtual_MFA_Applications)\.\) If the virtual MFA app supports multiple accounts \(multiple virtual MFA devices\), choose the option to create a new account \(a new virtual MFA device\)\.

1. Determine whether the MFA app supports QR codes, and then do one of the following:
   + Use the app to scan the QR code\. For example, you might choose the camera icon or choose an option similar to **Scan code**, and then use the device's camera to scan the code\.
   + In the **Manage MFA Device** wizard, choose **Show secret key for manual configuration**, and then type the secret configuration key into your MFA app\.

   When you are finished, the virtual MFA device starts generating one\-time passwords\. 

1. In the **Manage MFA Device** wizard, in the **Authentication Code 1** box, type the one\-time password that currently appears in the virtual MFA device\. Wait up to 30 seconds for the device to generate a new one\-time password\. Then type the second one\-time password into the **Authentication Code 2** box\. Choose **Active Virtual MFA**\. 
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the MFA device successfully associates with the user but the MFA device is out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\. If this happens, you can [resync the device](id_credentials_mfa_sync.md)\.

The virtual MFA device is now ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA Devices With Your IAM Sign\-in Page](console_sign-in-mfa.md)\.

## Enable a Virtual MFA Device for Your AWS Account Root User \(Console\)<a name="enable-virt-mfa-for-root"></a>

You can use IAM in the AWS Management Console to configure and enable a virtual MFA device for your root user\. To enable MFA devices for the AWS account, you must be signed in to AWS using your root user credentials\. You cannot enable an MFA device for the AWS account root user with the AWS CLI, AWS API, Tools for Windows PowerShell, or any other command\-line tool\.

If your MFA device is lost, stolen, or not working, you can still sign in using alternative factors of authentication\. To do this, you must verify your identity using the email and phone that are registered with your account\. This means that if you can't sign in with your MFA device, you can sign in by verifying your identity using the email and phone that are registered with your account\. Before you enable MFA for your root user, review your account settings and contact information to make sure that you have access to the email and phone number\. To learn about signing in using alternative factors of authentication, see [What If an MFA Device Is Lost or Stops Working?](id_credentials_mfa_lost-or-broken.md)\. To disable this feature, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.

**Note**  
If you are using an AWS account created after September 14, 2017, you might see differences in the following console pages: **Sign in with authentication device** and **Troubleshoot your authentication device**\. However, the same features are provided\. In either case, if you cannot verify your account email address and phone number using alternative factors of authentication, contact [AWS Support](https://aws.amazon.com/forms/aws-mfa-support) to deactivate your MFA setting\.

**To configure and enable a virtual MFA device for use with your root user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Do one of the following:
   + **Option 1**: Choose **Dashboard**, and under **Security Status**, expand **Activate MFA on your root user**\. 
   + **Option 2**: On the right side of the navigation bar, choose your account name, and choose **My Security Credentials**\. If necessary, choose **Continue to Security Credentials**\. Then expand the **Multi\-Factor Authentication \(MFA\)** section on the page\.  
![\[My Security Credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Choose **Manage MFA** or **Activate MFA**, depending on which option you chose in the preceding step\.

1. In the wizard, choose **A virtual MFA device** and then choose **Next Step**\.

1. Confirm that a virtual MFA app is installed on the device, and then choose **Next Step**\. IAM generates and displays configuration information for the virtual MFA device, including a QR code graphic\. The graphic is a representation of the secret configuration key that is available for manual entry on devices that do not support QR codes\.

1. With the **Manage MFA Device** wizard still open, open the virtual MFA app on the device\. 

1. If the virtual MFA software supports multiple accounts \(multiple virtual MFA devices\), then choose the option to create a new account \(a new virtual device\)\.

1. The easiest way to configure the app is to use the app to scan the QR code\. If you cannot scan the code, you can type the configuration information manually\.
   + To use the QR code to configure the virtual MFA device, follow the app instructions for scanning the code\. For example, you might need to tap the camera icon or tap a command like **Scan account barcode**, and then use the device's camera to scan the QR code\.
   + If you cannot scan the code, type the configuration information manually by typing the **Secret Configuration Key** value into the app\. For example, to do this in the AWS Virtual MFA app, choose **Manually add account**, and then type the secret configuration key and choose **Create**\.
**Important**  
Make a secure backup of the QR code or secret configuration key, or make sure that you enable multiple virtual MFA devices for your account\. A virtual MFA device might become unavailable, for example, if you lose the smartphone where the virtual MFA device is hosted\)\. If that happens, you will not be able to sign in to your account and you will have to contact customer service to remove MFA protection for the account\. 
**Note**  
The QR code and secret configuration key generated by IAM are tied to your AWS account and cannot be used with a different account\. They can, however, be reused to configure a new MFA device for your account in case you lose access to the original MFA device\.

   The device starts generating six\-digit numbers\. 

1. In the **Manage MFA Device** wizard, in the **Authentication Code 1** box, type the six\-digit number that's currently displayed by the MFA device\. Wait up to 30 seconds for the device to generate a new number, and then type the new six\-digit number into the **Authentication Code 2** box\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the MFA device successfully associates with the user but the MFA device is out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\. If this happens, you can [resync the device](id_credentials_mfa_sync.md)\.

1. Choose **Next Step**, and then choose **Finish**\.

The device is ready for use with AWS\. For information about using MFA with the AWS Management Console, see [Using MFA Devices With Your IAM Sign\-in Page](console_sign-in-mfa.md)\.

## Replace or "Rotate" a Virtual MFA Device<a name="replace-virt-mfa"></a>

You can have only one virtual MFA device assigned to a user at a time\. If the user loses a device or needs to replace it for any reason, you must first deactivate the old device\. Then you can add the new device for the user\.
+ To deactivate the device currently associated with a user, see [Deactivating MFA Devices](id_credentials_mfa_disable.md)\.
+ To add a replacement virtual MFA device for an IAM user, follow the steps in the procedure [Enable a Virtual MFA Device for an IAM User \(AWS Management Console\)](#enable-virt-mfa-for-iam-user) above\.
+ To add a replacement virtual MFA device for the AWS account root user, follow the steps in the procedure [Enable a Virtual MFA Device for Your AWS Account Root User \(Console\)](#enable-virt-mfa-for-root) earlier in this topic\.