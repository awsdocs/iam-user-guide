# Enabling MFA Devices<a name="id_credentials_mfa_enable"></a>

The following overview procedure describes how to set up and use MFA and provides links to related information\.

1. *Get an MFA token device or an SMS \(Short Message Service\)\-compatible mobile device such as one of the following\.* You can enable only one MFA device per AWS account root user or IAM user, and the device can only be used by the specified user\.
   + A hardware\-based token device, such as one of the AWS supported hardware token devices discussed on the [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/) page\.
   + A virtual token device, which is a software application that is compliant with [RFC 6238, a standards\-based TOTP \(time\-based one\-time password\) algorithm](https://tools.ietf.org/html/rfc6238)\. You can install the application on a mobile device, such as a tablet or smartphone\. For a list of a few supported apps that you can use as virtual MFA devices, see the **Virtual MFA Applications** section of the [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/) page\.
   + A mobile phone that can receive standard SMS text messages\.
**Note**  
If you choose to use SMS\-based MFA, text messaging charges from your mobile device's carrier may apply\.   
SMS\-based MFA are only available for IAM users and cannot be used for the root user\.

1. *Enable the MFA device\.* You can enable an MFA device for an IAM user in the AWS Management Console, the AWS CLI, Tools for Windows PowerShell or the IAM API\. You can only use the AWS Management Console to enable an MFA device for the AWS account root user\. 

   For information about enabling each type of MFA device, see the following topics:
   + Hardware MFA device: [Enabling a Hardware MFA Device \(Console\)](id_credentials_mfa_enable_physical.md)
   + Virtual MFA device: [Enabling a Virtual Multi\-factor Authentication \(MFA\) Device](id_credentials_mfa_enable_virtual.md)
   + SMS MFA device: [PREVIEW – Enabling SMS Text Message MFA Devices](id_credentials_mfa_enable_sms.md)

1. *Use the MFA device when you log in to or access AWS resources\.* Note the following:
   + To access an AWS website, you need an MFA code from the device in addition to the usual user name and password\. If AWS determines that the IAM user you sign in as is MFA\-enabled with SMS, then it automatically sends the MFA code to the configured phone number\.
   + To access MFA\-protected API operations, you need an MFA code, the identifier for the MFA device \(the device serial number of a physical device or the ARN of a virtual or SMS device defined in AWS\), and the usual access key ID and secret access key\. 
**Note**  
You cannot pass the MFA information for an SMS MFA device to AWS STS APIs to request temporary credentials\.

   For more information, see [Using MFA Devices With Your IAM Sign\-in Page](console_sign-in-mfa.md) 

**Topics**
+ [Enabling a Virtual Multi\-factor Authentication \(MFA\) Device](id_credentials_mfa_enable_virtual.md)
+ [Enabling a Hardware MFA Device \(Console\)](id_credentials_mfa_enable_physical.md)
+ [PREVIEW – Enabling SMS Text Message MFA Devices](id_credentials_mfa_enable_sms.md)
+ [Enable and manage virtual MFA devices \(AWS CLI, Tools for Windows PowerShell, or AWS API\)](id_credentials_mfa_enable_cliapi.md)