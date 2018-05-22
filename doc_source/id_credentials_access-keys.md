# Managing Access Keys for IAM Users<a name="id_credentials_access-keys"></a>

**Note**  
If you found this topic because you are trying to configure the Product Advertising API to sell Amazon products on your website, see these topics:  
[Getting Started with the Product Advertising API](http://docs.aws.amazon.com/AWSECommerceService/latest/GSG/GettingStarted.html)
[Getting Started as a Product Advertising API Developer](http://docs.aws.amazon.com/AWSECommerceService/latest/DG/CHAP_GettingStarted.html)

Users need their own access keys to make programmatic calls to AWS from the [AWS Command Line Interface](https://aws.amazon.com/cli/) \(AWS CLI\), [Tools for Windows PowerShell](https://aws.amazon.com/documentation/powershell), the [AWS SDKs](https://aws.amazon.com/tools/), or direct HTTP calls using the API operations for individual AWS services\. To fill this need, you can create, modify, view, or rotate access keys \(access key IDs and secret access keys\) for IAM users\.

When you create an access key, IAM returns the access key ID and secret access key\. You should save these in a secure location and give them to the user\. 

**Important**  
To ensure the security of your AWS account, the secret access key is accessible only at the time you create it\. If a secret access key is lost, you must delete the access key for the associated user and create a new key\. For more details, see [Resetting Your Lost or Forgotten Passwords or Access Keys](id_credentials_access-keys_retrieve.md)\.

By default, when you create an access key, its status is `Active`, which means the user can use the access key for AWS CLI, Tools for Windows PowerShell, and API calls\. Each user can have two active access keys, which is useful when you must rotate the user's access keys\. You can disable a user's access key, which means it can't be used for API calls\. You might do this while you're rotating keys or to revoke API access for a user\. 

You can delete an access key at any time\. However, when you delete an access key, it's gone forever and cannot be retrieved\. \(You can always create new keys\.\)

You can give your users permission to list, rotate, and manage their own keys\. For more information, see [Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys](id_credentials_delegate-permissions_examples.md#creds-policies-credentials)\. 

For more information about the credentials used with AWS and IAM, see [Temporary Security Credentials](id_credentials_temp.md), and [Types of Security Credentials](http://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html) in the *Amazon Web Services General Reference*\.

**Topics**
+ [Creating, Modifying, and Viewing Access Keys \(Console\)](#Using_CreateAccessKey)
+ [Creating, Modifying, and Viewing Access Keys \(API, CLI, PowerShell\)](#Using_CreateAccessKey_CLIAPI)
+ [Rotating Access Keys](#Using_RotateAccessKey)

## Creating, Modifying, and Viewing Access Keys \(Console\)<a name="Using_CreateAccessKey"></a>

You can use the AWS Management Console to manage the access keys of IAM users\.

**To list the access key IDs for multiple users**

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

**To find which user owns a specific access key**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. In the search box, type or paste the access key ID of the user you want to find\.

1. If necessary, add the **Access key ID** column to the users table by completing the following steps:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage columns**, select **Access key ID**\.

   1. Choose **Close** to return to the list of users and confirm that the filtered user owns the specified access key\.

**To list a user's access keys**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the intended user, and then choose the **Security credentials** tab\. The user's access keys and the status of each key is displayed\.
**Note**  
Only the user's access key ID is visible\. The secret access key can only be retrieved when the key is created\.

**To create, modify, or delete a user's access keys**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. Choose the name of the preferred user, and then choose the **Security credentials** tab\. 

1. If needed, expand the **Access keys** section and do any of the following:
   + To create an access key, choose **Create access key**\. Then choose **Download \.csv file** to save the access key ID and secret access key to a CSV file on your computer\. Store the file in a secure location\. You will not have access to the secret access key again after this dialog box closes\. After you have downloaded the CSV file, choose **Close**\.
   + To disable an active access key, choose **Make inactive**\.
   + To reenable an inactive access key, choose **Make active**\.
   + To delete an access key, choose its **X** button at the far right of the row\. Then choose **Delete** to confirm\.

## Creating, Modifying, and Viewing Access Keys \(API, CLI, PowerShell\)<a name="Using_CreateAccessKey_CLIAPI"></a>

To manage a user's access keys from the AWS CLI, Tools for Windows PowerShell, or the AWS API, use the following commands:

### To create an access key<a name="w3ab1c19c19c29c23b5"></a>
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMAccessKey.html&tocid=New-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMAccessKey.html&tocid=New-IAMAccessKey)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html)

### To disable or reenable an access key<a name="w3ab1c19c19c29c23b7"></a>
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/update-access-key.html](http://docs.aws.amazon.com/cli/latest/reference/iam/update-access-key.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMAccessKey.html&tocid=Update-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMAccessKey.html&tocid=Update-IAMAccessKey)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html)

### To list a user's access keys<a name="w3ab1c19c19c29c23b9"></a>
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/list-access-keys.html](http://docs.aws.amazon.com/cli/latest/reference/iam/list-access-keys.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccessKey.html&tocid=Get-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccessKey.html&tocid=Get-IAMAccessKey)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccessKeys.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccessKeys.html)

### To determine when an access key was most recently used<a name="w3ab1c19c19c29c23c11"></a>
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html](http://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccessKeyLastUsed.html&tocid=Get-IAMAccessKeyLastUsed](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccessKeyLastUsed.html&tocid=Get-IAMAccessKeyLastUsed)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html)

### To delete an access key<a name="w3ab1c19c19c29c23c13"></a>
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html)
+ Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccessKey.html&tocid=Remove-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccessKey.html&tocid=Remove-IAMAccessKey)
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html)

## Rotating Access Keys<a name="Using_RotateAccessKey"></a>

As a security best practice, we recommend that you, an administrator, regularly rotate \(change\) the access keys for IAM users in your account\. If your users have the necessary permissions, they can rotate their own access keys\. For information about how to give your users permissions to rotate their own access keys, see [Allow Users to Manage Their Own Passwords, Access Keys, and SSH Keys](id_credentials_delegate-permissions_examples.md#creds-policies-credentials)\.

You can also apply a password policy to your account to require that all of your IAM users periodically rotate their passwords\. You can choose how often they must do so\. For more information, see [Setting an Account Password Policy for IAM Users](id_credentials_passwords_account-policy.md)\. 

**Important**  
If you use the AWS account root user credentials, we recommend that you also regularly rotate them\. The account password policy does not apply to the root user credentials\. IAM users cannot manage credentials for the AWS account root user, so you must use the root user credentials \(not a user's\) to change the root user credentials\. Note that we recommend against using the root user for everyday work in AWS\. 

**To determine when access keys needs rotating \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. If necessary, add the **Access key age** column to the users table by completing the following steps:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage columns**, select **Access key age**\.

   1. Choose **Close** to return to the list of users\.

1. The **Access key age** column shows the number of days since the oldest active access key was created\. You can use this information to find users with access keys that need rotating\. The column displays **None** for users with no access key\.

**To rotate access keys without interrupting your applications \(console\)**

The following steps describe the general process for rotating an access key without interrupting your applications\. These steps show the AWS CLI, Tools for Windows PowerShell and AWS API commands for rotating access keys\. You can also perform these tasks using the console; for details, see [Creating, Modifying, and Viewing Access Keys \(Console\)](#Using_CreateAccessKey), in a preceding section\.

1. While the first access key is still active, create a second access key, which is active by default\. At this point, the user has two active access keys\.

   1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

   1. In the navigation pane, choose **Users**\.

   1. Choose the name of the intended user, and then choose the **Security credentials** tab\.

   1. Choose **Create access key** and then choose **Download \.csv file** to save the access key ID and secret access key to a `.csv` file on your computer\. Store the file in a secure location\. You will not have access to the secret access key again after this closes\. After you have downloaded the `.csv` file, choose **Close**\.

1. Update all applications and tools to use the new access key\.

1. <a name="id_credentials_access-keys-key-still-in-use"></a>Determine whether the first access key is still in use by reviewing the **Last used** column for the oldest access key\. One approach is to wait several days and then check the old access key for any use before proceeding\.

1. Even if the **Last used** column value indicates that the old key has never been used, we recommend that you do not immediately delete the first access key\. Instead, choose **Make inactive** to deactivate the first access key\.

1. Use only the new access key to confirm that your applications are working\. Any applications and tools that still use the original access key will stop working at this point because they no longer have access to AWS resources\. If you find such an application or tool, you can choose **Make active** to reenable the first access key\. Then return to [Step 3](#id_credentials_access-keys-key-still-in-use) and update this application to use the new key\.

1. After you wait some period of time to ensure that all applications and tools have been updated, you can delete the first access key:

   1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

   1. In the navigation pane, choose **Users**\.

   1. Choose the name of the intended user, and then choose the **Security credentials** tab\.

   1. Locate the access key to delete and choose its **X** button at the far right of the row\. Then choose **Delete** to confirm\.

**To rotate access keys without interrupting your applications \(API, AWS CLI, PowerShell\)**

1. While the first access key is still active, create a second access key, which is active by default\. At this point, the user has two active access keys\.
   + AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-access-key.html)
   + Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMAccessKey.html&tocid=New-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMAccessKey.html&tocid=New-IAMAccessKey)
   + AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccessKey.html)

1. <a name="step-update-apps"></a>Update all applications and tools to use the new access key\.

1. <a name="step-determine-use"></a>Determine whether the first access key is still in use:
   + AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html](http://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html)
   + Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccessKeyLastUsed.html&tocid=Get-IAMAccessKeyLastUsed](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccessKeyLastUsed.html&tocid=Get-IAMAccessKeyLastUsed)
   + AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html)

   One approach is to wait several days and then check the old access key for any use before proceeding\.

1. Even if step [Step 3](#step-determine-use) indicates no use of the old key, we recommend that you do not immediately delete the first access key\. Instead, change the state of the first access key to `Inactive`\.
   + AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/update-access-key.html](http://docs.aws.amazon.com/cli/latest/reference/iam/update-access-key.html)
   + Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMAccessKey.html&tocid=Update-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMAccessKey.html&tocid=Update-IAMAccessKey)
   + AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateAccessKey.html)

1. Use only the new access key to confirm that your applications are working\. Any applications and tools that still use the original access key will stop working at this point because they no longer have access to AWS resources\. If you find such an application or tool, you can switch its state back to `Active` to reenable the first access key\. Then return to step [Step 2](#step-update-apps) and update this application to use the new key\.

1. After you wait some period of time to ensure that all applications and tools have been updated, you can delete the first access key\.
   + AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-access-key.html)
   + Tools for Windows PowerShell: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccessKey.html&tocid=Remove-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMAccessKey.html&tocid=Remove-IAMAccessKey)
   + AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccessKey.html)

For more information, see the following:
+  [How to Rotate Access Keys for IAM Users](http://aws.amazon.com/blogs/security/how-to-rotate-access-keys-for-iam-users/)\. This entry on the *AWS Security Blog* provides more information on key rotation\. 
+ [IAM Best Practices](best-practices.md)\. This page provides general recommendations for helping to secure your AWS resources\.