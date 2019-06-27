# Logging IAM and AWS STS API Calls with AWS CloudTrail<a name="cloudtrail-integration"></a>

IAM and AWS STS are integrated with AWS CloudTrail, a service that provides a record of actions taken by an IAM user or role\. CloudTrail captures all API calls for IAM and AWS STS as events, including calls from the console and from API calls\. If you create a trail, you can enable continuous delivery of CloudTrail events to an Amazon S3 bucket\. If you don't configure a trail, you can still view the most recent events in the CloudTrail console in **Event history**\. You can use CloudTrail to get information about the request that was made to IAM or AWS STS\. For example, you can view the IP address from which the request was made, who made the request, when it was made, and additional details\. 

To learn more about CloudTrail, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

**Topics**
+ [IAM and AWS STS Information in CloudTrail](#iam-info-in-cloudtrail)
+ [Examples of Logged Events in CloudTrail Files](#cloudtrail-integration-understanding-records)
+ [Preventing Duplicate Log Entries in CloudTrail](#cloudtrail-integration-global-service)

## IAM and AWS STS Information in CloudTrail<a name="iam-info-in-cloudtrail"></a>

CloudTrail is enabled on your AWS account when you create the account\. When activity occurs in IAM or AWS STS, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your AWS account\. For more information, see [Viewing Events with CloudTrail Event History](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)\. 

For an ongoing record of events in your AWS account, including events for IAM and AWS STS, create a trail\. A trail enables CloudTrail to deliver log files to an Amazon S3 bucket\. By default, when you create a trail in the console, the trail applies to all Regions\. The trail logs events from all Regions in the AWS partition and delivers the log files to the Amazon S3 bucket that you specify\. Additionally, you can configure other AWS services to further analyze and act upon the event data collected in CloudTrail logs\. For more information, see: 
+ [Overview for Creating a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)
+ [CloudTrail Supported Services and Integrations](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations)
+ [Configuring Amazon SNS Notifications for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)
+ [Receiving CloudTrail Log Files from Multiple Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)

All IAM and AWS STS actions are logged by CloudTrail and are documented in the [IAM API Reference](https://docs.aws.amazon.com/IAM/latest/APIReference/API_Operations.html) and the [AWS Security Token Service API Reference](https://docs.aws.amazon.com/STS/latest/APIReference/API_Operations.html)\. IAM information is available to CloudTrail in the following ways: 
+ **API requests to IAM and AWS Security Token Service \(AWS STS\)** – CloudTrail logs all authenticated API requests \(made with credentials\) to IAM and AWS STS API operations\. CloudTrail also logs nonauthenticated requests to the AWS STS actions, `AssumeRoleWithSAML` and `AssumeRoleWithWebIdentity`, and logs information provided by the identity provider\. You can use this information to map calls made by a federated user with an assumed role back to the originating external federated caller\. In the case of `AssumeRole`, you can map calls back to the originating AWS service or to the account of the originating user\. The `userIdentity` section of the JSON data in the CloudTrail log entry contains the information that you need to map the AssumeRole\* request with a specific federated user\. For more information, see [CloudTrail userIdentity Element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html) in the *AWS CloudTrail User Guide*\.

  For example, calls to the IAM `CreateUser`, `DeleteRole`, `ListGroups`, and other API operations are all logged by CloudTrail\. 

  Examples for this type of log entry are presented later in this topic\. 
**Important**  
If you activate AWS STS endpoints in Regions other than the default global endpoint, then you must also turn on CloudTrail logging in those Regions\. This is necessary to record any AWS STS API calls that are made in those Regions\. For more information, see [Turning On CloudTrail in Additional Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/aggregating_logs_regions_turn_on_ct.html) in the AWS CloudTrail User Guide\.
+ **API requests to other AWS services** – Authenticated requests to other AWS service API operations are logged by CloudTrail, and these log entries contain information about who generated the request\. 

  For example, assume that you made a request to list Amazon EC2 instances or create an CodeDeploy deployment group\. Details about the person or service that made the request are contained in the log entry for that request\. This information helps you determine whether the request was made by the AWS account root user, an IAM user, a role, or another AWS service\. 

  For more details about the user identity information in CloudTrail log entries, see [userIdentity Element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/event_reference_user_identity.html) in the *AWS CloudTrail User Guide*\. 
+ **AWS sign\-in events** – Sign\-in events to the AWS Management Console, the AWS Discussion Forums, and the AWS Marketplace are logged by CloudTrail\. 

  For example, IAM and federated user sign\-in events—successful sign\-ins and failed sign\-in attempts—are logged by CloudTrail\. Additionally, successful sign\-in events by the root user are logged by CloudTrail\. Note that unsuccessful sign\-in events by the root user are *not *logged by CloudTrail\.

  If you enable CloudTrail to log sign\-in events to your logs, you need to be aware of how CloudTrail chooses where to log the events\.
  + If your users sign in directly to a console, they are redirected to either a global or a Regional sign\-in endpoint, based on whether the selected service console supports Regions\. For example, the main console home page supports Regions, so if you sign in to https://alias\.signin\.aws\.amazon\.com/console, you are redirected to a Regional sign\-in endpoint such as https://us\-east\-2\.signin\.aws\.amazon\.com\. This redirection creates a Regional CloudTrail log entry in the user's region's log:

    On the other hand, the Amazon S3 console does not support Regions, so if you sign in to https://alias\.signin\.aws\.amazon\.com/console/s3, AWS redirects you to the global sign\-in endpoint at https://signin\.aws\.amazon\.com\. This redirection creates a global CloudTrail log entry\.
  + You can manually request a certain Regional sign\-in endpoint by signing in to the Region\-enabled main console home page using a URL like https://alias\.signin\.aws\.amazon\.com/console?region=ap\-southeast\-1\. In this case, AWS redirects you to the `ap-southeast-1` Regional sign\-in endpoint and results in a Regional CloudTrail log event\.
**Important**  
As a security best practice, AWS does not log the entered user name text when the sign\-in failure is caused by *an incorrect user name*\. The user name text is masked by the value `HIDDEN_DUE_TO_SECURITY_REASONS`\. For an example of this, see [Sign\-in Failure Event Caused by Incorrect User Name](#hiddensecurity), later in this topic\. The reason the user name is obscured is because such failures might be caused by user errors like the following, which, if logged, could expose potentially sensitive information:  
You accidentally type your password in the user name box\.
You choose the link for one AWS account's sign\-in page, but then type the account number for a different one\.
You forget which account you are signing in to and accidentally type the account name of your personal email account, your bank sign\-in identifier, or some other private ID\. 

  Whether the sign\-in event is considered Regional or global depends on the console the user signs into and how the user constructs the sign\-in URL\.
  + Is the service console Regionalized? If so, then the sign\-in request is automatically redirected to a Regional sign\-in endpoint and the event is logged in that Region's CloudTrail log\. For example, if you sign in to https://*alias*\.signin\.aws\.amazon\.com/console, which is Regionalized, you are automatically redirected to a sign\-in endpoint in your Region, such as https://us\-east\-2\.signin\.aws\.amazon\.com\. The event is logged in that Region's log\.

    However, some services are not Regionalized yet\. For example, the Amazon S3 service is *not* currently Regionalized, so if you sign in to https://*alias*\.signin\.aws\.amazon\.com/console/s3, you are redirected to the global sign\-in endpoint at https://signin\.aws\.amazon\.com\. This redirection creates an event in your global log\.
  + You can also manually request a certain Regional sign\-in endpoint by using a URL like https://*alias*\.signin\.aws\.amazon\.com/console?region=ap\-southeast\-1, which redirects to the ap\-southeast\-1 Regional sign\-in endpoint\. This redirection results in an event in the Regional log\.
+ **How temporary credential requests are logged** – When a principal requests temporary credentials, the principal type determines how CloudTrail logs the event\. The following table shows how CloudTrail logs different information for each of the API calls that generate temporary credentials\.  
****    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/cloudtrail-integration.html)

## Examples of Logged Events in CloudTrail Files<a name="cloudtrail-integration-understanding-records"></a>

CloudTrail log files contain events that are formatted using JSON\. An event represents a single API request or sign\-in event and includes information about the requested action, any parameters, and the date and time of the action\. 

### IAM API Event in CloudTrail Log File<a name="cloudtrail-integration-iam-api-events"></a>

The following example shows a CloudTrail log entry for a request made for the IAM `GetUserPolicy` action\. 

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDACKCEVSQ6C2EXAMPLE",
    "arn": "arn:aws:iam::444455556666:user/Alice",
    "accountId": "444455556666",
    "accessKeyId": "AKIAI44QH8DHBEXAMPLE",
    "userName": "Alice",
    "sessionContext": {
      "attributes": {
        "mfaAuthenticated": "false",
        "creationDate": "2014-07-15T21:39:40Z"
      }
    },
    "invokedBy": "signin.amazonaws.com"
  },
  "eventTime": "2014-07-15T21:40:14Z",
  "eventSource": "iam.amazonaws.com",
  "eventName": "GetUserPolicy",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "signin.amazonaws.com",
  "userAgent": "signin.amazonaws.com",
  "requestParameters": {
    "userName": "Alice",
    "policyName": "ReadOnlyAccess-Alice-201407151307"
  },
  "responseElements": null,
  "requestID": "9EXAMPLE-0c68-11e4-a24e-d5e16EXAMPLE",
  "eventID": "cEXAMPLE-127e-4632-980d-505a4EXAMPLE"
}
```

From this event information, you can determine that the request was made to get a user policy named `ReadOnlyAccess-Alice-201407151307` for user `Alice`, as specified in the `requestParameters` element\. You can also see that the request was made by an IAM user named `Alice` on July 15, 2014 at 9:40 PM \(UTC\)\. In this case, the request originated in the AWS Management Console, as you can tell from the `userAgent` element\. 

### AWS STS API Event in CloudTrail Log File<a name="stscloudtrailexample"></a>

The IAM user named "Bob" in account 777788889999 calls the AWS STS `AssumeRole` action to assume the role `EC2-dev` in account 111122223333\. The next two examples show the CloudTrail log entries for the two affected accounts\. The first example shows the CloudTrail log entry for the request made in account 777788889999, the account that owns the user who calls `AssumeRole`\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDAQRSTUVWXYZEXAMPLE",
    "arn": "arn:aws:iam::777788889999:user/Bob",
    "accountId": "777788889999",
    "accessKeyId": "AKIAQRSTUVWXYZEXAMPLE",
    "userName": "Bob"
  },
  "eventTime": "2014-07-18T15:07:39Z",
  "eventSource": "sts.amazonaws.com",
  "eventName": "AssumeRole",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.101",
  "userAgent": "aws-cli/1.11.10 Python/2.7.8 Linux/3.2.45-0.6.wd.865.49.315.metal1.x86_64 botocore/1.4.67",
  "requestParameters": {
    "roleArn": "arn:aws:iam::111122223333:role/EC2-dev",
    "roleSessionName": "Bob-EC2-dev"
    "serialNumber": "arn:aws:iam::777788889999:mfa"
  },
  "responseElements": {
    "credentials": {
      "sessionToken": "<encoded session token blob>",
      "accessKeyId": "AKIAQRSTUVWXYZEXAMPLE",
      "expiration": "Jul 18, 2014 4:07:39 PM"
      },
    "assumedRoleUser": {
      "assumedRoleId": "AIDAQRSTUVWXYZEXAMPLE:Bob-EC2-dev",
      "arn": "arn:aws:sts::111122223333:assumed-role/EC2-dev/Bob-EC2-dev"
    }
  },
  "resources": [
    {
      "ARN": "arn:aws:iam::111122223333:role/EC2-dev",
      "accountId": "111122223333",
      "type": "AWS::IAM::Role"
    }
  ],
  "requestID": "4EXAMPLE-0e8d-11e4-96e4-e55c0EXAMPLE",
  "sharedEventID": "bEXAMPLE-efea-4a70-b951-19a88EXAMPLE",
  "eventID": "dEXAMPLE-ac7f-466c-a608-4ac8dEXAMPLE"
  "eventType": "AwsApiCall",   
  "recipientAccountId": "111122223333"
}
```

The second example shows the role owning account's \(111122223333\) CloudTrail log entry for the same request\.

```
{ 
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "AWSAccount",
    "principalId": "AIDAQRSTUVWXYZEXAMPLE",
    "accountId": "777788889999"
  },
  "eventTime": "2014-07-18T15:07:39Z",
  "eventSource": "sts.amazonaws.com",
  "eventName": "AssumeRole",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.101",
  "userAgent": "aws-cli/1.11.10 Python/2.7.8 Linux/3.2.45-0.6.wd.865.49.315.metal1.x86_64 botocore/1.4.67",
  "requestParameters": {   
    "roleArn": "arn:aws:iam:: 111122223333:role/EC2-dev",
    "roleSessionName": "Bob-EC2-dev",
    "serialNumber": "arn:aws:iam::777788889999:mfa"
  }, 
  "responseElements": {
    "credentials": {
      "sessionToken": "<encoded session token blob>",     
      "accessKeyId": "AKIAQRSTUVWXYZEXAMPLE",     
      "expiration": "Jul 18, 2014 4:07:39 PM"     
    },   
    "assumedRoleUser": {     
      "assumedRoleId": "AIDAQRSTUVWXYZEXAMPLE:Bob-EC2-dev",     
      "arn": "arn:aws:sts::111122223333:assumed-role/EC2-dev/Bob-EC2-dev"   
    } 
  }, 
  "requestID": "4EXAMPLE-0e8d-11e4-96e4-e55c0EXAMPLE",
  "sharedEventID": "bEXAMPLE-efea-4a70-b951-19a88EXAMPLE",
  "eventID": "dEXAMPLE-ac7f-466c-a608-4ac8dEXAMPLE"
}
```

The following example shows a CloudTrail log entry for a request made by an AWS service calling an API using permissions from an IAM role\.

```
{
  "eventVersion": "1.04",
  "userIdentity": {
    "type": "AssumedRole",
    "principalId": "AIDAQRSTUVWXYZEXAMPLE:devdsk",
    "arn": "arn:aws:sts::777788889999:assumed-role/AssumeNothing/devdsk",
    "accountId": "777788889999",
    "accessKeyId": "AKIAQRSTUVWXYZEXAMPLE",
    "sessionContext": {
      "attributes": {
        "mfaAuthenticated": "false",
        "creationDate": "2016-11-14T17:25:26Z"
      },
      "sessionIssuer": {
        "type": "Role",
        "principalId": "AIDAQRSTUVWXYZEXAMPLE",
        "arn": "arn:aws:iam::777788889999:role/AssumeNothing",
        "accountId": "777788889999",
        "userName": "AssumeNothing"
      }
    }
  },
  "eventTime": "2016-11-14T17:25:45Z",
  "eventSource": "s3.amazonaws.com",
  "eventName": "DeleteBucket",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.1",
  "userAgent": "[aws-cli/1.11.10 Python/2.7.8 Linux/3.2.45-0.6.wd.865.49.315.metal1.x86_64 botocore/1.4.67]",
  "requestParameters": {
    "bucketName": "my-test-bucket-cross-account"
  },
  "responseElements": null,
  "requestID": "EXAMPLE463D56D4C",
  "eventID": "dEXAMPLE-265a-41e0-9352-4401bEXAMPLE",
  "eventType": "AwsApiCall",
  "recipientAccountId": "777788889999"
}
```

The following example shows a CloudTrail log entry for a request made for the AWS STS `AssumeRoleWithSAML` action\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "SAMLUser",
    "principalId": "<id of identity provider>:<canonical id of user>",
    "userName": "<canonical id of user>",
    "identityProvider": "<id of identity provider>"
  },
  "eventTime": "2016-03-23T01:39:57Z",
  "eventSource": "sts.amazonaws.com",
  "eventName": "AssumeRoleWithSAML",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.101",
  "userAgent": "aws-cli/1.3.23 Python/2.7.6 Linux/2.6.18-164.el5",
  "requestParameters": {
    "sAMLAssertionID": "_c0046cEXAMPLEb9d4b8eEXAMPLE2619aEXAMPLE",
    "roleSessionName": "MyAssignedRoleSessionName",
    "durationSeconds": 3600,
    "roleArn": "arn:aws:iam::444455556666:role/SAMLTestRoleShibboleth",
    "principalArn": "arn:aws:iam::444455556666:saml-provider/Shibboleth"
  },
  "responseElements": {
    "subjectType": "transient",
    "issuer": "https://server.example.com/idp/shibboleth",
    "credentials": {
      "accessKeyId": "AKIAIOSFODNN7EXAMPLE",
      "expiration": "Mar 23, 2016 2:39:57 AM",
      "sessionToken": "<encoded session token blob>"
    },
    "nameQualifier": "<id of identity provider>",
    "assumedRoleUser": {
      "assumedRoleId": "AROAD35QRSTUVWEXAMPLE:MyAssignedRoleSessionName",
      "arn": "arn:aws:sts::444455556666:assumed-role/SAMLTestRoleShibboleth/MyAssignedRoleSessionName"
    },
    "subject": "<canonical id of user>",
    "audience": "https://signin.aws.amazon.com/saml"
  },
  "resources": [  
    { 
      "ARN": "arn:aws:iam::444455556666:role/SAMLTestRoleShibboleth",   
      "accountId": "444455556666",
      "type": "AWS::IAM::Role" 
    },
    {
      "ARN": "arn:aws:iam::444455556666:saml-provider/test-saml-provider",   
      "accountId": "444455556666",
      "type": "AWS::IAM::SAMLProvider" 
    }
  ],
  "requestID": "6EXAMPLE-e595-11e5-b2c7-c974fEXAMPLE",
  "eventID": "dEXAMPLE-265a-41e0-9352-4401bEXAMPLE",
  "eventType": "AwsApiCall",
  "recipientAccountId": "444455556666"
}
```

The following example shows a CloudTrail log entry for a request made for the AWS STS `AssumeRoleWithWebIdentity` action\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "WebIdentityUser",
    "principalId": "accounts.google.com:<id-of-application>.apps.googleusercontent.com:<id-of-user>",
    "userName": "<id of user>",
    "identityProvider": "accounts.google.com"
  },
  "eventTime": "2016-03-23T01:39:51Z",
  "eventSource": "sts.amazonaws.com",
  "eventName": "AssumeRoleWithWebIdentity",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.101",
  "userAgent": "aws-cli/1.3.23 Python/2.7.6 Linux/2.6.18-164.el5",
  "requestParameters": {
    "durationSeconds": 3600,
    "roleArn": "arn:aws:iam::444455556666:role/FederatedWebIdentityRole",
    "roleSessionName": "MyAssignedRoleSessionName"
  },
  "responseElements": {
    "provider": "accounts.google.com",
    "subjectFromWebIdentityToken": "<id of user>",
    "audience": "<id of application>.apps.googleusercontent.com",
    "credentials": {
      "accessKeyId": "ASIACQRSTUVWRAOEXAMPLE",
      "expiration": "Mar 23, 2016 2:39:51 AM",
      "sessionToken": "<encoded session token blob>"
    },
    "assumedRoleUser": {
      "assumedRoleId": "AROACQRSTUVWRAOEXAMPLE:MyAssignedRoleSessionName",
      "arn": "arn:aws:sts::444455556666:assumed-role/FederatedWebIdentityRole/MyAssignedRoleSessionName"
    }
  },
  "resources": [
    {
      "ARN": "arn:aws:iam::444455556666:role/FederatedWebIdentityRole",
      "accountId": "444455556666",
      "type": "AWS::IAM::Role" 
    }
  ],
  "requestID": "6EXAMPLE-e595-11e5-b2c7-c974fEXAMPLE",
  "eventID": "bEXAMPLE-0b30-4246-b28c-e3da3EXAMPLE",
  "eventType": "AwsApiCall",
  "recipientAccountId": "444455556666"
}
```

