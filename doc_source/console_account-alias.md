# Your AWS Account ID and Its Alias<a name="console_account-alias"></a>

An account alias substitutes for an account ID in the web address for your account\. You can create and manage an account alias from the AWS Management Console, AWS CLI, or AWS API\.

**Topics**
+ [Finding Your AWS Account ID](#FindingYourAWSId)
+ [About Account Aliases](#AboutAccountAlias)
+ [Creating, Deleting, and Listing an AWS Account Alias](#CreateAccountAlias)

## Finding Your AWS Account ID<a name="FindingYourAWSId"></a>

To find your AWS account ID number on the AWS Management Console, choose **Support** on the navigation bar on the upper\-right, and then choose **Support Center**\. Your currently signed\-in account ID appears in the upper\-right corner below the **Support** menu\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/account-id-support-center.console.png)

## About Account Aliases<a name="AboutAccountAlias"></a>

If you want the URL for your sign\-in page to contain your company name \(or other friendly identifier\) instead of your AWS account ID, you can create an account alias\. This section provides information about AWS account aliases and lists the API operations that you use to create an alias\.

Your sign\-in page URL has the following format, by default\.

```
https://Your_AWS_Account_ID.signin.aws.amazon.com/console/
```

If you create an AWS account alias for your AWS account ID, your sign\-in page URL looks like the following example\. 

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
Your AWS account can have only one alias\. If you create a new alias for your AWS account, the new alias overwrites the previous alias, and the URL containing the previous alias stops working\.
The account alias must be unique across all Amazon Web Services products\. It must contain only digits, lowercase letters, and hyphens\. For more information on limitations on AWS account entities, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.

### Creating and Deleting Aliases \(Console\)<a name="CreateAlias_Console"></a>

You can create and delete an account alias from the AWS Management Console\.

**To create or remove an account alias \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Dashboard**\.

1. Find the **IAM users sign\-in link**, and choose **Customize** to the right of the link\.

1. Type the name you want to use for your alias, then choose **Yes, Create**\.

1. To remove the alias, choose **Customize**, and then choose **Yes, Delete**\. The sign\-in URL reverts to using your AWS account ID\.

### Creating, Deleting, and Listing Aliases \(AWS CLI\)<a name="CreateAlias_APICLI"></a>

To create an alias for your AWS Management Console sign\-in page URL, run the following command:
+ `[aws iam create\-account\-alias](http://docs.aws.amazon.com/cli/latest/reference/iam/create-account-alias.html)`

To delete an AWS account ID alias, run the following command:
+ `[aws iam delete\-account\-alias](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-account-alias.html)`

To display your AWS account ID alias, run the following command: 
+ `[aws iam list\-account\-aliases](http://docs.aws.amazon.com/cli/latest/reference/iam/list-account-aliases.html)`

### Creating, Deleting, and Listing Aliases \(AWS API\)<a name="CreateAlias_API"></a>

To create an alias for your AWS Management Console sign\-in page URL, call the following operation:
+ `[CreateAccountAlias](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccountAlias.html)` 

To delete an AWS account ID alias, call the following operation:
+ `[DeleteAccountAlias](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccountAlias.html)` 

To display your AWS account ID alias, call the following operation:
+ `[ListAccountAliases](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccountAliases.html)` 