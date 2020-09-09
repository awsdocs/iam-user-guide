# How IAM users sign in to your AWS account<a name="getting-started_how-users-sign-in"></a>

After you create IAM users \(with passwords\), those users can sign in to the AWS Management Console\. To sign in, they need your account ID or alias\. They can also sign in from a custom URL that includes your account ID\. 

**Note**  
If your company has an existing identity system, you might want to create a single sign\-on \(SSO\) option\. SSO gives users access to the AWS Management Console without requiring them to have an IAM user identity\. SSO also eliminates the need for users to sign in to your organization's site and to AWS separately\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\. 

Before you create a sign\-in URL for your account, you create an account alias so that the URL includes your account name instead of an account ID\. For more information, see [Your AWS account ID and its alias](console_account-alias.md)\. 

You can find the sign\-in URL for an account on the IAM console dashboard\.

![\[IAM dashboard, sign-in URL\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccountAlias.console.png)

To create a sign\-in URL for your IAM users, use the following pattern:

```
https://account-ID-or-alias.signin.aws.amazon.com/console
```

IAM users can also sign in at the following endpoint and enter the account ID or alias manually, instead of using your custom URL:

```
https://signin.aws.amazon.com/console
```

## Permissions required for console activities<a name="console_signin-permissions-required"></a>

IAM users in your account have access only to the AWS resources that you specify in a policy\. That policy must be attached to the user or to an IAM group that the user belongs to\. To work in the console, users must have permissions to perform the actions that the console performs, such as listing and creating AWS resources\. For more information, see [Access management for AWS resources](access.md) and [Example IAM identity\-based policies](access_policies_examples.md)\.

If users in your account need programmatic access, you can create an access key pair \(an access key ID and a secret access key\) for each user\. For more information, see [Managing access keys \(console\)](id_credentials_access-keys.md#Using_CreateAccessKey)\.

## Logging sign\-in details in CloudTrail<a name="console_signin-cloudtrail"></a>

If you enable CloudTrail to log sign\-in events, you must understand how CloudTrail logs the events\. CloudTrail includes global and Regions log entries\. Where a sign\-in event is logged in CloudTrail depends on how your users sign in\. For details, see [Logging IAM Events with CloudTrail](https://docs.aws.amazon.com/IAM/latest/UserGuide/cloudtrail-integration.html)\.