### Sign\-in Failure Event in CloudTrail Log File<a name="cloudtrail-integration-signin-failure"></a>

The following example shows a CloudTrail log entry for a failed sign\-in event\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDACKCEVSQ6C2EXAMPLE",
    "arn":"arn:aws:iam::111122223333:user/Alice",
    "accountId": "111122223333",
    "userName": "Alice"
  },
  "eventTime": "2014-07-08T17:35:27Z",
  "eventSource": "signin.amazonaws.com",
  "eventName": "ConsoleLogin",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.100",
  "userAgent": "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:24.0) Gecko/20100101 Firefox/24.0",
  "errorMessage": "Failed authentication",
  "requestParameters": null,
  "responseElements": {
    "ConsoleLogin": "Failure"
  },
  "additionalEventData": {
    "MobileVersion": "No",
    "LoginTo": "https://console.aws.amazon.com/sns",
    "MFAUsed": "No"
  },
  "eventID": "11ea990b-4678-4bcd-8fbe-62509088b7cf"
}
```

From this information, you can determine that the sign\-in attempt was made by an IAM user named Alice, as shown in the `userIdentity` element\. You can also see that the sign\-in attempt failed, as shown in the `responseElements` element\. You can see that Alice tried to sign in to the Amazon SNS console at 5:35 PM \(UTC\) on July 8, 2014\.

### Sign\-in Failure Event Caused by Incorrect User Name<a name="hiddensecurity"></a>

The following example shows a CloudTrail log entry for an unsuccessful sign\-in event caused by the user entering an incorrect user name\. AWS masks the `userName` text with `HIDDEN_DUE_TO_SECURITY_REASONS` to help prevent exposing potentially sensitive information\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "accountId": "123456789012",
    "accessKeyId": "",
    "userName": "HIDDEN_DUE_TO_SECURITY_REASONS"
  },
  "eventTime": "2015-03-31T22:20:42Z",
  "eventSource": "signin.amazonaws.com",
  "eventName": "ConsoleLogin",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.101",
  "userAgent": "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:24.0) Gecko/20100101 Firefox/24.0",
  "errorMessage": "No username found in supplied account",
  "requestParameters": null,
  "responseElements": {
    "ConsoleLogin": "Failure"
  },
  "additionalEventData": {
    "LoginTo": "https://console.aws.amazon.com/console/home?state=hashArgs%23&isauthcode=true",
    "MobileVersion": "No",
    "MFAUsed": "No"
  },
  "eventID": "a7654656-0417-45c6-9386-ea8231385051",
  "eventType": "AwsConsoleSignin",
  "recipientAccountId": "123456789012"
}
```

