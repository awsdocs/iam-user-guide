# Managed policies and inline policies<a name="access_policies_managed-vs-inline"></a>

When you set the permissions for an identity in IAM, you must decide whether to use an AWS managed policy, a customer managed policy, or an inline policy\. The following sections provide more information about each of the types of identity\-based policies and when to use them\.

**Topics**
+ [AWS managed policies](#aws-managed-policies)
+ [Customer managed policies](#customer-managed-policies)
+ [Inline policies](#inline-policies)
+ [Choosing between managed policies and inline policies](access_policies-choosing-managed-or-inline.md)
+ [Getting started with managed policies](access_policies-getting-started-managed.md)
+ [Converting an inline policy to a managed policy](access_policies-convert-inline-to-managed.md)
+ [Deprecated AWS managed policies](access_policies_managed-deprecated.md)

## AWS managed policies<a name="aws-managed-policies"></a>

An *AWS managed policy* is a standalone policy that is created and administered by AWS\. *Standalone policy* means that the policy has its own Amazon Resource Name \(ARN\) that includes the policy name\. For example, `arn:aws:iam::aws:policy/IAMReadOnlyAccess` is an AWS managed policy\. For more information about ARNs, see [IAM ARNs](reference_identifiers.md#identifiers-arns)\.

AWS managed policies make it convenient for you to assign appropriate permissions to users, groups, and roles\. It is faster than writing the policies yourself, and includes permissions for many common use cases\. 

You cannot change the permissions defined in AWS managed policies\. AWS occasionally updates the permissions defined in an AWS managed policy\. When AWS does this, the update affects all principal entities \(users, groups, and roles\) that the policy is attached to\. AWS is most likely to update an AWS managed policy when a new AWS service is launched or new API calls become available for existing services\. For example, the AWS managed policy called **ReadOnlyAccess** provides read\-only access to all AWS services and resources\. When AWS launches a new service, AWS updates the **ReadOnlyAccess** policy to add read\-only permissions for the new service\. The updated permissions are applied to all principal entities that the policy is attached to\. 

Full access AWS managed policies define permissions for service administrators by granting full access to a service\.
+ [AmazonDynamoDBFullAccess](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonDynamoDBFullAccess.html)
+ [IAMFullAccess](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/IAMFullAccess.html)

Power\-user AWS managed policies provide full access to AWS services and resources, but do not allow managing users and groups\.
+ [AWSCodeCommitPowerUser](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AWSCodeCommitPowerUser.html) 
+ [AWSKeyManagementServicePowerUser](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AWSKeyManagementServicePowerUser.html)

Partial\-access AWS managed policies provide specific levels of access to AWS services without allowing [permissions management](access_policies_understand-policy-summary-access-level-summaries.md#access_policies_access-level) access level permissions\. 
+ [AmazonMobileAnalyticsWriteOnlyAccess](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonMobileAnalyticsWriteOnlyAccess.html)
+ [AmazonEC2ReadOnlyAccess](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AmazonEC2ReadOnlyAccess.html) 

One particularly useful category of AWS managed policies are those designed for job functions\. These policies align closely with commonly used job functions in the IT industry and facilitate granting permissions for these job functions\. One key advantage of using job function policies is that they are maintained and updated by AWS as new services and API operations are introduced\. For example, the [AdministratorAccess](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/AdministratorAccess.html) job function provides full access and permissions delegation to every service and resource in AWS\. We recommend that you use this policy only for the account administrator\. For power users that require full access to every service except limited access to IAM and Organizations, use the [PowerUserAccess](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/PowerUserAccess.html) job function\. For a list and descriptions of the job function policies, see [AWS managed policies for job functions](access_policies_job-functions.md)\.

The following diagram illustrates AWS managed policies\. The diagram shows three AWS managed policies: **AdministratorAccess**, **PowerUserAccess**, and **AWSCloudTrailReadOnlyAccess**\. Notice that a single AWS managed policy can be attached to principal entities in different AWS accounts, and to different principal entities in a single AWS account\. 

![\[Diagram of AWS managed policies\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-aws-managed-policies.diagram.png)

## Customer managed policies<a name="customer-managed-policies"></a>

You can create standalone policies in your own AWS account that you can attach to principal entities \(users, groups, and roles\)\. You create these *customer managed policies* for your specific use cases, and you can change and update them as often as you like\. Like AWS managed policies, when you attach a policy to a principal entity, you give the entity the permissions that are defined in the policy\. When you update permissions in the policy, the changes are applied to all principal entities that the policy is attached to\.

A great way to create a customer managed policy is to start by copying an existing AWS managed policy\. That way you know that the policy is correct at the beginning and all you need to do is customize it to your environment\.

The following diagram illustrates customer managed policies\. Each policy is an entity in IAM with its own [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns) that includes the policy name\. Notice that the same policy can be attached to multiple principal entities—for example, the same **DynamoDB\-books\-app** policy is attached to two different IAM roles\.

![\[Diagram of customer managed policies\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-customer-managed-policies.diagram.png)

## Inline policies<a name="inline-policies"></a>

An inline policy is a policy created for a single IAM identity \(a user, group, or role\)\. Inline policies maintain a strict one\-to\-one relationship between a policy and an identity\. They are deleted when you delete the identity\. You can create a policy and embed it in an identity, either when you create the identity or later\. If a policy could apply to more than one entity, it’s better to use a managed policy\.

The following diagram illustrates inline policies\. Each policy is an inherent part of the user, group, or role\. Notice that two roles include the same policy \(the **DynamoDB\-books\-app** policy\), but they are not sharing a single policy\. Each role has its own copy of the policy\.

![\[Diagram of inline policies\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-inline-policies.diagram.png)