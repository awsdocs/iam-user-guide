# Using MFA devices with your IAM sign\-in page<a name="console_sign-in-mfa"></a>

IAM users who are configured with [multi\-factor authentication \(MFA\)](id_credentials_mfa.md) devices must use their MFA devices to sign in to the AWS Management Console\. After the user enters the user name and password, AWS checks the user's account to see if MFA is required for that user\. The following sections provide information on how users complete signing in when MFA is required\. 

**Topics**
+ [Signing in with a virtual MFA device](#console_sign-in-mfa-virtual)
+ [Signing in with a U2F security key](#console_sign-in-mfa-u2f)
+ [Signing in with a hardware MFA device](#console_sign-in-mfa-hardware)

## Signing in with a virtual MFA device<a name="console_sign-in-mfa-virtual"></a>

If MFA is required for the user, a second sign\-in page appears\. In the **MFA code** box, the user must enter the numeric code provided by the MFA application\.

If the MFA code is correct, the user can access the AWS Management Console\. If the code is incorrect, the user can try again with another code\. 

A virtual MFA device can go out of sync\. If a user cannot sign in to the AWS Management Console after several tries, the user is prompted to synchronize the virtual MFA device\. The user can follow the on\-screen prompts to synchronize the virtual MFA device\. For information about how you can synchronize a device on behalf of a user in your AWS account, see [Resynchronizing virtual and hardware MFA devices](id_credentials_mfa_sync.md)\. 

## Signing in with a U2F security key<a name="console_sign-in-mfa-u2f"></a>

If MFA is required for the user, a second sign\-in page appears\. The user needs to tap the U2F security key\.

Unlike other MFA devices, U2F security keys do not go out of sync\. Administrators can deactivate a U2F security key if it's lost or broken\. For more information, see [Deactivating MFA devices \(console\)](id_credentials_mfa_disable.md#deactive-mfa-console)\.

For information on browsers that support U2F and U2F devices that AWS supports, see [Supported configurations for using U2F security keys](id_credentials_mfa_u2f_supported_configurations.md)\.

## Signing in with a hardware MFA device<a name="console_sign-in-mfa-hardware"></a>

If MFA is required for the user, a second sign\-in page appears\. In the **MFA code** box, the user must enter the numeric code provided by a hardware MFA device\. 

If the MFA code is correct, the user can access the AWS Management Console\. If the code is incorrect, the user can try again with another code\. 

A hardware MFA device can go out of sync\. If a user cannot sign in to the AWS Management Console after several tries, the user is prompted to synchronize the MFA token device\. The user can follow the on\-screen prompts to synchronize the MFA token device\. For information about how you can synchronize a device on behalf of a user in your AWS account, see [Resynchronizing virtual and hardware MFA devices](id_credentials_mfa_sync.md)\. 