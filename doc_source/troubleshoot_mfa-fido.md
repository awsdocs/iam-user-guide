# Troubleshooting FIDO security keys<a name="troubleshoot_mfa-fido"></a>

Use the information here to help you diagnose common issues that you might encounter when working with FIDO2 security keys\.

**Topics**
+ [I can't enable my FIDO security key](#troubleshoot_mfa-fido-cant-enable)
+ [I can't sign in using my FIDO security key](#troubleshoot_mfa-fido-signin)
+ [I lost or broke my FIDO security key](#troubleshoot_mfa-fido-lost)
+ [Other issues](#troubleshoot_mfa-fido-other-issues)

## I can't enable my FIDO security key<a name="troubleshoot_mfa-fido-cant-enable"></a>

Consult the following solutions depending on your status as an IAM user or system administrator

### IAM users<a name="troubleshoot_mfa-fido-cant-enable-iam-user"></a>

If you can't enable your FIDO security key, check the following:
+ Are you using a supported configuration?

  For information on devices and browsers you can use with WebAuthn and AWS, see [Supported configurations for using FIDO security keys](id_credentials_mfa_fido_supported_configurations.md)\.
+ Are you using Mozilla Firefox?

  Most Firefox versions that support WebAuthn do not enable support by default\. To enable support for WebAuthn in Firefox, do the following:

  1. From the Firefox address bar, type **about:config**\.

  1. In the Search bar of the screen that opens, type **u2f**\.

  1. Choose **security\.webauth\.u2f** and change its value to **true**\.
+ Are you using any browser plugins?

  AWS does not support the use of plugins to add WebAuthn browser support\. Instead, use a browser that offers native support of the WebAuthn standard\.

  Even if you're using a supported browser, you may have a plugin that is incompatible with WebAuthn\. An incompatible plugin may prevent you from enabling and using your FIDO\-compliant security key\. You should disable any plugins that might be incompatible and restart your browser\. Then retry enabling the FIDO security key\.
+ Do you have the appropriate permissions?

  If you don't have any of the above compatibility issues, you may not have the appropriate permissions\. Contact your system administrator\. 

### System administrators<a name="troubleshoot_mfa-fido-cant-enable-sys-admin"></a>

If you're an administrator and your IAM users can't enable their FIDO security keys despite using a supported configuration, make sure they have the appropriate permissions\. For a detailed example, see [IAM tutorial: Permit users to manage their credentials and MFA settings](tutorial_users-self-manage-mfa-and-creds.md)\.

## I can't sign in using my FIDO security key<a name="troubleshoot_mfa-fido-signin"></a>

If you're an IAM user and you can't sign in to the AWS Management Console using WebAuthn, first see [Supported configurations for using FIDO security keys](id_credentials_mfa_fido_supported_configurations.md)\. If you're using a supported configuration but cannot sign in, contact your system administrator for assistance\. 

## I lost or broke my FIDO security key<a name="troubleshoot_mfa-fido-lost"></a>

Only *one* MFA device \(virtual, FIDO security key, or hardware\) is assigned to a user at a time\. Replacing a FIDO security key is similar to replacing a hardware MFA device\. For information on what to do if you lose or break any type of MFA device, see [What if an MFA device is lost or stops working?](id_credentials_mfa_lost-or-broken.md)\.

## Other issues<a name="troubleshoot_mfa-fido-other-issues"></a>

If you have an issue with FIDO security keys that is not covered here, do one of the following:
+ IAM users: Contact your system administrator\.
+ AWS account root users: Contact [AWS Support](https://aws.amazon.com/premiumsupport/)\.