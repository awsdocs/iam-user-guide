# Business Use Cases<a name="IAM_UseCases"></a>

A simple business use case for IAM can help you understand basic ways you might implement the service to control the AWS access that your users have\. The use case is described in general terms, without the mechanics of how you'd use the IAM API to achieve the results you want\. 

This use case looks at two typical ways a fictional company called Example Corp might use IAM\. The first scenario considers Amazon Elastic Compute Cloud \(Amazon EC2\)\. The second considers Amazon Simple Storage Service \(Amazon S3\)\. 

For more information about using IAM with other services from AWS, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md)\.

**Topics**
+ [Initial Setup of Example Corp](#InitSetupExampleCorp_IAM)
+ [Use Case for IAM with Amazon EC2](#UseCase_EC2)
+ [Use Case for IAM with Amazon S3](#UseCase_S3)

## Initial Setup of Example Corp<a name="InitSetupExampleCorp_IAM"></a>

Joe is the founder of Example Corp\. Upon starting the company, he creates his own AWS account and uses AWS products by himself\. Then he hires employees to work as developers, admins, testers, managers, and system administrators\. 

Joe uses the AWS Management Console with the AWS account root user credentials to create a user for himself called *Joe*, and a group called *Admins*\. He gives the Admins group permissions to perform all actions on all the AWS account's resources using the AWS managed policy [AdministratorAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AdministratorAccess)\. Then he adds the Joe user to the Admins group\. For a step\-by\-step guide to creating an Administrators group and an IAM user for yourself, then adding your user to the Administrators group, see [Creating Your First IAM Admin User and Group](getting-started_create-admin-group.md)\. 

At this point, Joe can stop using the root user's credentials to interact with AWS, and instead he begins using only his user credentials\.

Joe also creates a group called *AllUsers* so that he can easily apply any account\-wide permissions to all users in the AWS account\. He adds himself to the group\. He then creates a group called *Developers*, a group called *Testers*, a group called *Managers*, and a group called *SysAdmins*\. He creates users for each of his employees, and puts the users in their respective groups\. He also adds them all to the AllUsers group\. For information about creating groups, see [Creating IAM Groups](id_groups_create.md)\. For information about creating users, see [Creating an IAM User in Your AWS Account](id_users_create.md)\. For information about adding users to groups, see [Managing IAM Groups](id_groups_manage.md)\. 

## Use Case for IAM with Amazon EC2<a name="UseCase_EC2"></a>

A company like Example Corp typically uses IAM to interact with services like Amazon EC2\. To understand this part of the use case, you need a basic understanding of Amazon EC2\. For more information about Amazon EC2, go to the [Amazon EC2 User Guide for Linux Instances](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/)\.

### Amazon EC2 Permissions for the Groups<a name="EC2_PermissionsGroups"></a>

To provide "perimeter" control, Joe attaches a policy to the AllUsers group\. This policy denies any AWS request from a user if the originating IP address is outside Example Corp's corporate network\.

At Example Corp, different groups require different permissions:
+ **System Administrators** – Need permission to create and manage AMIs, instances, snapshots, volumes, security groups, and so on\. Joe attaches a policy to the SysAdmins group that gives members of the group permission to use all the Amazon EC2 actions\.
+ **Developers** – Need the ability to work with instances only\. Joe therefore attaches a policy to the Developers group that allows developers to call `DescribeInstances`, `RunInstances`, `StopInstances`, `StartInstances`, and `TerminateInstances`\. 
**Note**  
Amazon EC2 uses SSH keys, Windows passwords, and security groups to control who has access to the operating system of specific Amazon EC2 instances\. There's no method in the IAM system to allow or deny access to the operating system of a specific instance\.
+ **Managers** – Should not be able to perform any Amazon EC2 actions except listing the Amazon EC2 resources currently available\. Therefore, Joe attaches a policy to the Managers group that only lets them call Amazon EC2 "Describe" APIs\.

For examples of what these policies might look like, see [Example Policies](access_policies_examples.md) and [Using AWS Identity and Access Management](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/index.html?UsingIAM.html) in the *Amazon EC2 User Guide for Linux Instances*\.

### User's Role Change<a name="EC2_UserRoleChange"></a>

At some point, one of the developers, Don, changes roles and becomes a manager\. Joe moves Don from the Developers group to the Managers group\. Now that he's in the Managers group, Don's ability to interact with Amazon EC2 instances is limited\. He can't launch or start instances\. He also can't stop or terminate existing instances, even if he was the user who launched or started the instance\. He can list only the instances that Example Corp users have launched\.

## Use Case for IAM with Amazon S3<a name="UseCase_S3"></a>

Companies like Example Corp would also typically use IAM with Amazon S3\. Joe has created an Amazon S3 bucket for the company called *example\_bucket*\.

### Creation of Other Users and Groups<a name="S3_CreationOtherUsersGroups"></a>

As employees, Don and Mary each need to be able to create their own data in the company's bucket\. They also need to read and write shared data that all developers work on\. To enable this, Joe logically arranges the data in example\_bucket using an Amazon S3 key prefix scheme as shown in the following figure\.

```
/example_bucket
    /home
        /don
        /mary
    /share
        /developers
        /managers
```

Joe divides the master `/example_bucket` into a set of home directories for each employee, and a shared area for groups of developers and managers\.

Now Joe creates a set of policies to assign permissions to the users and groups:
+ **Home directory access for Don** – Joe attaches a policy to Don that lets him read, write, and list any objects with the Amazon S3 key prefix `/example_bucket/home/don/` 
+ **Home directory access for Mary** – Joe attaches a policy to Mary that lets her read, write, and list any objects with the Amazon S3 key prefix `/example_bucket/home/mary/`
+ **Shared directory access for the Developers group** – Joe attaches a policy to the group that lets developers read, write, and list any objects in `/example_bucket/share/developers/`
+ **Shared directory access for the Managers group** – Joe attaches a policy to the group that lets managers read, write, and list objects in `/example_bucket/share/managers/`

**Note**  
Amazon S3 doesn't automatically give a user who creates a bucket or object permission to perform other actions on that bucket or object\. Therefore, in your IAM policies, you must explicitly give users permission to use the Amazon S3 resources they create\.

For examples of what these policies might look like, see [Access Control](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingAuthAccess.html) in the *Amazon Simple Storage Service Developer Guide*\. For information on how policies are evaluated at run time, see [IAM JSON Policy Evaluation Logic](reference_policies_evaluation-logic.md)\. 

### User's Role Change<a name="S3_UserRoleChange"></a>

At some point, one of the developers, Don, changes roles and becomes a manager\. We assume that he no longer needs access to the documents in the `share/developers` directory\. Joe, as an admin, moves Don to the `Managers` group and out of the `Developers` group\. With just that simple reassignment, Don automatically gets all permissions granted to the `Managers` group, but can no longer access data in the `share/developers` directory\.

### Integration with a Third\-Party Business<a name="S3_3rdPartyBusiness"></a>

Organizations often work with partner companies, consultants, and contractors\. Example Corp has a partner called the Widget Company, and a Widget Company employee named Natalie needs to put data into a bucket for Example Corp's use\. Joe creates a group called *WidgetCo* and a user named `Natalie` and adds Natalie to the WidgetCo group\. Joe also creates a special bucket called *example\_partner\_bucket* for Natalie to use\.

Joe updates existing policies or adds new ones to accommodate the partner Widget Company\. For example, Joe can create a new policy that denies members of the WidgetCo group the ability to use any actions other than write\. This policy would be necessary only if there's a broad policy that gives all users access to a wide set of Amazon S3 actions\.