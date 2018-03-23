# Finding Unused Credentials<a name="id_credentials_finding-unused"></a>

To increase the security of your AWS account, remove IAM user credentials \(that is, passwords and access keys\) that are not needed\. For example, when users leave your organization or no longer need AWS access, find the credentials that they were using and ensure that they are no longer operational\. Ideally, you delete credentials if they are no longer needed\. You can always recreate them at a later date if the need arises\. At the very least you should change the password or deactivate the access keys so that the former users no longer have access\.

Of course, the definition of *unused* can vary and usually means a credential that has not been used within a specified period of time\.

## Finding Unused Passwords<a name="finding-unused-passwords"></a>

You can use the AWS Management Console to view password usage information for your users\. If you have a large number of users, you can use the console to download a credential report with information about when each user last used their console password\. You can also access the information from the AWS CLI, Tools for Windows PowerShell, or the IAM API\.

**To find unused passwords \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. If necessary, add the **Console last sign\-in** column to the users table:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage Columns**, select **Console last sign\-in**\.

   1. Choose **Close** to return to the list of users\.

1. The **Console last sign\-in** column shows the number of days since the user last signed in to AWS through the console\. You can use this information to find users with passwords who have not signed in for more than a specified period of time\. The column displays **Never** for users with passwords that have never signed in\. **None** indicates users with no passwords\. Passwords that have not been used recently might be good candidates for removal\.

**To find unused passwords by downloading the credentials report \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Credential report**\.

1. Choose **Download Report** to download a comma\-separated value \(CSV\) file named `status_reports_<date>T<time>.csv`\. The fifth column contains the `password_last_used` column with the dates or one of the following:
   + **N/A** – Users that do not have a password assigned at all\.
   + **no\_information** – Users that have not used their password since IAM began tracking password age on October 20, 2014\.

**To find unused passwords \(API, CLI, PowerShell\)**  
You can use the following commands to find unused passwords:
+ **AWS CLI** –`[aws iam list\-users](http://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html)` returns a list of users, each with a `PasswordLastUsed` value\. If the value is missing, then the user either has no password or the password has not been used since IAM began tracking password age on October 20, 2014\.

   
+ **Tools for Windows PowerShell** – `[Get\-IAMUsers](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMUsers.html&tocid=Get-IAMUsers)` returns a collection of `User` objects, each of which has a `PasswordLastUsed` property\. If the property value is `1/1/0001 12:00:00 AM`, then the user either has no password or the password has not been used since IAM began tracking password age on October 20, 2014\.

   
+ **IAM API** –` [ListUsers](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html)` returns a collection of users, each of which has a `<PasswordLastUsed>` value\. If the value is missing, then the user either has no password or the password has not been used since IAM began tracking password age on October 20, 2014\.

  For information about the commands to download the credentials report, see [Getting Credential Reports \(AWS CLI, Tools for Windows PowerShell, or IAM API\)](id_credentials_getting-report.md#getting-credential-reports-cliapi)\.

## Finding Unused Access Keys<a name="finding-unused-access-keys"></a>

You can use the AWS Management Console to view access key usage information for your users\. If you have a large number of users, you can use the console to download a credentials report to find when each user last used their access keys\. You can also access the information from the AWS CLI, Tools for Windows PowerShell, or the IAM API\.

**To find unused access keys \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. If necessary, add the **Access key last used** column to the users table:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage Columns**, select **Access key last used**\.

   1. Choose **Close** to return to the list of users\.

1. The **Access key last used** column shows the number of days since the user last accessed AWS programmatically\. You can use this information to find users with access keys that have not been used for more than a specified period of time\. The column displays **None** for users with no access keys\. Access keys that have not been used recently might be good candidates for removal\.

**To find unused access keys by downloading the credentials report \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Credential Report**\.

1. Choose **Download Report** to download a comma\-separated value \(CSV\) file named `status_reports_<date>T<time>.csv`\. Columns 11 through 13 contain the last used date, region, and service information for access key 1\. Columns 16 through 18 contain the same information for access key 2\. The value is **N/A** if the user does not have an access key or the user has not used the access key since IAM began tracking access key age on April 22, 2015\.

**To find unused access keys \(API, CLI, PowerShell\)**  
You can use the following commands to find unused access keys:

**AWS CLI**  
+ `[aws iam list\-access\-keys](http://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html)` returns information about the access keys for a user, including the `AccessKeyID`\.
+ `[aws iam get\-access\-key\-last\-used](http://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html)` takes an access key ID and returns output that includes the `LastUsedDate`, the `Region` in which the access key was last used, and the `ServiceName` of the last service requested\. If the `LastUsedDate` field is missing, then the access key has not been used since IAM began tracking access key age on April 22, 2015\.

   

**Tools for Windows PowerShell**  
+ `[Get\-IAMAccessKey](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccessKey.html&tocid=Get-IAMAccessKey)` returns a collection of access key objects associated with the specified user\. Each object has an `AccessKeyId` property\.
+ `[Get\-IAMAccessKeyLastUsed](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMAccessKeyLastUsed.html&tocid=Get-IAMAccessKeyLastUsed)` takes an access key ID and returns an object with an `AccessKeyLastUsed` property object\. The methods of that object include the `LastUsedDate`, the `Region` in which the access key was last used, and the `ServiceName` of the last service requested\. If the property value is `1/1/0001 12:00:00 AM`, then the access key has not been used since IAM began tracking access key age on April 22, 2015\.

   

**IAM API**  
+ `[ListAccessKeys](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccessKeys.html)` returns a list of `AccessKeyID` values for access keys that are associated with the specified user\. 
+ `[GetAccessKeyLastUsed](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html)` takes an access key ID and returns a collection of values\. Included are the `LastUsedDate`, the `Region` in which the access key was last used, and the `ServiceName` of the last service requested\. If the value is missing, then user either has no access key or the access key has not been used since IAM began tracking access key age on April 22, 2015\.

For information about the commands to download the credentials report, see [Getting Credential Reports \(AWS CLI, Tools for Windows PowerShell, or IAM API\)](id_credentials_getting-report.md#getting-credential-reports-cliapi)