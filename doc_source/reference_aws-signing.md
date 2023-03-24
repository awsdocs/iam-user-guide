# Signing AWS API requests<a name="reference_aws-signing"></a>

**Important**  
If you use an AWS SDK or AWS command line tool to send API requests to AWS, these tools sign the API requests for you\. You must only sign AWS API requests as described in this documentation if you do not use an AWS SDK or AWS command line tool to send AWS API requests\.

When you send API requests to AWS, you must sign them so that AWS can identify the sender\. For security, most requests are signed using your AWS security credentials\.

When an AWS service receives an authenticated request, it recreates the signature using the authentication information contained in the request\. If the signatures match, the service processes the request\. Otherwise, it rejects the request\.

Signature Version 4 is the AWS signing protocol\. AWS also supports an extension, Signature Version 4A, which supports signatures for multi\-Region API requests\. For more information, see the [sigv4a\-signing\-examples](https://github.com/aws-samples/sigv4a-signing-examples) project on GitHub\.

**Topics**
+ [When to sign requests](#when-do-you-need-to-sign)
+ [Why requests are signed](#why-requests-are-signed)
+ [Elements of an AWS API request signature](signing-elements.md)
+ [Create a signed AWS API request](create-signed-request.md)
+ [Troubleshoot signed requests for AWS APIs](signature-v4-troubleshooting.md)

## When to sign requests<a name="when-do-you-need-to-sign"></a>

When you write custom code that sends API requests to AWS, you must include code that signs the requests\. You might write custom code because:
+ You are working with a programming language for which there is no AWS SDK\.
+ You need complete control over how requests are sent to AWS\.

## Why requests are signed<a name="why-requests-are-signed"></a>

The signing process helps secure requests in the following ways:
+ **Verify the identity of the requester**

  Requests must be sent by someone with a valid access key\.
+ **Protect data in transit**

  To prevent tampering with a request while it's in transit, some of the request elements are used to calculate a hash \(digest\) of the request, and the resulting hash value is included as part of the request\. When an AWS service receives the request, it uses the same information to calculate a hash and matches it against the hash value in your request\. If the values don't match, AWS denies the request\.
+ **Protect against potential replay attacks**

  In most cases, a request must reach AWS within five minutes of the time stamp in the request\. Otherwise, AWS denies the request\.