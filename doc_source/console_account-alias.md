# Your AWS Account ID and Its Alias<a name="console_account-alias"></a>

## Finding Your AWS Account ID<a name="FindingYourAWSId"></a>

To find your AWS account ID number on the AWS Management Console, choose **Support** on the navigation bar on the upper\-right, and then choose **Support Center**\. Your currently signed\-in account ID appears in the upper\-right corner below the **Support** menu\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/account-id-support-center.console.png)

## About Account Aliases<a name="AboutAccountAlias"></a>

If you want the URL for your sign\-in page to contain your company name \(or other friendly identifier\) instead of your AWS account ID, you can create an alias for your AWS account ID\. This section provides information about AWS account aliases and lists the API actions you use to create an alias\.

Your sign\-in page URL has the following format, by default\.

```
https://Your_AWS_Account_ID.signin.aws.amazon.com/console/
```

If you create an AWS account alias for your AWS account ID, your sign\-in page URL will look like the following example\. 

```
https://Your_Alias.signin.aws.amazon.com/console/
```

**Note**  
The original URL containing your AWS account ID remains active and can be used after you create your AWS account alias\.

**Tip**  
To create a bookmark for your account sign\-in page in your web browser, you should manually type the sign\-in URL in the bookmark entry\. Don't use your web browser's "bookmark this page" feature\. 

## Creating, Deleting, and Listing an AWS Account Alias<a name="CreateAccountAlias"></a>

You can use the AWS Management Console, the IAM API, or the command line interface to create or delete your AWS account alias\.

**Important**  
Your AWS account can have only one alias\. If you create a new alias for your AWS account, the new alias overwrites the old alias, and the URL containing the old alias stops working\.

### AWS Management Console<a name="CreateAlias_Console"></a>

**To create or remove an account alias**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. On the navigation pane, select **Dashboard**\.

1. Find the **IAM users sign\-in link**, and click **Customize** to the right of the link\.

1. Type the name you want to use for your alias, then click **Yes, Create**\.

1. To remove the alias, click **Customize**, and then click **Yes, Delete**\. The sign\-in URL reverts to using your AWS account ID\.

### API or CLI<a name="CreateAlias_APICLI"></a>

To create an alias for your AWS Management Console sign\-in page URL
+ AWS CLI: `[aws iam create\-account\-alias](http://docs.aws.amazon.com/cli/latest/reference/iam/create-account-alias.html)`
+ Tools for Windows PowerShell: `[New\-IAMAccountAlias](http://docs.aws.amazon.com//powershell/latest/reference/Index.html?page=New-IAMAccountAlias.html&tocid=New-IAMAccountAlias)`
+ AWS API: `[CreateAccountAlias](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccountAlias.html)` 

To delete an AWS account ID alias
+ AWS CLI:`[aws iam delete\-account\-alias](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-account-alias.html)`
+ Tools for Windows PowerShell: `[Remove\-IAMAccountAlias](http://docs.aws.amazon.com//powershell/latest/reference/Index.html?page=Remove-IAMAccountAlias.html&tocid=Remove-IAMAccountAlias)`
+ AWS API: `[DeleteAccountAlias](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccountAlias.html)` 

To display your AWS account ID alias
+ AWS CLI: `[aws iam list\-account\-aliases](http://docs.aws.amazon.com/cli/latest/reference/iam/list-account-aliases.html)`
+ Tools for Windows PowerShell: `[Get\-IAMAccountAlias\.html](http://docs.aws.amazon.com//powershell/latest/reference/Index.html?page=Get-IAMAccountAlias.html&tocid=Get-IAMAccountAlias)`
+ AWS API: `[ListAccountAliases](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccountAliases.html)` 

**Note**  
The account alias must be unique across all Amazon Web Services products\. It must contain only digits, lowercase letters, and hyphens\. For more information on limitations on AWS account entities, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\. 