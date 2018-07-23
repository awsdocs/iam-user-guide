# Access Management<a name="access"></a>

AWS Identity and Access Management \(IAM\) is a web service that helps you securely control access to AWS resources\. The access management portion of IAM helps you define what a user or other entity is allowed to do in an account, often referred to as *authorization*\. Permissions are defined using permissions policies and permissions boundaries\. Most permission policies are JSON policy documents in AWS that, when attached to an identity or resource, defines their permissions\. A permissions boundary is an advanced feature in which you use policies to limit the maximum permissions that a principal can have\. These boundaries can be applied to AWS Organizations organizations or to IAM users or roles\. For more information about policy types and uses, see [Policies and Permissions](access_policies.md)\.

When a [principal](intro-structure.md#intro-structure-principal) makes a request in AWS, the IAM service checks whether the principal is authenticated \(signed in\) and authorized \(has permissions\)\. You manage access in AWS by creating policies and attaching them to IAM identities, AWS resources, or other AWS objects \(such as AWS Organizations organizations\)\. Those policies specify the permissions that are allowed or denied\. For details about the rest of the authentication and authorization process, see [Understanding How IAM Works](intro-structure.md)\.

![\[AccessManagement_Diagram\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/access-diagram_800.png)

During authorization, IAM uses values from the [request context](intro-structure.md#intro-structure-request) to check for matching policies and determine whether to allow or deny the request\. 

AWS checks each policy that applies to the context of the request\. If a single policy denies the request, AWS denies the entire request and stops evaluating policies\. This is called an *explicit deny*\. Because requests are *denied by default*, IAM authorizes your request only if every part of your request is allowed by the applicable policies\. The [evaluation logic](reference_policies_evaluation-logic.md) follows these rules:
+ By default, all requests are denied\. \(In general, requests made using the AWS account root user credentials for resources in the account are always allowed\.\) 
+ An explicit allow in a permissions policy overrides this default\.
+ A permissions boundary \(an AWS Organizations SCP or a user or role boundary\) or a policy used during AWS STS role assumption overrides the allow\. If one or more of these items exists, they must all allow the request\. Otherwise, it is implicitly denied\.
+ An explicit deny in any policy overrides any allows\.

After your request has been authenticated and authorized, AWS approves the request\. If you need to make a request in a different account, the resource in that account must have a resource\-based policy that allows access from your account\. Otherwise, you must assume a role within that account with the permissions that you need\.

## Access Management Resources<a name="access_resources"></a>

For more information about permissions and about creating policies, see the following resources:
+ The following entries in the AWS Security Blog cover common ways to write policies for access to Amazon S3 buckets and objects\.
  + [Writing IAM Policies: How to Grant Access to an Amazon S3 Bucket](http://aws.amazon.com/blogs/security/writing-iam-policies-how-to-grant-access-to-an-amazon-s3-bucket/)
  + [Writing IAM policies: Grant Access to User\-Specific Folders in an Amazon S3 Bucket](http://aws.amazon.com/blogs/security/writing-iam-policies-grant-access-to-user-specific-folders-in-an-amazon-s3-bucket/)
  + [IAM Policies and Bucket Policies and ACLs\! Oh My\! \(Controlling Access to S3 Resources\)](http://aws.amazon.com/blogs/security/iam-policies-and-bucket-policies-and-acls-oh-my-controlling-access-to-s3-resources/)
  + [A Primer on RDS Resource\-Level Permissions](http://aws.amazon.com/blogs/security/a-primer-on-rds-resource-level-permissions)
  + [Demystifying EC2 Resource\-Level Permissions](http://aws.amazon.com/blogs/security/demystifying-ec2-resource-level-permissions/)