# Resources to learn more about IAM<a name="resources"></a>

IAM is a rich product, and you'll find many resources to help you learn more about how IAM can help you secure your AWS account and resources\. 

**Topics**
+ [Users and groups](#resources-users-and-groups)
+ [Credentials \(passwords, access keys, and MFA devices\)](#resources-credentials)
+ [Permissions and policies](#resources-permissions-and-policies)
+ [Federation and delegation](#resources-federation-and-delegation)
+ [IAM and other AWS products](#resources-iam-and-other-services)
+ [General security practices](#resources-general-security)
+ [General resources](#resources-general)

## Users and groups<a name="resources-users-and-groups"></a>

Consult these resources for creating, managing, and using users and groups\.
+ **[Creating your first IAM admin user and group](getting-started_create-admin-group.md)** – A step\-by\-step procedure that shows how to create an IAM users and assign permissions\.
+ **[IAM Identities \(users, groups, and roles\)](id.md)** – An in\-depth discussion of how to administer IAM users and groups\.
+  [http://aws.amazon.com/blogs/security/guidelines-for-when-to-use-accounts-users-and-groups](http://aws.amazon.com/blogs/security/guidelines-for-when-to-use-accounts-users-and-groups) – An AWS Security Blog post that discusses how to organize user access with separate AWS accounts or with IAM users and groups in a single account\.

## Credentials \(passwords, access keys, and MFA devices\)<a name="resources-credentials"></a>

Review the following guides to manage passwords for your AWS account and for IAM users\. You'll also find information about *access keys*—the secret key that you use to make programmatic calls to AWS\.
+ **[AWS Security Credentials](https://docs.aws.amazon.com/general/latest/gr/aws-security-credentials.html)** – Describes the types of credentials you use to access Amazon Web Services, explains how to create and manage them, and includes recommendations for managing access keys securely\.
+ **[Managing user passwords in AWS](id_credentials_passwords.md)** and **[Managing access keys for IAM users](id_credentials_access-keys.md)** – Describes options for managing credentials for IAM users in your account\.
+  **[Using multi\-factor authentication \(MFA\) in AWS](id_credentials_mfa.md)** – Describes how to configure your account and IAM users to require both a password and a one\-time use code that is generated on a device before sign\-in is allowed\. \(This is sometimes called two\-factor authentication\.\)

## Permissions and policies<a name="resources-permissions-and-policies"></a>

Learn the inner workings of IAM policies and find tips on the best ways to confer permissions:
+ **[Policies and permissions in IAM](access_policies.md)** – Introduces the policy language that is used to define permissions\. Describes how permissions can be attached to users or groups or, for some AWS products, to resources themselves\.
+  **[IAM JSON policy elements reference](reference_policies_elements.md)** – Provides descriptions and examples of each policy language element\.
+  **[Example IAM identity\-based policies](access_policies_examples.md)** – Shows examples of policies for common tasks in various AWS products\.
+ **[AWS Policy Generator](http://aws.amazon.com/blogs/aws/aws-policy-generator/)** – Create custom policies by choosing products and actions from a list\.
+  **[IAM Policy Simulator](https://policysim.aws.amazon.com/)** – Test whether a policy would allow or deny a specific request to AWS\.

## Federation and delegation<a name="resources-federation-and-delegation"></a>

You can grant access to resources in your AWS account for users who are authenticated \(signed in\) elsewhere\. These can be IAM users in another AWS account \(known as *delegation*\), users who are authenticated with your organization's sign\-in process, or users from an Internet identity provider like Login with Amazon, Facebook, Google, or any other OpenID Connect \(OIDC\) compatible identity provider\. In these cases, the users get temporary security credentials to access AWS resources\. 
+  **[IAM Tutorial: Delegate access across AWS accounts using IAM roles](tutorial_cross-account-with-roles.md)** – Guides you through granting cross\-account access to an IAM user in another AWS account\. 
+ **[Common scenarios for temporary credentials](id_credentials_temp.md#sts-introduction)** – Describes ways in which users can be federated into AWS after being authenticated outside of AWS\. 
+ **[Web Identity Federation Playground](http://aws.amazon.com/blogs/https:aws/the-aws-web-identity-federation-playground/)** – Lets you experiment with Login with Amazon, Google, or Facebook to authenticate and then make a call to Amazon S3\. 

## IAM and other AWS products<a name="resources-iam-and-other-services"></a>

Most AWS products are integrated with IAM so that you can use IAM features to help protect access to the resources in those products\. The following resources discuss IAM and security for some of the most popular AWS products\. For a complete list of products that work with IAM, including links to more information on each, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. 

### Using IAM with Amazon EC2<a name="resources-iam-and-ec2"></a>
+ [Controlling Access to Amazon EC2 Resources](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html) – Describes how to use IAM features to permit users to administer Amazon EC2 instances, volumes, and more\.
+  [Using instance profiles](id_roles_use_switch-role-ec2_instance-profiles.md) – Describes how to use IAM roles to securely provide credentials for applications that run on Amazon EC2 instances and that need access to other AWS products\. 

### Using IAM with Amazon S3<a name="resources-iam-and-s3"></a>
+ [Managing Access Permissions to Your Amazon S3 Resources](https://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html) – Discusses the Amazon S3 security model for buckets and objects, which includes IAM policies\.
+ [ Writing IAM Policies: Grant Access to User\-Specific Folders in an Amazon S3 Bucket](http://aws.amazon.com/blogs/security/writing-iam-policies-grant-access-to-user-specific-folders-in-an-amazon-s3-bucket) – Discusses how to let users protect their own folders in Amazon S3\. \(For more posts about Amazon S3 and IAM, choose the **S3** tag below the title of the blog post\.\) 

### Using IAM with Amazon RDS<a name="resources-iam-and-rds"></a>
+ [Using AWS Identity and Access Management \(IAM\) to Manage Access to Amazon RDS Resources](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.html) – Describes how to use IAM to control access to database instances, database snapshots, and more\. 
+ [A Primer on RDS Resource\-Level Permissions](http://aws.amazon.com/blogs/security/a-primer-on-rds-resource-level-permissions) – Describes how to use IAM to control access to specific Amazon RDS instances\. 

### Using IAM with Amazon DynamoDB<a name="resources-iam-and-ddb"></a>
+ [Using IAM to Control Access to DynamoDB Resources](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html) – Describes how to use IAM to permit users to administer DynamoDB tables and indexes\. 
+ The following video \(8:55\) explains how to provide access control for individual DynamoDB database items or attributes \(or both\)\. 

## General security practices<a name="resources-general-security"></a>

Find expert tips and guidance on the best ways to secure your AWS account and resources:
+ **[AWS Security Best Practices](https://d0.awsstatic.com/whitepapers/Security/AWS_Security_Best_Practices.pdf)** \(PDF\) – Provides an in\-depth look at how to manage security across AWS accounts and products, including suggestions for security architecture, use of IAM, encryption and data security, and more\. 
+ **[Security best practices in IAM](best-practices.md)** – Offers recommendations for ways to use IAM to help secure your AWS account and resources\. 
+ **[AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)** – Use AWS CloudTrail to track a history of API calls made to AWS and store that information in log files\. This helps you determine which users and accounts accessed resources in your account, when the calls were made, what actions were requested, and more\. 

## General resources<a name="resources-general"></a>

Explore the following resources to learn more about IAM and AWS\. 
+ [https://aws.amazon.com/iam/](https://aws.amazon.com/iam/) – General information about the AWS Identity and Access Management product\.
+ [https://forums.aws.amazon.com/forum.jspa?forumID=76](https://forums.aws.amazon.com/forum.jspa?forumID=76) – A community forum for customers to discuss technical questions related to IAM\. 
+ ** [Classes & Workshops](https://aws.amazon.com/training/course-descriptions/)** – Links to role\-based and specialty courses as well as self\-paced labs to help sharpen your AWS skills and gain practical experience\.
+ ** [AWS Developer Tools](https://aws.amazon.com/tools/)** – Links to developer tools, SDKs, IDE toolkits, and command line tools for developing and managing AWS applications\.
+ ** [AWS Whitepapers](https://aws.amazon.com/whitepapers/)** – Links to a comprehensive list of technical AWS whitepapers, covering topics such as architecture, security, and economics and authored by AWS Solutions Architects or other technical experts\.
+ ** [AWS Support Center](https://console.aws.amazon.com/support/home#/)** – The hub for creating and managing your AWS Support cases\. Also includes links to other helpful resources, such as forums, technical FAQs, service health status, and AWS Trusted Advisor\.
+ ** [AWS Support](https://aws.amazon.com/premiumsupport/)** – The primary web page for information about AWS Support, a one\-on\-one, fast\-response support channel to help you build and run applications in the cloud\.
+ ** [Contact Us](https://aws.amazon.com/contact-us/)** – A central contact point for inquiries concerning AWS billing, account, events, abuse, and other issues\. 
+ ** [AWS Site Terms](https://aws.amazon.com/terms/)** – Detailed information about our copyright and trademark; your account, license, and site access; and other topics\.