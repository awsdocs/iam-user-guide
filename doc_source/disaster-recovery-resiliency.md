# Resilience in AWS Identity and Access Management<a name="disaster-recovery-resiliency"></a>

The AWS global infrastructure is built around AWS Regions and Availability Zones\. AWS Regions provide multiple physically separated and isolated Availability Zones, which are connected with low\-latency, high\-throughput, and highly redundant networking\. With Availability Zones, you can design and operate applications and databases that automatically fail over between zones without interruption\. Availability Zones are more highly available, fault tolerant, and scalable than traditional single or multiple data center infrastructures\. 

For more information about AWS Regions and Availability Zones, see [AWS Global Infrastructure](http://aws.amazon.com/about-aws/global-infrastructure/)\.

AWS Identity and Access Management \(IAM\) and AWS Security Token Service \(AWS STS\) are available globally\. By default, AWS STS requests go to a single global endpoint\. But you can choose to use a Regional AWS STS endpoint to reduce latency or provide additional redundancy for your applications\. To learn more, see [Managing AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\.