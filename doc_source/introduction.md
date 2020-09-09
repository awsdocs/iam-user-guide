# What is IAM?<a name="introduction"></a>

AWS Identity and Access Management \(IAM\) is a web service that helps you securely control access to AWS resources\. You use IAM to control who is authenticated \(signed in\) and authorized \(has permissions\) to use resources\.

  When you first create an AWS account, you begin with a single sign\-in identity that has complete access to all AWS services and resources in the account\. This identity is called the AWS account *root user* and is accessed by signing in with the email address and password that you used to create the account\. We strongly recommend that you do not use the root user for your everyday tasks, even the administrative ones\. Instead, adhere to the [best practice of using the root user only to create your first IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#create-iam-users)\. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks\. 

**Topics**
+ [Video introduction to IAM](#intro-video)
+ [IAM features](#intro-features)
+ [Accessing IAM](#intro-accessing)
+ [Understanding how IAM works](intro-structure.md)
+ [Overview of AWS identity management: Users](introduction_identity-management.md)
+ [Overview of access management: Permissions and policies](introduction_access-management.md)
+ [What is ABAC for AWS?](introduction_attribute-based-access-control.md)
+ [Security features outside IAM](introduction_security-outside-iam.md)
+ [Quick links to common tasks](introduction_quick-links-common-tasks.md)

## Video introduction to IAM<a name="intro-video"></a>

AWS Training and Certification provides a 10\-minute video introduction to IAM:

[Introduction to AWS Identity and Access Management](https://www.aws.training/learningobject/video?id=16448)

## IAM features<a name="intro-features"></a>

IAM gives you the following features:

**Shared access to your AWS account**  
You can grant other people permission to administer and use resources in your AWS account without having to share your password or access key\. 

**Granular permissions**  
You can grant different permissions to different people for different resources\. For example, you might allow some users complete access to Amazon Elastic Compute Cloud \(Amazon EC2\), Amazon Simple Storage Service \(Amazon S3\), Amazon DynamoDB, Amazon Redshift, and other AWS services\. For other users, you can allow read\-only access to just some S3 buckets, or permission to administer just some EC2 instances, or to access your billing information but nothing else\.

**Secure access to AWS resources for applications that run on Amazon EC2**  
You can use IAM features to securely provide credentials for applications that run on EC2 instances\. These credentials provide permissions for your application to access other AWS resources\. Examples include S3 buckets and DynamoDB tables\. 

**Multi\-factor authentication \(MFA\)**  
You can add two\-factor authentication to your account and to individual users for extra security\. With MFA you or your users must provide not only a password or access key to work with your account, but also a code from a specially configured device\. 

**Identity federation**  
You can allow users who already have passwords elsewhere—for example, in your corporate network or with an internet identity provider—to get temporary access to your AWS account\. 

**Identity information for assurance**  
If you use [AWS CloudTrail](https://aws.amazon.com/cloudtrail/), you receive log records that include information about those who made requests for resources in your account\. That information is based on IAM identities\.

**PCI DSS Compliance**  
IAM supports the processing, storage, and transmission of credit card data by a merchant or service provider, and has been validated as being compliant with Payment Card Industry \(PCI\) Data Security Standard \(DSS\)\. For more information about PCI DSS, including how to request a copy of the AWS PCI Compliance Package, see [PCI DSS Level 1](https://aws.amazon.com/compliance/pci-dss-level-1-faqs/)\. 

**Integrated with many AWS services**  
For a list of AWS services that work with IAM, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. 

**Eventually Consistent**  
IAM, like many other AWS services, is [eventually consistent](https://wikipedia.org/wiki/Eventual_consistency)\. IAM achieves high availability by replicating data across multiple servers within Amazon's data centers around the world\. If a request to change some data is successful, the change is committed and safely stored\. However, the change must be replicated across IAM, which can take some time\. Such changes include creating or updating users, groups, roles, or policies\. We recommend that you do not include such IAM changes in the critical, high\-availability code paths of your application\. Instead, make IAM changes in a separate initialization or setup routine that you run less frequently\. Also, be sure to verify that the changes have been propagated before production workflows depend on them\. For more information, see [Changes that I make are not always immediately visible](troubleshoot_general.md#troubleshoot_general_eventual-consistency)\.

**Free to use**  
AWS Identity and Access Management \(IAM\) and AWS Security Token Service \(AWS STS\) are features of your AWS account offered at no additional charge\. You are charged only when you access other AWS services using your IAM users or AWS STS temporary security credentials\. For information about the pricing of other AWS products, see the [Amazon Web Services pricing page](https://aws.amazon.com/pricing/)\.

## Accessing IAM<a name="intro-accessing"></a>

You can work with AWS Identity and Access Management in any of the following ways\.

**AWS Management Console**  
The console is a browser\-based interface to manage IAM and AWS resources\. For more information about accessing IAM through the console, see [Signing in to the AWS Management Console as an IAM user or root user](console.md)\. For a tutorial that guides you through using the console, see [Creating your first IAM admin user and group](getting-started_create-admin-group.md)\.

**AWS Command Line Tools**  
You can use the AWS command line tools to issue commands at your system's command line to perform IAM and AWS tasks\. Using the command line can be faster and more convenient than the console\. The command line tools are also useful if you want to build scripts that perform AWS tasks\.  
AWS provides two sets of command line tools: the [AWS Command Line Interface](https://aws.amazon.com/cli/) \(AWS CLI\) and the [AWS Tools for Windows PowerShell](https://aws.amazon.com/powershell/)\. For information about installing and using the AWS CLI, see the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/)\. For information about installing and using the Tools for Windows PowerShell, see the [AWS Tools for Windows PowerShell User Guide](https://docs.aws.amazon.com/powershell/latest/userguide/)\.

**AWS SDKs**  
AWS provides SDKs \(software development kits\) that consist of libraries and sample code for various programming languages and platforms \(Java, Python, Ruby, \.NET, iOS, Android, etc\.\)\. The SDKs provide a convenient way to create programmatic access to IAM and AWS\. For example, the SDKs take care of tasks such as cryptographically signing requests, managing errors, and retrying requests automatically\. For information about the AWS SDKs, including how to download and install them, see the [Tools for Amazon Web Services](https://aws.amazon.com/tools/) page\.

**IAM HTTPS API**  
You can access IAM and AWS programmatically by using the IAM HTTPS API, which lets you issue HTTPS requests directly to the service\. When you use the HTTPS API, you must include code to digitally sign requests using your credentials\. For more information, see [Calling the IAM API using HTTP query requests](programming.md) and the [IAM API Reference](https://docs.aws.amazon.com/IAM/latest/APIReference/)\.