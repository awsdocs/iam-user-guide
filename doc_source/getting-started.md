# Getting started with IAM<a name="getting-started"></a>

Before you get started using IAM you should sign up for an AWS account and create your administrative user using the process described in [Getting set up with IAM](getting-set-up.md)\. Then, review core IAM concepts involved in creating roles, to get ready to walk through how to perform the necessary tasks using the AWS Management Console\.

**Note**  
This set of documentation deals primarily with the IAM service\. To learn about getting started with AWS and using multiple services to solve a problem such as building and launching your first project, see the [Getting Started Resource Center](https://aws.amazon.com/getting-started/)\.

IAM roles are a secure way to grant permissions to entities you trust\. Roles are an IAM identity that you can create in your account that has specific permissions\. An IAM role has some similarities to an IAM user\. Roles and users are both AWS identities with permissions policies that determine what the identity can and cannot do in AWS\. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it\. Also, a role does not have standard long\-term credentials such as a password or access keys associated with it\. Instead, when you assume a role, it provides you with temporary security credentials for your role session\. Using roles helps you follow the IAM best practices\. You can use a role to:
+ Enable workforce identities and Identity Center enabled applications access to the AWS Management Console using AWS IAM Identity Center \(successor to AWS Single Sign\-On\)\.
+ Delegate permission to an AWS service to carry out actions on your behalf\.
+ Enable application code running on an Amazon EC2 instance to access or modify AWS resources\.
+ Grant access to another AWS account\.

Roles have two types of policies attached to them:
+ **Trust policy** – Policy which defines which identities can assume the role\. Creating a role with the IAM console automatically creates a default trust policy that you can customize\. A role can have only one trust policy\.
+ **Permissions policy** – Policy which defines which AWS resources a role can access and the actions it can perform on those resources\. Permissions policies can be AWS managed policies, customer managed policies, or inline policies attached directly to the role\. You can attach multiple permissions policies to an IAM role\.

You can also use AWS Identity and Access Management Roles Anywhere to give access to machine identities\. Using IAM Roles Anywhere means you don't need to manage long\-term credentials for workloads running outside of AWS\. For more information, see [What is AWS Identity and Access Management Roles Anywhere?](https://docs.aws.amazon.com/rolesanywhere/latest/userguide/introduction.html) in the *AWS Identity and Access Management Roles Anywhere User Guide*\.

**Topics**
+ [How IAM users sign in to your AWS account](getting-started_how-users-sign-in.md)
+ [IAM console search](console_search.md)