### Sign\-in Success Event in CloudTrail Log File<a name="cloudtrail-integration-signin-success"></a>

The following example shows a CloudTrail log entry for a successful sign\-in event\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDACKCEVSQ6C2EXAMPLE",
    "arn":"arn:aws:iam::111122223333:user/Bob",
    "accountId": "111122223333",
    "userName": "Bob"
  },
  "eventTime": "2014-07-16T15:49:27Z",
  "eventSource": "signin.amazonaws.com",
  "eventName": "ConsoleLogin",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.110",
  "userAgent": "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:24.0) Gecko/20100101 Firefox/24.0",
  "requestParameters": null,
  "responseElements": {
    "ConsoleLogin": "Success"
  },
  "additionalEventData": {
    "MobileVersion": "No",
    "LoginTo": "[https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)",
    "MFAUsed": "No"
  },
  "eventID": "3fcfb182-98f8-4744-bd45-10a395ab61cb"
}
```

For more details about the information contained in CloudTrail log files, see [CloudTrail Event Reference](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/eventreference.html) in the *AWS CloudTrail User Guide*\.

## Preventing Duplicate Log Entries in CloudTrail<a name="cloudtrail-integration-global-service"></a>

CloudTrail creates trails in each Region separately\. These trails include information for events that occur in those Regions, plus global \(non\-Region\-specific\) events such as IAM API calls, non\-Region specific AWS STS calls \(calls to `sts.amazonaws.com`\), and AWS sign\-in events\. For example, assume that you have two trails, each in a different Region\. If you then create a new IAM user, the `CreateUser` event is added to the log files in both Regions, creating a duplicate log entry\. 

AWS Security Token Service \(STS\) is a global service with a single endpoint at https://sts\.amazonaws\.com\. Calls to this endpoint are logged as calls to a global service\. However, because this endpoint is physically located in the US East \(N\. Virginia\) Region, your logs list us\-east\-1 as the event Region\. CloudTrail does not write these logs to the US East \(Ohio\) Region unless you choose to include global service logs in that Region\. CloudTrail writes calls to all Regional endpoints to their respective Regions\. For example, calls to `sts.us-east-2.amazonaws.com` are published to the US East \(Ohio\) Region, calls to `sts.eu-central-1.amazonaws.com` are published to the EU \(Frankfurt\) Region, etc\. 

For more information about multiple Regions and AWS STS, see [Managing AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\. 

The following table lists the Regions and how CloudTrail logs AWS STS requests in each Region\. The "Location" column indicates which logs CloudTrail writes to\. "Global" means that the event is logged in any Region for which you choose to include global service logs in that Region\. "Region" means that the event is logged only in the Region where the endpoint is located\. The last column indicates how the request's Region is identified in the log entry\.


****  

| Region name | Region identity in CloudTrail log | Endpoint | Location of CloudTrail logs | 
| --- | --- | --- | --- | 
| n/a \- global | us\-east\-1 | sts\.amazonaws\.com | Global | 
| US East \(Ohio\) | us\-east\-2 | sts\.us\-east\-2\.amazonaws\.com | Region | 
| US East \(N\. Virginia\) | us\-east\-1 | sts\.us\-east\-1\.amazonaws\.com | Region | 
| US West \(N\. California\) | us\-west\-1 | sts\.us\-west\-1\.amazonaws\.com | Region | 
| US West \(Oregon\) | us\-west\-2 | sts\.us\-west\-2\.amazonaws\.com | Region | 
| Canada \(Central\) | ca\-central\-1 | sts\.ca\-central\-1\.amazonaws\.com | Region | 
| EU \(Frankfurt\) | eu\-central\-1 | sts\.eu\-central\-1\.amazonaws\.com | Region | 
| EU \(Ireland\) | eu\-west\-1 | sts\.eu\-west\-1\.amazonaws\.com | Region | 
| EU \(London\) | eu\-west\-2 | sts\.eu\-west\-2\.amazonaws\.com | Region | 
| Asia Pacific \(Tokyo\) | ap\-northeast\-1 | sts\.ap\-northeast\-1\.amazonaws\.com | Region | 
| Asia Pacific \(Seoul\) | ap\-northeast\-2 | sts\.ap\-northeast\-2\.amazonaws\.com | Region | 
| Asia Pacific \(Mumbai\) | ap\-south\-1 | sts\.ap\-south\-1\.amazonaws\.com | Region | 
| Asia Pacific \(Singapore\) | ap\-southeast\-1 | sts\.ap\-southeast\-1\.amazonaws\.com | Region | 
| Asia Pacific \(Sydney\) | ap\-southeast\-2 | sts\.ap\-southeast\-2\.amazonaws\.com | Region | 
| South America \(São Paulo\) | sa\-east\-1 | sts\.sa\-east\-1\.amazonaws\.com | Region | 

When you configure CloudTrail to aggregate trail information from multiple Regions in your account into a single Amazon S3 bucket, IAM events are duplicated in the logs\. In other words, the trail for each Region writes the same IAM event to the aggregated log\. To prevent this duplication, you can include global events selectively\. A typical approach is to enable global events in one trail and to disable global events in all other trails that write to the same Amazon S3 bucket\. That way only one set of global events is written\.

For more information, see [Aggregating Logs](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/aggregatinglogs.html) in the *AWS CloudTrail User Guide*\. 