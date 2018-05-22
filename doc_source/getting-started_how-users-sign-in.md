# How Users Sign In to Your Account<a name="getting-started_how-users-sign-in"></a>

After you create IAM users \(with passwords\), those users can sign in to the AWS Management Console using your account ID or alias, or from a custom URL that includes your account ID\. 

**Note**  
If your company has an existing identity system, you might want to create a single sign\-on \(SSO\) option\. SSO gives users access to the AWS Management Console without requiring them to have an IAM user identity\. SSO also eliminates the need for users to sign in to your organization's site and to AWS separately\. For more information, see [Creating a URL that Enables Federated Users to Access the AWS Management Console \(Custom Federation Broker\)](id_roles_providers_enable-console-custom-url.md)\. 

Before you create a sign\-in URL for your account, you create an account alias so that the URL includes your account name instead of an account ID\. For more information, see [Your AWS Account ID and Its Alias](console_account-alias.md)\. 

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

## Permissions Required for Console Activities<a name="console_signin-permissions-required"></a>

IAM users in your account have access only to the AWS resources that you specify in the policy that is attached to the user or to an IAM group that the user belongs to\. To work in the console, users must have permissions to perform the actions that the console performs, such as listing and creating AWS resources\. For more information, see [Access Management](access.md) and [Example Policies](access_policies_examples.md)\.

## Logging Sign\-In Details in CloudTrail<a name="console_signin-cloudtrail"></a>

If you enable CloudTrail to log sign\-in events to your logs, you need to be aware of how CloudTrail chooses where to log the events\.
+ If your users sign\-in directly to a console, they are redirected to either a global or a regional sign\-in endpoint, based on whether the selected service console supports regions\. For example, the main console home page supports regions, so if you sign in to the following URL:

  ```
  https://alias.signin.aws.amazon.com/console
  ```

  you are redirected to a ''default" regional sign\-in endpoint `https://us-east-1.signin.aws.amazon.com`, resulting in a regional CloudTrail log entry in that region's log:

  On the other hand, the Amazon S3 console does not support regions, so if you sign in to the following URL

  ```
  https://alias.signin.aws.amazon.com/console/s3
  ```

  AWS redirects you to the global sign\-in endpoint at `https://signin.aws.amazon.com`, resulting in a global CloudTrail log entry\.
+ You can manually request a certain regional sign\-in endpoint by signing in to the region\-enabled main console home page using a URL syntax like the following:

  ```
  https://alias.signin.aws.amazon.com/console?region=ap-southeast-1
  ```

  AWS redirects you to the `ap-southeast-1` regional sign\-in endpoint and results in a CloudTrail log event in that region\.

For more information about CloudTrail and IAM, see [Logging IAM Events with AWS CloudTrail ](http://docs.aws.amazon.com/IAM/latest/UserGuide/cloudtrail-integration.html)\.

If users need programmatic access to work with your account, you can create an access key pair \(an access key ID and a secret access key\) for each user, as described in [Creating, Modifying, and Viewing Access Keys \(Console\)](id_credentials_access-keys.md#Using_CreateAccessKey)\.