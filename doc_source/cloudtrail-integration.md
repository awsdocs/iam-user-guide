# Logging IAM and AWS STS API calls with AWS CloudTrail<a name="cloudtrail-integration"></a>

IAM and AWS STS are integrated with AWS CloudTrail, a service that provides a record of actions taken by an IAM user or role\. CloudTrail captures all API calls for IAM and AWS STS as events, including calls from the console and from API calls\. If you create a trail, you can enable continuous delivery of CloudTrail events to an Amazon S3 bucket\. If you don't configure a trail, you can still view the most recent events in the CloudTrail console in **Event history**\. You can use CloudTrail to get information about the request that was made to IAM or AWS STS\. For example, you can view the IP address from which the request was made, who made the request, when it was made, and additional details\. 

To learn more about CloudTrail, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

**Topics**
+ [IAM and AWS STS information in CloudTrail](#iam-info-in-cloudtrail)
+ [Logging IAM and AWS STS API requests](#cloudtrail-integration_apis)
+ [Logging API requests to other AWS services](#cloudtrail-integration_api-other-services)
+ [Logging regional sign\-in events](#cloudtrail-integration_signin-regions)
+ [Logging user sign\-in events](#cloudtrail-integration_signin-users)
+ [Logging sign\-in events for temporary credentials](#cloudtrail-integration_signin-tempcreds)
+ [Example IAM API events in CloudTrail log](#cloudtrail-integration_examples-iam-api)
+ [Example AWS STS API events in CloudTrail log](#cloudtrail-integration_examples-sts-api)
+ [Example sign\-in events in CloudTrail log](#cloudtrail-integration_examples-signin)

## IAM and AWS STS information in CloudTrail<a name="iam-info-in-cloudtrail"></a>

CloudTrail is enabled on your AWS account when you create the account\. When activity occurs in IAM or AWS STS, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your AWS account\. For more information, see [Viewing Events with CloudTrail Event History](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)\. 

For an ongoing record of events in your AWS account, including events for IAM and AWS STS, create a trail\. A trail enables CloudTrail to deliver log files to an Amazon S3 bucket\. By default, when you create a trail in the console, the trail applies to all Regions\. The trail logs events from all Regions in the AWS partition and delivers the log files to the Amazon S3 bucket that you specify\. Additionally, you can configure other AWS services to further analyze and act upon the event data collected in CloudTrail logs\. For more information, see: 
+ [Overview for Creating a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)
+ [CloudTrail Supported Services and Integrations](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations)
+ [Configuring Amazon SNS Notifications for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)
+ [Receiving CloudTrail Log Files from Multiple Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)

All IAM and AWS STS actions are logged by CloudTrail and are documented in the [IAM API Reference](https://docs.aws.amazon.com/IAM/latest/APIReference/API_Operations.html) and the [AWS Security Token Service API Reference](https://docs.aws.amazon.com/STS/latest/APIReference/API_Operations.html)\.

## Logging IAM and AWS STS API requests<a name="cloudtrail-integration_apis"></a>

CloudTrail logs all authenticated API requests \(made with credentials\) to IAM and AWS STS API operations\. CloudTrail also logs nonauthenticated requests to the AWS STS actions, `AssumeRoleWithSAML` and `AssumeRoleWithWebIdentity`, and logs information provided by the identity provider\. You can use this information to map calls made by a federated user with an assumed role back to the originating external federated caller\. In the case of `AssumeRole`, you can map calls back to the originating AWS service or to the account of the originating user\. The `userIdentity` section of the JSON data in the CloudTrail log entry contains the information that you need to map the AssumeRole\* request with a specific federated user\. For more information, see [CloudTrail userIdentity Element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html) in the *AWS CloudTrail User Guide*\.

For example, calls to the IAM `CreateUser`, `DeleteRole`, `ListGroups`, and other API operations are all logged by CloudTrail\. 

Examples for this type of log entry are presented later in this topic\. 

**Important**  
If you activate AWS STS endpoints in Regions other than the default global endpoint, then you must also turn on CloudTrail logging in those Regions\. This is necessary to record any AWS STS API calls that are made in those Regions\. For more information, see [Turning On CloudTrail in Additional Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/aggregating_logs_regions_turn_on_ct.html) in the AWS CloudTrail User Guide\.

## Logging API requests to other AWS services<a name="cloudtrail-integration_api-other-services"></a>

Authenticated requests to other AWS service API operations are logged by CloudTrail, and these log entries contain information about who generated the request\. 

For example, assume that you made a request to list Amazon EC2 instances or create an CodeDeploy deployment group\. Details about the person or service that made the request are contained in the log entry for that request\. This information helps you determine whether the request was made by the AWS account root user, an IAM user, a role, or another AWS service\. 

For more details about the user identity information in CloudTrail log entries, see [userIdentity Element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/event_reference_user_identity.html) in the *AWS CloudTrail User Guide*\. 

## Logging regional sign\-in events<a name="cloudtrail-integration_signin-regions"></a>

If you enable CloudTrail to log sign\-in events to your logs, you need to be aware of how CloudTrail chooses where to log the events\.
+ If your users sign in directly to a console, they are redirected to either a global or a Regional sign\-in endpoint\. The endpoint depends on whether the selected service console supports Regions\. For example, the main console home page supports Regions\. If you sign in to https://alias\.signin\.aws\.amazon\.com/console, you are redirected to a Regional sign\-in endpoint such as https://us\-east\-2\.signin\.aws\.amazon\.com\. This redirection creates a Regional CloudTrail log entry in the user's Region's log\.

  On the other hand, the Amazon S3 console does not support Regions, so if you sign in to https://alias\.signin\.aws\.amazon\.com/console/s3, AWS redirects you to the global sign\-in endpoint at https://signin\.aws\.amazon\.com\. This redirection creates a global CloudTrail log entry\.
+ You can manually request a certain Regional sign\-in endpoint by signing in to the Region\-enabled main console home page using a URL like https://alias\.signin\.aws\.amazon\.com/console?region=ap\-southeast\-1\. In this case, AWS redirects you to the `ap-southeast-1` Regional sign\-in endpoint and results in a Regional CloudTrail log event\.

Whether the sign\-in event is considered Regional or global depends on the console the user signs into and how the user constructs the sign\-in URL\.
+ Is the service console Regionalized? If so, then the sign\-in request is automatically redirected to a Regional sign\-in endpoint and the event is logged in that Region's CloudTrail log\. For example, if you sign in to https://*alias*\.signin\.aws\.amazon\.com/console, which is Regionalized, you are redirected to a sign\-in endpoint in your Region, such as https://us\-east\-2\.signin\.aws\.amazon\.com\. The event is logged in that Region's log\.

  However, some services are not Regionalized yet\. For example, the Amazon S3 service is *not* currently Regionalized\. If you sign in to https://*alias*\.signin\.aws\.amazon\.com/console/s3, you are redirected to the global sign\-in endpoint at https://signin\.aws\.amazon\.com\. This redirection creates an event in your global log\.
+ You can also manually request a specific Regional sign\-in endpoint by using a URL such as https://*alias*\.signin\.aws\.amazon\.com/console?region=ap\-southeast\-1\. This URL redirects to the `ap-southeast-1` Regional sign\-in endpoint\. This redirection results in an event in the Regional log\.

### Preventing duplicate regional log entries<a name="cloudtrail-integration-global-service"></a>

CloudTrail creates separate trails in each Region\. These trails include information for events that occur in those Regions, plus global events and events that are not region\-specific\. Examples include IAM API calls, AWS STS calls to the global endpoint, and AWS sign\-in events\. For example, assume that you have two trails, each in a different Region\. If you then create a new IAM user, the `CreateUser` event is added to the log files in both Regions, creating a duplicate log entry\. 

AWS Security Token Service \(STS\) is a global service with a single global endpoint at https://sts\.amazonaws\.com\. Calls to this endpoint are logged as calls to a global service\. However, because this endpoint is physically located in the US East \(N\. Virginia\) Region, your logs list us\-east\-1 as the event Region\. CloudTrail does not write these logs to the US East \(Ohio\) Region unless you choose to include global service logs in that Region\. AWS STS also allows calls to Regional endpoints, such as `sts.eu-central-1.amazonaws.com`\. CloudTrail writes calls to all Regional endpoints to their respective Regions\. For example, calls to `sts.us-east-2.amazonaws.com` are published to the US East \(Ohio\) Region\. Calls to `sts.eu-central-1.amazonaws.com` are published in the Europe \(Frankfurt\) Region logs\. 

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
| Europe \(Frankfurt\) | eu\-central\-1 | sts\.eu\-central\-1\.amazonaws\.com | Region | 
| Europe \(Ireland\) | eu\-west\-1 | sts\.eu\-west\-1\.amazonaws\.com | Region | 
| Europe \(London\) | eu\-west\-2 | sts\.eu\-west\-2\.amazonaws\.com | Region | 
| Asia Pacific \(Tokyo\) | ap\-northeast\-1 | sts\.ap\-northeast\-1\.amazonaws\.com | Region | 
| Asia Pacific \(Seoul\) | ap\-northeast\-2 | sts\.ap\-northeast\-2\.amazonaws\.com | Region | 
| Asia Pacific \(Mumbai\) | ap\-south\-1 | sts\.ap\-south\-1\.amazonaws\.com | Region | 
| Asia Pacific \(Singapore\) | ap\-southeast\-1 | sts\.ap\-southeast\-1\.amazonaws\.com | Region | 
| Asia Pacific \(Sydney\) | ap\-southeast\-2 | sts\.ap\-southeast\-2\.amazonaws\.com | Region | 
| South America \(São Paulo\) | sa\-east\-1 | sts\.sa\-east\-1\.amazonaws\.com | Region | 

When you configure CloudTrail to aggregate trail information from multiple Regions in your account into a single Amazon S3 bucket, IAM events are duplicated in the logs\. In other words, the trail for each Region writes the same IAM event to the aggregated log\. To prevent this duplication, you can include global events selectively\. A typical approach is to enable global events in one trail\. Then disable global events in all other trails that write to the same Amazon S3 bucket\. That way only one set of global events is written\.

For more information, see [Aggregating Logs](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/aggregatinglogs.html) in the *AWS CloudTrail User Guide*\. 

## Logging user sign\-in events<a name="cloudtrail-integration_signin-users"></a>

CloudTrail logs sign\-in events to the AWS Management Console, the AWS discussion forums, and AWS Marketplace\. CloudTrail logs successful and failed sign\-in attempts for IAM users and federated users\. 

For AWS account root users, only successful sign\-in events are logged\. Unsuccessful sign\-in events by the root user are *not *logged by CloudTrail\.

As a security best practice, AWS does not log the entered IAM user name text when the sign\-in failure is caused by *an incorrect user name*\. The user name text is masked by the value `HIDDEN_DUE_TO_SECURITY_REASONS`\. For an example of this, see [Example sign\-in failure event caused by incorrect user name](#hiddensecurity), later in this topic\. The user name text is obscured because such failures might be caused by user errors\. Logging these errors could expose potentially sensitive information\. For example:
+ You accidentally type your password in the user name box\.
+ You choose the link for one AWS account's sign\-in page, but then type the account number for a different one\.
+ You forget which account you are signing in to and accidentally type the account name of your personal email account, your bank sign\-in identifier, or some other private ID\. 

## Logging sign\-in events for temporary credentials<a name="cloudtrail-integration_signin-tempcreds"></a>

When a principal requests temporary credentials, the principal type determines how CloudTrail logs the event\. This can be complicated when a principal assumes a role in another account\. There are multiple API calls to perform operations related to role cross\-account operations\. First, the principal calls an AWS STS API to retrieve the temporary credentials\. That operation is logged in the calling account and the account where the AWS STS operation is performed\. Then the principal then uses the role to perform other API calls in the assumed role's account\.

You can use the `aws:RoleSessionName` condition key to require that your users provide a specific session name when they assume a role\. For example, you can require that IAM users specify their own user name as their session name\. This makes it easier for administrators that are reviewing AWS CloudTrail logs to learn who performed an action\. For more information, see [`aws:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname)\.

The following table shows how CloudTrail logs different information for each of the API calls that generate temporary credentials\.


****  

| Principal type | STS API | User identity in CloudTrail log for caller's account | User identity in CloudTrail log for the assumed role's account | User identity in CloudTrail log for the role's subsequent API calls | 
| --- | --- | --- | --- | --- | 
| AWS account root user credentials | GetSessionToken | Root user identity | Role owner account is same as calling account | Root user identity | 
| IAM user | GetSessionToken | IAM user identity | Role owner account is same as calling account | IAM user identity | 
| IAM user | GetFederationToken | IAM user identity | Role owner account is same as calling account | IAM user identity | 
| IAM user | AssumeRole | IAM user identity | Account number and principal ID \(if a user\), or AWS service principal | Role identity only \(no user\) | 
| Externally authenticated user | AssumeRoleWithSAML | n/a | SAML user identity | Role identity only \(no user\) | 
| Externally authenticated user | AssumeRoleWithWebIdentity | n/a | OIDC/Web user identity | Role identity only \(no user\) | 

## Example IAM API events in CloudTrail log<a name="cloudtrail-integration_examples-iam-api"></a>

CloudTrail log files contain events that are formatted using JSON\. An API event represents a single API request and includes information about the principal, the requested action, any parameters, and the date and time of the action\. 

### Example IAM API event in CloudTrail log file<a name="cloudtrail-integration-iam-api-events"></a>

The following example shows a CloudTrail log entry for a request made for the IAM `GetUserPolicy` action\. 

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDACKCEVSQ6C2EXAMPLE",
    "arn": "arn:aws:iam::444455556666:user/JaneDoe",
    "accountId": "444455556666",
    "accessKeyId": "AKIAI44QH8DHBEXAMPLE",
    "userName": "JameDoe",
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
    "userName": "JaneDoe",
    "policyName": "ReadOnlyAccess-JaneDoe-201407151307"
  },
  "responseElements": null,
  "requestID": "9EXAMPLE-0c68-11e4-a24e-d5e16EXAMPLE",
  "eventID": "cEXAMPLE-127e-4632-980d-505a4EXAMPLE"
}
```

From this event information, you can determine that the request was made to get a user policy named `ReadOnlyAccess-JaneDoe-201407151307` for user `JaneDoe`, as specified in the `requestParameters` element\. You can also see that the request was made by an IAM user named `JaneDoe` on July 15, 2014 at 9:40 PM \(UTC\)\. In this case, the request originated in the AWS Management Console, as you can tell from the `userAgent` element\. 

## Example AWS STS API events in CloudTrail log<a name="cloudtrail-integration_examples-sts-api"></a>

CloudTrail log files contain events that are formatted using JSON\. An API event represents a single API request and includes information about the principal, the requested action, any parameters, and the date and time of the action\. 

### Example cross\-account AWS STS API events in CloudTrail log files<a name="stscloudtrailexample"></a>

The IAM user named `JohnDoe` in account 777788889999 calls the AWS STS `AssumeRole` action to assume the role `EC2-dev` in account 111122223333\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDAQRSTUVWXYZEXAMPLE",
    "arn": "arn:aws:iam::777788889999:user/JohnDoe",
    "accountId": "777788889999",
    "accessKeyId": "AKIAQRSTUVWXYZEXAMPLE",
    "userName": "JohnDoe"
  },
  "eventTime": "2014-07-18T15:07:39Z",
  "eventSource": "sts.amazonaws.com",
  "eventName": "AssumeRole",
  "awsRegion": "us-east-2",
  "sourceIPAddress": "192.0.2.101",
  "userAgent": "aws-cli/1.11.10 Python/2.7.8 Linux/3.2.45-0.6.wd.865.49.315.metal1.x86_64 botocore/1.4.67",
  "requestParameters": {
    "roleArn": "arn:aws:iam::111122223333:role/EC2-dev",
    "roleSessionName": "JohnDoe-EC2-dev"
    "serialNumber": "arn:aws:iam::777788889999:mfa"
  },
  "responseElements": {
    "credentials": {
      "sessionToken": "<encoded session token blob>",
      "accessKeyId": "AKIAQRSTUVWXYZEXAMPLE",
      "expiration": "Jul 18, 2014 4:07:39 PM"
      },
    "assumedRoleUser": {
      "assumedRoleId": "AIDAQRSTUVWXYZEXAMPLE:JohnDoe-EC2-dev",
      "arn": "arn:aws:sts::111122223333:assumed-role/EC2-dev/JohnDoe-EC2-dev"
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

The second example shows the assumed role account's \(111122223333\) CloudTrail log entry for the same request\.

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
    "roleSessionName": "JohnDoe-EC2-dev",
    "serialNumber": "arn:aws:iam::777788889999:mfa"
  }, 
  "responseElements": {
    "credentials": {
      "sessionToken": "<encoded session token blob>",     
      "accessKeyId": "AKIAQRSTUVWXYZEXAMPLE",     
      "expiration": "Jul 18, 2014 4:07:39 PM"     
    },   
    "assumedRoleUser": {     
      "assumedRoleId": "AIDAQRSTUVWXYZEXAMPLE:JohnDoe-EC2-dev",     
      "arn": "arn:aws:sts::111122223333:assumed-role/EC2-dev/JohnDoe-EC2-dev"   
    } 
  }, 
  "requestID": "4EXAMPLE-0e8d-11e4-96e4-e55c0EXAMPLE",
  "sharedEventID": "bEXAMPLE-efea-4a70-b951-19a88EXAMPLE",
  "eventID": "dEXAMPLE-ac7f-466c-a608-4ac8dEXAMPLE"
}
```

### Example AWS STS role chaining API event in CloudTrail log file<a name="stscloudtrailexample-assumerole"></a>

The following example shows a CloudTrail log entry for a request made by John Doe in account 111111111111\. John previously used his `JohnDoe` user to assume the `JohnRole1` role\. For this request, he uses the credentials from that role to assume the `JonRole2` role\. This is known as [role chaining](id_roles_terms-and-concepts.md#iam-term-role-chaining)\. John passes two [session tags](id_session-tags.md) into the request\. He sets those two tags as transitive\. The request inherits the `Department` tag as transitive because John set it as transitive when he assumed `JohnRole1`\. For more information about transitive keys in role chains, see [Chaining roles with session tags](id_session-tags.md#id_session-tags_role-chaining)\.

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole",
        "principalId": "AROAIN5ATK5U7KEXAMPLE:JohnRole1",
        "arn": "arn:aws:sts::111111111111:assumed-role/JohnDoe/JohnRole1",
        "accountId": "111111111111",
        "accessKeyId": "AKIAI44QH8DHBEXAMPLE",
        "sessionContext": {
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2019-10-02T21:50:54Z"
            },
            "sessionIssuer": {
                "type": "Role",
               "principalId": "AROAIN5ATK5U7KEXAMPLE",
                "arn": "arn:aws:iam::111111111111:role/JohnRole1",
                "accountId": "111111111111",
                "userName": "JohnDoe"
            }
        }
    },
    "eventTime": "2019-10-02T22:12:29Z",
    "eventSource": "sts.amazonaws.com",
    "eventName": "AssumeRole",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "123.145.67.89",
    "userAgent": "aws-cli/1.16.248 Python/3.4.7 Linux/4.9.184-0.1.ac.235.83.329.metal1.x86_64 botocore/1.12.239",
    "requestParameters": {
        "incomingTransitiveTags": {
            "Department": "Engineering"
        },
        "tags": [
            {
                "value": "johndoe@example.com",
                "key": "Email"
            },
            {
                "value": "12345",
                "key": "CostCenter"
            }
        ],
        "roleArn": "arn:aws:iam::111111111111:role/JohnRole2",
        "roleSessionName": "Role2WithTags",
        "transitiveTagKeys": [
            "Email",
            "CostCenter"
        ],
        "durationSeconds": 3600
    },
    "responseElements": {
        "credentials": {
            "accessKeyId": "ASIAWHOJDLGPOEXAMPLE",
            "expiration": "Oct 2, 2019 11:12:29 PM",
            "sessionToken": "AgoJb3JpZ2luX2VjEB4aCXVzLXdlc3QtMSJHMEXAMPLETOKEN+//rJb8Lo30mFc5MlhFCEbubZvEj0wHB/mDMwIgSEe9gk/Zjr09tZV7F1HDTMhmEXAMPLETOKEN/iEJ/rkqngII9///////////ARABGgw0MjgzMDc4NjM5NjYiDLZjZFKwP4qxQG5sFCryASO4UPz5qE97wPPH1eLMvs7CgSDBSWfonmRTCfokm2FN1+hWUdQQH6adjbbrVLFL8c3jSsBhQ383AvxpwK5YRuDE1AI/+C+WKFZb701eiv9J5La2EXAMPLETOKEN/c7S5Iro1WUJ0q3Cxuo/8HUoSxVhQHM7zF7mWWLhXLEQ52ivL+F6q5dpXu4aTFedpMfnJa8JtkWwG9x1Axj0Ypy2ok8v5unpQGWych1vwdvj6ez1Dm8Xg1+qIzXILiEXAMPLETOKEN/vQGqu8H+nxp3kabcrtOvTFTvxX6vsc8OGwUfHhzAfYGEXAMPLETOKEN/L6v1yMM3B1OwFOrQBno1HEjf1oNI8RnQiMNFdUOtwYj7HUZIOCZmjfN8PPHq77N7GJl9lzvIZKQA0Owcjg+mc78zHCj8y0siY8C96paEXAMPLETOKEN/E3cpksxWdgs91HRzJWScjN2+r2LTGjYhyPqcmFzzo2mCE7mBNEXAMPLETOKEN/oJy+2o83YNW5tOiDmczgDzJZ4UKR84yGYOMfSnF4XcEJrDgAJ3OJFwmTcTQICAlSwLEXAMPLETOKEN"
        },
        "assumedRoleUser": {
            "assumedRoleId": "AROAIFR7WHDTSOYQYHFUE:Role2WithTags",
            "arn": "arn:aws:sts::111111111111:assumed-role/test-role/Role2WithTags"
        }
    },
    "requestID": "b96b0e4e-e561-11e9-8b3f-7b396EXAMPLE",
    "eventID": "1917948f-3042-46ec-98e2-62865EXAMPLE",
    "resources": [
        {
            "ARN": "arn:aws:iam::111122223333:role/JohnRole2",
            "accountId": "111111111111",
            "type": "AWS::IAM::Role"
        }
    ],
    "eventType": "AwsApiCall",
    "recipientAccountId": "111111111111"
}
```

### Example AWS service AWS STS API event in CloudTrail log file<a name="stscloudtrailexample_service"></a>

The following example shows a CloudTrail log entry for a request made by an AWS service calling another service API using permissions from a service role\. It shows the CloudTrail log entry for the request made in account 777788889999\.

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

### Example SAML AWS STS API event in CloudTrail log file<a name="stscloudtrailexample_saml"></a>

The following example shows a CloudTrail log entry for a request made for the AWS STS `AssumeRoleWithSAML` action\. The request includes the SAML attributes `CostCenter` and `Project` that are passed through the SAML assertion as [session tags](id_session-tags.md)\. Those tags are set as transitive so that they [persist in role chaining scenarios](id_session-tags.md#id_session-tags_role-chaining)\.

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "SAMLUser",
        "principalId": "SampleUkh1i4+ExamplexL/jEvs=:SamlExample",
        "userName": "SamlExample",
        "identityProvider": "bdGOnTesti4+ExamplexL/jEvs="
    },
    "eventTime": "2019-11-01T19:14:36Z",
    "eventSource": "sts.amazonaws.com",
    "eventName": "AssumeRoleWithSAML",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "192.0.2.101",
    "userAgent": "aws-cli/1.16.263 Python/3.4.7 Linux/4.9.184-0.1.ac.235.83.329.metal1.x86_64 botocore/1.12.253",
    "requestParameters": {
        "sAMLAssertionID": "_c0046cEXAMPLEb9d4b8eEXAMPLE2619aEXAMPLE",
        "roleSessionName": "MyAssignedRoleSessionName",
        "principalTags": {
            "CostCenter": "987654",
            "Project": "Unicorn",
            "Department": "Engineering"
        },
        "transitiveTagKeys": [
            "CostCenter",
            "Project"
        ],
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
        "nameQualifier": "bdGOnTesti4+ExamplexL/jEvs=",
        "assumedRoleUser": {
            "assumedRoleId": "AROAD35QRSTUVWEXAMPLE:MyAssignedRoleSessionName",
            "arn": "arn:aws:sts::444455556666:assumed-role/SAMLTestRoleShibboleth/MyAssignedRoleSessionName"
        },
        "subject": "SamlExample",
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

### Example web identity AWS STS API event in CloudTrail log file<a name="stscloudtrailexample_web-identity"></a>

The following example shows a CloudTrail log entry for a request made for the AWS STS `AssumeRoleWithWebIdentity` action\. The request includes the attributes `CostCenter` and `Project` that are passed through the identity provider token as [session tags](id_session-tags.md)\. Those tags are set as transitive so that they [persist in role chaining scenarios](id_session-tags.md#id_session-tags_role-chaining)\.

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
        "principalTags": {
            "CostCenter": "24680",
            "Project": "Pegasus"
        },
        "transitiveTagKeys": [
            "CostCenter",
            "Project"
        ],
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

## Example sign\-in events in CloudTrail log<a name="cloudtrail-integration_examples-signin"></a>

CloudTrail log files contain events that are formatted using JSON\. A sign\-in event represents a single sign\-in request and includes information about the sign\-in principal, the Region, and the date and time of the action\. 

### Example sign\-in success event in CloudTrail log file<a name="cloudtrail-integration-signin-success"></a>

The following example shows a CloudTrail log entry for a successful sign\-in event\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDACKCEVSQ6C2EXAMPLE",
    "arn":"arn:aws:iam::111122223333:user/JohnDoe",
    "accountId": "111122223333",
    "userName": "JohnDoe"
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

### Example sign\-in failure event in CloudTrail log file<a name="cloudtrail-integration-signin-failure"></a>

The following example shows a CloudTrail log entry for a failed sign\-in event\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "IAMUser",
    "principalId": "AIDACKCEVSQ6C2EXAMPLE",
    "arn":"arn:aws:iam::111122223333:user/JaneDoe",
    "accountId": "111122223333",
    "userName": "JaneDoe"
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

From this information, you can determine that the sign\-in attempt was made by an IAM user named `JaneDoe`, as shown in the `userIdentity` element\. You can also see that the sign\-in attempt failed, as shown in the `responseElements` element\. You can see that `JaneDoe` tried to sign in to the Amazon SNS console at 5:35 PM \(UTC\) on July 8, 2014\.

### Example sign\-in failure event caused by incorrect user name<a name="hiddensecurity"></a>

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