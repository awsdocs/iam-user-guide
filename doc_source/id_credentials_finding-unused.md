# Finding unused credentials<a name="id_credentials_finding-unused"></a>

To increase the security of your AWS account, remove IAM user credentials \(that is, passwords and access keys\) that are not needed\. For example, when users leave your organization or no longer need AWS access, find the credentials that they were using and ensure that they are no longer operational\. Ideally, you delete credentials if they are no longer needed\. You can always recreate them at a later date if the need arises\. At the very least, you should change the password or deactivate the access keys so that the former users no longer have access\.

Of course, the definition of *unused* can vary and usually means a credential that has not been used within a specified period of time\.

## Finding unused passwords<a name="finding-unused-passwords"></a>

You can use the AWS Management Console to view password usage information for your users\. If you have a large number of users, you can use the console to download a credential report with information about when each user last used their console password\. You can also access the information from the AWS CLI or the IAM API\.

**To find unused passwords \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users**\.

1. If necessary, add the **Console last sign\-in** column to the users table:

   1. Above the table on the far right, choose the settings icon \(![\[Settings icon\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-settings-icon.console.png)\)\.

   1. In **Manage Columns**, select **Console last sign\-in**\.

   1. Choose **Close** to return to the list of users\.

1. The **Console last sign\-in** column shows the number of days since the user last signed in to AWS through the console\. You can use this information to find users with passwords who have not signed in for more than a specified period of time\. The column displays **Never** for users with passwords that have never signed in\. **None** indicates users with no passwords\. Passwords that have not been used recently might be good candidates for removal\.
**Important**  
Due to a service issue, password last used data does not include password use from May 3rd 2018 22:50 PDT to May 23rd 2018 14:08 PDT\. This affects [last sign\-in](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_finding-unused.html) dates shown in the IAM console and password last used dates in the [IAM credential report](https://docs.aws.amazon.com/IAM/latest/UserGuide/SupportedTypes.xmlid_credentials_getting-report.html), and returned by the [GetUser API operation](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html)\. If users signed in during the affected time, the password last used date that is returned is the date the user last signed in before May 3rd 2018\. For users that signed in after May 23rd 2018 14:08 PDT, the returned password last used date is accurate\.  
If you use password last used information to identify unused credentials for deletion, such as deleting users who did not sign in to AWS in the last 90 days, we recommend that you adjust your evaluation window to include dates after May 23rd 2018\. Alternatively, if your users use access keys to access AWS programmatically you can refer to access key last used information because it is accurate for all dates\. 

**To find unused passwords by downloading the credentials report \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Credential report**\.

1. Choose **Download Report** to download a comma\-separated value \(CSV\) file named `status_reports_<date>T<time>.csv`\. The fifth column contains the `password_last_used` column with the dates or one of the following:
   + **N/A** – Users that do not have a password assigned at all\.
   + **no\_information** – Users that have not used their password since IAM began tracking password age on October 20, 2014\.

**To find unused passwords \(AWS CLI\)**  
Run the following command to find unused passwords:
+ `[aws iam list\-users](https://docs.aws.amazon.com/cli/latest/reference/iam/list-users.html)` returns a list of users, each with a `PasswordLastUsed` value\. If the value is missing, then the user either has no password or the password has not been used since IAM began tracking password age on October 20, 2014\.

**To find unused passwords \(AWS API\)**  
Call the following operation to find unused passwords:
+  ` [ListUsers](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUsers.html)` returns a collection of users, each of which has a `<PasswordLastUsed>` value\. If the value is missing, then the user either has no password or the password has not been used since IAM began tracking password age on October 20, 2014\.

For information about the commands to download the credentials report, see [Getting credential reports \(AWS CLI\)](id_credentials_getting-report.md#getting-credential-reports-cliapi)\.

## Finding unused access keys<a name="finding-unused-access-keys"></a>

You can use the AWS Management Console to view access key usage information for your users\. If you have a large number of users, you can use the console to download a credentials report to find when each user last used their access keys\. You can also access the information from the AWS CLI or the IAM API\.

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

1. Choose **Download Report** to download a comma\-separated value \(CSV\) file named `status_reports_<date>T<time>.csv`\. Columns 11 through 13 contain the last used date, Region, and service information for access key 1\. Columns 16 through 18 contain the same information for access key 2\. The value is **N/A** if the user does not have an access key or the user has not used the access key since IAM began tracking access key age on April 22, 2015\.

**To find unused access keys \(AWS CLI\)**  
Run the following commands to find unused access keys:
+ `[aws iam list\-access\-keys](https://docs.aws.amazon.com/cli/latest/reference/iam/list-access-keys.html)` returns information about the access keys for a user, including the `AccessKeyID`\.
+ `[aws iam get\-access\-key\-last\-used](https://docs.aws.amazon.com/cli/latest/reference/iam/get-access-key-last-used.html)` takes an access key ID and returns output that includes the `LastUsedDate`, the `Region` in which the access key was last used, and the `ServiceName` of the last service requested\. If `LastUsedDate` is missing, then the access key has not been used since IAM began tracking access key age on April 22, 2015\.

**To find unused access keys \(AWS API\)**  
Call the following operations to find unused access keys:
+ `[ListAccessKeys](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccessKeys.html)` returns a list of `AccessKeyID` values for access keys that are associated with the specified user\. 
+ `[GetAccessKeyLastUsed](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccessKeyLastUsed.html)` takes an access key ID and returns a collection of values\. Included are the `LastUsedDate`, the `Region` in which the access key was last used, and the `ServiceName` of the last service requested\. If the value is missing, then either the user has no access key or the access key has not been used since IAM began tracking access key age on April 22, 2015\.

For information about the commands to download the credentials report, see [Getting credential reports \(AWS CLI\)](id_credentials_getting-report.md#getting-credential-reports-cliapi)\.