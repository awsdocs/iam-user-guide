# Data protection in AWS Identity and Access Management<a name="data-protection"></a>

The AWS [shared responsibility model](http://aws.amazon.com/compliance/shared-responsibility-model/) applies to data protection in AWS Identity and Access Management\. As described in this model, AWS is responsible for protecting the global infrastructure that runs all of the AWS Cloud\. You are responsible for maintaining control over your content that is hosted on this infrastructure\. This content includes the security configuration and management tasks for the AWS services that you use\. For more information about data privacy, see the [Data Privacy FAQ](http://aws.amazon.com/compliance/data-privacy-faq)\. For information about data protection in Europe, see the [AWS Shared Responsibility Model and GDPR](http://aws.amazon.com/blogs/security/the-aws-shared-responsibility-model-and-gdpr/) blog post on the *AWS Security Blog*\.

For data protection purposes, we recommend that you protect AWS account credentials and set up individual user accounts with AWS Identity and Access Management \(IAM\)\. That way each user is given only the permissions necessary to fulfill their job duties\. We also recommend that you secure your data in the following ways:
+ Use multi\-factor authentication \(MFA\) with each account\.
+ Use SSL/TLS to communicate with AWS resources\. We recommend TLS 1\.2 or later\.
+ Set up API and user activity logging with AWS CloudTrail\.
+ Use AWS encryption solutions, along with all default security controls within AWS services\.
+ Use advanced managed security services such as Amazon Macie, which assists in discovering and securing sensitive data that is stored in Amazon S3\.
+ If you require FIPS 140\-2 validated cryptographic modules when accessing AWS through a command line interface or an API, use a FIPS endpoint\. For more information about the available FIPS endpoints, see [Federal Information Processing Standard \(FIPS\) 140\-2](http://aws.amazon.com/compliance/fips/)\.

We strongly recommend that you never put confidential or sensitive information, such as your customers' email addresses, into tags or free\-form fields such as a **Name** field\. This includes when you work with IAM or other AWS services using the console, API, AWS CLI, or AWS SDKs\. Any data that you enter into tags or free\-form fields used for names may be used for billing or diagnostic logs\. If you provide a URL to an external server, we strongly recommend that you do not include credentials information in the URL to validate your request to that server\.

## Data encryption in IAM and AWS STS<a name="data-encryption"></a>

Data encryption typically falls into two categories: encryption at rest and encryption in transit\.

### Encryption at rest<a name="encryption-at-rest"></a>

Data that is collected and stored by IAM is encrypted at rest\.
+ **IAM** – Data collected and stored within IAM includes IP addresses, customer account metadata, and customer identifying data that includes passwords\. Customer account metadata and customer identifying data are encrypted at rest using AES 256 or is hashed using SHA 256\.
+  **AWS STS** – AWS STS does not collect customer content except for service logs that log successful, erroneous, and faulty requests to the service\. 

### Encryption in transit<a name="encryption-in-transit"></a>

Customer identifying data, including passwords, is encrypted in transit using TLS 1\.1 and 1\.2\. All AWS STS endpoints support HTTPS for encrypting data in transit\. For a list of AWS STS endpoints, see [Regions and endpoints](id_credentials_temp_enable-regions.md#id_credentials_region-endpoints)\. 

## Key management in IAM and AWS STS<a name="key-management"></a>

You can't manage encryption keys using IAM or AWS STS\. For more information about encryption keys, see [What is AWS KMS?](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) in the AWS Key Management Service Developer Guide

## Internetwork traffic privacy in IAM and AWS STS<a name="inter-network-traffic-privacy"></a>

Requests to IAM must be made using Transport Layer Security protocol \(TLS\)\. You can secure connections to the AWS STS service by using VPC endpoints\. To learn more, see [Using AWS STS interface VPC endpoints](id_credentials_sts_vpce.md)\.