# Overview of access management: Permissions and policies<a name="introduction_access-management"></a>

The access management portion of AWS Identity and Access Management \(IAM\) helps you define what a principal entity is allowed to do in an account\. A principal entity is a person or application that is authenticated using an IAM entity \(user or role\)\. Access management is often referred to as *authorization*\. You manage access in AWS by creating policies and attaching them to IAM identities \(users, groups of users, or roles\) or AWS resources\. A policy is an object in AWS that, when associated with an identity or resource, defines their permissions\. AWS evaluates these policies when a principal uses an IAM entity \(user or role\) to make a request\. Permissions in the policies determine whether the request is allowed or denied\. Most policies are stored in AWS as JSON documents\. For more information about policy types and uses, see [Policies and permissions in IAM](access_policies.md)\.

## Policies and accounts<a name="intro-access-accounts"></a>

If you manage a single account in AWS, then you define the permissions within that account using policies\. If you manage permissions across multiple accounts, it is more difficult to manage permissions for your users\. You can use IAM roles, resource\-based policies, or access control lists \(ACLs\) for cross\-account permissions\. However, if you own multiple accounts, we instead recommend using the AWS Organizations service to help you manage those permissions\. For more information, see [What is AWS Organizations?](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) in the *Organizations User Guide*\.

## Policies and users<a name="intro-access-users"></a>

IAM users are identities in the service\. When you create an IAM user, they can't access anything in your account until you give them permission\. You give permissions to a user by creating an identity\-based policy, which is a policy that is attached to the user or a group to which the user belongs\. The following example shows a JSON policy that allows the user to perform all Amazon DynamoDB actions \(`dynamodb:*`\) on the `Books` table in the `123456789012` account within the `us-east-2` Region\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "dynamodb:*",
    "Resource": "arn:aws:dynamodb:us-east-2:123456789012:table/Books"
  }
}
```

 After you attach this policy to your IAM user, the user only has those DynamoDB permissions\. Most users have multiple policies that together represent the permissions for that user\.

Actions or resources that are not explicitly allowed are denied by default\. For example, if the preceding policy is the only policy that is attached to a user, then that user is allowed to only perform DynamoDB actions on the `Books` table\. Actions on all other tables are prohibited\. Similarly, the user is not allowed to perform any actions in Amazon EC2, Amazon S3, or in any other AWS service\. The reason is that permissions to work with those services are not included in the policy\. 

The IAM console includes *policy summary* tables that describe the access level, resources, and conditions that are allowed or denied for each service in a policy\. Policies are summarized in three tables: the [policy summary](access_policies_understand-policy-summary.md), the [service summary](access_policies_understand-service-summary.md), and the [action summary](access_policies_understand-action-summary.md)\. The *policy summary* table includes a list of services\. Choose a service there to see the *service summary*\. This summary table includes a list of the actions and associated permissions for the chosen service\. You can choose an action from that table to view the *action summary*\. This table includes a list of resources and conditions for the chosen action\. 

![\[Policy summaries diagram image that illustrates the 3 tables and their relationship\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_summaries-diagram.png)

You can view policy summaries on the **Users** page for all policies \(managed and inline\) that are attached to that user\. View summaries on the **Policies** page for all managed policies\.

For example, the previous policy is summarized in the AWS Management Console as follows:

![\[DynamoDB Example Summary\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-summary-dynamodbexample.png)

You can also view the JSON document for the policy\. For information about viewing the summary or JSON document, see [Understanding permissions granted by a policy](access_policies_understand.md)\.

## Policies and groups<a name="intro-access-groups"></a>

You can organize IAM users into *IAM groups* and attach a policy to a group\. In that case, individual users still have their own credentials, but all the users in a group have the permissions that are attached to the group\. Use groups for easier permissions management, and to follow our [Security best practices in IAM](best-practices.md)\. 

![\[Users can be organized into groups to make it easier to manage permissions, because users have the permissions assigned to a group.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/iam-intro-users-and-groups.diagram.png)

Users or groups can have multiple policies attached to them that grant different permissions\. In that case, the users' permissions are calculated based on the combination of policies\. But the basic principle still applies: If the user has not been granted an explicit permission for an action and a resource, the user does not have those permissions\. 

## Federated users and roles<a name="intro-access-roles"></a>

Federated users don't have permanent identities in your AWS account the way that IAM users do\. To assign permissions to federated users, you can create an entity referred to as a *role* and define permissions for the role\. When a federated user signs in to AWS, the user is associated with the role and is granted the permissions that are defined in the role\. For more information, see [Creating a role for a third\-party Identity Provider \(federation\)](id_roles_create_for-idp.md)\.

## Identity\-based and resource\-based policies<a name="intro-access-resource-based-policies"></a>

Identity\-based policies are permissions policies that you attach to an IAM identity, such as an IAM user, group, or role\. Resource\-based policies are permissions policies that you attach to a resource such as an Amazon S3 bucket or an IAM role trust policy\.

***Identity\-based policies*** control what actions the identity can perform, on which resources, and under what conditions\. Identity\-based policies can be further categorized:
+ **Managed policies** – Standalone identity\-based policies that you can attach to multiple users, groups, and roles in your AWS account\. You can use two types of managed policies: 
  + **AWS managed policies** – Managed policies that are created and managed by AWS\. If you are new to using policies, we recommend that you start by using AWS managed policies\.
  + **Customer managed policies** – Managed policies that you create and manage in your AWS account\. Customer managed policies provide more precise control over your policies than AWS managed policies\. You can create and edit an IAM policy in the visual editor or by creating the JSON policy document directly\. For more information, see [Creating IAM policies](access_policies_create.md) and [Editing IAM policies](access_policies_manage-edit.md)\.
+ **Inline policies** – Policies that you create and manage and that are embedded directly into a single user, group, or role\. In most cases, we don't recommend using inline policies\.

***Resource\-based policies*** control what actions a specified principal can perform on that resource and under what conditions\. Resource\-based policies are inline policies, and there are no managed resource\-based policies\. To enable cross\-account access, you can specify an entire account or IAM entities in another account as the principal in a resource\-based policy\.

The IAM service supports only one type of resource\-based policy called a role *trust policy*, which is attached to an IAM role\. Because an IAM role is both an identity and a resource that supports resource\-based policies, you must attach both a trust policy and an identity\-based policy to an IAM role\. Trust policies define which principal entities \(accounts, users, roles, and federated users\) can assume the role\. To learn how IAM roles are different from other resource\-based policies, see [How IAM roles differ from resource\-based policies](id_roles_compare-resource-policies.md)\.

To see which services support resource\-based policies, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. To learn more about resource\-based policies, see [Identity\-based policies and resource\-based policies](access_policies_identity-vs-resource.md)\.