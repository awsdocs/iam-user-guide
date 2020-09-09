# Resynchronizing virtual and hardware MFA devices<a name="id_credentials_mfa_sync"></a>

You can use AWS to resynchronize your virtual and hardware multi\-factor authentication \(MFA\) devices\. If your device is not synchronized when you try to use it, the sign\-in attempt fails and IAM prompts you to resynchronize the device\.

**Note**  
U2F security keys do not go out of sync\. If a U2F security key is lost or broken, you can deactivate it\. For instructions on deactivating any MFA device type, see [To deactivate an MFA device for another IAM user \(console\)](id_credentials_mfa_disable.md#deactivate-mfa-for-user)\.

As an AWS administrator, you can resynchronize your IAM users' virtual and hardware MFA devices if they get out of synchronization\.

If your AWS account root user MFA device is not working, you can resynchronize your device using the IAM console with or without completing the sign\-in process\. 

**Topics**
+ [Permissions required](#id_credentials_mfa_sync_console-permissions-required)
+ [Resynchronizing virtual and hardware MFA devices \(IAM console\)](#id_credentials_mfa_sync_console)
+ [Resynchronizing virtual and hardware MFA devices \(AWS CLI\)](#id_credentials_mfa_sync_cli)
+ [Resynchronizing virtual and hardware MFA devices \(AWS API\)](#id_credentials_mfa_sync_api)

## Permissions required<a name="id_credentials_mfa_sync_console-permissions-required"></a>

To resynchronize virtual or hardware MFA devices for your own IAM user, you must have the permissions from the following policy: This policy does not allow you to create or deactivate a device\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowListActions",
            "Effect": "Allow",
            "Action": [
                "iam:ListVirtualMFADevices"
            ],
            "Resource": "*"
        },
        {
            "Sid": "AllowUserToViewAndManageTheirOwnUserMFA",
            "Effect": "Allow",
            "Action": [
                "iam:ListMFADevices",
                "iam:ResyncMFADevice"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        },
        {
            "Sid": "BlockAllExceptListedIfNoMFA",
            "Effect": "Deny",
            "NotAction": [
                "iam:ListMFADevices",
                "iam:ListVirtualMFADevices",
                "iam:ResyncMFADevice"
            ],
            "Resource": "*",
            "Condition": {
                "BoolIfExists": {
                    "aws:MultiFactorAuthPresent": "false"
                }
            }
        }
    ]
}
```

## Resynchronizing virtual and hardware MFA devices \(IAM console\)<a name="id_credentials_mfa_sync_console"></a>

You can use the IAM console to resynchronize virtual and hardware MFA devices\.

**To resynchronize a virtual or hardware MFA device for your own IAM user \(console\)**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

   To get your AWS account ID, contact your administrator\.

1. In the navigation bar on the upper right, choose your user name, and then choose **My Security Credentials**\.   
![\[AWS Management Console My Security Credentials link\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-user.shared.console.png)

1. On the **AWS IAM credentials** tab, in the **Multi\-factor authentication** section, choose **Manage MFA device**\.

1. In the **Manage MFA device** wizard, choose **Resync**, and then choose **Continue**\.

1. Type the next two sequentially generated codes from the device into **MFA code 1** and **MFA code 2**\. Then choose **Continue**\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the request appears to work but the device remains out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\.

**To resynchronize a virtual or hardware MFA device for another IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**, and then choose the name of the user whose MFA device needs to be resynchronized\.

1. Choose the **Security credentials** tab\. Next to **Assigned MFA device**, choose **Manage**\.

1. In the **Manage MFA device** wizard, choose **Resync**, and then choose **Continue**\.

1. Type the next two sequentially generated codes from the device into **MFA code 1** and **MFA code 2**\. Then choose **Continue**\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the request appears to work but the device remains out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\.

**To resynchronize your root user MFA before signing in \(console\)**

1. On the **Amazon Web Services Sign In With Authentication Device** page, choose **Having problems with your authentication device? Click here**\.
**Note**  
You might see different text, such as **Sign in using MFA** and **Troubleshoot your authentication device**\. However, the same features are provided\.

1. In the **Re\-Sync With Our Servers** section, type the next two sequentially generated codes from the device into **MFA code 1** and **MFA code 2**\. Then choose **Re\-sync authentication device**\.

1. If necessary, type your password again and choose **Sign in**\. Then complete the sign\-in using your MFA device\.

**To resynchronize your root user MFA device after signing in \(console\)**

1. Sign in to the [IAM console](https://console.aws.amazon.com/iam/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.
**Note**  
If you see three text boxes, then you previously signed in to the console with *[IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html)* credentials\. Your browser might remember this preference and open this account\-specific sign\-in page every time that you try to sign in\. You cannot use the IAM user sign\-in page to sign in as the account owner\. If you see the [IAM user sign\-in page](https://docs.aws.amazon.com/IAM/latest/UserGuide/console.html#user-sign-in-page), choose **Sign in using root user email** near the bottom of the page\. This returns you to the main sign\-in page\. From there, you can sign in as the root user using your AWS account email address and password\.

1. On the right side of the navigation bar, choose on your account name, and then choose **My Security Credentials**\. If necessary, choose **Continue to Security Credentials**\.  
![\[My Security Credentials in the navigation menu\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-root.shared.console.png)

1. Expand the **Multi\-factor authentication \(MFA\)** section on the page\.

1. Next to your active MFA device, choose **Resync**\.

1. In the **Manage MFA device** dialog box, type the next two sequentially generated codes from the device into **MFA code 1** and **MFA code 2**\. Then choose **Continue**\.
**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the MFA device is successfully associated with the user, but the MFA device is out of sync\. This happens because time\-based one\-time passwords \(TOTP\) expire after a short period of time\.

## Resynchronizing virtual and hardware MFA devices \(AWS CLI\)<a name="id_credentials_mfa_sync_cli"></a>

You can resynchronize virtual and hardware MFA devices from the AWS CLI\.

**To resynchronize a virtual or hardware MFA device for an IAM user \(AWS CLI\)**  
At a command prompt, issue the [aws iam resync\-mfa\-device](https://docs.aws.amazon.com/cli/latest/reference/iam/resync-mfa-device.html) command:
+ Virtual MFA device: Specify Amazon Resource Name \(ARN\) of device as the serial number\.

  ```
  aws iam resync-mfa-device --user-name Richard --serial-number arn:aws:iam::123456789012:mfa/RichardsMFA --authentication-code1 123456 --authentication-code2 987654
  ```
+ Hardware MFA device: Specify hardware device's serial number as serial number\. The format is vendor\-specific\. For example, you can purchase a gemalto token from Amazon\. Its serial number is typically four letters followed by four numbers\.

  ```
  aws iam resync-mfa-device --user-name Richard --serial-number ABCD12345678 --authentication-code1 123456 --authentication-code2 987654
  ```

**Important**  
Submit your request immediately after generating the codes\. If you generate the codes and then wait too long to submit the request, the request fails because the codes expire after a short time\.

## Resynchronizing virtual and hardware MFA devices \(AWS API\)<a name="id_credentials_mfa_sync_api"></a>

IAM has an API call that performs synchronization\. In this case, we recommend that you give your virtual and hardware MFA device users permission to access this API call\. Then build a tool based on that API call so your users can resynchronize their devices whenever they need to\.

**To resynchronize a virtual or hardware MFA device for an IAM user \(AWS API\)**
+ Send the [ResyncMFADevice](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ResyncMFADevice.html) request\.