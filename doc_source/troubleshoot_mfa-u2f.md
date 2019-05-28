# Troubleshooting U2F Security Keys<a name="troubleshoot_mfa-u2f"></a>

Use the information here to help you diagnose common issues that you might encounter when working with U2F security keys\.

**Topics**
+ [I Can't Enable My U2F Security Key](#troubleshoot_mfa-u2f-cant-enable)
+ [I Can't Sign in Using My U2F Security Key](#troubleshoot_mfa-u2f-signin)
+ [I Lost or Broke My U2F Key](#troubleshoot_mfa-u2f-lost)
+ [Other Issues](#troubleshoot_mfa-u2f-other-issues)

## I Can't Enable My U2F Security Key<a name="troubleshoot_mfa-u2f-cant-enable"></a>

Consult the following solutions depending on your status as an IAM user or system administrator

### IAM Users<a name="troubleshoot_mfa-u2f-cant-enable-iam-user"></a>

If you can't enable your U2F security key, check the following:
+ Are you using a supported configuration?

  For information on devices and browsers you can use with U2F and AWS, see [Supported Configurations for Using U2F Security Keys](id_credentials_mfa_u2f_supported_configurations.md)\.
+ Are you using Mozilla Firefox?

  Most Firefox versions that support U2F do not enable support by default\. To enable support for U2F in Firefox, do the following:

  1. From the Firefox address bar, type **about:config**\.

  1. In the Search bar of the screen that opens, type **u2f**\.

  1. Choose **security\.webauth\.u2f** and change its value to **true**\.
+ Are you using any browser plugins?

  AWS does not support the use of plugins to add U2F browser support\. Instead, use a browser that offers native support of the U2F standard\.

  Even if you're using a supported browser, you may have a plugin that is incompatible with U2F\. An incompatible plugin may prevent you from enabling and using your U2F security key\. You should disable any plugins that might be incompatible and restart your browser\. Then retry enabling the U2F security key\.
+ Do you have the appropriate permissions?

  If you don't have any of the above compatibility issues, you may not have the appropriate permissions\. Contact your system administrator\. 

### System Administrators<a name="troubleshoot_mfa-u2f-cant-enable-sys-admin"></a>

If you're an administrator and your IAM users can't enable their U2F security keys despite using a supported configuration, make sure they have the appropriate permissions\. For a detailed example, see [Tutorial: Enable Your Users to Configure Their Own Credentials and MFA Settings](tutorial_users-self-manage-mfa-and-creds.md)\.

## I Can't Sign in Using My U2F Security Key<a name="troubleshoot_mfa-u2f-signin"></a>

If you're an IAM user and you can't sign in to the AWS Management Console using U2F, first see [Supported Configurations for Using U2F Security Keys](id_credentials_mfa_u2f_supported_configurations.md)\. If you're using a supported configuration but cannot sign in, contact your system administrator for assistance\. 

## I Lost or Broke My U2F Key<a name="troubleshoot_mfa-u2f-lost"></a>

Only *one* MFA device \(virtual, U2F security key, or hardware\) is assigned to a user at a time\. Replacing a U2F security key is similar to replacing a hardware MFA device\. For information on what to do if you lose or break any type of MFA device, see [What If an MFA Device Is Lost or Stops Working?](id_credentials_mfa_lost-or-broken.md)\.

## Other Issues<a name="troubleshoot_mfa-u2f-other-issues"></a>

If you have an issue with U2F security keys that is not covered here, do one of the following:
+ IAM users: Contact your system administrator\.
+ AWS account root users: Contact [AWS Support](https://aws.amazon.com/premiumsupport/)\.