# Using Multi\-Factor Authentication \(MFA\) in AWS<a name="id_credentials_mfa"></a>

For increased security, we recommend that you configure multi\-factor authentication \(MFA\) to help protect your AWS resources\. MFA adds extra security because it requires users to type a unique authentication code from an approved authentication device or SMS \(Short Message Service\) text message when they access AWS websites or services\. 
+ **Security token\-based**\. This type of MFA requires you to assign an MFA device \(hardware or virtual\) to the IAM user or the AWS account root user\. A virtual device is a software application running on a phone or other mobile device that emulates a physical device\. Either way, the device generates a six\-digit numeric code based upon a time\-synchronized one\-time password algorithm\. The user must type a valid code from the device on a second webpage during sign\-in\. Each MFA device assigned to a user must be unique; a user cannot type a code from another user's device to authenticate\. For more information about enabling security token\-based MFA, see [Enabling a Hardware MFA Device \(Console\)](id_credentials_mfa_enable_physical.md) and [Enabling a Virtual Multi\-factor Authentication \(MFA\) Device](id_credentials_mfa_enable_virtual.md)\.
+ **SMS text message\-based**\. This type of MFA requires you to configure the IAM user with the phone number of the user's SMS\-compatible mobile device\. When the user signs in, AWS sends a six\-digit numeric code by SMS text message to the user's mobile device\. The user is required to type that code on a second webpage during sign\-in\. Note that SMS\-based MFA is available only for IAM users\. You cannot use this type of MFA with the AWS account root user\. For more information about enabling SMS text messaging\-based MFA, see [PREVIEW – Enabling SMS Text Message MFA Devices](id_credentials_mfa_enable_sms.md)\.
**Note**  
AWS will stop supporting SMS MFA on February 1, 2019\. If your account is already participating in the SMS MFA Preview program, you can continue using this feature until then\. We encourage you to use MFA through either a [hardware\-based](id_credentials_mfa_enable_physical.md) or [virtual \(software\-based\)](id_credentials_mfa_enable_virtual.md) MFA device\. 
**Tip**  
You can view users in your account with an assigned SMS MFA device\. To do so, go to the IAM console, choose **Users** from the navigation pane, and look for users with **SMS** in the **MFA** column of the table\.

No matter how the user receives the six\-digit numeric MFA code, the user types it on a second page of the sign\-in process for the AWS Management Console\. In some cases, a user may work with the AWS STS API or CLI instead of the console\. In that case, you can pass hardware or virtual MFA device codes as parameters to STS API calls to get temporary credentials\.

**Note**  
Currently, you can use SMS\-based MFA only with AWS Management Console\. You cannot use SMS\-based MFA with the API or AWS CLI\.

This section shows you how to configure MFA for your users and set them up to use token devices or SMS text messages\. It also describes how to synchronize and deactivate existing token devices, and what to do when a device is lost or stops working\.

**Note**  
When you enable MFA for the AWS account root user, it affects only the root user credentials\. IAM users in the account are distinct identities with their own credentials, and each identity has its own MFA configuration\.

For answers to commonly asked questions about AWS MFA, go to the [AWS Multi\-Factor Authentication FAQs](http://aws.amazon.com/iam/faqs/#MFA_FAQs)\. 

**Topics**
+ [Enabling MFA Devices](id_credentials_mfa_enable.md)
+ [Checking MFA Status](id_credentials_mfa_checking-status.md)
+ [Resynchronize MFA Devices](id_credentials_mfa_sync.md)
+ [Deactivating MFA Devices](id_credentials_mfa_disable.md)
+ [What If an MFA Device Is Lost or Stops Working?](id_credentials_mfa_lost-or-broken.md)
+ [Configuring MFA\-Protected API Access](id_credentials_mfa_configure-api-require.md)
+ [Sample Policies with MFA Conditions](id_credentials_mfa_sample-policies.md)
+ [Sample Code: Requesting Credentials with Multi\-factor Authentication](id_credentials_mfa_sample-code.md)