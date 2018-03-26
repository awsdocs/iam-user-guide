# Resynchronize MFA Devices<a name="id_credentials_mfa_sync"></a>

As an AWS administrator, you can recynchronize your IAM user MFA devices if they get out of synchronization\. If a user's device is not synchronized when they try to use it, the user's sign\-in attempt fails and IAM prompts the user to resynchronize the device\.

If your AWS account root user MFA device is not working, you can resynchronize your device using the IAM console with or without completing the sign\-in process\. 

## Resynchronize an MFA Device \(IAM Console\)<a name="id_credentials_mfa_sync_console"></a>

**To resynchronize an MFA device for an IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**, and then choose the name of the user whose MFA device needs to be resynchronized\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose the pencil icon \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/pencil_edit_icon.png)\)\.

1. In the **Manage MFA Device** wizard, choose **Resynchronize MFA device**, and then choose **Next Step**\.

1. Type the next two sequentially generated codes from the device into **Authentication Code 1** and **Authentication Code 2**\. Then choose **Next Step**\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the request appears to work but the device remains out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\.

**To resynchronize your root user MFA before signing in \(console\)**

1. On the **Amazon Web Services Sign In With Authentication Device** page, choose **Having problems with your authentication device? Click here**\.
**Note**  
If you are using an AWS account created after September 14, 2017, on the **Sign in with authentication device** page, choose **Troubleshoot your authentication device**\.

1. In the **Re\-Sync With Our Servers** section, type the next two sequentially generated codes from the device into **Authentication Code 1** and **Authentication Code 2**\. Then choose **Re\-sync authentication device**\.

1. If required, type your password again and choose **Sign in**\. Then complete the sign\-in using your MFA device\.

**To resynchronize your root user MFA device after signing in \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. On the right side of the navigation bar, choose your account name, and choose **Security Credentials**\. If necessary, choose **Continue to Security Credentials**\.

1. Expand the **Multi\-Factor Authentication \(MFA\)** section on the page\.

1. Next to your active MFA device, choose **Re\-sync**\.

1. In the **Manage MFA Device** dialog, type the next two sequentially generated codes from the device into **Authentication Code 1** and **Authentication Code 2**\. Then choose **Next Step**\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the MFA device successfully associates with the user but the MFA device is out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\.

## Resynchronize an MFA Device \(AWS CLI\)<a name="id_credentials_mfa_sync_cli"></a>

**To resynchronize an MFA device for an IAM user \(AWS CLI\)**
+ At a command prompt, issue the [http://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html](http://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html) command:
  + Virtual MFA device: specify Amazon Resource Name \(ARN\) of device as `SerialNumber`\.

    ```
    $ aws iam resync-mfa-device --user-name Bob --serial-number arn:aws:iam::123456789012:mfa/BobsMFA --authentication-code-1 123456 --authentication-code-2 987654
    ```
  + Physical MFA device: specify physical device's serial number as `SerialNumber`\. The format is vendor specific\.

    ```
    PS C:\>Sync-IAMMFADevice -SerialNumber ABCD12345678 -AuthenticationCode1 123456 -AuthenticationCode2 987654 -UserName Bob
    ```
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the request fails because the codes expire after a short time\.

## Tools for Windows PowerShell<a name="id_credentials_mfa_sync_twp"></a>

**To resynchronize an MFA device for an IAM user \(Tools for Windows PowerShell\)**
+ Use the [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Sync-IAMMFADevice.html&tocid=Sync-IAMMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Sync-IAMMFADevice.html&tocid=Sync-IAMMFADevice) cmdlet:
  + Virtual MFA device: specify Amazon Resource Name \(ARN\) of device as `SerialNumber`\.

    ```
    PS C:\>Sync-IAMMFADevice -UserName Bob -SerialNumber arn:aws:iam::123456789012:mfa/BobsMFA -AuthenticationCode1 123456 -AuthenticationCode2 987654 
    ```
  + Physical MFA device: specify physical device's serial number as `SerialNumber`\. The format is vendor specific\.

    ```
    PS C:\>Sync-IAMMFADevice -UserName Bob -SerialNumber ABCD12345678 -AuthenticationCode1 123456 -AuthenticationCode2 987654 
    ```
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the request appears to work but the device remains out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\.

## IAM API<a name="id_credentials_mfa_sync_api"></a>

IAM has an API call that performs synchronization\. In this case, we recommend that you give your MFA users permission to access this API call\. You should build a tool based on that API call that lets your users resynchronize their devices whenever they need to\.

**To resynchronize an MFA device for an IAM user \(API\)**
+ Send the [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html) request\.