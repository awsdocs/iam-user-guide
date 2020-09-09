# Security features outside IAM<a name="introduction_security-outside-iam"></a>

You use IAM to control access to tasks that are performed using the AWS Management Console, the [AWS Command Line Tools](https://aws.amazon.com/tools/#Command_Line_Tools), or service API operations using the [AWS SDKs](https://aws.amazon.com/tools/)\. Some AWS products have other ways to secure their resources as well\. The following list provides some examples, though it is not exhaustive\. 

**Amazon EC2**  
In Amazon Elastic Compute Cloud you log into an instance with a key pair \(for Linux instances\) or using a user name and password \(for Microsoft Windows instances\)\.   
For more information, see the following documentation:   
+ [Getting Started with Amazon EC2 Linux Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html) in the *Amazon EC2 User Guide for Linux Instances*
+ [Getting Started with Amazon EC2 Windows Instances](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/EC2Win_GetStarted.html) in the *Amazon EC2 User Guide for Windows Instances*

**Amazon RDS**  
In Amazon Relational Database Service you log into the database engine with a user name and password that are tied to that database\.   
For more information, see [Getting Started with Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_GettingStarted.html) in the *Amazon RDS User Guide*\. 

**Amazon EC2 and Amazon RDS**  
In Amazon EC2 and Amazon RDS you use security groups to control traffic to an instance or database\.   
For more information, see the following documentation:   
+ [Amazon EC2 Security Groups for Linux Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html) in the *Amazon EC2 User Guide for Linux Instances*
+ [Amazon EC2 Security Groups for Windows Instances](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/using-network-security.html) in the *Amazon EC2 User Guide for Windows Instances*
+ [Amazon RDS Security Groups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html) in the *Amazon RDS User Guide*

**Amazon WorkSpaces**  
In Amazon WorkSpaces, users sign in to a desktop with a user name and password\.   
For more information, see [Getting Started with Amazon WorkSpaces](https://docs.aws.amazon.com/workspaces/latest/adminguide/getting_started.html) in the *Amazon WorkSpaces Administration Guide*\. 

**Amazon WorkDocs**  
In Amazon WorkDocs, users get access to shared documents by signing in with a user name and password\.   
For more information, see [Getting Started with Amazon WorkDocs](https://docs.aws.amazon.com/workdocs/latest/adminguide/getting_started.html) in the *Amazon WorkDocs Administration Guide*\. 

These access control methods are not part of IAM\. IAM lets you control how these AWS products are administered—creating or terminating an Amazon EC2 instance, setting up new Amazon WorkSpaces desktops, and so on\. That is, IAM helps you control the tasks that are performed by making requests to Amazon Web Services, and it helps you control access to the AWS Management Console\. However, IAM does not help you manage security for tasks like signing in to an operating system \(Amazon EC2\), database \(Amazon RDS\), desktop \(Amazon WorkSpaces\), or collaboration site \(Amazon WorkDocs\)\.

When you work with a specific AWS product, be sure to read the documentation to learn the security options for all the resources that belong to that product\. 