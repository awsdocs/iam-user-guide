# Understanding how IAM works<a name="intro-structure"></a>

Before you create users, you should understand how IAM works\. IAM provides the infrastructure necessary to control authentication and authorization for your account\. The IAM infrastructure includes the following elements:

**Topics**
+ [Terms](#intro-structure-terms)
+ [Principal](#intro-structure-principal)
+ [Request](#intro-structure-request)
+ [Authentication](#intro-structure-authentication)
+ [Authorization](#intro-structure-authorization)
+ [Actions or operations](#intro-structure-actions)
+ [Resources](#intro-structure-resources)

![\[IntroToIAM_Diagram\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/intro-diagram _policies_800.png)

## Terms<a name="intro-structure-terms"></a>

Learn more about IAM terms\.

Resources  
The user, group, role, policy, and identity provider objects that are stored in IAM\. As with other AWS services, you can add, edit, and remove resources from IAM\.

Identities  
The IAM resource objects that are used to identify and group\. You can attach a policy to an IAM identity\. These include users, groups, and roles\.

Entities  
The IAM resource objects that AWS uses for authentication\. These include IAM users, federated users, and assumed IAM roles\. 

Principals  
A person or application that uses the AWS account root user, an IAM user, or an IAM role to sign in and make requests to AWS\.

## Principal<a name="intro-structure-principal"></a>

A *principal* is a person or application that can make a request for an action or operation on an AWS resource\. The principal is authenticated as the AWS account root user or an IAM entity to make requests to AWS\. As a best practice, do not use your root user credentials for your daily work\. Instead, create IAM entities \(users and roles\)\. You can also support federated users or programmatic access to allow an application to access your AWS account\.

## Request<a name="intro-structure-request"></a>

When a principal tries to use the AWS Management Console, the AWS API, or the AWS CLI, that principal sends a *request* to AWS\. The request includes the following information:
+ **Actions or operations** – The actions or operations that the principal wants to perform\. This can be an action in the AWS Management Console, or an operation in the AWS CLI or AWS API\.
+ **Resources** – The AWS resource object upon which the actions or operations are performed\.
+ **Principal** – The person or application that used an entity \(user or role\) to send the request\. Information about the principal includes the policies that are associated with the entity that the principal used to sign in\. 
+ **Environment data** – Information about the IP address, user agent, SSL enabled status, or the time of day\.
+ **Resource data** – Data related to the resource that is being requested\. This can include information such as a DynamoDB table name or a tag on an Amazon EC2 instance\.

AWS gathers the request information into a *request context*, which is used to evaluate and authorize the request\.

## Authentication<a name="intro-structure-authentication"></a>

A principal must be authenticated \(signed in to AWS\) using their credentials to send a request to AWS\. Some services, such as Amazon S3 and AWS STS, allow a few requests from anonymous users\. However, they are the exception to the rule\.

To authenticate from the console as a root user, you must sign in with your email address and password\. As an IAM user, provide your account ID or alias, and then your user name and password\. To authenticate from the API or AWS CLI, you must provide your access key and secret key\. You might also be required to provide additional security information\. For example, AWS recommends that you use multi\-factor authentication \(MFA\) to increase the security of your account\. To learn more about the IAM entities that AWS can authenticate, see [IAM users](id_users.md) and [IAM roles](id_roles.md)\.

## Authorization<a name="intro-structure-authorization"></a>

You must also be authorized \(allowed\) to complete your request\. During authorization, AWS uses values from the request context to check for policies that apply to the request\. It then uses the policies to determine whether to allow or deny the request\. Most policies are stored in AWS as [JSON documents](access_policies.md#access_policies-json) and specify the permissions for principal entities\. There are [several types of policies](access_policies.md) that can affect whether a request is authorized\. To provide your users with permissions to access the AWS resources in their own account, you need only identity\-based policies\. Resource\-based policies are popular for granting [cross\-account access](access_permissions-required.md#UserPermissionsAcrossAccounts)\. The other policy types are advanced features and should be used carefully\.

AWS checks each policy that applies to the context of your request\. If a single permissions policy includes a denied action, AWS denies the entire request and stops evaluating\. This is called an *explicit deny*\. Because requests are *denied by default*, AWS authorizes your request only if every part of your request is allowed by the applicable permissions policies\. The evaluation logic for a request within a single account follows these general rules:
+ By default, all requests are denied\. \(In general, requests made using the AWS account root user credentials for resources in the account are always allowed\.\) 
+ An explicit allow in any permissions policy \(identity\-based or resource\-based\) overrides this default\.
+ The existence of an Organizations SCP, IAM permissions boundary, or a session policy overrides the allow\. If one or more of these policy types exists, they must all allow the request\. Otherwise, it is implicitly denied\.
+ An explicit deny in any policy overrides any allows\.

To learn more about how all types of policies are evaluated, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\. If you need to make a request in a different account, a policy in the other account must allow you to access the resource *and* the IAM entity that you use to make the request must have an identity\-based policy that allows the request\.

## Actions or operations<a name="intro-structure-actions"></a>

After your request has been authenticated and authorized, AWS approves the actions or operations in your request\. Operations are defined by a service, and include things that you can do to a resource, such as viewing, creating, editing, and deleting that resource\. For example, IAM supports approximately 40 actions for a user resource, including the following actions:
+ `CreateUser`
+ `DeleteUser`
+ `GetUser`
+ `UpdateUser`

To allow a principal to perform an operation, you must include the necessary actions in a policy that applies to the principal or the affected resource\. To see a list of actions, resource types, and condition keys supported by each service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

## Resources<a name="intro-structure-resources"></a>

After AWS approves the operations in your request, they can be performed on the related resources within your account\. A resource is an object that exists within a service\. Examples include an Amazon EC2 instance, an IAM user, and an Amazon S3 bucket\. The service defines a set of actions that can be performed on each resource\. If you create a request to perform an unrelated action on a resource, that request is denied\. For example, if you request to delete an IAM role but provide an IAM group resource, the request fails\. To see AWS service tables that identify which resources are affected by an action, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.