# How IAM users sign in to AWS<a name="id_users_sign-in"></a>

To sign in to the AWS Management Console as an IAM user, you must provide your account ID or account alias in addition to your user name and password\. When your administrator [created your IAM user in the console](id_users_create.md#id_users_create_console), they should have sent you your sign\-in credentials, including your user name and the URL to your account sign\-in page that includes your account ID or account alias\. 

```
https://My_AWS_Account_ID.signin.aws.amazon.com/console/
```

**Tip**  
To create a bookmark for your account sign\-in page in your web browser, you should manually type the sign\-in URL for your account in the bookmark entry\. Do not use your web browser bookmark feature because redirects can obscure the sign\-in URL\. 

You can also sign in at the following general sign\-in endpoint and type your account ID or account alias manually:

```
[https://console\.aws\.amazon\.com/](https://console.aws.amazon.com/)
```

For convenience, the AWS sign\-in page uses a browser cookie to remember the IAM user name and account information\. The next time the user goes to any page in the AWS Management Console, the console uses the cookie to redirect the user to the account sign\-in page\.

You have access only to the AWS resources that your administrator specifies in the policy that is attached to your IAM user identity\. To work in the console, you must have permissions to perform the actions that the console performs, such as listing and creating AWS resources\. For more information, see [Access management for AWS resources](access.md) and [Example IAM identity\-based policies](access_policies_examples.md)\.

**Note**  
If your organization has an existing identity system, you might want to create a single sign\-on \(SSO\) option\. SSO gives users access to the AWS Management Console for your account without requiring them to have an IAM user identity\. SSO also eliminates the need for users to sign in to your organization's site and to AWS separately\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\. 

**Logging sign\-in details in CloudTrail**  
If you enable CloudTrail to log sign\-in events to your logs, you need to be aware of how CloudTrail chooses where to log the events\.
+ If your users sign\-in directly to a console, they are redirected to either a global or a regional sign\-in endpoint, based on whether the selected service console supports regions\. For example, the main console home page supports regions, so if you sign in to the following URL:

  ```
  https://alias.signin.aws.amazon.com/console
  ```

  you are redirected to a regional sign\-in endpoint such as `https://us-east-2.signin.aws.amazon.com`, resulting in a regional CloudTrail log entry in the user's region's log:

  On the other hand, the Amazon S3 console does not support regions, so if you sign in to the following URL

  ```
  https://alias.signin.aws.amazon.com/console/s3
  ```

  AWS redirects you to the global sign\-in endpoint at `https://signin.aws.amazon.com`, resulting in a global CloudTrail log entry\.
+ You can manually request a certain regional sign\-in endpoint by signing in to the region\-enabled main console home page using a URL syntax like the following:

  ```
  https://alias.signin.aws.amazon.com/console?region=ap-southeast-1
  ```

  AWS redirects you to the `ap-southeast-1` regional sign\-in endpoint and results in a regional CloudTrail log event\.

For more information about CloudTrail and IAM, see [Logging IAM Events with AWS CloudTrail ](https://docs.aws.amazon.com/IAM/latest/UserGuide/cloudtrail-integration.html)\.

If users need programmatic access to work with your account, you can create an access key pair \(an access key ID and a secret access key\) for each user, as described in [Managing access keys \(console\)](id_credentials_access-keys.md#Using_CreateAccessKey)\.