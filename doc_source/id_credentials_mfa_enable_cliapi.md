# Enabling and managing virtual MFA devices \(AWS CLI or AWS API\)<a name="id_credentials_mfa_enable_cliapi"></a>

You can use AWS CLI commands or AWS API operations to enable a virtual MFA device for an IAM user\. You cannot enable an MFA device for the AWS account root user with the AWS CLI, AWS API, Tools for Windows PowerShell, or any other command line tool\. However, you can use the AWS Management Console to enable an MFA device for the root user\. 

When you enable an MFA device from the AWS Management Console, the console performs multiple steps for you\. If you instead create a virtual device using the AWS CLI, Tools for Windows PowerShell, or AWS API, then you must perform the steps manually and in the correct order\. For example, to create a virtual MFA device, you must create the IAM object and extract the code as either a string or a QR code graphic\. Then you must sync the device and associate it with an IAM user\. See the **Examples** section of [New\-IAMVirtualMFADevice](https://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMVirtualMFADevice.html&tocid=New-IAMVirtualMFADevice) for more details\. For a physical device, you skip the creation step and go directly to syncing the device and associating it with the user\. 

**To create the virtual device entity in IAM to represent a virtual MFA device**  
These commands provide an ARN for the device that is used in place of a serial number in many of the following commands\.
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/create-virtual-mfa-device.html](https://docs.aws.amazon.com/cli/latest/reference/iam/create-virtual-mfa-device.html) 
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateVirtualMFADevice.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateVirtualMFADevice.html) 

**To enable an MFA device for use with AWS**  
These commands synchronize the device with AWS and associate it with a user or the root user\. If the device is virtual, use the ARN of the virtual device as the serial number\.

**Important**  
Submit your request immediately after generating the authentication codes\. If you generate the codes and then wait too long to submit the request, the MFA device successfully associates with the user but the MFA device becomes out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\. If this happens, you can resynchronize the device using the commands described below\.
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/enable-mfa-device.html](https://docs.aws.amazon.com/cli/latest/reference/iam/enable-mfa-device.html) 
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_EnableMFADevice.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_EnableMFADevice.html) 

**To deactivate a device**  
Use these commands to disassociate the device from the user and deactivate it\. If the device is virtual, use the ARN of the virtual device as the serial number\. You must also separately delete the virtual device entity\. 
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html](https://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html) 
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeactivateMFADevice.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeactivateMFADevice.html)

**To list virtual MFA device entities**  
Use these commands to list virtual MFA device entities\.
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/list-virtual-mfa-devices.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-virtual-mfa-devices.html) 
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListVirtualMFADevices.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListVirtualMFADevices.html) 

**To resynchronize an MFA device**  
Use these commands if the device is generating codes that are not accepted by AWS\. If the device is virtual, use the ARN of the virtual device as the serial number\.
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html](https://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html) 
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html) 

**To delete a virtual MFA device entity in IAM**  
After the device is disassociated from the user, you can delete the device entity\.
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/delete-virtual-mfa-device.html](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-virtual-mfa-device.html) 
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteVirtualMFADevice.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteVirtualMFADevice.html) 

**To recover a virtual MFA device that is lost or not working**  
Sometimes, an IAM user's device that hosts the virtual MFA app is lost, replaced, or not working\. When this happens, the user can't recover it on their own\. IAM users must contact an administrator to deactivate the device\. For more information, see [What if an MFA device is lost or stops working?](id_credentials_mfa_lost-or-broken.md)\.