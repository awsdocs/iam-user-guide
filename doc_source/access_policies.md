# Policies and Permissions<a name="access_policies"></a>

You manage access in AWS by creating policies and attaching them to IAM identities or AWS resources\. A policy is an object in AWS that, when associated with an entity or resource, defines their permissions\. AWS evaluates these policies when a principal, such as a user, makes a request\. Permissions in the policies determine whether the request is allowed or denied\. Most policies are stored in AWS as JSON documents\.

IAM policies define permissions for an action regardless of the method that you use to perform the operation\. For example, if a policy allows the [GetUser](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html) action, then a user with that policy can get user information from the AWS Management Console, the AWS CLI, or the AWS API\. When you create an IAM user, you can set up the user to allow console or programmatic access\. The IAM user can sign in to the console using a user name and password\. Or they can use access keys to work with the CLI or API\.

## Policy Types<a name="access_policy-types"></a>

The following policy types, listed in order of frequency, are available for use in AWS\. For more details, see the sections below for each policy type\.
+ **[Identity\-based policies](#policies_id-based)** – Attach managed and inline policies to IAM identities, such as users, groups to which users belong, and roles\.
+ **[Resource\-based policies](#policies_resource-based)** – Attach inline policies to resources\. The most common examples of resource\-based policies are Amazon S3 bucket policies and IAM role trust policies\.
+ **[Organizations SCPs](#policies_scp)** – Use an AWS Organizations service control policy \(SCP\) to apply a permissions boundary to an AWS Organizations organization or organizational unit \(OU\)\.
+ **[Access control lists \(ACLs\)](#policies_acl)** – Use ACLs to control what principals can access a resource\. ACLs are similar to resource\-based policies, although they are the only policy type that does not use the JSON policy document structure\.

### Policy Permissions Categories<a name="access_permission-types"></a>

Policies can be categorized as permissions policies or permissions boundaries\.
+ **Permissions policies** – Attach permissions policies to an object in AWS to define the permissions for the object\. Within a single account, AWS evaluates all permissions policies together\. Permissions policies are the most common policies\. You can use the following policy types as permissions policies:
  + **Identity\-based policies** – When you attach a managed or inline policy to an IAM user, group, or role, the policy defines the permissions for that entity\.
  + **Resource\-based policies** – When you attach a JSON policy document to a resource, you define the permissions for that resource\. The service must support resource\-based policies\.
  + **Access control lists \(ACLs\)** – When you attach an ACL to a resource, you define a list of principals with permission to access that resource\. The resource must support ACLs\.
+ **Permissions boundaries** – You can also use policies to define the permissions boundary for a principal\. A permissions boundary controls the maximum permissions that a principal can have\. Permissions boundaries are an advanced AWS feature\. When more than one of these types of policies applies to a request, AWS [evaluates each permissions boundary separately](reference_policies_evaluation-logic.md#policy-eval-basics)\. You can apply a permissions boundary in the following situations:
  + **Organizations** – You can use an AWS Organizations service control policy \(SCP\) to apply a permissions boundary to an AWS Organizations organization or organizational unit \(OU\)\.
  + **IAM users or roles** – You can use a managed policy for a user or role's permissions boundary\. For more information, see [Permissions Boundaries for IAM Identities](access_policies_boundaries.md)\.

### Identity\-Based Policies<a name="policies_id-based"></a>

Identity\-based policies are JSON permissions policy documents that you can attach to a principal \(or identity\), such as an IAM user, role, or group\. These policies control what actions that identity can perform, on which resources, and under what conditions\. Identity\-based policies can be further categorized:
+ **Managed policies** – Standalone identity\-based policies that you can attach to multiple users, groups, and roles in your AWS account\. You can use two types of managed policies: 
  + **AWS managed policies** – Managed policies that are created and managed by AWS\. If you are new to using policies, we recommend that you start by using AWS managed policies\.
  + **Customer managed policies** – Managed policies that you create and manage in your AWS account\. Customer managed policies provide more precise control over your policies than AWS managed policies\. You can create and edit an IAM policy in the visual editor or by creating the JSON policy document directly\. For more information, see [Creating IAM Policies](access_policies_create.md) and [Editing IAM Policies](access_policies_manage-edit.md)\.
+ **Inline policies** – Policies that you create and manage and that are embedded directly into a single user, group, or role\.

To learn how to choose between a managed policy or an inline policy, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\.

### Resource\-Based Policies<a name="policies_resource-based"></a>

Resource\-based policies are JSON policy documents that you attach to a resource such as an Amazon S3 bucket\. These policies allow you to specify what actions a specified principal can perform on that resource and under what conditions\. Resource\-based policies are inline policies, and there are no managed resource\-based policies\. Remember that adding a principal to a resource\-based policy is only half of establishing the trust relationship\. You must also use an identity\-based policy to grant the principal access to the resource\.

Although IAM identities are technically AWS resources, you cannot attach a resource\-based policy to an IAM identity\. You must use identity\-based policies in IAM\. To see which services support resource\-based policies, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md)\. To learn more about resource\-based policies, see [Identity\-Based Policies and Resource\-Based Policies](access_policies_identity-vs-resource.md)\. 

*Trust policies* are resource\-based policies that are attached to a role\. They define which principals can assume the role\. When you create a role in IAM, the role must have a trust policy and a permissions policy\. The trust policy indicates who can assume the role\. The permissions policy indicates what they can do with that role\. Remember that no trusted entities can assume the role until the administrator for that account grants them permission to assume the role\. For more information, see [Granting a User Permissions to Switch Roles](id_roles_use_permissions-to-switch.md)\.

### Service Control Policies \(SCPs\)<a name="policies_scp"></a>

AWS Organizations is a service for grouping centrally managing the AWS accounts that your business owns\. If you enable all features in an organization, then you can apply service control policies \(SCPs\) to any or all of your accounts\. SCPs are JSON policies that apply a permissions boundary to an AWS Organizations organization or organizational unit \(OU\)\. This permissions boundary controls the maximum services and actions that can be accessed by the entities in those accounts\.

For more information about Organizations and SCPs, see [About Service Control Policies](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_about-scps.html) in the *AWS Organizations User Guide*\.

### Access Control Policies \(ACLs\)<a name="policies_acl"></a>

Access control policies \(ACLs\) allow you to control what principals can access a resource\. ACLs are similar to resource\-based policies, although they are the only policy type that does not use the JSON policy document format\. Amazon S3, AWS WAF, and Amazon VPC are examples of services that support ACLs\. To learn more about ACLs, see [Access Control List \(ACL\) Overview](http://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

## Policies Passed During AWS STS Role Assumption<a name="access_policies-assume-roles"></a>

An IAM role can have a permissions policy and a permissions boundary\. When you assume the role using one of the AWS STS `AssumeRole*` API operations, you can also [pass another permissions policy](id_roles_use_switch-role-api.md) that further restricts the permissions of the temporary security credentials that the API operation returns\. If your role includes more than one of these permissions types, then the role's access is determined by the intersection of all of the applicable policy types\.

For example, consider a role with a permissions boundary that allows all Amazon EC2 and CloudWatch actions\. That role has a permissions policy that allows only the `ec2:StartInstances`, `ec2:StopInstances`, and `s3:ListBucket` actions\. An administrator passes a permissions policy during AWS STS role assumption that allows starting and stopping only the `MyCompanyInstance` Amazon EC2 instance and listing the `MyCompanyBucket` Amazon S3 bucket\. When AWS evaluates the three policy types, the resulting access is the intersection of the three policy types\. In this case, anyone assuming the role can only start and stop the `MyCompanyInstance` Amazon EC2 instance\. They cannot perform the actions that appear in only one or two policy types\.

## Policies and the Root User<a name="access_policies-root"></a>

The AWS account root user is affected by some policy types but not others\. You cannot attach identity\-based policies to the root user, and you cannot set the permissions boundary for the root user\. However, you can specify the root user as the principal in a resource\-based policy or an ACL\. As a member of an account, the root user is affected by any SCPs for the account\.

## Overview of JSON Policies<a name="access_policies-json"></a>

Most policies are stored in AWS as JSON documents\. Identity\-based policies, policies used to set boundaries, or AWS STS boundary policies are JSON policy documents that you attach to a user or role\. Resource\-based policies are JSON policy documents that you attach to a resource\. SCPs are JSON policy documents with restricted syntax that you attach to an AWS Organizations organizational unit \(OU\)\. ACLs are also attached to a resource, but you must use a different syntax\.

It is not necessary for you to understand the JSON syntax\. You can use the visual editor in the AWS Management Console to create and edit customer managed policies without ever using JSON\. However, if you choose to use inline policies for groups, you are still required to create and edit those policies in the JSON editor using the console\. For more information about using the visual editor, see [Creating IAM Policies](access_policies_create.md) and [Editing IAM Policies](access_policies_manage-edit.md)\.

### JSON Policy Document Structure<a name="policies-introduction"></a>

As illustrated in the following figure, a JSON policy document includes these elements:
+ Optional policywide information at the top of the document
+ One or more individual statements**

Each statement includes information about a single permission\. If a policy includes multiple statements, AWS applies a logical `OR` across the statements when evaluating them\. If multiple policies apply to a request, AWS applies a logical `OR` across all of those policies when evaluating them\. 

![\[JSON policy document structure\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_General_Policy_Structure.diagram.png)

The information in a statement is contained within a series of elements\.
+ **Version** – Specify the version of the policy language that you want to use\. As a best practice, use the latest `2012-10-17` version\.
+ **Statement** – Use this main policy element as a container for the following elements\. You can include more than one statement in a policy\.
+ **Sid** – Include an optional statement ID to differentiate between your statements\.
+ **Effect** – Use `Allow` or `Deny` to indicate whether the policy allows or denies access\.
+ **Principal** – Indicate the account, user, role, or federated user to which you would like to allow or deny access\. If you are creating a policy to attach to a user or role, you cannot include this element\. The principal is implied as that user or role\.
+ **Action** – Include a list of actions that the policy allows or denies\.
+ **Resource** – Specify a list of resources to which the actions apply\.
+ **Condition** \(Optional\) – Specify the circumstances under which the policy grants permission\.

To learn about these and other more advanced policy elements, see [IAM JSON Policy Elements Reference](reference_policies_elements.md)\. 

### Multiple Statements and Multiple Policies<a name="policies-syntax-multiples"></a>

If you want to define more than one permission for an entity \(user, group, or role\), you can use multiple statements in a single policy, or attach multiple policies\. If you try to define multiple permissions in a single statement, your policy might not grant the access that you expect\. As a best practice, break up policies by resource type\. 

Because of the [limited size of policies](reference_iam-limits.md), it might be necessary to use multiple policies for more complex permissions\. It's also a good idea to create functional groupings of permissions in a separate customer managed policy\. For example, Create one policy for IAM user management, one for self\-management, and another policy for S3 bucket management\. Regardless of the combination of multiple statements and multiple policies, AWS [evaluates](reference_policies_evaluation-logic.md) your policies the same way\.

For example, the following policy has three statements, each of which defines a separate set of permissions within a single account\. The statements define the following:
+ The first statement, with an `Sid` \(Statement ID\) of `FirstStatement`, lets the user with the attached policy change their own password\. The `Resource` element in this statement is "`*`" \(which means "all resources"\), but in practice, the `ChangePassword` API operation \(or equivalent `change-password` CLI command\) affects only the password for the user who makes the request\. 
+ The second statement lets the user list all the Amazon S3 buckets in their AWS account\. The `Resource` element in this statement is `"*"` \(which means "all resources"\)\. But because policies don't grant access to resources in other accounts, the user can list only the buckets in their own AWS account\. 
+ The third statement lets the user list and retrieve any object that is in a bucket named `confidential-data`, but only when the user is authenticated with multi\-factor authentication \(MFA\)\. The `Condition` element in the policy enforces the MFA authentication\.

  When a policy statement contains a `Condition` element, the statement is only in effect when the `Condition` element evaluates to true\. In this case, the `Condition` evaluates to true when the user is MFA\-authenticated\. If the user is not MFA\-authenticated, this `Condition` evaluates to false\. In that case, the third statement in this policy does not apply and the user does not have access to the `confidential-data` bucket\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "FirstStatement",
      "Effect": "Allow",
      "Action": ["iam:ChangePassword"],
      "Resource": "*"
    },
    {
      "Sid": "SecondStatement",
      "Effect": "Allow",
      "Action": "s3:ListAllMyBuckets",
      "Resource": "*"
    },
    {
      "Sid": "ThirdStatement",
      "Effect": "Allow",
      "Action": [
        "s3:List*",
        "s3:Get*"
      ],
      "Resource": [
        "arn:aws:s3:::confidential-data",
        "arn:aws:s3:::confidential-data/*"
      ],
      "Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
    }
  ]
}
```

### Examples of JSON Policy Syntax<a name="policies-syntax-examples"></a>

The following identity\-based policy allows the implied principal to list a single Amazon S3 bucket named `example_bucket`: 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "s3:ListBucket",
    "Resource": "arn:aws:s3:::example_bucket"
  }
}
```

The following resource\-based policy can be attached to an Amazon S3 bucket\. The policy allows members of a specific AWS account to perform any Amazon S3 actions in the bucket named `mybucket`\. It allows any action that can be performed on a bucket or the objects within it\. \(Because the policy grants trust only to the account, individual users in the account must still be granted permissions for the specified Amazon S3 actions\.\) 

```
{
  "Version": "2012-10-17",
  "Id": "S3-Account-Permissions",
  "Statement": [{
    "Sid": "1",
    "Effect": "Allow",
    "Principal": {"AWS": ["arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:root"]},
    "Action": "s3:*",
    "Resource": [
      "arn:aws:s3:::mybucket",
      "arn:aws:s3:::mybucket/*"
    ]
  }]
}
```

To view example policies for common scenarios, see [Example Policies](access_policies_examples.md)\. 