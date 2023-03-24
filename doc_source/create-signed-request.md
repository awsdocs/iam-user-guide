# Create a signed AWS API request<a name="create-signed-request"></a>

The following is an overview of the process to create a signed request\. For more information, see the [code examples in the AWS SDKs](#code-signing-examples)\.

**Topics**
+ [Step 1: Create a canonical request](#create-canonical-request)
+ [Step 2: Create a hash of the canonical request](#create-canonical-request-hash)
+ [Step 3: Create a string to sign](#create-string-to-sign)
+ [Step 4: Calculate the signature](#calculate-signature)
+ [Step 5: Add the signature to the request](#add-signature-to-request)
+ [Temporary security credentials](#temporary-security-credentials)
+ [Code examples in the AWS SDKs](#code-signing-examples)

## Step 1: Create a canonical request<a name="create-canonical-request"></a>

Create a canonical request by concatenating the following strings, separated by newline characters\. This helps ensure that the signature that you calculate and the signature that AWS calculates can match\.

```
HTTPMethod
CanonicalUri
CanonicalQueryString
CanonicalHeaders
SignedHeaders
HashedPayload
```
+ *HTTPMethod* – The HTTP method\.
+ *CanonicalUri* – The URI\-encoded version of the absolute path component URL \(everything between the host and the question mark character \(?\) that starts the query string parameters\)\. If the absolute path is empty, use a forward slash character \(/\)\.
+ *CanonicalQueryString* – The URL\-encoded query string parameters, separated by ampersands \(&\)\. Percent\-encode reserved characters, including the space character\. Encode names and values separately\. If there are empty parameters, append the equals sign to the parameter name before encoding\. After encoding, sort the parameters alphabetically by key name\. If there is no query string, use an empty string \(""\)\.
+ *CanonicalHeaders* – The request headers, that will be signed, and their values, separated by newline characters\. Header names must use lowercase characters, must appear in alphabetical order, and must be followed by a colon \(:\)\. For the values, trim any leading or trailing spaces, convert sequential spaces to a single space, and separate the values for a multi\-value header using commas\. You must include the `host` header \(HTTP/1\.1\) or the `:authority` header \(HTTP/2\), and any `x-amz-*` headers in the signature\. You can optionally include other standard headers in the signature, such as `content-type`\.
+ *SignedHeaders* – The list of headers that you included in *CanonicalHeaders*, separated by semicolons \(;\)\. This indicates which headers are part of the signing process\. Header names must use lowercase characters and must appear in alphabetical order\.
+ *HashedPayload* – A string created using the payload in the body of the HTTP request as input to a hash function\. This string uses lowercase hexadecimal characters\. If the payload is empty, use an empty string as the input to the hash function\.

The following is an example of a canonical request that calls the Amazon EC2 `DescribeInstances` API action\.

```
GET
/
Action=DescribeInstances&Version=2016-11-15
content-type:application/x-www-form-urlencoded; charset=utf-8
host:ec2.amazonaws.com
x-amz-date:20220830T123600Z

host;x-amz-date
payload-hash
```

## Step 2: Create a hash of the canonical request<a name="create-canonical-request-hash"></a>

Create a hash \(digest\) of the canonical request using the same algorithm that you used to create the hash of the payload\. The hash of the canonical request is a string of lowercase hexadecimal characters\.

## Step 3: Create a string to sign<a name="create-string-to-sign"></a>

Create a string by concatenating the following strings, separated by newline characters\. Do not end this string with a newline character\.

```
Algorithm
RequestDateTime
CredentialScope
HashedCanonicalRequest
```
+ *Algorithm* – The algorithm used to create the hash of the canonical request\. For SHA\-256, the algorithm is `AWS4-HMAC-SHA256`\.
+ *RequestDateTime* – The date and time used in the credential scope\.
+ *CredentialScope* – The credential scope\. This restricts the resulting signature to the specified Region and service\. The string has the following format: *YYYYMMDD*/*region*/*service*/aws4\_request\.
+ *HashedCanonicalRequest* – The hash of the canonical request\.

The following is an example string to sign\.

```
AWS4-HMAC-SHA256
20220830T123600Z
20220830/us-east-1/ec2/aws4_request
canonical-request-hash
```

## Step 4: Calculate the signature<a name="calculate-signature"></a>

After you create the string to sign, you are ready to calculate the signature for the authentication information that you'll add to your request\. For each step, call the hash function with the required key and data\.

```
hash(key, data)
```

The result of each call to the hash function becomes the input for the next call to the hash function\.

**Required input**
+ A string, `Key`, that contains your secret access key
+ A string, `Date`, that contains the date used in the credential scope, in the format *YYYYMMDD*
+ A string, `Region`, that contains the Region code \(for example, `us-east-1`\)
+ A string, `Service`, that contains the service code \(for example, `ec2`\)
+ The string to sign that you created in the previous step\.

**To calculate the signature**

1. Concatenate "AWS4" and the secret access key\. Call the hash function with the concatenated string as the key and the date string as the data\.

   ```
   kDate = hash("AWS4" + Key, Date)
   ```

1. Call the hash function with the result of the previous call as the key and the Region string as the data\.

   ```
   kRegion = hash(kDate, Region)
   ```

1. Call the hash function with the result of the previous call as the key and the service string as the data\.

   ```
   kService = hash(kRegion, Service)
   ```

1. Call the hash function with the result of the previous call as the key and "aws4\_request" as the data\.

   ```
   kSigning = hash(kService, "aws4_request")
   ```

1. Call the hash function with the result of the previous call as the key and the string to sign as the data\. The result is the signature as a binary value\.

   ```
   signature = hash(kSigning, string-to-sign)
   ```

1. Convert the signature from binary to hexadecimal representation, in lowercase characters\.

## Step 5: Add the signature to the request<a name="add-signature-to-request"></a>

You can add authentication information to a request using either the HTTP `Authorization` header or query string parameters\. You can't add authentication information using both the `Authorization` header and query string parameters\.

**Example: Authorization header**  
The following example shows an `Authorization` header for the `DescribeInstances` action\. For readability, this example is formatted with line breaks\. In your code, this must be a continuous string\. There is no comma between the algorithm and `Credential`\. However, the other elements must be separated by commas\.  

```
Authorization: AWS4-HMAC-SHA256
Credential=AKIAIOSFODNN7EXAMPLE/20220830/us-east-1/ec2/aws4_request,
SignedHeaders=host;x-amz-date,
Signature=calculated-signature
```

**Example: Request with authentication parameters in the query string**  
The following example shows a query for the `DescribeInstances` action that includes the authentication information\. For readability, this example is formatted with line breaks and is not URL encoded\. In your code, the query string must be a continuous string that is URL encoded\.  

```
https://ec2.amazonaws.com/?
Action=DescribeInstances&
Version=2016-11-15&
X-Amz-Algorithm=AWS4-HMAC-SHA256&
X-Amz-Credential=AKIAIOSFODNN7EXAMPLE/20220830/us-east-1/ec2/aws4_request&
X-Amz-Date=20220830T123600Z&
X-Amz-SignedHeaders=host;x-amz-date&
X-Amz-Signature=calculated-signature
```

## Temporary security credentials<a name="temporary-security-credentials"></a>

Instead of using long\-term credentials to sign a request, you can use temporary security credentials provided by AWS Security Token Service \(AWS STS\)\.

When you use temporary security credentials, you must add `X-Amz-Security-Token` to the Authorization header or the query string to hold the session token\. Some services require that you add `X-Amz-Security-Token` to the canonical request\. Other services require only that you add `X-Amz-Security-Token` at the end, after you calculate the signature\. Check the documentation for each AWS service for details\.

## Code examples in the AWS SDKs<a name="code-signing-examples"></a>

The AWS SDKs include source code on GitHub that shows how to sign AWS API requests\.
+ AWS SDK for \.NET – [AWS4Signer\.cs](https://github.com/aws/aws-sdk-net/blob/master/sdk/src/Core/Amazon.Runtime/Internal/Auth/AWS4Signer.cs)
+ AWS SDK for C\+\+ – [AWSAuthV4Signer\.cpp](https://github.com/aws/aws-sdk-cpp/blob/main/src/aws-cpp-sdk-core/source/auth/signer/AWSAuthV4Signer.cpp)
+ AWS SDK for Go – [v4\.go](https://github.com/aws/aws-sdk-go/blob/main/aws/signer/v4/v4.go)
+ AWS SDK for Java – [BaseAws4Signer\.java](https://github.com/aws/aws-sdk-java-v2/blob/master/core/auth/src/main/java/software/amazon/awssdk/auth/signer/internal/BaseAws4Signer.java)
+ AWS SDK for JavaScript – [v4\.js](https://github.com/aws/aws-sdk-js/blob/master/lib/signers/v4.js)
+ AWS SDK for PHP – [SignatureV4\.php](https://github.com/aws/aws-sdk-php/blob/master/src/Signature/SignatureV4.php)
+ AWS SDK for Python \(Boto\) – [signers\.py](https://github.com/boto/botocore/blob/develop/botocore/signers.py)
+ AWS SDK for Ruby – [signer\.rb](https://github.com/aws/aws-sdk-ruby/blob/version-3/gems/aws-sigv4/lib/aws-sigv4/signer.rb)