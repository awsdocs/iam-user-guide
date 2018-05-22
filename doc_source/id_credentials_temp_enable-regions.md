# Activating and Deactivating AWS STS in an AWS Region<a name="id_credentials_temp_enable-regions"></a>

By default, the AWS Security Token Service \(AWS STS\) is available as a global service, and all AWS STS requests go to a single endpoint at `https://sts.amazonaws.com`\. You can optionally send your AWS STS requests to endpoints in any of the AWS regions shown in the table that follows\. All regions are enabled by default, but you can disable any regions that you know you don't need\.

You might choose to send your AWS STS requests to a regional endpoint for the following reasons:
+ **Reduce latency** – By making your AWS STS calls to an endpoint that is geographically closer to your services and applications, you can access AWS STS services with lower latency and better response times\.
+ **Build in Redundancy** – By adding code to your application that switches your AWS STS API calls to a different region, you ensure that if the first region stops responding, your application continues to operate\. This redundancy is not automatic; you must build the functionality into your code\.

When you activate a region for an account, you enable the STS endpoints in that region to issue temporary credentials for users and roles in that account when a request is made to an endpoint in the region\. The credentials are still recognized and usable globally\. It is not the account of the caller, but the account from which temporary credentials are requested that must activate the region\.

For example, imagine a user in account A wants to send an `sts:AssumeRole` API request to the STS regional endpoint `https://sts.us-west-2.amazonaws.com`\. The request is for temporary credentials for the role named `Developer` in account B\. Because the request is to create credentials for an entity in account B, account B must activate the `us-west-2` region\. Users from account A \(or any other account\) can call the `us-west-2` endpoint to request credentials for account B whether or not the region is activated in their accounts\.

**To activate or deactivate AWS STS in a region**
**Note**  
All regions are activated by default\. You need to activate a region only if it was previously deactivated\.

1. Sign in as an IAM user with permissions to perform IAM administration tasks \(`"iam:*"`\) for the account for which you want to activate AWS STS in a new region\.

1. Open the IAM console and in the navigation pane choose [https://console.aws.amazon.com/iam/home?#account_settings](https://console.aws.amazon.com/iam/home?#account_settings)\. 

1. Expand the **Security Token Service Regions** list, find the region that you want to use, and then choose **Activate** or **Deactivate**\.

## Writing Code to Use AWS STS Regions<a name="id_credentials_temp_enable-regions_writing_code"></a>

After you activate a region for your AWS account, you can direct AWS STS API calls to that region\. The following Java code snippet demonstrates how to configure an `AWSSecurityTokenServiceClient` object to make requests from the EU \(Ireland\) \(eu\-west\-1\) region with the `setEndpoint` method\.

```
AWSSecurityTokenServiceClient stsClient = new AWSSecurityTokenServiceClient();
stsClient.setEndpoint("sts.eu-west-1.amazonaws.com");
```

**Important**  
Do not use the `setRegion` method to set a regional endpoint for AWS STS because, for backward compatibility, that method continues to resolve to the original single global endpoint of sts\.amazonaws\.com\. 

In the example, the first line instantiates an `AWSSecurityTokenServiceClient` object called `stsClient`\. The second line configures the `stsClient` object by calling its `setEndpoint` method and passing the URL of the endpoint as the only parameter\. All API calls that use this `stsClient` object are now directed to the specified endpoint\.

For all other language and programming environment combinations, refer to the [documentation for the relevant SDK](https://aws.amazon.com/tools/)\. 

Nothing else about using AWS STS in a region changes\. As always, the credentials retrieved from the AWS STS endpoint in a region are not limited to that region; you can use them globally\.

The following table lists the regions and their endpoints\. It indicates which ones are activated by default and which ones you can activate or deactivate\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_enable-regions.html)

**Note**  
Calls to regional endpoints, such as `us-east-2.amazonaws.com`, are logged in AWS CloudTrail the same as any call to a regional service\. Calls to the global endpoint, `sts.amazonaws.com`, are logged as calls to a global service\. For more information, see [Logging IAM Events with AWS CloudTrail](cloudtrail-integration.md)\.