# Getting started with IAM<a name="getting-started"></a>

This topic shows you how to give access to your AWS resources by creating AWS Identity and Access Management \(IAM\) users in your AWS account\. First, you'll learn about IAM concepts you should understand before you create groups and users, and then you'll walk through how to perform the necessary tasks using the AWS Management Console\. The first task is to set up an administrators group for your AWS account\. Having an administrators group for your AWS account isn't required, but we strongly recommend it\.

**Note**  
This set of documentation deals primarily with the IAM service\. To learn about getting started with AWS and using multiple services to solve a problem such as building and launching your first project, see the [Getting Started Resource Center](https://aws.amazon.com/getting-started/)\.

The following figure shows a simple example of an AWS account with three groups\. A group is a collection of users who have similar responsibilities\. In this example, one group is for administrators \(it's called *Admins*\)\. There's also a *Developers* group and a *Test* group\. Each group has multiple users\. Each user can be in more than one group, although the figure doesn't illustrate that\. You can't put groups inside other groups\. You use policies to grant permissions to groups\.

![\[Example layout of AWS account, groups, and users\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/Account_Group_Example.diagram.png)

In the procedure that follows, you will perform the following tasks:
+ Create an Administrators group and give the group permission to access all of your AWS account's resources\.
+ Create a user for yourself and add that user to the Administrators group\.
+ Create a password for your user so you can sign in to the AWS Management Console\.

You will grant the Administrators group permission to access all your available AWS account resources\. Available resources are any AWS products you use, or that you are signed up for\. Users in the Administrators group can also access your AWS account information, *except* for your AWS account's security credentials\.

**Topics**
+ [Creating your first IAM admin user and group](getting-started_create-admin-group.md)
+ [Creating your first IAM delegated user and group](getting-started_create-delegated-user.md)
+ [How IAM users sign in to your AWS account](getting-started_how-users-sign-in.md)
+ [IAM console search](console_search.md)