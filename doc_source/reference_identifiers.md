# IAM Identifiers<a name="reference_identifiers"></a>

IAM uses a few different identifiers for users, groups, roles, policies, and server certificates\. This section describes the identifiers and when you use each\.

**Topics**
+ [Friendly Names and Paths](#identifiers-friendly-names)
+ [IAM ARNs](#identifiers-arns)
+ [Unique IDs](#identifiers-unique-ids)

## Friendly Names and Paths<a name="identifiers-friendly-names"></a>

When you create a user, a role, a group, or a policy, or when you upload a server certificate, you give it a friendly name, such as Bob, TestApp1, Developers, ManageCredentialsPermissions, or ProdServerCert\. 

If you are using the IAM API or AWS Command Line Interface \(AWS CLI\) to create IAM entities, you can also give the entity an optional path\. You can use a single path, or nest multiple paths as if they were a folder structure\. For example, you could use the nested path `/division_abc/subdivision_xyz/product_1234/engineering/` to match your company's organizational structure\. You could then create a policy to allow all users in that path to access the policy simulator API\. To view this policy, see [IAM: Access the Policy Simulator API Based on User Path](reference_policies_examples_iam_policy-sim-path.md)\. For additional examples of how you might use paths, see [IAM ARNs](#identifiers-arns)\.

Just because you give a user and group the same path doesn't automatically put that user in that group\. For example, you might create a Developers group and specify its path as /division\_abc/subdivision\_xyz/product\_1234/engineering/\. Just because you create a user named Bob and give him that same path doesn't automatically put Bob in the Developers group\. IAM doesn't enforce any boundaries between users or groups based on their paths\. Users with different paths can use the same resources \(assuming they've been granted permission to those resources\)\. For information about limitations on names, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.

## IAM ARNs<a name="identifiers-arns"></a>

Most resources have a friendly name \(for example, a user named `Bob` or a group named `Developers`\)\. However, the permission policy language requires you to specify the resource or resources using the following *Amazon Resource Name \(ARN\)* format\. 

```
arn:partition:service:region:account:resource
```

Where:
+ `partition` identifies the partition that the resource is in\. For standard AWS regions, the partition is `aws`\. If you have resourses in other partitions, the partition is `aws-partitionname`\. For example, the partition for resources in the China \(Beijing\) region is `aws-cn`\.
+ `service` identifies the AWS product\. For IAM resources, this is always `iam`\.
+ `region` is the region the resource resides in\. For IAM resources, this is always left blank\.
+ `account` is the AWS account ID with no hyphens \(for example, 123456789012\)\.
+ `resource` is the portion that identifies the specific resource by name\.

You can use ARNs in IAM for users \(IAM and federated\), groups, roles, policies, instance profiles, virtual MFA devices, and [server certificates](id_credentials_server-certs.md)\. The following table shows the ARN format for each and an example\. The region portion of the ARN is blank because IAM resources are global\. 

**Note**  
Many of the following examples include paths in the resource part of the ARN\. Paths cannot be created or manipulated in the AWS Management Console\. To use paths you must work with the resource by using the AWS API, the AWS CLI, or the Tools for Windows PowerShell\.

The following examples show ARNs for different types of IAM resources\.
+ *The AWS account \- the account itself:*

  `arn:aws:iam::123456789012:root`
+ *An IAM user in the account:*

  `arn:aws:iam::123456789012:user/Bob`
+ *Another user with a path reflecting an organization chart:*

  `arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/Bob`
+ *An IAM group:*

  `arn:aws:iam::123456789012:group/Developers`
+ *An IAM group with a path:*

  `arn:aws:iam::123456789012:group/division_abc/subdivision_xyz/product_A/Developers`
+ *An IAM role:*

  `arn:aws:iam::123456789012:role/S3Access`
+ *A managed policy:*

  `arn:aws:iam::123456789012:policy/ManageCredentialsPermissions`
+ *An instance profile that can be associated with an EC2 instance:*

  `arn:aws:iam::123456789012:instance-profile/Webserver` 
+ *A federated user identified in IAM as "Bob":*

  `arn:aws:sts::123456789012:federated-user/Bob`
+ *The active session of someone assuming the role of "Accounting\-Role", with a role session name of "Mary":*

  `arn:aws:sts::123456789012:assumed-role/Accounting-Role/Mary` 
+ *The multi\-factor authentication device assigned to the user named Bob:*

  `arn:aws:iam::123456789012:mfa/Bob`
+ *A server certificate*

  `arn:aws:iam::123456789012:server-certificate/ProdServerCert` 
+ *A server certificate with a path that reflects an organization chart:*

  `arn:aws:iam::123456789012:server-certificate/division_abc/subdivision_xyz/ProdServerCert`
+ *Identity providers \(SAML and OIDC\):*

  `arn:aws:iam::123456789012:saml-provider/ADFSProvider`

  `arn:aws:iam::123456789012:oidc-provider/GoogleProvider` 

The following example shows a policy you could assign to Bob to allow him to manage his own access keys\. Notice that the resource is the IAM user Bob\.

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": ["iam:*AccessKey*"],
    "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:user/division_abc/subdivision_xyz/Bob"
  }]
}
```

**Note**  
When you use ARNs to identify resources in an IAM policy, you can include *policy variables* that let you include placeholders for run\-time information \(such as the user's name\) as part of the ARN\. For more information, see [IAM Policy Elements: Variables](reference_policies_variables.md) 

You can use wildcards in the *resource* portion of the ARN to specify multiple users or groups or policies\. For example, to specify all users working on product\_1234, you would use:

```
arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/product_1234/*
```

Let's say you have users whose names start with the string `app_`\. You could refer to them all with the following ARN\.

```
arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/product_1234/app_*
```

To specify all users, groups, or policies in your AWS account, use a wildcard after the `user/`, `group/`, or `policy` part of the ARN, respectively\.

```
arn:aws:iam::123456789012:user/*
arn:aws:iam::123456789012:group/*
arn:aws:iam::123456789012:policy/*
```

Don't use a wildcard in the `user/`, `group/`, or `policy` part of the ARN\. In other words, the following is not allowed:

```
arn:aws:iam::123456789012:u*
```

**Example Use of Paths and ARNs for a Project\-Based Group**  
Paths cannot be created or manipulated in the AWS Management Console\. To use paths you must work with the resource by using the AWS API, the AWS CLI, or the Tools for Windows PowerShell\.  
In this example, Jules in the Marketing\_Admin group creates a project\-based group within the /marketing/ path, and assigns users from different parts of the company to the group\. This example illustrates that a user's path isn't related to the groups the user is in\.  
The marketing group has a new product they'll be launching, so Jules creates a new group in the /marketing/ path called Widget\_Launch\. Jules then assigns the following policy to the group, which gives the group access to objects in the part of the example\_bucket designated to this particular launch\.   

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::example_bucket/marketing/newproductlaunch/widget/*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket*",
      "Resource": "arn:aws:s3:::example_bucket",
      "Condition": {"StringLike": {"s3:prefix": "marketing/newproductlaunch/widget/*"}}
    }
  ]
}
```
Jules then assigns the users who are working on this launch to the group\. This includes Patricia and Eli from the /marketing/ path\. It also includes Chris and Chloe from the /sales/ path, and Aline and Jim from the /legal/ path\.

## Unique IDs<a name="identifiers-unique-ids"></a>

When IAM creates a user, group, role, policy, instance profile, or server certificate, it assigns to each entity a unique ID that looks like the following example:

`AIDAJQABLZS4A3QDU576Q`

For the most part, you use friendly names and [ARNs](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) when you work with IAM entities, so you don't need to know the unique ID for a specific entity\. However, the unique ID can sometimes be useful when it isn't practical to use friendly names\. 

One example pertains to reusing friendly names in your AWS account\. Within your account, a friendly name for a user, group, or policy must be unique\. For example, you might create an IAM user named David\. Your company uses Amazon S3 and has a bucket with folders for each employee; the bucket has a resource\-based policy \(a bucket policy\) that lets users access only their own folders in the bucket\. Suppose that the employee named David leaves your company and you delete the corresponding IAM user\. But later another employee named David starts and you create a new IAM user named David\. If the bucket policy specifies the IAM user named David, the policy could end up granting the new David access to information in the Amazon S3 bucket that was left by the former David\. 

However, every IAM user has a unique ID, even if you create a new IAM user that reuses a friendly name that you deleted before\. In the example, the old IAM user David and the new IAM user David have different unique IDs\. If you create resource policies for Amazon S3 buckets that grant access by unique ID and not just by user name, it reduces the chance that you could inadvertently grant access to information that an employee should not have\. 

Another example where user IDs can be useful is if you maintain your own database \(or other store\) of IAM user information\. The unique ID can provide a unique identifier for each IAM user you create, even if over time you have IAM users that reuse a name, as in the previous example\.

### Getting the Unique ID<a name="identifiers-get-unique-id"></a>

The unique ID for an IAM entity is not available in the IAM console\. To get the unique ID, you can use the following AWS CLI commands or IAM API calls\.

AWS CLI:
+  [get\-group](http://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html) 
+  [get\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html) 
+  [get\-user](http://docs.aws.amazon.com/cli/latest/reference/iam/get-user.html) 
+  [get\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html) 
+  [get\-instance\-profile](http://docs.aws.amazon.com/cli/latest/reference/iam/get-instance-profile.html) 
+  [get\-server\-certificate](http://docs.aws.amazon.com/cli/latest/reference/iam/get-server-certificate.html) 

IAM API:
+  [GetGroup](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetGroup.html) 
+  [GetRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html) 
+  [GetUser](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetUser.html) 
+  [GetPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicy.html) 
+  [GetInstanceProfile](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetInstanceProfile.html) 
+  [GetServerCertificate](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServerCertificate.html) 