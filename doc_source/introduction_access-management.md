# Overview of Access Management: Permissions and Policies<a name="introduction_access-management"></a>

The access management portion of AWS Identity and Access Management \(IAM\) helps you to define what a user or other entity is allowed to do in an account, often referred to as *authorization*\. Permissions are granted through policies that are created and then attached to users, groups, or roles\.

## Policies and Users<a name="intro-access-users"></a>

By default, IAM users can't access anything in your account\. You grant permissions to a user by creating a *policy*, which is a document that defines the effect, actions, resources, and optional conditions\. The following example shows a policy that grants permission to perform Amazon DynamoDB actions \(`dynamodb:*`\) on the Books table in the account 123456789012 within the us\-east\-2 region\.

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

 When you attach the policy to a user, group, or role, then the IAM entity has those DynamoDB permissions\. Typically, users in your account have multiple policies that together represent the permissions for that user\.

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

## User\-based and Resource\-based Policies<a name="intro-access-resource-based-policies"></a>

In the previous example, you saw a policy that you can attach to a user or to a group\. When you create a policy for a user like that, you specify the actions that are permitted and the resource \(EC2 instance, RDS database, etc\.\) that the user is allowed to access\.

In some cases you can attach a policy to a resource in addition to attaching it to a user or group\. For example, in Amazon S3, you can attach a policy to a bucket\. A *resource\-based policy* contains slightly different information than a user\-based policy\. In a resource\-based policy you specify what actions are permitted and what resource is affected \(just like a user\-based policy\)\. However, you also explicitly list who is allowed access to the resource\. \(In a user\-based policy, the "who" is established by whomever the policy is attached to\.\)

The following example shows an S3 bucket policy that allows an IAM user named bob in AWS account 777788889999 to put objects into the bucket called example\-bucket\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {"AWS": "arn:aws:iam::777788889999:user/bob"},
    "Action": [
      "s3:PutObject",
      "s3:PutObjectAcl"
    ],
    "Resource": "arn:aws:s3:::example-bucket/*"
  }
}
```

Resource\-based policies include a `Principal` element that specifies who is granted the permissions\. In the preceding example, the `Principal` element is set to the [Amazon Resource Name](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) \(ARN\) of an IAM user named bob in AWS account 777788889999\. This indicates that the resource \(in this case, the S3 bucket\) is accessible to that IAM user but no one else\. 