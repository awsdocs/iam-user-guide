# Supported configurations for using FIDO security keys<a name="id_credentials_mfa_fido_supported_configurations"></a>

You can use WebAuthn as a multi\-factor authentication \(MFA\) method in AWS using currently supported configurations\. These include FIDO\-compliant devices supported by AWS and browsers that support WebAuthn\.

## FIDO devices supported by AWS<a name="id_credentials_mfa_fido_supported_devices"></a>

AWS currently supports FIDO\-compliant security devices that plug into USB ports on your computer\.

**Note**  
AWS requires access to the physical USB port on your computer to verify your FIDO\-compliant device\. WebAuthn MFA will not work with a virtual machine, a remote connection, or a browser's incognito mode\.

For information on purchasing a supported device, see [Multi\-Factor Authentication](http://aws.amazon.com/iam/details/mfa/)\.

## Browsers that support WebAuthn<a name="id_credentials_mfa_fido_browsers"></a>

The following browsers currently support the use of FIDO\-compliant security keys:
+ Google Chrome, version 38 and later\.
+ Opera, version 40 and later\.
+ Mozilla Firefox, version 57 and later\.
**Note**  
Most Firefox versions that currently support WebAUthn do not enable support by default\. For instructions on enabling WebAuthn support in Firefox, see [Troubleshooting FIDO security keys](troubleshoot_mfa-fido.md)\.
+ Safari, version 13 and later\.

### Browser plugins<a name="id_credentials_mfa_fido_plugins"></a>

AWS currently supports only browsers that natively support the FIDO2/WebAuthn standard\. AWS does not support using plugins to add FIDO2/WebAuthn browser support\. Also note that some browser plugins are incompatible with the U2F standard and can cause unexpected results with FIDO2 security keys\. 

For information on disabling browser plugins and other troubleshooting tips, see [I can't enable my FIDO security key](troubleshoot_mfa-fido.md#troubleshoot_mfa-fido-cant-enable)\. 

## Mobile environments<a name="id_credentials_mfa_fido_mobile_environments"></a>

AWS does not currently support the use of FIDO\-compliant security keys with mobile browsers or non\-USB FIDO2 devices\. 

The AWS Console Mobile App does not currently support using FIDO\-compliant security keys for MFA\.

## AWS CLI and AWS API<a name="id_credentials_mfa_fido_cliapi"></a>

AWS currently supports using FIDO\-compliant security keys only in the AWS Management Console\. Using FIDO\-compliant security keys for MFA is not currently supported in the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/) and [AWS API](https://aws.amazon.com/tools/), or for access to [MFA\-protected API operations](id_credentials_mfa_configure-api-require.md)\.

## Additional resources<a name="id_credentials_mfa_fido_additional_resources"></a>
+ For more information on using FIDO\-compliant security keys in AWS, see [Enabling a FIDO security key \(console\)](id_credentials_mfa_enable_fido.md)\.
+ For help with troubleshooting FIDO in AWS, see [Troubleshooting FIDO security keys](troubleshoot_mfa-fido.md)\.
+ For general industry information on FIDO support, see [FIDO2 Project](https://en.wikipedia.org/wiki/FIDO2_Project)\. 