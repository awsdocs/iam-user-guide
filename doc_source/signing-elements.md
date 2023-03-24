# Elements of an AWS API request signature<a name="signing-elements"></a>

Each HTTP/HTTPS request that uses Signature Version 4 signing must contain these elements\.

**Topics**
+ [Endpoint specification](#endpoint-specification)
+ [Action](#action)
+ [Action parameters](#parameters)
+ [Date](#date)
+ [Authentication information](#authentication)

## Endpoint specification<a name="endpoint-specification"></a>

Specifies the DNS name of the endpoint to which you send the request\. This name usually contains the service code and the Region\. For example, the endpoint for Amazon DynamoDB in the `us-east-1` Region is `dynamodb.us-east-1.amazonaws.com`\.

For HTTP/1\.1 requests, you must include the `Host` header\. For HTTP/2 requests, you can include the `:authority` header or the `Host` header\. Use only the `:authority` header for compliance with the HTTP/2 specification\. Not all services support HTTP/2 requests\.

For the endpoints supported by each service, see [Service endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html) in the *AWS General Reference*\.

## Action<a name="action"></a>

Specifies an API action for the service\. For example, the DynamoDB `CreateTable` action or the Amazon EC2 `DescribeInstances` action\.

For the actions supported by each service, see the [Service Authorization Reference](https://docs.aws.amazon.com/service-authorization/latest/reference/)\.

## Action parameters<a name="parameters"></a>

Specifies the parameters for the action specified in the request\. Each AWS API action has a set of required and optional parameters\. The API version is usually a required parameter\.

For the parameters supported by an API action, see the [API Reference](https://docs.aws.amazon.com/index.html) for the service\.

## Date<a name="date"></a>

Specifies the date and time of the request\. Including the date and time in a request helps prevent third parties from intercepting your request and resubmitting it later\. The date that you specify in the credential scope must match the date of your request\.

The time stamp must be in UTC and use the following ISO 8601 format: *YYYYMMDD*T*HHMMSS*Z\. For example, `20220830T123600Z`\. Do not include milliseconds in the time stamp\.

You can use a `date` or an `x-amz-date` header, or include `x-amz-date` as a query parameter\. If we can't find an `x-amz-date` header, then we look for a `date` header\.

## Authentication information<a name="authentication"></a>

Each request that you send must include the following information\. AWS uses this information to ensure the validity and authenticity of the request\.
+ Algorithm – Use `AWS4-HMAC-SHA256` to specify Signature Version 4 with the `HMAC-SHA256` hash algorithm\.
+ Credential – A string that consists of your access key ID, the date in *YYYYMMDD* format, the Region code, the service code, and the `aws4_request` termination string, separated by slashes \(/\)\. The Region code, service code, and termination string must use lowercase characters\.

  ```
  AKIAIOSFODNN7EXAMPLE/YYYYMMDD/region/service/aws4_request
  ```
+ Signed headers – The HTTP headers to include in the signature, separated by semicolons \(;\)\. For example, `host;x-amz-date`\.
+ Signature – A hexadecimal\-encoded string that represents the calculated signature\. You must calculate the signature using the algorithm that you specified in the `Algorithm` parameter\. 