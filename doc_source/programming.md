# Calling the API by Making HTTP Query Requests<a name="programming"></a>

**Topics**
+ [Endpoints](#IAMEndpoints)
+ [HTTPS Required](#IAMHTTPSRequired)
+ [Signing IAM API Requests](#SigVersion)

This section contains general information about using the Query API for AWS Identity and Access Management \(IAM\) and AWS Security Token Service \(AWS STS\)\. For details about the API actions and errors, go to the [IAM API Reference](http://docs.aws.amazon.com/IAM/latest/APIReference/) or the [AWS Security Token Service API Reference](http://docs.aws.amazon.com/STS/latest/APIReference/)\. 

**Note**  
Instead of making direct calls to the IAM or AWS STS APIs, you can use one of the AWS SDKs\. The AWS SDKs consist of libraries and sample code for various programming languages and platforms \(Java, Ruby, \.NET, iOS, Android, etc\.\)\. The SDKs provide a convenient way to create programmatic access to IAM and AWS\. For example, the SDKs take care of tasks such as cryptographically signing requests \(see below\), managing errors, and retrying requests automatically\. For information about the AWS SDKs, including how to download and install them, see the [Tools for Amazon Web Services](http://aws.amazon.com/tools/) page\. 

The Query API for IAM and AWS STS lets you call service actions\. Query API requests are HTTPS requests that must contain an `Action` parameter to indicate the action to be performed\. IAM and AWS STS support GET and POST requests for all actions\. That is, the API does not require you to use GET for some actions and POST for others\. However, GET requests are subject to the limitation size of a URL; although this limit is browser dependent, a typical limit is 2048 bytes\. Therefore, for Query API requests that require larger sizes, you must use a POST request\. 

The response is an XML document\. For details about the response, see the individual action pages in the [IAM API Reference](http://docs.aws.amazon.com/IAM/latest/APIReference/) or the [AWS Security Token Service API Reference](http://docs.aws.amazon.com/STS/latest/APIReference/)\.

## Endpoints<a name="IAMEndpoints"></a>

IAM and AWS STS each have a single global endpoint:
+ \(IAM\) [https://iam\.amazonaws\.com](https://iam.amazonaws.com)
+ \(AWS STS\) [https://sts\.amazonaws\.com](https://sts.amazonaws.com)

**Note**  
AWS STS also supports sending requests to regional endpoints in addition to the global endpoint\. Before you can use AWS STS in a region, you must first activate STS in that region for your AWS account\. For more information about activating additional regions for AWS STS, see [Activating and Deactivating AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\.

For more information about AWS endpoints and regions for all services, see [Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/index.html?rande.html) in the *AWS General Reference*\. 

## HTTPS Required<a name="IAMHTTPSRequired"></a>

Because the Query API returns sensitive information such as security credentials, you must use HTTPS with all API requests\. 

## Signing IAM API Requests<a name="SigVersion"></a>

Requests must be signed using an access key ID and a secret access key\. We strongly recommend that you do not use your AWS account root user credentials for everyday work with IAM\. You can use the credentials for an IAM user or you can use AWS STS to generate temporary security credentials\.

To sign your API requests, we recommend using AWS Signature Version 4\. For information about using Signature Version 4, go to [Signature Version 4 Signing Process](http://docs.aws.amazon.com/general/latest/gr/signature-version-4.html) in the *AWS General Reference*\. 

If you need to use Signature Version 2, information about using Signature Version 2 is available in the [AWS General Reference](http://docs.aws.amazon.com/general/latest/gr/signing_aws_api_requests.html)\.

For more information, see the following:
+  [AWS Security Credentials](http://docs.aws.amazon.com/general/latest/gr/aws-security-credentials.html)\. Provides general information about the types of credentials used for accessing AWS\. 
+ [IAM Best Practices](best-practices.md)\. Presents a list of suggestions for using IAM service to help secure your AWS resources\. 
+ [Temporary Security Credentials](id_credentials_temp.md)\. Describes how to create and use temporary security credentials\. 