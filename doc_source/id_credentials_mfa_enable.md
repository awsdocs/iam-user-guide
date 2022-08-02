# Enabling MFA devices for users in AWS<a name="id_credentials_mfa_enable"></a>

The steps for configuring MFA depend on the type of MFA device you are using\.

**Topics**
+ [General steps for enabling MFA devices](#id_credentials_mfa_enable-overview)
+ [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md)
+ [Enabling a FIDO security key \(console\)](id_credentials_mfa_enable_fido.md)
+ [Enabling a hardware MFA device \(console\)](id_credentials_mfa_enable_physical.md)
+ [Enabling and managing virtual MFA devices \(AWS CLI or AWS API\)](id_credentials_mfa_enable_cliapi.md)

## General steps for enabling MFA devices<a name="id_credentials_mfa_enable-overview"></a>

The following overview procedure describes how to set up and use MFA and provides links to related information\.

**Note**  
You can also watch this English\-language video, [How to Setup AWS Multi\-Factor Authentication \(MFA\) and AWS Budget Alerts](https://www.youtube.com/watch?v=e6A7z7FqQDE), for more information\.

1. *Get an MFA device such as one of the following\.* You can enable only one MFA device per AWS account root user or IAM user\.
   + A virtual MFA device, which is a software app that is compliant with [RFC 6238, a standards\-based TOTP \(time\-based one\-time password\) algorithm](https://datatracker.ietf.org/doc/html/rfc6238)\. You can install the app on a phone or other device\. For a list of a few supported apps that you can use as virtual MFA devices, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.
   + A FIDO security key with an [AWS supported configuration](id_credentials_mfa_fido_supported_configurations.md), such as one of the FIDO2 devices discussed on the [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/) page\.
   + A hardware\-based MFA device, such as one of the AWS supported hardware token devices discussed on the [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/) page\.

1. *Enable the MFA device\.* 
   + IAM users with virtual or hardware MFA devices: Enable from the AWS Management Console, AWS CLI, or the IAM API\.
   + IAM users with FIDO security keys: Enable from the AWS Management Console only\.
   + AWS account root users with any type of MFA device: Enable from the AWS Management Console only\.

   For information about enabling each type of MFA device, see the following pages:
   + Virtual MFA device: [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md)
   + FIDO security key: [Enabling a FIDO security key \(console\)](id_credentials_mfa_enable_fido.md) 
   + Hardware MFA device: [Enabling a hardware MFA device \(console\)](id_credentials_mfa_enable_physical.md)

1. *Use the MFA device when you log in to or access AWS resources\.* Note the following:
   + FIDO security keys: To access an AWS website, enter your credentials and then tap the FIDO security key when prompted\.
   + Virtual MFA devices and hardware MFA devices: To access an AWS website, you need an MFA code from the device in addition to your user name and password\. 

     To access MFA\-protected API operations, you need the following:
     + An MFA code
     + The identifier for the MFA device \(the device serial number of a physical device or the ARN of a virtual device defined in AWS\)
     + The usual access key ID and secret access key
**Notes**  
You cannot pass the MFA information for a FIDO security key to AWS STS API operations to request temporary credentials\.
You cannot use AWS CLI commands or AWS API operations to enable [FIDO security keys](id_credentials_mfa_enable_fido.md)\.

For more information, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\. 