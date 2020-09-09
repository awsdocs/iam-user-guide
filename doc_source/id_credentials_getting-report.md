# Getting credential reports for your AWS account<a name="id_credentials_getting-report"></a>

You can generate and download a *credential report* that lists all users in your account and the status of their various credentials, including passwords, access keys, and MFA devices\. You can get a credential report from the AWS Management Console, the [AWS SDKs](https://aws.amazon.com/tools) and [Command Line Tools](https://aws.amazon.com/tools/#Command_Line_Tools), or the IAM API\. 

You can use credential reports to assist in your auditing and compliance efforts\. You can use the report to audit the effects of credential lifecycle requirements, such as password and access key rotation\. You can provide the report to an external auditor, or grant permissions to an auditor so that he or she can download the report directly\.

You can generate a credential report as often as once every four hours\. When you request a report, IAM first checks whether a report for the AWS account has been generated within the past four hours\. If so, the most recent report is downloaded\. If the most recent report for the account is older than four hours, or if there are no previous reports for the account, IAM generates and downloads a new report\. 

**Topics**
+ [Required permissions](#id_credentials_required_permissions)
+ [Understanding the report format](#id_credentials_understanding_the_report_format)
+ [Getting credential reports \(console\)](#getting-credential-reports-console)
+ [Getting credential reports \(AWS CLI\)](#getting-credential-reports-cliapi)
+ [Getting credential reports \(AWS API\)](#getting-credential-reports-api)

## Required permissions<a name="id_credentials_required_permissions"></a>

The following permissions are needed to create and download reports:
+ To create a credential report: `GenerateCredentialReport` 
+ To download the report: `GetCredentialReport`

## Understanding the report format<a name="id_credentials_understanding_the_report_format"></a>

Credential reports are formatted as comma\-separated values \(CSV\) files\. You can open CSV files with common spreadsheet software to perform analysis, or you can build an application that consumes the CSV files programmatically and performs custom analysis\. 

The CSV file contains the following columns:

**user**  
The friendly name of the user\. 

**arn**  
The Amazon Resource Name \(ARN\) of the user\. For more information about ARNs, see [IAM ARNs](reference_identifiers.md#identifiers-arns)\. 

**user\_creation\_time**  
The date and time when the user was created, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601)\.

**password\_enabled**  
When the user has a password, this value is `TRUE`\. Otherwise it is `FALSE`\.The value for the AWS account root user is always `not_supported`\.

**password\_last\_used**  
The date and time when the AWS account root user or IAM user's password was last used to sign in to an AWS website, in [ISO 8601 date\-time format](http://www.iso.org/iso/iso8601)\. AWS websites that capture a user's last sign\-in time are the AWS Management Console, the AWS Discussion Forums, and the AWS Marketplace\. When a password is used more than once in a 5\-minute span, only the first use is recorded in this field\.   
+ The value in this field is `no_information` in these cases:
  + The user's password has never been used\.
  + There is no sign\-in data associated with the password, such as when user's password has not been used after IAM started tracking this information on October 20, 2014\.
+ The value in this field is `N/A` \(not applicable\) when the user does not have a password\.

**Important**  
Due to a service issue, password last used data does not include password use from May 3rd 2018 22:50 PDT to May 23rd 2018 14:08 PDT\. This affects [last sign\-in](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_finding-unused.html) dates shown in the IAM console and password last used dates in the [IAM credential report](https://docs.aws.amazon.com/IAM/latest/UserGuide/SupportedTypes.xmlid_credentials_getting-report.html), and returned by the [GetUser API operation](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html)\. If users signed in during the affected time, the password last used date that is returned is the date the user last signed in before May 3rd 2018\. For users that signed in after May 23rd 2018 14:08 PDT, the returned password last used date is accurate\.  
If you use password last used information to identify unused credentials for deletion, such as deleting users who did not sign in to AWS in the last 90 days, we recommend that you adjust your evaluation window to include dates after May 23rd 2018\. Alternatively, if your users use access keys to access AWS programmatically you can refer to access key last used information because it is accurate for all dates\. 

**password\_last\_changed**  
The date and time when the user's password was last set, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601)\. If the user does not have a password, the value in this field is `N/A` \(not applicable\)\. The value for the AWS account \(root\) is always `not_supported`\.

**password\_next\_rotation**  
When the account has a [password policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingPasswordPolicies.html) that requires password rotation, this field contains the date and time, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601), when the user is required to set a new password\. The value for the AWS account \(root\) is always `not_supported`\.

**mfa\_active**  
When a [multi\-factor authentication](id_credentials_mfa.md) \(MFA\) device has been enabled for the user, this value is `TRUE`\. Otherwise it is `FALSE`\.

**access\_key\_1\_active**  
When the user has an access key and the access key's status is `Active`, this value is `TRUE`\. Otherwise it is `FALSE`\.

**access\_key\_1\_last\_rotated**  
The date and time, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601), when the user's access key was created or last changed\. If the user does not have an active access key, the value in this field is `N/A` \(not applicable\)\.

**access\_key\_1\_last\_used\_date**  
The date and time, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601), when the user's access key was most recently used to sign an AWS API request\. When an access key is used more than once in a 15\-minute span, only the first use is recorded in this field\.   
The value in this field is `N/A` \(not applicable\) in these cases:  
+ The user does not have an access key\.
+ The access key has never been used\.
+ The access key has not been used after IAM started tracking this information on April 22, 2015\.

**access\_key\_1\_last\_used\_region**  
The [AWS Region](https://docs.aws.amazon.com/general/latest/gr/rande.html) in which the access key was most recently used\. When an access key is used more than once in a 15\-minute span, only the first use is recorded in this field\.   
The value in this field is `N/A` \(not applicable\) in these cases:  
+ The user does not have an access key\.
+ The access key has never been used\.
+ The access key was last used before IAM started tracking this information on April 22, 2015\.
+ The last used service is not Region\-specific, such as Amazon S3\.

**access\_key\_1\_last\_used\_service**  
The AWS service that was most recently accessed with the access key\. The value in this field uses the service's namespace—for example, `s3` for Amazon S3 and `ec2` for Amazon EC2\. When an access key is used more than once in a 15\-minute span, only the first use is recorded in this field\.   
The value in this field is `N/A` \(not applicable\) in these cases:  
+ The user does not have an access key\.
+ The access key has never been used\.
+ The access key was last used before IAM started tracking this information on April 22, 2015\.

**access\_key\_2\_active**  
When the user has a second access key and the second key's status is `Active`, this value is `TRUE`\. Otherwise it is `FALSE`\.  
Users can have up to two access keys, to make rotation easier\. For more information about rotating access keys, see [Rotating access keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.

**access\_key\_2\_last\_rotated**  
The date and time, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601), when the user's second access key was created or last changed\. If the user does not have a second active access key, the value in this field is `N/A` \(not applicable\)\.

**access\_key\_2\_last\_used\_date**  
The date and time, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601), when the user's second access key was most recently used to sign an AWS API request\. When an access key is used more than once in a 15\-minute span, only the first use is recorded in this field\.   
The value in this field is `N/A` \(not applicable\) in these cases:  
+ The user does not have a second access key\.
+ The user's second access key has never been used\.
+ The user's second access key was last used before IAM started tracking this information on April 22, 2015\.

**access\_key\_2\_last\_used\_region**  
The [AWS Region](https://docs.aws.amazon.com/general/latest/gr/rande.html) in which the user's second access key was most recently used\. When an access key is used more than once in a 15\-minute span, only the first use is recorded in this field\. The value in this field is `N/A` \(not applicable\) in these cases:  
+ The user does not have a second access key\.
+ The user's second access key has never been used\.
+ The user's second access key was last used before IAM started tracking this information on April 22, 2015\.
+ The last used service is not Region\-specific, such as Amazon S3\.

**access\_key\_2\_last\_used\_service**  
The AWS service that was most recently accessed with the user's second access key\. The value in this field uses the service's namespace—for example, `s3` for Amazon S3 and `ec2` for Amazon EC2\. When an access key is used more than once in a 15\-minute span, only the first use is recorded in this field\. The value in this field is `N/A` \(not applicable\) in these cases:  
+ The user does not have a second access key\.
+ The user's second access key has never been used\.
+ The user's second access key was last used before IAM started tracking this information on April 22, 2015\.

**cert\_1\_active**  
When the user has an X\.509 signing certificate and that certificate's status is `Active`, this value is `TRUE`\. Otherwise it is `FALSE`\.

**cert\_1\_last\_rotated**  
The date and time, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601), when the user's signing certificate was created or last changed\. If the user does not have an active signing certificate, the value in this field is `N/A` \(not applicable\)\.

**cert\_2\_active**  
When the user has a second X\.509 signing certificate and that certificate's status is `Active`, this value is `TRUE`\. Otherwise it is `FALSE`\.  
Users can have up to two X\.509 signing certificates, to make certificate rotation easier\.

**cert\_2\_last\_rotated**  
The date and time, in [ISO 8601 date\-time format](https://en.wikipedia.org/wiki/ISO_8601), when the user's second signing certificate was created or last changed\. If the user does not have a second active signing certificate, the value in this field is `N/A` \(not applicable\)\.

## Getting credential reports \(console\)<a name="getting-credential-reports-console"></a>

You can use the AWS Management Console to download a credential report as a comma\-separated values \(CSV\) file\.

**To download a credential report \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Credential report**\.

1. Choose **Download Report**\.

## Getting credential reports \(AWS CLI\)<a name="getting-credential-reports-cliapi"></a>

Run the following commands:
+ To generate a credential report: [https://docs.aws.amazon.com/cli/latest/reference/iam/generate-credential-report.html](https://docs.aws.amazon.com/cli/latest/reference/iam/generate-credential-report.html)
+ To retrieve a credential report: [https://docs.aws.amazon.com/cli/latest/reference/iam/get-credential-report.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-credential-report.html)

## Getting credential reports \(AWS API\)<a name="getting-credential-reports-api"></a>

Call the following operations:
+ To generate a credential report: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GenerateCredentialReport.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GenerateCredentialReport.html)
+ To retrieve a credential report: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetCredentialReport.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetCredentialReport.html)