# IAM groups<a name="id_groups"></a>

An IAM [*group*](#id_groups) is a collection of IAM users\. Groups let you specify permissions for multiple users, which can make it easier to manage the permissions for those users\. For example, you could have a group called *Admins* and give that group the types of permissions that administrators typically need\. Any user in that group automatically has the permissions that are assigned to the group\. If a new user joins your organization and needs administrator privileges, you can assign the appropriate permissions by adding the user to that group\. Similarly, if a person changes jobs in your organization, instead of editing that user's permissions, you can remove him or her from the old groups and add him or her to the appropriate new groups\.

A group cannot be identified as a `Principal` in a resource\-based policy\. A group is a way to attach policies to multiple users at one time\. When you attach an identity\-based policy to a group, all of the users in the group receive the permissions from the group\. For more information about these policy types, see [Identity\-based policies and resource\-based policies](access_policies_identity-vs-resource.md)\.

Following are some important characteristics of groups:
+ A group can contain many users, and a user can belong to multiple groups\.
+ Groups can't be nested; they can contain only users, not other groups\.
+ There's no default group that automatically includes all users in the AWS account\. If you want to have a group like that, you need to create it and assign each new user to it\.
+ The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\.

The following diagram shows a simple example of a small company\. The company owner creates an `Admins` group for users to create and manage other users as the company grows\. The `Admins` group creates a `Developers` group and a `Test` group\. Each of these groups consists of users \(humans and applications\) that interact with AWS \(Jim, Brad, DevApp1, and so on\)\. Each user has an individual set of security credentials\. In this example, each user belongs to a single group\. However, users can belong to multiple groups\. 

![\[Example of relationship between AWS accounts, users, and groups\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/Relationship_Between_Entities_Example.diagram.png)