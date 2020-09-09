# Managing access keys for IAM users<a name="id_credentials_access-keys"></a>

**Note**  
If you found this page because you are looking for information about the Product Advertising API to sell Amazon products on your website, see the [Product Advertising API 5\.0 Documentation](https://webservices.amazon.com/paapi5/documentation/)\.

Access keys are long\-term credentials for an IAM user or the AWS account root user\. You can use access keys to sign programmatic requests to the AWS CLI or AWS API \(directly or using the AWS SDK\)\. For more information, see [Signing AWS API Requests](https://docs.aws.amazon.com/general/latest/gr/signing_aws_api_requests.html) in the *Amazon Web Services General Reference*\. 

Access keys consist of two parts: an access key ID \(for example, `AKIAIOSFODNN7EXAMPLE`\) and a secret access key \(for example, `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY`\)\. Like a user name and password, you must use both the access key ID and secret access key together to authenticate your requests\. Manage your access keys as securely as you do your user name and password\.

**Important**  
Do not provide your access keys to a third party, even to help [find your canonical user ID](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html#FindingCanonicalId)\. By doing this, you might give someone permanent access to your account\.

As a best practice, use temporary security credentials \(IAM roles\) instead of access keys, and disable any AWS account root user access keys\. For more information, see [Best Practices for Managing AWS Access Keys](https://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html) in the *Amazon Web Services General Reference*\.

If you still need to use long\-term access keys, you can create, modify, view, or rotate your access keys \(access key IDs and secret access keys\)\. You can have a maximum of two access keys\. This allows you to rotate the active keys according to best practices\.

When you create an access key pair, save the access key ID and secret access key in a secure location\. The secret access key is available only at the time you create it\. If you lose your secret access key, you must delete the access key and create a new one\. For more details, see [Resetting lost or forgotten passwords or access keys for AWS](id_credentials_access-keys_retrieve.md)\.

**Topics**
+ [Permissions required](#access-keys_required-permissions)
+ [Managing access keys \(console\)](#Using_CreateAccessKey)
+ [Managing access keys \(AWS CLI\)](#Using_CreateAccessKey_CLIAPI)
+ [Managing access keys \(AWS API\)](#Using_CreateAccessKey_API)
+ [Rotating access keys](#Using_RotateAccessKey)
+ [Auditing access keys](#Using_access-keys-audit)

## Permissions required<a name="access-keys_required-permissions"></a>

To create access keys for your own IAM user, you must have the permissions from the following policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "CreateOwnAccessKeys",
            "Effect": "Allow",
            "Action": [
                "iam:CreateAccessKey",
                "iam:GetUser",
                "iam:ListAccessKeys"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        }
    ]
}
```

To rotate access keys for your own IAM user, you must have the permissions from the following policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ManageOwnAccessKeys",
            "Effect": "Allow",
            "Action": [
                "iam:CreateAccessKey",
                "iam:DeleteAccessKey",
                "iam:GetAccessKeyLastUsed",
                "iam:GetUser",
                "iam:ListAccessKeys",
                "iam:UpdateAccessKey"
            ],
            "Resource": "arn:aws:iam::*:user/${aws:username}"
        }
    ]
}
```

## Managing access keys \(console\)<a name="Using_CreateAccessKey"></a>

You can use the AWS Management Console to manage an IAM user's access keys\.

**To create, modify, or delete your own IAM user access keys \(console\)**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

   To get your AWS account ID, contact your administrator\.

1. In the navigation bar on the upper right, choose your user name, and then choose **My Security Credentials**\.   
![\[AWS Management Console My Security Credentials link\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/security-credentials-user.shared.console.png)

1. Expand the **Access keys \(access key ID and secret access key\)** section\.

1. Do any of the following:
   + To create an access key, choose **Create New Access Key**\. If this feature is disabled, then you must delete one of the existing keys before you can create a new one\. A warning explains that you have only this one opportunity to view or download the secret access key\. To copy the key to paste it somewhere else for safekeeping, choose **Show Access Key**\. To save the access key ID and secret access key to a `.csv` file to a secure location on your computer, choose **Download Key File**\.
   + To disable an active access key, choose **Make Inactive**\.
   + To reenable an inactive access key, choose **Make Active**\.
   + Before you delete an access key, make sure that it's no longer in use\. You cannot recover an access key after you delete it\. To delete your access key, choose **Delete**\. When prompted for confirmation, choose **Yes**\.

**To create, modify, or delete another IAM user's access keys \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the user whose access keys you want to manage, and then choose the **Security credentials** tab\.

1. In the **Access keys** section, do any of the following:
   + To create an access key, choose **Create access key**\. Then choose **Download \.csv file** to save the access key ID and secret access key to a CSV file on your computer\. Store the file in a secure location\. You will not have access to the secret access key again after this dialog box closes\. After you download the CSV file, choose **Close**\. When you create an access key, the key pair is active by default, and you can use the pair right away\.
   + To disable an active access key, choose **Make inactive**\.
   + To reenable an inactive access key, choose **Make active**\.
   + Before you delete an access key, make sure that it's no longer in use\. You cannot recover an access key after you delete it\. To delete an access key, choose its **X** button at the end of the row\. When prompted for confirmation, choose **Delete**\.

**To list the access keys for an IAM user \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the intended user, and then choose the **Security credentials** tab\. The user's access keys and the status of each key is displayed\.
**Note**  
Only the user's access key ID is visible\. The secret access key can only be retrieved when the key is created\.

**To list the access key IDs for multiple IAM users \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. If necessary, add the **Access key ID** column to the users table by completing the following steps:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage columns**, select **Access key ID**\.

   1. Choose **Close** to return to the list of users\.

1. The **Access key ID** column shows each access key ID, followed by its state; for example, **23478207027842073230762374023 \(Active\)** or **22093740239670237024843420327 \(Inactive\)**\. 

   You can use this information to view and copy the access keys for users with one or two access keys\. The column displays **None** for users with no access key\.
**Note**  
Only the user's access key ID and status is visible\. The secret access key can only be retrieved when the key is created\.

**To find which IAM user owns a specific access key \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. In the search box, type or paste the access key ID of the user you want to find\.

1. If necessary, add the **Access key ID** column to the users table by completing the following steps:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage columns**, select **Access key ID**\.

   1. Choose **Close** to return to the list of users and confirm that the filtered user owns the specified access key\.

## Managing access keys \(AWS CLI\)<a name="Using_CreateAccessKey_CLIAPI"></a>

To manage an IAM user's access keys from the AWS CLI, run the following commands\.
+ To create an access key: [https://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html](https://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html)
+ To disable or reenable an access key: [https://docs.aws.amazon.com/cli/latest/reference/iam/update-access-key.html](https://docs.aws.amazon.com/cli/latest/reference/iam/update-access-key.html)
+ To list a user's access keys: [https://docs.aws.amazon.com/cli/latest/reference/iam/list-access-keys.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-access-keys.html)
+ To determine when an access key was most recently used: [https://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html)
+ To delete an access key: [https://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html)

## Managing access keys \(AWS API\)<a name="Using_CreateAccessKey_API"></a>

To manage an IAM user's access keys from the AWS API, call the following operations\.
+ To create an access key: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html)
+ To disable or reenable an access key: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html)
+ To list a user's access keys: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccessKeys.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccessKeys.html)
+ To determine when an access key was most recently used: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html)
+ To delete an access key: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html)

## Rotating access keys<a name="Using_RotateAccessKey"></a>

As a security best practice, we recommend that you regularly rotate \(change\) IAM user access keys\. If your administrator granted you the necessary permissions, you can rotate your own access keys\.

Administrators, for details about granting your users permissions to rotate their own access keys, see [AWS: Allows IAM users to manage their own password, access keys, and SSH public keys on the my security credentials page](reference_policies_examples_aws_my-sec-creds-self-manage-pass-accesskeys-ssh.md)\. You can also apply a password policy to your account to require that all of your IAM users periodically rotate their passwords\. You can choose how often they must do so\. For more information, see [Setting an account password policy for IAM users](id_credentials_passwords_account-policy.md)\. 

**Important**  
As a best practice, do not use your AWS account root user\. If you use the AWS account root user credentials, we recommend that you also regularly rotate them\. The account password policy does not apply to the root user credentials\. IAM users cannot manage credentials for the AWS account root user, so you must use the root user credentials \(not a user's\) to change the root user credentials\. Note that we recommend against using the root user for everyday work in AWS\. 

**Topics**
+ [Rotating IAM user access keys \(console\)](#rotating_access_keys_console)
+ [Rotating access keys \(AWS CLI\)](#rotating_access_keys_cli)
+ [Rotating access keys \(AWS API\)](#rotating_access_keys_api)

### Rotating IAM user access keys \(console\)<a name="rotating_access_keys_console"></a>

You can rotate access keys from the AWS Management Console\.

**To rotate access keys for an IAM user without interrupting your applications \(console\)**

1. While the first access key is still active, create a second access key\.

   1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

   1. In the navigation pane, choose **Users**\.

   1. Choose the name of the intended user, and then choose the **Security credentials** tab\.

   1. Choose **Create access key** and then choose **Download \.csv file** to save the access key ID and secret access key to a `.csv` file on your computer\. Store the file in a secure location\. You will not have access to the secret access key again after this closes\. After you have downloaded the `.csv` file, choose **Close**\.

      The new access key is active by default\. At this point, the user has two active access keys\.

1. Update all applications and tools to use the new access key\.

1. <a name="id_credentials_access-keys-key-still-in-use"></a>Determine whether the first access key is still in use by reviewing the **Last used** column for the oldest access key\. One approach is to wait several days and then check the old access key for any use before proceeding\.

1. Even if the **Last used** column value indicates that the old key has never been used, we recommend that you do not immediately delete the first access key\. Instead, choose **Make inactive** to deactivate the first access key\.

1. Use only the new access key to confirm that your applications are working\. Any applications and tools that still use the original access key will stop working at this point because they no longer have access to AWS resources\. If you find such an application or tool, you can choose **Make active** to reenable the first access key\. Then return to [Step 3](#id_credentials_access-keys-key-still-in-use) and update this application to use the new key\.

1. After you wait some period of time to ensure that all applications and tools have been updated, you can delete the first access key:

   1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

   1. In the navigation pane, choose **Users**\.

   1. Choose the name of the intended user, and then choose the **Security credentials** tab\.

   1. Locate the access key to delete and choose its **X** button at the far right of the row\. Then choose **Delete** to confirm\.

**To determine when access keys need rotating \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. If necessary, add the **Access key age** column to the users table by completing the following steps:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage columns**, select **Access key age**\.

   1. Choose **Close** to return to the list of users\.

1. The **Access key age** column shows the number of days since the oldest active access key was created\. You can use this information to find users with access keys that need rotating\. The column displays **None** for users with no access key\.

### Rotating access keys \(AWS CLI\)<a name="rotating_access_keys_cli"></a>

You can rotate access keys from the AWS Command Line Interface\.

**To rotate access keys without interrupting your applications \(AWS CLI\)**

1. While the first access key is still active, create a second access key, which is active by default\. Run the following command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html](https://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html)

     At this point, the user has two active access keys\.

1. <a name="step-update-apps"></a>Update all applications and tools to use the new access key\.

1. <a name="step-determine-use"></a>Determine whether the first access key is still in use by using this command:
   +  [https://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html)

   One approach is to wait several days and then check the old access key for any use before proceeding\.

1. Even if step [Step 3](#step-determine-use) indicates no use of the old key, we recommend that you do not immediately delete the first access key\. Instead, change the state of the first access key to `Inactive` using this command:
   +  [https://docs.aws.amazon.com/cli/latest/reference/iam/update-access-key.html](https://docs.aws.amazon.com/cli/latest/reference/iam/update-access-key.html)

1. Use only the new access key to confirm that your applications are working\. Any applications and tools that still use the original access key will stop working at this point because they no longer have access to AWS resources\. If you find such an application or tool, you can switch its state back to `Active` to reenable the first access key\. Then return to step [Step 2](#step-update-apps) and update this application to use the new key\.

1. After you wait some period of time to ensure that all applications and tools have been updated, you can delete the first access key with this command:
   + [https://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html)

For more information, see the following:
+  [How to Rotate Access Keys for IAM Users](http://aws.amazon.com/blogs/security/how-to-rotate-access-keys-for-iam-users/)\. This entry on the *AWS Security Blog* provides more information on key rotation\. 
+ [Security best practices in IAM](best-practices.md)\. This page provides general recommendations for helping to secure your AWS resources\.

### Rotating access keys \(AWS API\)<a name="rotating_access_keys_api"></a>

You can rotate access keys using the AWS API\.

**To rotate access keys without interrupting your applications \(AWS API\)**

1. While the first access key is still active, create a second access key, which is active by default\. Call the following operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html)

     At this point, the user has two active access keys\.

1. <a name="step-update-apps-2"></a>Update all applications and tools to use the new access key\.

1. <a name="step-determine-use-2"></a>Determine whether the first access key is still in use by calling this operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html)

   One approach is to wait several days and then check the old access key for any use before proceeding\.

1. Even if step [Step 3](#step-determine-use-2) indicates no use of the old key, we recommend that you do not immediately delete the first access key\. Instead, change the state of the first access key to `Inactive` calling this operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html)

1. Use only the new access key to confirm that your applications are working\. Any applications and tools that still use the original access key will stop working at this point because they no longer have access to AWS resources\. If you find such an application or tool, you can switch its state back to `Active` to reenable the first access key\. Then return to step [Step 2](#step-update-apps-2) and update this application to use the new key\.

1. After you wait some period of time to ensure that all applications and tools have been updated, you can delete the first access key calling this operation:
   + [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html)

For more information, see the following:
+  [How to Rotate Access Keys for IAM Users](http://aws.amazon.com/blogs/security/how-to-rotate-access-keys-for-iam-users/)\. This entry on the *AWS Security Blog* provides more information on key rotation\. 
+ [Security best practices in IAM](best-practices.md)\. This page provides general recommendations for helping to secure your AWS resources\.

## Auditing access keys<a name="Using_access-keys-audit"></a>

You can review the AWS access keys in your code to determine whether the keys are from an account that you own\. You can pass an access key ID using the [https://docs.aws.amazon.com/cli/latest/reference/sts/get-access-key-info.html](https://docs.aws.amazon.com/cli/latest/reference/sts/get-access-key-info.html) AWS CLI command or the [https://docs.aws.amazon.com/STS/latest/APIReference/API_GetAccessKeyInfo.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetAccessKeyInfo.html) AWS API operation\.

The AWS CLI and AWS API operations return the ID of the AWS account to which the access key belongs\. Access key IDs beginning with `AKIA` are long\-term credentials for an IAM user or an AWS account root user\. Access key IDs beginning with `ASIA` are temporary credentials that are created using AWS STS operations\. If the account in the response belongs to you, you can sign in as the root user and review your root user access keys\. Then, you can pull a [credentials report](id_credentials_getting-report.md) to learn which IAM user owns the keys\. To learn who requested the temporary credentials for an `ASIA` access key, view the AWS STS events in your CloudTrail logs\.

For security purposes, you can [review AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) to learn who used the temporary credentials to perform an action in AWS\. You can use the `aws:RoleSessionName` condition key in the role trust policy to require users to specify a session name when they assume a role\. For example, you can require that IAM users specify their own user name as their session name\. For more information, see `aws:RoleSessionName`\.

This operation does not indicate the state of the access key\. The key might be active, inactive, or deleted\. Active keys might not have permissions to perform an operation\. Providing a deleted access key might return an error that the key doesn't exist\.