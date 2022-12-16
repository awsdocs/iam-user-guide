# Business use cases for IAM<a name="IAM_UseCases"></a>

A simple business use case for IAM can help you understand basic ways you might implement the service to control the AWS access that your users have\. The use case is described in general terms, without the mechanics of how you'd use the IAM API to achieve the results you want\. 

This use case looks at two typical ways a fictional company called Example Corp might use IAM\. The first scenario considers Amazon Elastic Compute Cloud \(Amazon EC2\)\. The second considers Amazon Simple Storage Service \(Amazon S3\)\. 

For more information about using IAM with other services from AWS, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

**Topics**
+ [Initial setup of example corp](#InitSetupExampleCorp_IAM)
+ [Use case for IAM with Amazon EC2](#UseCase_EC2)
+ [Use case for IAM with Amazon S3](#UseCase_S3)

## Initial setup of example corp<a name="InitSetupExampleCorp_IAM"></a>

Nikki Wolf and Mateo Jackson are the founders of Example Corp\. Upon starting the company, they create an AWS account and set up AWS IAM Identity Center \(successor to AWS Single Sign\-On\) \(IAM Identity Center\) to create administrative accounts to use with their AWS resources\. When you set up account access for the administrative user, IAM Identity Center creates a corresponding IAM role\. This role, which is controlled by IAM Identity Center, is created in the relevant AWS account, and the policies specified in the **AdministratorAccess** permission set are attached to the role\.

Since they now have administrator accounts, Nikki and Mateo no longer need to use their root user to access their AWS account\. They plan to only use the root user to complete the tasks that only the root user can perform\. After reviewing the security best practices they configure multi\-factor authentication \(MFA\) for their root user credentials and decide how to safeguard their root user credentials\.

As their company grows, they hire employees to work as developers, admins, testers, managers, and system administrators\. Nikki is in charge of operations, while Mateo manages the engineering teams\. They set up an Active Directory Domain Server to manage the employees accounts and manage access to internal company resources\.

To give their employees access to AWS resources, they use IAM Identity Center to connect their company's Active Directory to their AWS account\. 

Because they connected Active Directory to IAM Identity Center, the users, group, and group membership are synchronized and defined\. They must assign permission sets and roles to the different groups to give the users the correct level of access to AWS resources\. They use [AWS managed policies for job functions](access_policies_job-functions.md) in the AWS Management Console to create these permissions sets:
+ *Administrator*
+ *Billing*
+ *Developers*
+ *Network administrators*
+ *Database administrators*
+ *System administrators*
+ *Support users*

Then they assign these permissions sets to the roles assigned to their Active Directory groups\.

For a step\-by\-step guide describing the initial configuration of IAM Identity Center, see [Getting started](https://docs.aws.amazon.com/singlesignon/latest/userguide/get-started-assign-account-access-admin-user.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\. For more information about provisioning IAM Identity Center user access, see [Single sign\-on access to AWS accounts](https://docs.aws.amazon.com/singlesignon/latest/userguide/useracces.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\.

## Use case for IAM with Amazon EC2<a name="UseCase_EC2"></a>

A company like Example Corp typically uses IAM to interact with services like Amazon EC2\. To understand this part of the use case, you need a basic understanding of Amazon EC2\. For more information about Amazon EC2, go to the [Amazon EC2 User Guide for Linux Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/)\.

### Amazon EC2 permissions for the user groups<a name="EC2_PermissionsGroups"></a>

To provide "perimeter" control, Nikki attaches a policy to the AllUsers user group\. This policy denies any AWS request from a user if the originating IP address is outside Example Corp's corporate network\.

At Example Corp, different user groups require different permissions:
+ **System administrators** – Need permission to create and manage AMIs, instances, snapshots, volumes, security groups, and so on\. Nikki attaches the `AmazonEC2FullAccess` AWS managed policy to the SysAdmins user group that gives members of the group permission to use all the Amazon EC2 actions\.
+ **Developers** – Need the ability to work with instances only\. Mateo therefore creates and attaches a policy to the Developers user group that allows developers to call `DescribeInstances`, `RunInstances`, `StopInstances`, `StartInstances`, and `TerminateInstances`\. 
**Note**  
Amazon EC2 uses SSH keys, Windows passwords, and security groups to control who has access to the operating system of specific Amazon EC2 instances\. There's no method in the IAM system to allow or deny access to the operating system of a specific instance\.
+ **Support users** – Should not be able to perform any Amazon EC2 actions except listing the Amazon EC2 resources currently available\. Therefore, Nikki creates and attaches a policy to the Support users group that only lets them call Amazon EC2 "Describe" API operations\.

For examples of what these policies might look like, see [Example IAM identity\-based policies](access_policies_examples.md) and [Using AWS Identity and Access Management](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/index.html?UsingIAM.html) in the *Amazon EC2 User Guide for Linux Instances*\.

### User's job function change<a name="EC2_UserRoleChange"></a>

At some point, one of the developers, Paulo Santos, changes job functions and becomes a manager\. As a manager, Paulo becomes part of the Support users group so that he can open support cases for his developers\. Mateo moves Paulo from the Developers user group to the Support users group\. As a result of this move, his ability to interact with Amazon EC2 instances is limited\. He can't launch or start instances\. He also can't stop or terminate existing instances, even if he was the user who launched or started the instance\. He can list only the instances that Example Corp users have launched\.

## Use case for IAM with Amazon S3<a name="UseCase_S3"></a>

Companies like Example Corp would also typically use IAM with Amazon S3\. John has created an Amazon S3 bucket for the company called *aws\-s3\-bucket*\.

### Creation of other users and user groups<a name="S3_CreationOtherUsersGroups"></a>

As employees, Zhang Wei and Mary Major each need to be able to create their own data in the company's bucket\. They also need to read and write shared data that all developers work on\. To enable this, Mateo logically arranges the data in aws\-s3\-bucket using an Amazon S3 key prefix scheme as shown in the following figure\.

```
/aws-s3-bucket
    /home
        /zhang
        /major
    /share
        /developers
        /managers
```

Mateo divides the `/aws-s3-bucket` into a set of home directories for each employee, and a shared area for groups of developers and managers\.

Now Mateo creates a set of policies to assign permissions to the users and user groups:
+ **Home directory access for Zhang** – Mateo attaches a policy to Wei that lets him read, write, and list any objects with the Amazon S3 key prefix `/aws-s3-bucket/home/zhang/` 
+ **Home directory access for Major** – Mateo attaches a policy to Mary that lets her read, write, and list any objects with the Amazon S3 key prefix `/aws-s3-bucket/home/major/`
+ **Shared directory access for the developers user group** – Mateo attaches a policy to the user group that lets developers read, write, and list any objects in `/aws-s3-bucket/share/developers/`
+ **Shared directory access for the managers user group** – Mateo attaches a policy to the user group that lets managers read, write, and list objects in `/aws-s3-bucket/share/managers/`

**Note**  
Amazon S3 doesn't automatically give a user who creates a bucket or object permission to perform other actions on that bucket or object\. Therefore, in your IAM policies, you must explicitly give users permission to use the Amazon S3 resources they create\.

For examples of what these policies might look like, see [Access Control](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingAuthAccess.html) in the *Amazon Simple Storage Service User Guide*\. For information on how policies are evaluated at runtime, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\. 

### User's job function change<a name="S3_UserRoleChange"></a>

At some point, one of the developers, Zhang Wei, changes job functions and becomes a manager\. We assume that he no longer needs access to the documents in the `share/developers` directory\. Mateo, as an admin, moves Wei to the `Managers` user group and out of the `Developers` user group\. With just that simple reassignment, Wei automatically gets all permissions granted to the `Managers` user group, but can no longer access data in the `share/developers` directory\.

### Integration with a third\-party business<a name="S3_3rdPartyBusiness"></a>

Organizations often work with partner companies, consultants, and contractors\. Example Corp has a partner called the Widget Company, and a Widget Company employee named Shirley Rodriguez needs to put data into a bucket for Example Corp's use\. Nikki creates a user group called *WidgetCo* and a user named `Shirley` and adds Shirley to the WidgetCo user group\. Nikki also creates a special bucket called *aws\-s3\-bucket1* for Shirley to use\.

Nikki updates existing policies or adds new ones to accommodate the partner Widget Company\. For example, Nikki can create a new policy that denies members of the WidgetCo user group the ability to use any actions other than write\. This policy would be necessary only if there's a broad policy that gives all users access to a wide set of Amazon S3 actions\.