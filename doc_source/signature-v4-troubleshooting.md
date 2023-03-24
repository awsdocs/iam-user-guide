# Troubleshoot signed requests for AWS APIs<a name="signature-v4-troubleshooting"></a>

When you develop code that creates a signed request, you might receive HTTP 403 `SignatureDoesNotMatch` errors from the AWS services that you test against\. This error means that the signature value in your HTTP request to AWS did not match the signature that the AWS service calculated\.

**Topics**
+ [Canonicalization errors](#signature-v4-troubleshooting-canonical-errors)
+ [Credential scope errors](#signature-v4-troubleshooting-credential-scope)
+ [Key signing errors](#signature-v4-troubleshooting-key-signing)

## Canonicalization errors<a name="signature-v4-troubleshooting-canonical-errors"></a>

If you incorrectly calculated the canonical request or the string to sign, the signature verification step performed by the service fails with the following error message:

```
The request signature we calculated does not match the signature you provided
```

The error response includes the canonical request and the string to sign that the service calculated\. You can compare these strings with the strings that you calculated\.

You can also verify that you didn't send the request through a proxy that modifies the headers or the request\.

## Credential scope errors<a name="signature-v4-troubleshooting-credential-scope"></a>

The credential scope restricts a signature to a specific date, Region, and service\. This string has the following format:

```
YYYYMMDD/region/service/aws4_request
```

**Date**  
If the credential scope does not specify the same date as the x\-amz\-date header, the signature verification step fails with the following error message:

```
Date in Credential scope does not match YYYYMMDD from ISO-8601 version of date from HTTP
```

If the request specifies a time in the future, the signature verification step fails with the following error message:

```
Signature not yet current: date is still later than date
```

If the request has expired, the signature verification step fails with the following error message:

```
Signature expired: date is now earlier than date
```

**Region**  
If the credential scope does not specify the same Region as the request, the signature verification step fails with the following error message:

```
Credential should be scoped to a valid Region, not region-code
```

**Service**  
If the credential scope does not specify the same service as the host header, the signature verification step fails with the following error message:

```
Credential should be scoped to correct service: 'service'
```

**Termination string**  
If the credential scope does not end with aws4\_request, the signature verification step fails with the following error message:

```
Credential should be scoped with a valid terminator: 'aws4_request'
```

## Key signing errors<a name="signature-v4-troubleshooting-key-signing"></a>

Errors that are caused by incorrect derivation of the signing key or improper use of cryptography are more difficult to troubleshoot\. After you verify that the canonical string and the string to sign are correct, you can also check for one of the following issues:
+ The secret access key does not match the access key ID that you specified\.
+ There is a problem with your key derivation code\.

To verify that the secret key matches the access key ID, you can test them with a known working implementation\. For example, use an AWS SDK or the AWS CLI to make a request to AWS\.