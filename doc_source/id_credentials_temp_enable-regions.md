# Managing AWS STS in an AWS Region<a name="id_credentials_temp_enable-regions"></a>

By default, the AWS Security Token Service \(AWS STS\) is available as a global service, and all AWS STS requests go to a single endpoint at `https://sts.amazonaws.com`\. AWS recommends using Regional AWS STS endpoints instead of the global endpoint to reduce latency, build in redundancy, and increase session token validity\.
+ **Reduce latency** – By making your AWS STS calls to an endpoint that is geographically closer to your services and applications, you can access AWS STS services with lower latency and better response times\.
+ **Build in redundancy** – You can add code to your application that switches your AWS STS API calls to a different Region\. This ensures that if the first Region stops responding, your application continues to operate\. This redundancy is not automatic\. You must build the functionality into your code\.
+ **Increase session token validity** – Session tokens from Regional AWS STS endpoints are valid in all AWS Regions\. Session tokens from the global STS endpoint are valid only in AWS Regions that are enabled by default\. If you intend to enable a new Region for your account, you can use session tokens from Regional AWS STS endpoints\. If you choose to use the global endpoint, you must change the Region compatibility of AWS STS session tokens for the global endpoint\. Doing so ensures that tokens are valid in all AWS Regions\.

## Managing global endpoint session tokens<a name="sts-regions-manage-tokens"></a>

Most AWS Regions are enabled for operations in all AWS services by default\. Those Regions are automatically activated for use with AWS STS\. Some Regions, such as Asia Pacific \(Hong Kong\), must be manually enabled\. To learn more about enabling and disabling AWS Regions, see [Managing AWS Regions](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html) in the *AWS General Reference*\. When you enable these AWS Regions, they are automatically activated for use with AWS STS\. You cannot activate the AWS STS endpoint for a Region that is disabled\. Tokens that are valid in all AWS Regions include more characters than tokens that are valid in Regions that are enabled by default\. Changing this setting might affect existing systems where you temporarily store tokens\.

You can change this setting using the AWS Management Console, AWS CLI, or AWS API\.

**To change the Region compatibility of session tokens for the global endpoint \(console\)**

1. Sign in as a root user or a user with permissions to perform IAM administration tasks\. To change the compatibility of session tokens, you must have a policy that allows the `iam:SetSecurityTokenServicePreferences` action\.

