# Infrastructure security in AWS Identity and Access Management<a name="infrastructure-security"></a>

As managed services, AWS Identity and Access Management \(IAM\) and AWS Security Token Service \(AWS STS\) are protected by the AWS global network security procedures that are described in the [Amazon Web Services: Overview of Security Processes](https://d0.awsstatic.com/whitepapers/Security/AWS_Security_Whitepaper.pdf) whitepaper\.

You use AWS published API calls to access IAM through the network\. Clients must support Transport Layer Security \(TLS\) 1\.0 or later\. We recommend TLS 1\.2 or later\. Clients must also support cipher suites with perfect forward secrecy \(PFS\) such as Ephemeral Diffie\-Hellman \(DHE\) or Elliptic Curve Ephemeral Diffie\-Hellman \(ECDHE\)\. Most modern systems such as Java 7 and later support these modes\.

Additionally, requests must be signed by using an access key ID and a secret access key that is associated with an IAM principal\. Or you can use AWS STS to generate temporary security credentials to sign requests\.

IAM can be accessed programmatically by using the IAM HTTPS API, which lets you issue HTTPS requests directly to the service\. The Query API returns sensitive information, including security credentials\. Therefore, you must use HTTPS with all API requests\. When you use the HTTPS API, you must include code to digitally sign requests using your credentials\.

You can call these API operations from any network location, but IAM does support resource\-based access policies, which can include restrictions based on the source IP address\. You can also use IAM policies to control access from specific Amazon Virtual Private Cloud \(Amazon VPC\) endpoints or specific VPCs\. Effectively, this isolates network access to a given IAM resource from only the specific VPC within the AWS network\.