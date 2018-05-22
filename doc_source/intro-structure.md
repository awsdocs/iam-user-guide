# Understanding How IAM Works<a name="intro-structure"></a>

Before you create users, you should understand how IAM works\. IAM provides the infrastructure necessary to control authentication and authorization for your account\. The IAM infrastructure includes the following elements:

**Topics**
+ [Principal](#intro-structure-principal)
+ [Request](#intro-structure-request)
+ [Authentication](#intro-structure-authentication)
+ [Authorization](#intro-structure-authorization)
+ [Actions](#intro-structure-actions)
+ [Resources](#intro-structure-resources)

![\[IntroToIAM_Diagram\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/intro-diagram_800.png)

## Principal<a name="intro-structure-principal"></a>

A principal is an entity that can take an action on an AWS resource\. Your administrative IAM user is your first *principal*\. Over time, you can allow users and services to assume a role\. You can support federated users or programmatic access to allow an application to access your AWS account\. Users, roles, federated users, and applications are all AWS principals\.

## Request<a name="intro-structure-request"></a>

When a principal tries to use the AWS Management Console, the AWS API, or the AWS CLI, that principal sends a *request* to AWS\. A request specifies the following information:
+ Actions \(or operations\) that the principal wants to perform
+ Resources upon which the actions are performed
+ Principal information, including the environment from which the request was made

Request information is assembled from several sources:
+ Principal \(the requester\), which is determined based on the authorization data\. This includes the aggregate permissions that are associated with that principal\. 
+ Environment data, such as the IP address, user agent, SSL enabled status, or the time of day\. This information is determined from the request\.
+ Resource data, or data related to the resource that is being requested\. This can include information such as a DynamoDB table name or a tag on an Amazon EC2 instance\. This information is determined from the request\.

AWS gathers this information into a *request context*, which is used to evaluate and authorize the request\.

## Authentication<a name="intro-structure-authentication"></a>

As a principal, you must be authenticated \(signed in to AWS\) to send a request to AWS\. Alternatively, a few services, like Amazon S3, allow requests from anonymous users\. To authenticate from the console, you must sign in with your user name and password\. To authenticate from the API or CLI, you must provide your access key and secret key\. You might also be required to provide additional security information\. AWS recommends that you use multi\-factor authentication \(MFA\) to increase the security of your account\. To learn more about the IAM identities that AWS can authenticate, see [Identities \(Users, Groups, and Roles\)](id.md)\.

## Authorization<a name="intro-structure-authorization"></a>

During authorization, IAM uses values from the request context to check for matching policies and determine whether to allow or deny the request\. Policies are stored in IAM as JSON documents and specify the permissions that are allowed or denied for principals \(*identity\-based policies*\) or resources \(*resource\-based policies*\)\. 

IAM checks each policy that matches the context of your request\. If a single policy includes a denied action, IAM denies the entire request and stops evaluating\. This is called an *explicit deny*\. Because requests are *denied by default*, IAM authorizes your request only if every part of your request is allowed by the matching policies\. The evaluation logic follows these rules:
+ By default, all requests are denied\.
+ An explicit allow overrides this default\.
+ An explicit deny overrides any allows\.

**Note**  
By default, only the [AWS account root user](id_root-user.md) has access to all the resources in that account\. So if you are not signed in as the root user, you must have permissions granted by a policy\.

## Actions<a name="intro-structure-actions"></a>

After your request has been authenticated and authorized, AWS approves the actions in your request\. Actions are defined by a service, and are the things that you can do to a resource, such as viewing, creating, editing, and deleting that resource\. For example, IAM supports around 40 actions for a user resource, including the following actions:
+ `CreateUser`
+ `DeleteUser`
+ `GetUser`
+ `UpdateUser`

To allow a principal to perform an action, you must include the necessary actions in a policy that applies to the principal or the affected resource\.

## Resources<a name="intro-structure-resources"></a>

After AWS approves the actions in your request, those actions can be performed on the related resources within your account\. A resource is an entity that exists within a service\. Examples include an Amazon EC2 instance, an IAM user, and an Amazon S3 bucket\. The service defines a set of actions that can be performed on each resource\. If you create a request to perform an unrelated action on a resource, that request is denied\. For example, if you request to delete an IAM role but provide an IAM group resource, the request fails\.

When you provide permissions using an identity\-based policy in IAM, then you provide permissions to access resources only within the same account\. If you need to make a request in a different account, the resource in that account must have an attached resource\-based policy that allows access from your account\. Otherwise, you must assume a role within that account with the permissions that you need\. To learn more about cross\-account permissions, see [Granting Permissions Across AWS Accounts](access_permissions-required.md#UserPermissionsAcrossAccounts) \.