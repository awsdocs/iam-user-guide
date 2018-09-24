# Resynchronizing Virtual and Hardware MFA Devices<a name="id_credentials_mfa_sync"></a>

As an AWS administrator, you can resynchronize your IAM users' virtual and hardware MFA devices if they get out of synchronization\. If a user's device is not synchronized when they try to use it, the user's sign\-in attempt fails and IAM prompts the user to resynchronize the device\.

**Note**  
U2F security keys do not go out of sync\. If a U2F security key is lost or broken, you can deactivate it\. For instructions on deactivating any MFA device type, see [To deactivate an MFA device for an IAM user \(console\)](id_credentials_mfa_disable.md#deactivate-mfa-for-user)\.

If your AWS account root user MFA device is not working, you can resynchronize your device using the IAM console with or without completing the sign\-in process\. 

**Topics**
+ [Resynchronizing Virtual and HardwareMFA Devices \(IAM Console\)](#id_credentials_mfa_sync_console)
+ [Resynchronizing Virtual and Hardware MFA Devices \(AWS CLI\)](#id_credentials_mfa_sync_cli)
+ [Resynchronizing Virtual and Hardware MFA Devices \(AWS API\)](#id_credentials_mfa_sync_api)

## Resynchronizing Virtual and HardwareMFA Devices \(IAM Console\)<a name="id_credentials_mfa_sync_console"></a>

You can use the IAM console to resynchronize virtual and hardware MFA devices\.

**To resynchronize a virtual or hardware MFA device for an IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**, and then choose the name of the user whose MFA device needs to be resynchronized\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose **Manage**\.

1. In the **Manage MFA Device** wizard, choose **Resync**, and then choose **Continue**\.

1. Type the next two sequentially generated codes from the device into **MFA Code 1** and **MFA Code 2**\. Then choose **Continue**\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the request appears to work but the device remains out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\.

**To resynchronize your root user MFA before signing in \(console\)**

1. On the **Amazon Web Services Sign In With Authentication Device** page, choose **Having problems with your authentication device? Click here**\.
**Note**  
If you are using an AWS account created after September 14, 2017, on the **Sign in usingMFA** page, choose **Troubleshoot your authentication device**\.

1. In the **Re\-Sync With Our Servers** section, type the next two sequentially generated codes from the device into **MFA Code 1** and **MFA Code 2**\. Then choose **Re\-sync authentication device**\.

1. If necessary, type your password again and choose **Sign in**\. Then complete the sign\-in using your MFA device\.

**To resynchronize your root user MFA device after signing in \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. On the right side of the navigation bar, choose your account name, and choose **Security Credentials**\. If necessary, choose **Continue to Security Credentials**\.

1. Expand the **Multi\-Factor Authentication \(MFA\)** section on the page\.

1. Next to your active MFA device, choose **Resync**\.

1. In the **Manage MFA Device** dialog box, type the next two sequentially generated codes from the device into **MFA Code 1** and **MFA Code 2**\. Then choose **Continue**\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the MFA device is successfully associated with the user, but the MFA device is out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\.

## Resynchronizing Virtual and Hardware MFA Devices \(AWS CLI\)<a name="id_credentials_mfa_sync_cli"></a>

You can resynchronize virtual and hardware MFA devices from the AWS CLI\.

**To resynchronize a virtual or hardware MFA device for an IAM user \(AWS CLI\)**  
At a command prompt, issue the [https://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html](https://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html) command:
+ Virtual MFA device: Specify Amazon Resource Name \(ARN\) of device as `SerialNumber`\.

  ```
  $ aws iam resync-mfa-device --user-name Richard --serial-number arn:aws:iam::123456789012:mfa/RichardsMFA --authentication-code-1 123456 --authentication-code-2 987654
  ```
+ Hardware MFA device: Specify hardware device's serial number as `SerialNumber`\. The format is vendor specific\.

  ```
  PS C:\>Sync-IAMMFADevice -SerialNumber ABCD12345678 -AuthenticationCode1 123456 -AuthenticationCode2 987654 -UserName Richard
  ```

**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the request fails because the codes expire after a short time\.

## Resynchronizing Virtual and Hardware MFA Devices \(AWS API\)<a name="id_credentials_mfa_sync_api"></a>

IAM has an API call that performs synchronization\. In this case, we recommend that you give your virtual and hardware MFA device users permission to access this API call\. Then build a tool based on that API call so your users can resynchronize their devices whenever they need to\.

**To resynchronize a virtual or hardware MFA device for an IAM user \(AWS API\)**
+ Send the [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html) request\.