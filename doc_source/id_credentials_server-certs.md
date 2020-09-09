# Managing server certificates in IAM<a name="id_credentials_server-certs"></a>

To enable HTTPS connections to your website or application in AWS, you need an SSL/TLS *server certificate*\. For certificates in a Region supported by AWS Certificate Manager \(ACM\), we recommend that you use ACM to provision, manage, and deploy your server certificates\. In unsupported Regions, you must use IAM as a certificate manager\. To learn which Regions ACM supports, see [AWS Certificate Manager endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/acm.html) in the *AWS General Reference*\.

ACM is the preferred tool to provision, manage, and deploy your server certificates\. With ACM you can request a certificate or deploy an existing ACM or external certificate to AWS resources\. Certificates provided by ACM are free and automatically renew\. In a [supported Region](https://docs.aws.amazon.com/general/latest/gr/acm.html), you can use ACM to manage server certificates from the console or programmatically\. For more information about using ACM, see the [https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html](https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html)\. For more information about requesting an ACM certificate, see [Request a Public Certificate](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-public.html) or [Request a Private Certificate](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-private.html) in the *AWS Certificate Manager User Guide*\. For more information about importing third party certificates into ACM, see [Importing Certificates](https://docs.aws.amazon.com/acm/latest/userguide/import-certificate.html) in the *AWS Certificate Manager User Guide*\.

Use IAM as a certificate manager only when you must support HTTPS connections in a Region that is not [supported by ACM](https://docs.aws.amazon.com/general/latest/gr/acm.html)\. IAM securely encrypts your private keys and stores the encrypted version in IAM SSL certificate storage\. IAM supports deploying server certificates in all Regions, but you must obtain your certificate from an external provider for use with AWS\. You cannot upload an ACM certificate to IAM\. Additionally, you cannot manage your certificates from the IAM Console\.

For more information about uploading third party certificates to IAM, see the following topics\.

**Topics**
+ [Uploading a server certificate \(AWS API\)](#upload-server-certificate)
+ [Retrieving a server certificate \(AWS API\)](#get-server-certificate)
+ [Listing server certificates \(AWS API\)](#list-server-certificates)
+ [Renaming a server certificate or updating its path \(AWS API\)](#rename-server-certificate)
+ [Deleting a server certificate \(AWS API\)](#delete-server-certificate)
+ [Troubleshooting](#server-certificate-troubleshooting)

## Uploading a server certificate \(AWS API\)<a name="upload-server-certificate"></a>

To upload a server certificate to IAM, you must provide the certificate and its matching private key\. When the certificate is not self\-signed, you must also provide a certificate chain\. \(You don't need a certificate chain when uploading a self\-signed certificate\.\) Before you upload a certificate, ensure that you have all these items and that they meet the following criteria:
+ The certificate must be valid at the time of upload\. You cannot upload a certificate before its validity period begins \(the certificate's `NotBefore` date\) or after it expires \(the certificate's `NotAfter` date\)\.
+ The private key must be unencrypted\. You cannot upload a private key that is protected by a password or passphrase\. For help decrypting an encrypted private key, see [Troubleshooting](#server-certificate-troubleshooting)\.
+ The certificate, private key, and certificate chain must all be PEM\-encoded\. For help converting these items to PEM format, see [Troubleshooting](#server-certificate-troubleshooting)\.

To use the [IAM API](https://docs.aws.amazon.com/IAM/latest/APIReference/) to upload a certificate, send an [UploadServerCertificate](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UploadServerCertificate.html) request\. The following example shows how to do this with the [AWS Command Line Interface \(AWS CLI\)](https://aws.amazon.com/cli/)\. The example assumes the following:
+ The PEM\-encoded certificate is stored in a file named `Certificate.pem`\.
+ The PEM\-encoded certificate chain is stored in a file named `CertificateChain.pem`\.
+ The PEM\-encoded, unencrypted private key is stored in a file named `PrivateKey.pem`\.

To use the following example command, replace these file names with your own and replace *ExampleCertificate* with a name for your uploaded certificate\. Type the command on one continuous line\. The following example includes line breaks and extra spaces to make it easier to read\.

```
aws iam upload-server-certificate --server-certificate-name ExampleCertificate
                                    --certificate-body file://Certificate.pem
                                    --certificate-chain file://CertificateChain.pem
                                    --private-key file://PrivateKey.pem
```

When the preceding command is successful, it returns metadata about the uploaded certificate, including its [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns), its friendly name, its identifier \(ID\), its expiration date, and more\.

**Note**  
If you are uploading a server certificate to use with Amazon CloudFront, you must specify a path using the `--path` option\. The path must begin with `/cloudfront` and must include a trailing slash \(for example, `/cloudfront/test/`\)\.

To use the AWS Tools for Windows PowerShell to upload a certificate, use [Publish\-IAMServerCertificate](https://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Publish-IAMServerCertificate.html&tocid=Publish-IAMServerCertificate)\.

## Retrieving a server certificate \(AWS API\)<a name="get-server-certificate"></a>

To use the IAM API to retrieve a certificate, send a [GetServerCertificate](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServerCertificate.html) request\. The following example shows how to do this with the AWS CLI\. Replace *ExampleCertificate* with the name of the certificate to retrieve\.

```
aws iam get-server-certificate --server-certificate-name ExampleCertificate
```

When the preceding command is successful, it returns the certificate, the certificate chain \(if one was uploaded\), and metadata about the certificate\.

**Note**  
You cannot download or retrieve a private key from IAM after you upload it\.

To use the AWS Tools for Windows PowerShell to retrieve a certificate, use [Get\-IAMServerCertificate](https://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMServerCertificate.html&tocid=Get-IAMServerCertificate)\.

## Listing server certificates \(AWS API\)<a name="list-server-certificates"></a>

To use the IAM API to list your uploaded server certificates, send a [ListServerCertificates](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListServerCertificates.html) request\. The following example shows how to do this with the AWS CLI\.

```
aws iam list-server-certificates
```

When the preceding command is successful, it returns a list that contains metadata about each certificate\.

To use the AWS Tools for Windows PowerShell to list your uploaded server certificates, use [Get\-IAMServerCertificates](https://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMServerCertificates.html&tocid=Get-IAMServerCertificates)\.

## Renaming a server certificate or updating its path \(AWS API\)<a name="rename-server-certificate"></a>

To use the IAM API to rename a server certificate or update its path, send an [UpdateServerCertificate](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateServerCertificate.html) request\. The following example shows how to do this with the AWS CLI\.

To use the following example command, replace the old and new certificate names and the certificate path, and type the command on one continuous line\. The following example includes line breaks and extra spaces to make it easier to read\.

```
aws iam update-server-certificate --server-certificate-name ExampleCertificate
                                    --new-server-certificate-name CloudFrontCertificate
                                    --new-path /cloudfront/
```

When the preceding command is successful, it does not return any output\.

To use the AWS Tools for Windows PowerShell to rename a server certificate or update its path, use [Update\-IAMServerCertificate](https://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Update-IAMServerCertificate.html&tocid=Update-IAMServerCertificate)\.

## Deleting a server certificate \(AWS API\)<a name="delete-server-certificate"></a>

To use the IAM API to delete a server certificate, send a [DeleteServerCertificate](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteServerCertificate.html) request\. The following example shows how to do this with the AWS CLI\.

To use the following example command, replace *ExampleCertificate* with the name of the certificate to delete\.

```
aws iam delete-server-certificate --server-certificate-name ExampleCertificate
```

When the preceding command is successful, it does not return any output\.

To use the AWS Tools for Windows PowerShell to delete a server certificate, use [Remove\-IAMServerCertificate](https://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMServerCertificate.html&tocid=Remove-IAMServerCertificate)\.

## Troubleshooting<a name="server-certificate-troubleshooting"></a>

Before you can upload a certificate to IAM, you must make sure that the certificate, private key, and certificate chain are all PEM\-encoded\. You must also ensure that the private key is unencrypted\. See the following examples\.

**Example PEM\-encoded certificate**  

```
-----BEGIN CERTIFICATE-----
Base64-encoded certificate
-----END CERTIFICATE-----
```

**Example PEM\-encoded, unencrypted private key**  

```
-----BEGIN RSA PRIVATE KEY-----
Base64-encoded private key
-----END RSA PRIVATE KEY-----
```

**Example PEM\-encoded certificate chain**  
A certificate chain contains one or more certificates\. You can use a text editor, the copy command in Windows, or the Linux cat command to concatenate your certificate files into a chain\. When you include multiple certificates, each certificate must certify the preceding certificate\. You accomplish this by concatenating the certificates, including the root CA certificate last\.  
The following example contains three certificates, but your certificate chain might contain more or fewer certificates\.  

```
-----BEGIN CERTIFICATE-----
Base64-encoded certificate
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
Base64-encoded certificate
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
Base64-encoded certificate
-----END CERTIFICATE-----
```

If these items are not in the right format for uploading to IAM, you can use [OpenSSL](https://openssl.org/) to convert them to the right format\.

**To convert a certificate or certificate chain from DER to PEM**  
Use the [OpenSSL **x509** command](https://openssl.org/docs/manmaster/man1/x509.html), as in the following example\. In the following example command, replace `Certificate.der` with the name of the file that contains your DER\-encoded certificate\. Replace `Certificate.pem` with the preferred name of the output file to contain the PEM\-encoded certificate\.  

```
openssl x509 -inform DER -in Certificate.der -outform PEM -out Certificate.pem
```
 

**To convert a private key from DER to PEM**  
Use the [OpenSSL **rsa** command](https://openssl.org/docs/manmaster/man1/rsa.html), as in the following example\. In the following example command, replace `PrivateKey.der` with the name of the file that contains your DER\-encoded private key\. Replace `PrivateKey.pem` with the preferred name of the output file to contain the PEM\-encoded private key\.  

```
openssl rsa -inform DER -in PrivateKey.der -outform PEM -out PrivateKey.pem
```
 

**To decrypt an encrypted private key \(remove the password or passphrase\)**  
Use the [OpenSSL **rsa** command](https://openssl.org/docs/manmaster/man1/rsa.html), as in the following example\. To use the following example command, replace `EncryptedPrivateKey.pem` with the name of the file that contains your encrypted private key\. Replace `PrivateKey.pem` with the preferred name of the output file to contain the PEM\-encoded unencrypted private key\.  

```
openssl rsa -in EncryptedPrivateKey.pem -out PrivateKey.pem
```
 

**To convert a certificate bundle from PKCS\#12 \(PFX\) to PEM**  
Use the [OpenSSL **pkcs12** command](https://openssl.org/docs/manmaster/man1/pkcs12.html), as in the following example\. In the following example command, replace `CertificateBundle.p12` with the name of the file that contains your PKCS\#12\-encoded certificate bundle\. Replace `CertificateBundle.pem` with the preferred name of the output file to contain the PEM\-encoded certificate bundle\.  

```
openssl pkcs12 -in CertificateBundle.p12 -out CertificateBundle.pem -nodes
```
 

**To convert a certificate bundle from PKCS\#7 to PEM**  
Use the [OpenSSL **pkcs7** command](https://openssl.org/docs/manmaster/man1/pkcs7.html), as in the following example\. In the following example command, replace `CertificateBundle.p7b` with the name of the file that contains your PKCS\#7\-encoded certificate bundle\. Replace `CertificateBundle.pem` with the preferred name of the output file to contain the PEM\-encoded certificate bundle\.  

```
openssl pkcs7 -in CertificateBundle.p7b -print_certs -out CertificateBundle.pem
```