# Using AWS STS interface VPC endpoints<a name="id_credentials_sts_vpce"></a>

If you use Amazon Virtual Private Cloud \(Amazon VPC\) to host your AWS resources, you can establish a private connection between your VPC and AWS STS\. You can use this connection to enable AWS STS to communicate with your resources on your VPC without going through the public internet\.

Amazon VPC is an AWS service that you can use to launch AWS resources in a virtual network that you define\. With a VPC, you have control over your network settings, such as the IP address range, subnets, route tables, and network gateways\. To connect your VPC to AWS STS, you define an *interface VPC endpoint* for AWS STS\. The endpoint provides reliable, scalable connectivity to AWS STS without requiring an internet gateway, network address translation \(NAT\) instance, or VPN connection\. For more information, see [What Is Amazon VPC?](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Introduction.html) in the *Amazon VPC User Guide*\.

Interface VPC endpoints are powered by AWS PrivateLink, an AWS technology that enables private communication between AWS services using an elastic network interface with private IP addresses\. For more information, see [AWS PrivateLink for AWS Services](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html)\.

The following steps are for users of Amazon VPC\. For more information, see [Getting Started with Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/GetStarted.html) in the *Amazon VPC User Guide*\.

## Availability<a name="id_credentials_sts_vpce_availability"></a>

AWS STS currently supports VPC endpoints in the following Regions:
+ US East \(Ohio\)
+ US East \(N\. Virginia\)
+ US West \(N\. California\)
+ US West \(Oregon\)
+ Asia Pacific \(Hong Kong\)
+ Asia Pacific \(Mumbai\)
+ Asia Pacific \(Osaka\-Local\)
+ Asia Pacific \(Seoul\)
+ Asia Pacific \(Singapore\)
+ Asia Pacific \(Sydney\)
+ Asia Pacific \(Tokyo\)
+ Canada \(Central\)
+ Europe \(Frankfurt\)
+ Europe \(Ireland\)
+ Europe \(London\)
+ Europe \(Milan\)
+ Europe \(Paris\)
+ Europe \(Stockholm\)
+ Middle East \(Bahrain\)
+ Africa \(Cape Town\)
+ South America \(São Paulo\)

## Create a VPC for AWS STS<a name="id_credentials_sts_vpce_create"></a>

To start using AWS STS with your VPC, create an interface VPC endpoint for AWS STS\. For more information, see [Creating an Interface Endpoint](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html) in the *Amazon VPC User Guide*\.

After you create the VPC endpoint, you must use the matching regional endpoint to send your AWS STS requests\. AWS STS recommends that you use both the `setRegion` and `setEndpoint` methods to make calls to a Regional endpoint\. You can use the `setRegion` method alone for manually enabled Regions, such as Asia Pacific \(Hong Kong\)\. In this case, the calls are directed to the STS Regional endpoint\. To learn how to manually enable a Region, see [Managing AWS Regions](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html) in the *AWS General Reference*\. If you use the `setRegion` method alone for Regions enabled by default, the calls are directed to the global endpoint of `[https://sts.amazonaws.com](https://sts.amazonaws.com)`\.

When you use regional endpoints, AWS STS calls other AWS services using either public endpoints or private interface VPC endpoints, whichever are in use\. For example, assume that you have created an interface VPC endpoint for AWS STS and have already requested temporary credentials from AWS STS from resources that are located in your VPC\. In that case, these credentials begin flowing through the interface VPC endpoint by default\. For more information about making Regional requests using AWS STS, see [Managing AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\.