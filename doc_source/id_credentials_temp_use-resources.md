# Using Temporary Security Credentials to Request Access to AWS Resources<a name="id_credentials_temp_use-resources"></a>

You can use temporary security credentials to make programmatic requests for AWS resources with the [AWS SDKs](https://aws.amazon.com/tools/) or API calls, the same way that you can use long\-term security credentials such as IAM user credentials\. However, there are a few differences:
+ When you make a call using temporary security credentials, the call must include a session token, which is returned along with those temporary credentials\. AWS uses the session token to validate the temporary security credentials\. 
+ The temporary credentials expire after a specified interval\. After the credentials expire, any calls that you make with those credentials will fail, so you must get a new set of credentials\. 

If you are using the [AWS SDKs](https://aws.amazon.com/tools), the [AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/) \(AWS CLI\), or the [Tools for Windows PowerShell](https://aws.amazon.com/powershell), the way in which you get and use temporary security credentials differs depending on the context\. If you are running code, AWS CLI, or Tools for Windows PowerShell commands inside an EC2 instance, you can take advantage of roles for Amazon EC2\. Otherwise, you can call an AWS STS API to get the temporary credentials, and then use them explicitly to make calls to AWS services\.

**Note**  
You can use AWS Security Token Service \(AWS STS\) to create and provide trusted users with temporary security credentials that can control access to your AWS resources\. For more information about AWS STS, see [Temporary Security Credentials](id_credentials_temp.md)\. AWS STS is a global service that has a default endpoint at `https://sts.amazonaws.com`\. This endpoint is in the US East \(Ohio\) region, although credentials that you get from this and other endpoints are valid globally and work with services and resources in any region\. You can also choose to make AWS STS API calls to endpoints in any of the supported regions\. This can reduce latency by making the requests from servers in a region that is geographically closer to you\. No matter which region your credentials come from, they work globally\. For more information, see [Activating and Deactivating AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\.

**Contents**
+ [Using Temporary Credentials in Amazon EC2 Instances](#using-temp-creds-sdk-ec2-instances)
+ [Using Temporary Security Credentials with the AWS SDKs](#using-temp-creds-sdk)
+ [Using Temporary Security Credentials with the AWS CLI](#using-temp-creds-sdk-cli)
+ [Using Temporary Security Credentials with the Tools for Windows PowerShell](#using-temp-creds-twp)
+ [Using Temporary Security Credentials with API Operations](#RequestWithSTS)
+ [More Information](#using-temp-creds-more-info)

## Using Temporary Credentials in Amazon EC2 Instances<a name="using-temp-creds-sdk-ec2-instances"></a>

If you want to run AWS CLI commands or code inside an EC2 instance, the recommended way to get credentials is to use [roles for Amazon EC2](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)\. You create an IAM role that specifies the permissions that you want to grant to applications that run on the EC2 instances\. When you launch the instance, you associate the role with the instance\.

Applications, AWS CLI, and Tools for Windows PowerShell commands that run on the instance can then get automatic temporary security credentials from the instance metadata\. You do not have to explicitly get the temporary security credentials—the AWS SDKs, AWS CLI, and Tools for Windows PowerShell automatically get the credentials from the EC2 instance metadata service and use them\. The temporary credentials have the permissions that you define for the role that is associated with the instance\.

For more information and for examples, see the following:
+  [Using IAM Roles to Grant Access to AWS Resources on Amazon Elastic Compute Cloud](http://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) — AWS SDK for Java
+  [Granting Access Using an IAM Role](http://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/net-dg-hosm.html) — AWS SDK for \.NET 
+  [Creating a Role](http://docs.aws.amazon.com/sdk-for-ruby/v2/developer-guide/iam-example-create-role.html) — AWS SDK for Ruby

## Using Temporary Security Credentials with the AWS SDKs<a name="using-temp-creds-sdk"></a>

To use temporary security credentials in code, you programmatically call an AWS STS API like `AssumeRole`, extract the resulting credentials and session token, and then use those values as credentials for subsequent calls to AWS\. The following example shows pseudocode for how to use temporary security credentials if you're using an AWS SDK:

```
assumeRoleResult = AssumeRole(role-arn);
tempCredentials = new SessionAWSCredentials(
   assumeRoleResult.AccessKeyId, 
   assumeRoleResult.SecretAccessKey, 
   assumeRoleResult.SessionToken);
s3Request = CreateAmazonS3Client(tempCredentials);
```

For an example written in Python \(using the [AWS SDK for Python \(Boto\)](https://aws.amazon.com/sdk-for-python/)\) that shows how to call `AssumeRole` to get temporary security credentials, and then use those credentials to make a call to Amazon S3, see [Switching to an IAM Role \(API\)](id_roles_use_switch-role-api.md)\.

For details about how to call `AssumeRole`, `GetFederationToken`, and other API operations, and about how to get the temporary security credentials and session token from the result, see the documentation for the SDK that you're working with\. You can find the documentation for all the AWS SDKs on the main [AWS documentation page](http://aws.amazon.com/documentation)\. 

You must make sure that you get a new set of credentials before the old ones expire\. In some SDKs, you can use a provider that manages the process of refreshing credentials for you; check the documentation for the SDK you're using\. 

## Using Temporary Security Credentials with the AWS CLI<a name="using-temp-creds-sdk-cli"></a>

You can use temporary security credentials with the AWS CLI\. This can be useful for testing policies\. 

Using the AWS CLI, you can call an AWS STS API like `AssumeRole` or `GetFederationToken` and then capture the resulting output\. The following example shows a call to `AssumeRole` that sends the output to a file\. In the example, the `profile` parameter is assumed to be a profile in the AWS CLI configuration file and is assumed to reference credentials for an IAM user who has permissions to assume the role\.

```
$ aws sts assume-role --role-arn arn:aws:iam::123456789012:role/role-name --role-session-name "RoleSession1" --profile IAM-user-name > assume-role-output.txt
```

When the command is finished, you can extract the access key ID, secret access key, and session token from wherever you've routed it, either manually or by using a script\. You can then assign these values to environment variables\. 

When you run AWS CLI commands, the AWS CLI looks for credentials in a specific order—first in environment variables and then in the configuration file\. Therefore, after you've put the temporary credentials into environment variables, the AWS CLI uses those credentials by default\. \(If you specify a `profile` parameter in the command, the AWS CLI skips the environment variables and looks in the configuration file, which lets you override the credentials in the environment variables if you need to\.\) 

The following example shows how you might set the environment variables for temporary security credentials and then call an AWS CLI command\. Because no `profile` parameter is included in the AWS CLI command, the AWS CLI looks for credentials first in environment variables and therefore uses the temporary credentials\. 

**Linux**

```
$ export AWS_ACCESS_KEY_ID=AKIAI44QH8DHBEXAMPLE
$ export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
$ export AWS_SESSION_TOKEN=AQoDYXdzEJr...<remainder of security token>
$ aws ec2 describe-instances --region us-west-1
```

**Windows**

```
C:\> SET AWS_ACCESS_KEY_ID=AKIAI44QH8DHBEXAMPLE
C:\> SET AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
C:\> SET AWS_SESSION_TOKEN=AQoDYXdzEJr...<remainder of token> 
C:\> aws ec2 describe-instances --region us-west-1
```

## Using Temporary Security Credentials with the Tools for Windows PowerShell<a name="using-temp-creds-twp"></a>

You can use temporary security credentials with the AWS Tools for Windows PowerShell\. This can be useful for testing policies\. 

With the Tools for Windows PowerShell, you can call an AWS STS API action like `AssumeRole` or `GetFederationToken` and then capture the resulting output\. The following example shows a PowerShell command that calls `AssumeRole` and stores the resulting role object in the variable `$role`\. The `StoredCredentials` parameter is assumed to be a profile in the Tools for Windows PowerShell configuration file set up by `Set-AWSCredentials` or `Initialized-AWSDefaults` and is assumed to reference credentials for an IAM user who has permissions to assume the role\.

```
PS C:\> $role = Use-STSRole -RoleArn arn:aws:iam::123456789012:role/MySampleRole -RoleSessionName RoleSession1 -StoredCredentials IAM-user-name
```

When the command is finished, you can extract the access key ID, secret access key, and session token from the variable\.

```
PS C:\> $role.AssumedRoleUser
Arn                                                            AssumedRoleId
---                                                            -------------
arn:aws:sts::123456789012:assumed-role/clirole/RoleSession1     AROAJVIFQ5TJISRUTVTUE:RoleSession1

PS C:\> $role.Credentials.AccessKeyId
AKIAIOSFODNN7EXAMPLE

PS C:\> $role.Credentials.SecretAccessKey
wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

PS C:\> $role.Credentials.SessionToken
AQoDYXdzEPT//////////wEXAMPLEtc764bNrC9SAPBSM22wDOk4x4HIZ8j4FZTwdQWLWsKWHGBuFqwAeMicRXmxfpSPfIeoIYRqT
flfKD8YUuwthAx7mSEI/qkPpKPi/kMcGdQrmGdeehM4IC1NtBmUpp2wUE8phUZampKsburEDy0KPkyQDYwT7WZ0wq5VSXDvp75YU9
HFvlRd8Tx6q6fE8YQcHNVXAkiY9q6d+xo0rKwT38xVqr7ZD0u0iPPkUL64lIZbqBAz+scqKmlzm8FDrypNC9Yjc8fPOLn9FX9KSYv
KTr4rvx3iSIlTJabIQwj2ICCR/oLxBA==

PS C:\> $role.Credentials.Expiration
Wednesday, July 08, 2015 3:22:32 PM
```

The following example shows how you might use the variable\-stored credentials and then use them to call an AWS CLI command\. 

```
PS C:\> Get-EC2Instance -Region us-west-2 -Credential $role.Credentials
```

## Using Temporary Security Credentials with API Operations<a name="RequestWithSTS"></a>

If you're making direct HTTPS API requests to AWS, you can sign those requests with the temporary security credentials that you get from the AWS Security Token Service \(AWS STS\)\. To do this, you use the access key ID and secret access key that you receive from AWS STS the same way you would use long\-term credentials to sign a request\. You also add to your API request the session token that you receive from AWS STS\. You add the session token to an HTTP header or to a query string parameter named `X-Amz-Security-Token`\. You add the session token to the HTTP header *or* the query string parameter, but not both\. For more information about signing HTTPS API requests, see [Signing AWS API Requests](http://docs.aws.amazon.com/general/latest/gr/signing_aws_api_requests.html) in the *AWS General Reference*\.

## More Information<a name="using-temp-creds-more-info"></a>

For more information about using AWS STS with other AWS services, see the following links:
+ **Amazon S3**\. See [Making Requests Using IAM User Temporary Credentials](http://docs.aws.amazon.com/AmazonS3/latest/dev/AuthUsingTempSessionToken.html) or [Making Requests Using Federated User Temporary Credentials](http://docs.aws.amazon.com/AmazonS3/latest/dev/AuthUsingTempFederationToken.html) in the *Amazon Simple Storage Service Developer Guide *\.
+ **Amazon SNS**\. See [Using Temporary Security Credentials](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#UsingTemporarySecurityCredentials_SNS) in the *Amazon Simple Notification Service Developer Guide*\.
+ **Amazon SQS**\. See [Using Temporary Security Credentials](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/UsingIAM.html#UsingTemporarySecurityCredentials_SQS) in the *Amazon Simple Queue Service Developer Guide*\.
+ **Amazon SimpleDB**\. See [Using Temporary Security Credentials](http://docs.aws.amazon.com/AmazonSimpleDB/latest/DeveloperGuide/index.html?UsingTemporarySecurityCredentials_SDB.html) in the *Amazon SimpleDB Developer Guide*\.