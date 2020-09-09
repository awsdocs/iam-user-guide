# Your AWS account ID and its alias<a name="console_account-alias"></a>

To sign in to an AWS account as an IAM user, you must have an account alias or an account ID for the AWS account\. If you are signed in to the AWS Management Console or have configured the AWS CLI or an AWS SDK with your account credentials, you can find the account alias or account ID for the AWS account\. If you cannot sign in, ask your administrator for the information that you need to sign in\.

**Topics**
+ [Finding your AWS account ID](#FindingYourAWSId)
+ [About account aliases](#AboutAccountAlias)
+ [Creating, deleting, and listing an AWS account alias](#CreateAccountAlias)

## Finding your AWS account ID<a name="FindingYourAWSId"></a>

You can find the account ID for your AWS account using the following methods\.

### Finding Your Account ID using the console<a name="FindId_Console"></a>

 In the navigation bar at the upper right, choose your user name and then choose **My Security Credentials**\. The account number appears either under **Account identifiers** \(if you are the root user\) or under **Account details** \(if you are an IAM user\)\.

### Finding Your Account ID using the AWS CLI<a name="FindId_CLI"></a>

Use the following command to view your user ID, account ID, and your user ARN:
+ [aws sts get\-caller\-identity](https://docs.aws.amazon.com/cli/latest/reference/sts/get-caller-identity.html)

### Finding Your Account ID using the API<a name="FindId_API"></a>

Use the following API to view your user ID, account ID, and your user ARN:
+ [GetCallerIdentity](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetCallerIdentity.html) 

## About account aliases<a name="AboutAccountAlias"></a>

If you want the URL for your sign\-in page to contain your company name \(or other friendly identifier\) instead of your AWS account ID, you can create an account alias\. This section provides information about AWS account aliases and lists the API operations that you use to create an alias\.

Your sign\-in page URL has the following format, by default\.

```
https://Your_Account_ID.signin.aws.amazon.com/console/
```

If you create an AWS account alias for your AWS account ID, your sign\-in page URL looks like the following example\.

```
https://Your_Account_Alias.signin.aws.amazon.com/console/
```

The original URL containing your AWS account ID remains active and can be used after you create your AWS account alias\.

**Tip**  
To create a bookmark for your account sign\-in page in your web browser, you should manually type the sign\-in URL in the bookmark entry\. Don't use your web browser's "bookmark this page" feature\.

## Creating, deleting, and listing an AWS account alias<a name="CreateAccountAlias"></a>

You can use the AWS Management Console, the IAM API, or the command line interface to create or delete your AWS account alias\.

**Considerations**
+ Your AWS account can have only one alias\. If you create a new alias for your AWS account, the new alias overwrites the previous alias, and the URL containing the previous alias stops working\.
+ The account alias must be unique across all Amazon Web Services products\. It must contain only digits, lowercase letters, and hyphens\. For more information on limitations on AWS account entities, see [IAM and STS quotas](reference_iam-quotas.md)\.

### Creating and deleting aliases \(console\)<a name="CreateAlias_Console"></a>

You can create and delete an account alias from the AWS Management Console\.

**To create or remove an account alias \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Dashboard**\.

1. Find the **IAM users sign\-in link**, and choose **Customize** to the right of the link\.

1. Type the name you want to use for your alias, then choose **Yes, Create**\.

1. To remove the alias, choose **Customize**, and then choose **Yes, Delete**\. The sign\-in URL reverts to using your AWS account ID\.

### Creating, deleting, and listing aliases \(AWS CLI\)<a name="CreateAlias_APICLI"></a>

To create an alias for your AWS Management Console sign\-in page URL, run the following command:
+ `[aws iam create\-account\-alias](https://docs.aws.amazon.com/cli/latest/reference/iam/create-account-alias.html)`

To delete an AWS account ID alias, run the following command:
+ `[aws iam delete\-account\-alias](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-account-alias.html)`

To display your AWS account ID alias, run the following command: 
+ `[aws iam list\-account\-aliases](https://docs.aws.amazon.com/cli/latest/reference/iam/list-account-aliases.html)`

### Creating, deleting, and listing aliases \(AWS API\)<a name="CreateAlias_API"></a>

To create an alias for your AWS Management Console sign\-in page URL, call the following operation:
+ `[CreateAccountAlias](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateAccountAlias.html)` 

To delete an AWS account ID alias, call the following operation:
+ `[DeleteAccountAlias](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteAccountAlias.html)` 

To display your AWS account ID alias, call the following operation:
+ `[ListAccountAliases](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListAccountAliases.html)` 