# Enable and manage virtual MFA devices \(AWS CLI, Tools for Windows PowerShell, or AWS API\)<a name="id_credentials_mfa_enable_cliapi"></a>

You can use AWS CLI commands or AWS API operations to enable a virtual MFA device for an IAM user\. You cannot enable an MFA device for the AWS account root user with the AWS CLI, AWS API, Tools for Windows PowerShell, or any other command\-line tool\. However, you can use the AWS Management Console to enable an MFA device for the root user\. 

When you enable an MFA device from the AWS Management Console, the console performs multiple steps for you\. If you instead create a virtual device using the AWS CLI, Tools for Windows PowerShell, or AWS API, then you must perform the steps manually and in the correct order\. For example, to create a virtual MFA device, you must create the IAM object, extract the code as either a string or a QR code graphic, and then sync the device and associate it with an IAM user\. See the **Examples** section of [New\-IAMVirtualMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMVirtualMFADevice.html&tocid=New-IAMVirtualMFADevice) for more details\. For a physical device, you skip the creation step and go directly to syncing the device and associating it with the user\. 

**To create the virtual device entity in IAM to represent a virtual MFA device**  
These commands provide an ARN for the device that is used in place of a serial number in many of the following commands\.
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/create-virtual-mfa-device.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-virtual-mfa-device.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMVirtualMFADevice.html&tocid=New-IAMVirtualMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMVirtualMFADevice.html&tocid=New-IAMVirtualMFADevice)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateVirtualMFADevice.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateVirtualMFADevice.html) 

**To enable an MFA device for use with AWS**  
These commands synchronize the device with AWS and associates it with a user or the root user\. If the device is virtual, use the ARN of the virtual device as the serial number\.

**Important**  
Submit your request immediately after generating the authentication codes\. If you generate the codes and then wait too long to submit the request, the MFA device successfully associates with the user but the MFA device becomes out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\. If this happens, you can resynchronize the device using the commands described below\.
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/enable-mfa-device.html](http://docs.aws.amazon.com/cli/latest/reference/iam/enable-mfa-device.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Enable-IAMMFADevice.html&tocid=Enable-IAMMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Enable-IAMMFADevice.html&tocid=Enable-IAMMFADevice) 
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_EnableMFADevice.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_EnableMFADevice.html) 

**To deactivate a device**  
These commands disassociate the device from the user and deactivates it\. If the device is virtual, use the ARN of the virtual device as the serial number\. You must also separately delete the virtual device entity\. 
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html](http://docs.aws.amazon.com/cli/latest/reference/iam/deactivate-mfa-device.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Disable-IAMMFADevice.html&tocid=Disable-IAMMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Disable-IAMMFADevice.html&tocid=Disable-IAMMFADevice) 
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeactivateMFADevice.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeactivateMFADevice.html)

**To list virtual MFA device entities**
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/list-virtual-mfa-devices.html](http://docs.aws.amazon.com/cli/latest/reference/iam/list-virtual-mfa-devices.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMVirtualMFADevice.html&tocid=Get-IAMVirtualMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMVirtualMFADevice.html&tocid=Get-IAMVirtualMFADevice) 
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListVirtualMFADevices.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListVirtualMFADevices.html) 

**To resynchronize an MFA device**  
Use these commands if the device is generating codes that are not accepted by AWS\. If the device is virtual, use the ARN of the virtual device as the serial number\.
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html](http://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Sync-IAMMFADevice.html&tocid=Sync-IAMMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Sync-IAMMFADevice.html&tocid=Sync-IAMMFADevice) 
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html) 

**To delete a virtual MFA device entity in IAM**  
After the device is disassociated from the user, you can delete the device entity\.
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/delete-virtual-mfa-device.html](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-virtual-mfa-device.html) 
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMVirtualMFADevice.html&tocid=Remove-IAMVirtualMFADevice](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMVirtualMFADevice.html&tocid=Remove-IAMVirtualMFADevice) 
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteVirtualMFADevice.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteVirtualMFADevice.html) 