# Resilience in AWS Identity and Access Management<a name="disaster-recovery-resiliency"></a>

The AWS global infrastructure is built around AWS Regions and Availability Zones\. AWS Regions have multiple physically separated and isolated Availability Zones, which are connected with low\-latency, high\-throughput, and highly redundant networking\. For more information about AWS Regions and Availability Zones, see [AWS Global Infrastructure](http://aws.amazon.com/about-aws/global-infrastructure/)\. 

AWS Identity and Access Management \(IAM\) and AWS Security Token Service \(AWS STS\) are self\-sustaining, Region\-based services that are available globally\. 

IAM is a critical AWS service\. Every operation performed in AWS must be authenticated and authorized by IAM\. IAM checks each request against the identities and policies stored in IAM to determine if the request is allowed or denied\. IAM was designed with a separate *control plane* and *data plane* so that the service authenticates even during unexpected failures\. IAM resources that are used in authorizations, such as roles and policies, are stored in the control plane\. IAM customers can change the configuration of these resources by using IAM operations such as `DeletePolicy` and `AttachRolePolicy`\. Those configuration change requests go to the control plane\. There is one IAM control plane for all commercial AWS Regions, which is located in the US East \(N\. Virginia\) Region\. The IAM system then propagates configuration changes to the IAM data planes in every [enabled AWS Region](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html#rande-manage-enable)\. The IAM data plane is essentially a read\-only replica of the IAM control plane configuration data\. Each AWS Region has a completely independent instance of the IAM data plane, which performs authentication and authorization for requests from the same Region\. In each Region, the IAM data plane is distributed across at least three Availability Zones, and has sufficient capacity to tolerate the loss of an Availability Zone without any customer impairment\. Both the IAM control and data planes were built for *zero planned downtime*, with all software updates and scaling operations performed in a manner that is invisible to customers\.

AWS STS requests always go to a single global endpoint by default\. You can use a Regional AWS STS endpoint to reduce latency or provide additional redundancy for your applications\. To learn more, see [Managing AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\.

Certain events can interrupt communication between AWS Regions over the network\. However, even when you can't communicate with the global IAM endpoint, AWS STS can still authenticate IAM principals and IAM can authorize your requests\. The specific details of an event that interrupts communication will determine your ability to access AWS services\. In most situations, you can continue to use IAM credentials in your AWS environment\. The following conditions might apply to an event that interrupts communication\.

**Access keys for IAM users**  
You can authenticate indefinitely in a Region with long\-term [access keys for IAM users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html)\. When you use the AWS Command Line Interface and APIs, you can provide AWS access keys so that AWS can verify your identity in programmatic requests\.  
As a best practice, we recommend that your users sign in with [ temporary credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_request.html) instead of long\-term access keys\.

**Temporary credentials**  
You can [request new temporary credentials](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_request.html) with the AWS STS Regional [service endpoint](https://docs.aws.amazon.com/general/latest/gr/sts.html#sts_region) for at least 24 hours\. The following API operations generate temporary credentials\.  
+ **AssumeRole**
+ **AssumeRoleWithWebIdentity**
+ **AssumeRoleWithSAML**
+ **GetFederationToken**
+ **GetSessionToken**

**Principals and permissions**  
+ You might not be able to add, modify, or remove principals or permissions in IAM\.
+ Your credentials might not reflect changes to your permissions that you recently applied in IAM\. For more information, see [Changes that I make are not always immediately visible](troubleshoot_general.md#troubleshoot_general_eventual-consistency)\.

**AWS Management Console**  
+ You might be able to use a Regional sign\-in endpoint to sign in to the AWS Management Console as an IAM user\. Regional sign\-in endpoints have the following URL format\.

  `https://{Account ID}.signin.aws.amazon.com/console?region={Region}`

  *Example: https://111122223333\.signin\.aws\.amazon\.com/console?region=us\-west\-2*
+ You might not be able to complete [Universal 2nd Factor \(U2F\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_u2f.html) multi\-factor authentication \(MFA\)\.

## Best practices for IAM resilience<a name="region-dependency-best-practices"></a>

AWS has built resilience into AWS Regions and Availability Zones\. When you observe the following IAM best practices in the systems that interact with your environment, you take advantage of that resilience\.

1. Use an AWS STS Regional [service endpoint](https://docs.aws.amazon.com/general/latest/gr/sts.html#sts_region) instead of the default global endpoint\.

1. Review the configuration of your environment for vital resources that routinely create or modify IAM resources, and prepare a fallback solution that uses existing IAM resources\.