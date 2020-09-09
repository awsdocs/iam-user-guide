# Using temporary credentials with AWS resources<a name="id_credentials_temp_use-resources"></a>

You can use temporary security credentials to make programmatic requests for AWS resources using the AWS CLI or AWS API \(using the [AWS SDKs](https://aws.amazon.com/tools/)\)\. The temporary credentials provide the same permissions that you have with use long\-term security credentials such as IAM user credentials\. However, there are a few differences:
+ When you make a call using temporary security credentials, the call must include a session token, which is returned along with those temporary credentials\. AWS uses the session token to validate the temporary security credentials\. 
+ The temporary credentials expire after a specified interval\. After the credentials expire, any calls that you make with those credentials will fail, so you must get a new set of credentials\. 
+ When you use temporary credentials to make a request, your principal might include a set of tags\. These tags come from session tags and tags that are attached to the role that you assume\. For more information about session tags, see [Passing session tags in AWS STS](id_session-tags.md)\.

If you are using the [AWS SDKs](https://aws.amazon.com/tools), the [AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/) \(AWS CLI\), or the [Tools for Windows PowerShell](https://aws.amazon.com/powershell), the way to get and use temporary security credentials differs with the context\. If you are running code, AWS CLI, or Tools for Windows PowerShell commands inside an EC2 instance, you can take advantage of roles for Amazon EC2\. Otherwise, you can call an [AWS STS API](https://docs.aws.amazon.com/STS/latest/APIReference/) to get the temporary credentials, and then use them explicitly to make calls to AWS services\.

**Note**  
You can use AWS Security Token Service \(AWS STS\) to create and provide trusted users with temporary security credentials that can control access to your AWS resources\. For more information about AWS STS, see [Temporary security credentials in IAM](id_credentials_temp.md)\. AWS STS is a global service that has a default endpoint at `https://sts.amazonaws.com`\. This endpoint is in the US East \(Ohio\) Region, although credentials that you get from this and other endpoints are valid globally\. These credentials work with services and resources in any Region\. You can also choose to make AWS STS API calls to endpoints in any of the supported Regions\. This can reduce latency by making the requests from servers in a Region that is geographically closer to you\. No matter which Region your credentials come from, they work globally\. For more information, see [Managing AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\.

**Contents**
+ [Using temporary credentials in Amazon EC2 instances](#using-temp-creds-sdk-ec2-instances)
+ [Using temporary security credentials with the AWS SDKs](#using-temp-creds-sdk)
+ [Using temporary security credentials with the AWS CLI](#using-temp-creds-sdk-cli)
+ [Using temporary security credentials with API operations](#RequestWithSTS)
+ [More information](#using-temp-creds-more-info)

## Using temporary credentials in Amazon EC2 instances<a name="using-temp-creds-sdk-ec2-instances"></a>

If you want to run AWS CLI commands or code inside an EC2 instance, the recommended way to get credentials is to use [roles for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)\. You create an IAM role that specifies the permissions that you want to grant to applications that run on the EC2 instances\. When you launch the instance, you associate the role with the instance\.

Applications, AWS CLI, and Tools for Windows PowerShell commands that run on the instance can then get automatic temporary security credentials from the instance metadata\. You do not have to explicitly get the temporary security credentials\. The AWS SDKs, AWS CLI, and Tools for Windows PowerShell automatically get the credentials from the EC2 instance metadata service and use them\. The temporary credentials have the permissions that you define for the role that is associated with the instance\.

For more information and for examples, see the following:
+  [Using IAM Roles to Grant Access to AWS Resources on Amazon Elastic Compute Cloud](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) — AWS SDK for Java
+  [Granting Access Using an IAM Role](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/net-dg-hosm.html) — AWS SDK for \.NET 
+  [Creating a Role](https://docs.aws.amazon.com/sdk-for-ruby/v3/developer-guide/iam-example-create-role.html) — AWS SDK for Ruby

## Using temporary security credentials with the AWS SDKs<a name="using-temp-creds-sdk"></a>

To use temporary security credentials in code, you programmatically call an AWS STS API like `AssumeRole` and extract the resulting credentials and session token\. You then use those values as credentials for subsequent calls to AWS\. The following example shows pseudocode for how to use temporary security credentials if you're using an AWS SDK:

```
assumeRoleResult = AssumeRole(role-arn);
tempCredentials = new SessionAWSCredentials(
   assumeRoleResult.AccessKeyId, 
   assumeRoleResult.SecretAccessKey, 
   assumeRoleResult.SessionToken);
s3Request = CreateAmazonS3Client(tempCredentials);
```

For an example written in Python \(using the [AWS SDK for Python \(Boto\)](https://aws.amazon.com/sdk-for-python/)\), see [Switching to an IAM role \(AWS API\)](id_roles_use_switch-role-api.md)\. This example shows how to call `AssumeRole` to get temporary security credentials and then use those credentials to make a call to Amazon S3\.

For details about how to call `AssumeRole`, `GetFederationToken`, and other API operations, see the [AWS Security Token Service API Reference](https://docs.aws.amazon.com/STS/latest/APIReference/)\. For information on getting the temporary security credentials and session token from the result, see the documentation for the SDK that you're working with\. You can find the documentation for all the AWS SDKs on the main [AWS documentation page](http://aws.amazon.com/documentation), in the **SDKs and Toolkits** section\.

You must make sure that you get a new set of credentials before the old ones expire\. In some SDKs, you can use a provider that manages the process of refreshing credentials for you; check the documentation for the SDK you're using\. 

## Using temporary security credentials with the AWS CLI<a name="using-temp-creds-sdk-cli"></a>

You can use temporary security credentials with the AWS CLI\. This can be useful for testing policies\. 

Using the [AWS CLI](https://docs.aws.amazon.com/cli/latest/reference/), you can call an [ AWS STS API](https://docs.aws.amazon.com/STS/latest/APIReference/) like `AssumeRole` or `GetFederationToken` and then capture the resulting output\. The following example shows a call to `AssumeRole` that sends the output to a file\. In the example, the `profile` parameter is assumed to be a profile in the AWS CLI configuration file\. It is also assumed to reference credentials for an IAM user who has permissions to assume the role\.

```
aws sts assume-role --role-arn arn:aws:iam::123456789012:role/role-name --role-session-name "RoleSession1" --profile IAM-user-name > assume-role-output.txt
```

When the command is finished, you can extract the access key ID, secret access key, and session token from wherever you've routed it\. You can do this either manually or by using a script\. You can then assign these values to environment variables\. 

When you run AWS CLI commands, the AWS CLI looks for credentials in a specific order—first in environment variables and then in the configuration file\. Therefore, after you've put the temporary credentials into environment variables, the AWS CLI uses those credentials by default\. \(If you specify a `profile` parameter in the command, the AWS CLI skips the environment variables\. Instead, the AWS CLI looks in the configuration file, which lets you override the credentials in the environment variables if you need to\.\) 

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

## Using temporary security credentials with API operations<a name="RequestWithSTS"></a>

If you're making direct HTTPS API requests to AWS, you can sign those requests with the temporary security credentials that you get from the AWS Security Token Service \(AWS STS\)\. To do this, you use the access key ID and secret access key that you receive from AWS STS\. You use the access key ID and secret access key the same way you would use long\-term credentials to sign a request\. You also add to your API request the session token that you receive from AWS STS\. You add the session token to an HTTP header or to a query string parameter named `X-Amz-Security-Token`\. You add the session token to the HTTP header *or* the query string parameter, but not both\. For more information about signing HTTPS API requests, see [Signing AWS API Requests](https://docs.aws.amazon.com/general/latest/gr/signing_aws_api_requests.html) in the *AWS General Reference*\.

## More information<a name="using-temp-creds-more-info"></a>

For more information about using AWS STS with other AWS services, see the following links:
+ **Amazon S3**\. See [Making Requests Using IAM User Temporary Credentials](https://docs.aws.amazon.com/AmazonS3/latest/dev/AuthUsingTempSessionToken.html) or [Making Requests Using Federated User Temporary Credentials](https://docs.aws.amazon.com/AmazonS3/latest/dev/AuthUsingTempFederationToken.html) in the *Amazon Simple Storage Service Developer Guide *\.
+ **Amazon SNS**\. See [Using Temporary Security Credentials](https://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#UsingTemporarySecurityCredentials_SNS) in the *Amazon Simple Notification Service Developer Guide*\.
+ **Amazon SQS**\. See [Using Temporary Security Credentials](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/UsingIAM.html#UsingTemporarySecurityCredentials_SQS) in the *Amazon Simple Queue Service Developer Guide*\.
+ **Amazon SimpleDB**\. See [Using Temporary Security Credentials](https://docs.aws.amazon.com/AmazonSimpleDB/latest/DeveloperGuide/index.html?UsingTemporarySecurityCredentials_SDB.html) in the *Amazon SimpleDB Developer Guide*\.