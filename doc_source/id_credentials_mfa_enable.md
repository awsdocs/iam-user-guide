# Enabling MFA devices for users in AWS<a name="id_credentials_mfa_enable"></a>

The steps for configuring MFA depend on the type of MFA device you are using\.

**Topics**
+ [General steps for enabling MFA devices](#id_credentials_mfa_enable-overview)
+ [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md)
+ [Enabling a FIDO security key \(console\)](id_credentials_mfa_enable_fido.md)
+ [Enabling a hardware TOTP token \(console\)](id_credentials_mfa_enable_physical.md)
+ [Enabling and managing virtual MFA devices \(AWS CLI or AWS API\)](id_credentials_mfa_enable_cliapi.md)

## General steps for enabling MFA devices<a name="id_credentials_mfa_enable-overview"></a>

The following overview procedure describes how to set up and use MFA and provides links to related information\.

**Note**  
You can also watch this English\-language video, [How to Setup AWS Multi\-Factor Authentication \(MFA\) and AWS Budget Alerts](https://www.youtube.com/watch?v=e6A7z7FqQDE), for more information\.

1. *Get an MFA device such as one of the following\.* You can enable up to eight MFA devices per AWS account root user or IAM user of any combination of the following types\.
   + A virtual MFA device, which is a software app that is compliant with [RFC 6238, a standards\-based TOTP \(time\-based one\-time password\) algorithm](https://datatracker.ietf.org/doc/html/rfc6238)\. You can install the app on a phone or other device\. For a list of a few supported apps that you can use as virtual MFA devices, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.
   + A FIDO security key with an [AWS supported configuration](id_credentials_mfa_fido_supported_configurations.md)\. The FIDO Alliance maintains a list of all [FIDO Certified products](https://fidoalliance.org/certification/fido-certified-products/) that are compatible with FIDO specifications\.
   + A hardware\-based MFA device from a third\-party provider like a token device\. These tokens are used exclusively with AWS accounts\. For more information, see [Enabling a hardware TOTP token \(console\)](id_credentials_mfa_enable_physical.md)\. You can purchase these tokens directly from the manufacturers as a key fob or display card device\.

1. *Enable the MFA device\.* 
   + **Virtual or Hardware TOTP tokens** –You can use AWS CLI commands or AWS API operations to enable a virtual MFA device for an IAM user\. You cannot enable an MFA device for the AWS account root user with the AWS CLI, AWS API, Tools for Windows PowerShell, or any other command line tool\. However, you can use the AWS Management Console to enable an MFA device for the root user\.
   + **FIDO security keys** – Root users and IAM users with FIDO security keys can enable from the AWS Management Console only, not from the AWS CLI or AWS API\.

   For information about enabling each type of MFA device, see the following pages:
   + Virtual MFA device: [Enabling a virtual multi\-factor authentication \(MFA\) device \(console\)](id_credentials_mfa_enable_virtual.md)
   + FIDO security key: [Enabling a FIDO security key \(console\)](id_credentials_mfa_enable_fido.md) 
   + Hardware TOTP token: [Enabling a hardware TOTP token \(console\)](id_credentials_mfa_enable_physical.md)

1. *Enable Multiple MFA devices \(recommended\)*
   + We recommend that you enable multiple MFA devices to the AWS account root user and IAM users in your AWS accounts\. This allows you to raise the security bar in your AWS accounts and simplify managing access to highly privileged users, such as the AWS account root user\.
   + You can register up to **eight** MFA devices of any combination of the [ currently supported MFA types](https://aws.amazon.com/iam/features/mfa/) with your AWS account root user and IAM users\. With multiple MFA devices, you only need one MFA device to sign in to the AWS Management Console or create a session through the AWS CLI as that user\. An IAM user must authenticate with an existing MFA device to enable or disable an additional MFA device\.
   + In the event of a lost, stolen, or inaccessible MFA device you can use one of the remaining MFA devices to access the AWS account without performing the AWS account recovery procedure\. If an MFA device is lost or stolen, it should be disassociated from the IAM principal with which it is associated\.
   + The use of multiple MFAs allows your employees in geographically dispersed locations or working remotely to use hardware\-based MFA to access AWS without having to coordinate the physical exchange of a single hardware device between employees\.
   + The use of additional MFA devices for IAM principals allows you to use one or more MFAs for everyday usage, while also maintaining physical MFA devices in a secure physical location such as a vault or safe for backup and redundancy\.

1. *Use the MFA device when you log in to or access AWS resources\.* Note the following:
   + **FIDO security keys** – To access an AWS website, enter your credentials and then tap the FIDO security key when prompted\.
   + **Virtual MFA devices and hardware TOTP tokens** – To access an AWS website, you need an MFA code from the device in addition to your user name and password\. 

     To access MFA\-protected API operations, you need the following:
     + An MFA code
     + The identifier for the MFA device \(the device serial number of a physical device or the ARN of a virtual device defined in AWS\)
     + The usual access key ID and secret access key
**Notes**  
You cannot pass the MFA information for a FIDO security key to AWS STS API operations to request temporary credentials\.
You cannot use AWS CLI commands or AWS API operations to enable [FIDO security keys](id_credentials_mfa_enable_fido.md)\.

For more information, see [Using MFA devices with your IAM sign\-in page](console_sign-in-mfa.md)\. 