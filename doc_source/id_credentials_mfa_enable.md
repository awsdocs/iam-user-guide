# Enabling MFA devices for users in AWS<a name="id_credentials_mfa_enable"></a>

The steps for configuring MFA depend on the type of MFA device you are using\.

**Topics**
+ [General steps for enabling MFA devices](#id_credentials_mfa_enable-overview)
+ [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md)
+ [Enabling a U2F security key \(console\)](id_credentials_mfa_enable_u2f.md)
+ [Enabling a hardware MFA device \(console\)](id_credentials_mfa_enable_physical.md)
+ [PREVIEW – Enabling SMS text message MFA devices](id_credentials_mfa_enable_sms.md)
+ [Enabling and managing virtual MFA devices \(AWS CLI or AWS API\)](id_credentials_mfa_enable_cliapi.md)

## General steps for enabling MFA devices<a name="id_credentials_mfa_enable-overview"></a>

The following overview procedure describes how to set up and use MFA and provides links to related information\.

1. *Get an MFA device such as one of the following\.* You can enable only one MFA device per AWS account root user or IAM user\.
   + A virtual MFA device, which is a software app that is compliant with [RFC 6238, a standards\-based TOTP \(time\-based one\-time password\) algorithm](https://tools.ietf.org/html/rfc6238)\. You can install the app on a phone or other device\. For a list of a few supported apps that you can use as virtual MFA devices, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.
   + A U2F security key with an [AWS supported configuration](id_credentials_mfa_u2f_supported_configurations.md), such as one of the U2F devices discussed on the [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/) page\.
   + A hardware\-based MFA device, such as one of the AWS supported hardware token devices discussed on the [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/) page\.
   + A mobile phone that can receive standard short message service \(SMS\) text messages\.
**Notes**  
If you choose to use SMS\-based MFA, text messaging charges from your mobile device's carrier may apply\. 
SMS\-based MFA is only available for IAM users and cannot be used for the root user\.

1. *Enable the MFA device\.* 
   + IAM users with virtual or hardware MFA devices: Enable from the AWS Management Console, AWS CLI, or the IAM API\.
   + IAM users with U2F security keys or a mobile phone that can receive SMS text messages: Enable from the AWS Management Console only\.
   + AWS account root users with any type of MFA device \(except SMS MFA, which is not supported for root users\): Enable from the AWS Management Console only\.

   For information about enabling each type of MFA device, see the following pages:
   + Virtual MFA device: [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md)
   + U2F security key: [Enabling a U2F security key \(console\)](id_credentials_mfa_enable_u2f.md) 
   + Hardware MFA device: [Enabling a hardware MFA device \(console\)](id_credentials_mfa_enable_physical.md)
   + SMS MFA device: [PREVIEW – Enabling SMS text message MFA devices](id_credentials_mfa_enable_sms.md)

1. *Use the MFA device when you log in to or access AWS resources\.* Note the following:
   + U2F security keys: To access an AWS website, enter your credentials and then tap the U2F security key when prompted\.
   + Virtual MFA devices, hardware MFA devices, and SMS MFA devices: To access an AWS website, you need an MFA code from the device in addition to your user name and password\. If AWS determines that the IAM user you sign in as is MFA\-enabled with SMS, then it automatically sends the MFA code to the configured phone number\.

     To access MFA\-protected API operations, you need the following:
     + An MFA code
     + The identifier for the MFA device \(the device serial number of a physical device or the ARN of a virtual or SMS device defined in AWS\)
     + The usual access key ID and secret access key
**Notes**  
You cannot pass the MFA information for a U2F security key or SMS MFA device to AWS STS API operations to request temporary credentials\.
You cannot use AWS CLI commands or AWS API operations to enable [U2F security keys](id_credentials_mfa_enable_u2f.md)\.

For more information, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\. 