1. Open the [IAM console](https://console.aws.amazon.com/iam/home?#home)\. In the navigation pane, choose **Account settings**\.

1. Under **Security Token Service \(STS\)** section **Session Tokens from the STS endpoints**\. The **Global endpoint** indicates `Valid only in AWS Regions enabled by default`\. Choose **Change**\.

1. In the **Change region compatibility** dialog box, select **All AWS Regions**\. Then choose **Save changes**\.
**Note**  
Tokens that are valid in all AWS Region include more characters than tokens that are valid in Regions that are enabled by default\. Changing this setting might affect existing systems where you temporarily store tokens\.

**To change the Region compatibility of session tokens for the global endpoint \(AWS CLI\)**  
Set the session token version\. Version 1 tokens are valid only in AWS Regions that are available by default\. These tokens do not work in manually enabled Regions, such as Asia Pacific \(Hong Kong\)\. Version 2 tokens are valid in all Regions\. However, version 2 tokens include more characters and might affect systems where you temporarily store tokens\.
+ [https://docs.aws.amazon.com/cli/latest/reference/iam/set-security-token-service-preferences.html](https://docs.aws.amazon.com/cli/latest/reference/iam/set-security-token-service-preferences.html)

**To change the Region compatibility of session tokens for the global endpoint \(AWS API\)**  
Set the session token version\. Version 1 tokens are valid only in AWS Regions that are available by default\. These tokens do not work in manually enabled Regions, such as Asia Pacific \(Hong Kong\)\. Version 2 tokens are valid in all Regions\. However, version 2 tokens include more characters and might affect systems where you temporarily store tokens\.
+ [https://docs.aws.amazon.com/IAM/latest/APIReference/API_SetSecurityTokenServicePreferences.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_SetSecurityTokenServicePreferences.html) 

## Activating and deactivating AWS STS in an AWS Region<a name="sts-regions-activate-deactivate"></a>

When you activate STS endpoints for a Region, AWS STS can issue temporary credentials to users and roles in your account that make an AWS STS request\. Those credentials can then be used in any Region that is enabled by default or is manually enabled\. You must activate the Region in the account where the temporary credentials are generated\. It does not matter whether a user is signed into the same account or a different account when they make the request\.

For example, imagine a user in account A wants to send an `sts:AssumeRole` API request to the AWS STS Regional endpoint `https://sts.us-west-2.amazonaws.com`\. The request is for temporary credentials for the role named `Developer` in account B\. Because the request is to create credentials for an entity in account B, account B must activate the `us-west-2` Region\. Users from account A \(or any other account\) can call the `us-west-2` endpoint to request credentials for account B whether or not the Region is activated in their accounts\.

**Note**  
Active Regions are available to everyone that uses temporary credentials in that account\. To control which IAM users or roles can access the Region, use the `aws:RequestedRegion` condition key in your permissions policies\.

**To activate or deactivate AWS STS in a Region that is enabled by default \(console\)**

1. Sign in as a root user or a user with permissions to perform IAM administration tasks\.

1. Open the [IAM console](https://console.aws.amazon.com/iam/home?#home) and in the navigation pane choose [https://console.aws.amazon.com/iam/home?#account_settings](https://console.aws.amazon.com/iam/home?#account_settings)\.

1. In the **Security Token Service \(STS\)** section **Endpoints**, find the Region that you want to configure, and then choose **Active** or **Inactive** in the **STS status** column\.

1. In the dialog box that opens, choose **Activate** or **Deactivate**\.

For Regions that must be enabled, we activate AWS STS automatically when you enable the Region\. After you enable a Region, AWS STS is always active for the Region and you cannot deactivate it\. To learn how to enable a Region, see [Managing ](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html)AWS Regions in the *AWS General Reference*\.

## Writing code to use AWS STS Regions<a name="id_credentials_temp_enable-regions_writing_code"></a>

After you activate a Region, you can direct AWS STS API calls to that Region\. The following Java code snippet demonstrates how to configure an `AWSSecurityTokenService` object to make requests to the Europe \(Ireland\) \(eu\-west\-1\) Region\.

```
EndpointConfiguration regionEndpointConfig = new EndpointConfiguration("https://sts.eu-west-1.amazonaws.com", "eu-west-1");
AWSSecurityTokenService stsRegionalClient = AWSSecurityTokenServiceClientBuilder.standard()
.withCredentials(credentials)
.withEndpointConfiguration(regionEndpointConfig)
.build();
```

AWS STS recommends that you make calls to a Regional endpoint\. To learn how to manually enable a Region, see [Managing ](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html)AWS Regions in the *AWS General Reference*\.

In the example, the first line instantiates an `EndpointConfiguration` object called `regionEndpointConfig`, passing the URL of the endpoint and the AWS Region as the parameters\.

To learn how to set AWS STS regional endpoints using an environment variable for AWS SDKs, see [AWS STS Regionalized endpoints](https://docs.aws.amazon.com/sdkref/latest/guide/feature-sts-regionalized-endpoints.html) in the *AWS SDKs and Tools Reference Guide*\.

For all other language and programming environment combinations, refer to the [documentation for the relevant SDK](https://aws.amazon.com/tools/)\.

## Regions and endpoints<a name="id_credentials_region-endpoints"></a>

The following table lists the Regions and their endpoints\. It indicates which ones are activated by default and which ones you can activate or deactivate\.

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_enable-regions.html)

¹You must [enable the Region](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html) to use it\. This automatically activates AWS STS\. You cannot manually activate or deactivate AWS STS in these Regions\.

²To use AWS in China, you need an account and credentials specific to AWS in China\.

## AWS CloudTrail and Regional endpoints<a name="sts-regions-cloudtrail"></a>

Calls to Regional endpoints, such as `us-east-2.amazonaws.com`, are logged in AWS CloudTrail the same as any call to a Regional service\. Calls to the global endpoint, `sts.amazonaws.com`, are logged as calls to a global service\. For more information, see [Logging IAM and AWS STS API calls with AWS CloudTrail](cloudtrail-integration.md)\.