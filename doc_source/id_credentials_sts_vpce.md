# Using AWS STS Interface VPC Endpoints<a name="id_credentials_sts_vpce"></a>

If you use Amazon Virtual Private Cloud \(Amazon VPC\) to host your AWS resources, you can establish a private connection between your VPC and AWS STS\. You can use this connection to enable AWS STS to communicate with your resources on your VPC without going through the public internet\.

Amazon VPC is an AWS service that you can use to launch AWS resources in a virtual network that you define\. With a VPC, you have control over your network settings, such as the IP address range, subnets, route tables, and network gateways\. To connect your VPC to AWS STS, you define an *interface VPC endpoint* for AWS STS\. The endpoint provides reliable, scalable connectivity to AWS STS without requiring an internet gateway, network address translation \(NAT\) instance, or VPN connection\. For more information, see [What Is Amazon VPC?](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html) in the *Amazon VPC User Guide*\.

Interface VPC endpoints are powered by AWS PrivateLink, an AWS technology that enables private communication between AWS services using an elastic network interface with private IP addresses\. For more information, see [AWS PrivateLink for AWS Services](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html#what-is-privatelink)\.

The following steps are for users of Amazon VPC\. For more information, see [Getting Started with Amazon VPC](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/GetStarted.html) in the *Amazon VPC User Guide*\.

## Availability<a name="id_credentials_sts_vpce_availability"></a>

AWS STS currently supports VPC endpoints in the US West \(Oregon\) Region only\.

## Create a VPC for AWS STS<a name="id_credentials_sts_vpce_create"></a>

To start using AWS STS with your VPC, create an interface VPC endpoint for AWS STS\. For more information, see [Creating an Interface Endpoint](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpce-interface.html) in the *Amazon VPC User Guide*\.

After you create the VPC endpoint, you must use the matching regional endpoint to send your AWS STS requests\. For more information, see [Activating and Deactivating AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\. When you use regional endpoints, AWS STS calls other AWS services using either public endpoints or private interface VPC endpoints, whichever are in use\. For example, assume that you have created an interface VPC endpoint for AWS STS and have already requested temporary credentials from AWS STS from resources that are located in your VPC\. In that case, these credentials begin flowing through the interface VPC endpoint by default\. 