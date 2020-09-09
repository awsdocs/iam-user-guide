# Access management for AWS resources<a name="access"></a>

AWS Identity and Access Management \(IAM\) is a web service that helps you securely control access to AWS resources\. When a [principal](intro-structure.md#intro-structure-principal) makes a request in AWS, the AWS enforcement code checks whether the principal is authenticated \(signed in\) and authorized \(has permissions\)\. You manage access in AWS by creating policies and attaching them to IAM identities or AWS resources\. Policies are JSON documents in AWS that, when attached to an identity or resource, define their permissions\. For more information about policy types and uses, see [Policies and permissions in IAM](access_policies.md)\.

For details about the rest of the authentication and authorization process, see [Understanding how IAM works](intro-structure.md)\.

![\[AccessManagement_Diagram\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/access-diagram_800.png)

During authorization, the AWS enforcement code uses values from the [request context](intro-structure.md#intro-structure-request) to check for matching policies and determine whether to allow or deny the request\. 

AWS checks each policy that applies to the context of the request\. If a single policy denies the request, AWS denies the entire request and stops evaluating policies\. This is called an *explicit deny*\. Because requests are *denied by default*, IAM authorizes your request only if every part of your request is allowed by the applicable policies\. The [evaluation logic](reference_policies_evaluation-logic.md) for a request within a single account follows these rules:
+ By default, all requests are implicitly denied\. \(Alternatively, by default, the AWS account root user has full access\.\) 
+ An explicit allow in an identity\-based or resource\-based policy overrides this default\.
+ If a permissions boundary, Organizations SCP, or session policy is present, it might override the allow with an implicit deny\.
+ An explicit deny in any policy overrides any allows\.

After your request has been authenticated and authorized, AWS approves the request\. If you need to make a request in a different account, a policy in the other account must allow you to access the resource\. In addition, the IAM entity that you use to make the request must have an identity\-based policy that allows the request\.

## Access management resources<a name="access_resources"></a>

For more information about permissions and about creating policies, see the following resources:

The following entries in the AWS Security Blog cover common ways to write policies for access to Amazon S3 buckets and objects\.
+ [Writing IAM Policies: How to Grant Access to an Amazon S3 Bucket](http://aws.amazon.com/blogs/security/writing-iam-policies-how-to-grant-access-to-an-amazon-s3-bucket/)
+ [Writing IAM policies: Grant Access to User\-Specific Folders in an Amazon S3 Bucket](http://aws.amazon.com/blogs/security/writing-iam-policies-grant-access-to-user-specific-folders-in-an-amazon-s3-bucket/)
+ [IAM Policies and Bucket Policies and ACLs\! Oh My\! \(Controlling Access to S3 Resources\)](http://aws.amazon.com/blogs/security/iam-policies-and-bucket-policies-and-acls-oh-my-controlling-access-to-s3-resources/)
+ [A Primer on RDS Resource\-Level Permissions](http://aws.amazon.com/blogs/security/a-primer-on-rds-resource-level-permissions)
+ [Demystifying EC2 Resource\-Level Permissions](http://aws.amazon.com/blogs/security/demystifying-ec2-resource-level-permissions/)