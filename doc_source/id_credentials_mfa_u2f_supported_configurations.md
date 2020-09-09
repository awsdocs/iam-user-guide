# Supported configurations for using U2F security keys<a name="id_credentials_mfa_u2f_supported_configurations"></a>

You can use U2F as a multi\-factor authentication \(MFA\) method in AWS using currently supported configurations\. These include U2F devices supported by AWS and browsers that support U2F\.

## U2F devices supported by AWS<a name="id_credentials_mfa_u2f_supported_devices"></a>

AWS currently supports U2F\-compliant security devices that plug into USB ports on your computer\.

**Note**  
AWS requires access to the physical USB port on your computer to verify your U2F device\. U2F MFA will not work with a virtual machine or remote connection\.

For information on purchasing a supported device, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.

## Browsers that support U2F<a name="id_credentials_mfa_u2f_browsers"></a>

The following browsers currently support the use of U2F security keys:
+ Google Chrome, version 38 and later\.
+ Opera, version 40 and later\.
+ Mozilla Firefox, version 57 and later\.
**Note**  
Most Firefox versions that currently support U2F do not enable support by default\. For instructions on enabling U2F support in Firefox, see [Troubleshooting U2F security keys](troubleshoot_mfa-u2f.md)\.

### Browser plugins<a name="id_credentials_mfa_u2f_plugins"></a>

AWS currently supports only browsers that natively support the U2F standard\. AWS does not support using plugins to add U2F browser support\. Also note that some browser plugins are incompatible with the U2F standard and can cause unexpected results with U2F security keys\. 

For information on disabling browser plugins and other troubleshooting tips, see [I can't enable my U2F security key](troubleshoot_mfa-u2f.md#troubleshoot_mfa-u2f-cant-enable)\. 

## Mobile environments<a name="id_credentials_mfa_u2f_mobile_environments"></a>

AWS does not currently support the use of U2F security keys with mobile browsers or non\-USB U2F devices\. 

The AWS Console Mobile App does not currently support using U2F security keys for MFA\.

## AWS CLI and AWS API<a name="id_credentials_mfa_u2f_cliapi"></a>

AWS currently supports using U2F security keys only in the AWS Management Console\. Using U2F security keys for MFA is not currently supported in the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/) and [AWS API](https://aws.amazon.com/tools/), or for access to [MFA\-protected API operations](id_credentials_mfa_configure-api-require.md)\.

## Additional resources<a name="id_credentials_mfa_u2f_additional_resources"></a>
+ For more information on using U2F security keys in AWS, see [Enabling a U2F security key \(console\)](id_credentials_mfa_enable_u2f.md)\.
+ For help with troubleshooting U2F in AWS, see [Troubleshooting U2F security keys](troubleshoot_mfa-u2f.md)\.
+ For general industry information on U2F support, see [Universal 2nd Factor](https://en.wikipedia.org/wiki/Universal_2nd_Factor)\. 