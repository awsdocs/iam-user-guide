# Data protection in AWS Identity and Access Management<a name="data-protection"></a>

AWS Identity and Access Management \(IAM\) and AWS Security Token Service \(AWS STS\) conform to the AWS [shared responsibility model](http://aws.amazon.com/compliance/shared-responsibility-model/), which includes regulations and guidelines for data protection\. AWS is responsible for protecting the global infrastructure that runs all the AWS services\. AWS maintains control over data hosted on this infrastructure, including the security configuration controls for handling customer content and personal data\. AWS customers and APN partners, acting either as data controllers or data processors, are responsible for any personal data that they put in the AWS Cloud\. 

For data protection purposes, we recommend that you protect AWS account credentials and set up individual user accounts with IAM\. That way each user is given only the permissions necessary to fulfill their job duties\. We also recommend that you secure your data in the following ways:
+ Use multi\-factor authentication \(MFA\) with each account\.
+ Use SSL/TLS to communicate with AWS resources\.
+ Set up API and user activity logging with AWS CloudTrail\.
+ Use AWS encryption solutions, along with all default security controls within AWS services\.
+ Use advanced managed security services, such as Amazon Macie, which assist in discovering and securing personal data that is stored in Amazon S3\.

We strongly recommend that you never put sensitive identifying information, such as your customers' account numbers, into free\-form fields such as a **Name** field\. This includes when you work with IAM or other AWS services using the console, API, AWS CLI, or AWS SDKs\. Any data that you enter into IAM or other services might get picked up for inclusion in diagnostic logs\. When you provide a URL to an external server, don't include credentials information in the URL to validate your request to that server\.

For more information about data protection, see the [AWS Shared Responsibility Model and GDPR](http://aws.amazon.com/blogs/security/the-aws-shared-responsibility-model-and-gdpr/) blog post on the *AWS Security Blog*\.

## Data encryption in IAM and AWS STS<a name="data-encryption"></a>

Data encryption typically falls into two categories: encryption at rest and encryption in transit\.

### Encryption at rest<a name="encryption-at-rest"></a>

Data that is collected and stored by IAM is encrypted at rest\.
+ **IAM** – Data collected and stored within IAM includes IP addresses, customer account metadata, and customer identifying data, including passwords\. Customer account metadata and customer identifying data are encrypted at rest using AES 256 and SHA 256 for hashes\.
+  **AWS STS** – AWS STS does not collect customer content except for service logs that log successful, erroneous, and faulty requests to the service\. 

### Encryption in transit<a name="encryption-in-transit"></a>

Customer identifying data, including passwords, is encrypted in transit using TLS 1\.1 and 1\.2\. All AWS STS endpoints support HTTPS for encrypting data in transit\. For a list of AWS STS endpoints, see [Regions and endpoints](id_credentials_temp_enable-regions.md#id_credentials_region-endpoints)\. 

## Key management in IAM and AWS STS<a name="key-management"></a>

You can't manage encryption keys using IAM or AWS STS\. For more information about encryption keys, see [What is AWS KMS?](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) in the AWS Key Management Service Developer Guide

## Internetwork traffic privacy in IAM and AWS STS<a name="inter-network-traffic-privacy"></a>

Requests to IAM must be made using Transport Layer Security protocol \(TLS\)\. You can secure connections to the AWS STS service by using VPC endpoints\. To learn more, see [Using AWS STS interface VPC endpoints](id_credentials_sts_vpce.md)\.