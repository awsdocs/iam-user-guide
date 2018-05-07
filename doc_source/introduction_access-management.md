# Overview of Access Management: Permissions and Policies<a name="introduction_access-management"></a>

The access management portion of AWS Identity and Access Management \(IAM\) helps you to define what a user or other entity is allowed to do in an account, often referred to as *authorization*\. Permissions are granted through policies\. A policy is an entity in AWS that, when attached to an identity or resource, defines their permissions\. AWS evaluates these policies when a principal, such as a user, makes a request\. Permissions in the policies determine whether the request is allowed or denied\. Policies are stored in AWS as JSON documents attached to principals as *identity\-based policies*, or to resources as *resource\-based policies*\.

## Policies and Users<a name="intro-access-users"></a>

By default, IAM users can't access anything in your account\. You grant permissions to a user by creating an identity\-based policy, which is a policy attached to the user\. The following example shows a policy that grants permission to perform all Amazon DynamoDB actions \(`dynamodb:*`\) on the Books table in the account 123456789012 within the us\-east\-2 region\.

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

 When you attach the policy to an IAM user, then the user has those DynamoDB permissions\. Typically, users in your account have multiple policies that together represent the permissions for that user\.

Any actions or resources that are not explicitly allowed are denied by default\. For example, if the above policy is the only policy attached to a user, then that user is allowed to perform DynamoDB actions on the Books table only\. Actions on all other tables are prohibited\. Similarly, the user is not allowed to perform any actions in Amazon EC2, Amazon S3, or in any other AWS service, because permissions to work with those services are not included in the policy\. 

The IAM console includes *policy summary* tables that describe the access level, resources, and conditions that are allowed or denied for each service in a policy\. Policies are summarized in three tables: the [policy summary](access_policies_understand-policy-summary.md), the [service summary](access_policies_understand-service-summary.md), and the [action summary](access_policies_understand-action-summary.md)\. The *policy summary* table includes a list of services\. Choose a service there to see the *service summary*\. This summary table includes a list of the actions and associated permissions for the chosen service\. You can choose an action from that table to view the *action summary*\. This table includes a list of resources and conditions for the chosen action\. 

![\[Policy summaries diagram image that illustrates the 3 tables and their relationship\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_summaries-diagram.png)

You can view policy summaries on the **Users** page for all policies \(managed and inline\) that are attached to that user\. View summaries on the **Policies** page for all managed policies\.

For example, the previous policy is summarized in the AWS Management Console as follows:

![\[DynamoDB Example Summary\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-summary-dynamodbexample.png)

You can also view the JSON document for the policy\. For information about viewing the summary or JSON document, see [Understanding Permissions Granted by a Policy](access_policies_understand.md)\.

## Policies and Groups<a name="intro-access-groups"></a>

You can organize IAM users into *IAM groups* and attach a policy to a group\. In that case, individual users still have their own credentials, but all the users in a group have the permissions that are attached to the group\. Use groups for easier permissions management, and to follow our [IAM Best Practices](best-practices.md)\. 

![\[Users can be organized into groups to make it easier to manage permissions, because users have the permissions assigned to a group.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/iam-intro-users-and-groups.diagram.png)

Users or groups can have multiple policies attached to them that grant different permissions\. In that case, the users' permissions are calculated based on the combination of policies\. But the basic principle still applies: If the user has not been granted an explicit permission for an action and a resource, the user does not have those permissions\. 

## Federated Users and Roles<a name="intro-access-roles"></a>

Federated users don't have permanent identities in your AWS account the way that IAM users do\. To assign permissions to federated users, you can create an entity referred to as a *role* and define permissions for the role\. When a federated user signs in to AWS, the user is associated with the role and is granted the permissions that are defined in the role\. For more information, see [Creating a Role for a Third\-Party Identity Provider \(Federation\)](id_roles_create_for-idp.md)\.

## Identity\-based and Resource\-based Policies<a name="intro-access-resource-based-policies"></a>

Identity\-based policies are permission policies that you can attach to a principal \(or identity\), such as an IAM user, role, or group\. Resource\-based policies are JSON policy documents that you attach to a resource such as an Amazon S3 bucket\.

Identity\-based policies control what actions that identity can perform, on which resources, and under what conditions\. Identity\-based policies can be further categorized:
+ **Managed policies** – Standalone identity\-based policies that you can attach to multiple users, groups, and roles in your AWS account\. You can use two types of managed policies: 
  + **AWS managed policies** – Managed policies that are created and managed by AWS\. If you are new to using policies, we recommend that you start by using AWS managed policies\.
  + **Customer managed policies** – Managed policies that you create and manage in your AWS account\. Customer managed policies provide more precise control over your policies than AWS managed policies\. You can create and edit an IAM policy in the visual editor or by creating the JSON policy document directly\. For more information, see [Creating IAM Policies](access_policies_create.md) and [Editing IAM Policies](access_policies_manage-edit.md)\.
+ **Inline policies** – Policies that you create and manage and that are *embedded* directly into a single user, group, or role\.

Resource\-based policies control what actions a specified principal can perform on that resource and under what conditions\. Resource\-based policies are inline policies, and there are no managed resource\-based policies\.

Although IAM identities are technically AWS resources, you cannot attach a resource\-based policy to an IAM identity\. You must use identity\-based policies in IAM\. To see which services support resource\-based policies, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md)\. To learn more about resource\-based policies, see [Identity\-Based Policies and Resource\-Based Policies](access_policies_identity-vs-resource.md)\. 

*Trust policies* are resource\-based policies that are attached to a role that define which principals can assume the role\. When you create a role in IAM, the role must have two things: The first is a trust policy that indicates who can assume the role\. The second is a permission policy that indicates what they can do with that role\. Remember that adding an account to the trust policy of a role is only half of establishing the trust relationship\. By default, no users in the trusted accounts can assume the role until the administrator for that account grants the users the permission to assume the role\. For more information, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

**Important**  
Throughout the AWS documentation, when we refer to an IAM policy without mentioning any of the specific categories above, we mean an identity\-based, customer managed policy\.

When a user tries to perform an operation in AWS, IAM checks all the policies that exist on the user, its groups, or the affected resource\. If there is an identity\-based policy and a resource\-based policy that apply to the same operation, then both must allow the operation\. This means that the identity\-based policy must allow the action on the resource\. This means that the resource\-based policy must also allow the action for the principal making the call\.

For example, in Amazon S3, you can attach a resource\-based policy to a bucket\. This is called a bucket policy\. The following example shows an S3 bucket policy that allows an IAM user named bob in AWS account 777788889999 to put objects into the bucket to which the policy is attached\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {"AWS": "arn:aws:iam::777788889999:user/bob"},
    "Action": [
      "s3:PutObject",
      "s3:PutObjectAcl"
    ]
  }
}
```

Resource\-based policies include a `Principal` element that specifies who is granted the permissions\. In the preceding example, the `Principal` element is set to the [Amazon Resource Name](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) \(ARN\) of an IAM user named bob in AWS account 777788889999\. This indicates that the resource \(in this case, the S3 bucket\) is accessible to that IAM user but no one else\. 