# How IAM roles differ from resource\-based policies<a name="id_roles_compare-resource-policies"></a>

For some AWS services, you can grant cross\-account access to your resources\. To do this, you attach a policy directly to the resource that you want to share, instead of using a role as a proxy\. The resource that you want to share must support [resource\-based policies](access_policies_identity-vs-resource.md)\. Unlike an identity\-based policy, a resource\-based policy specifies who \(which principal\) can access that resource\. 

**Note**  
IAM roles and resource\-based policies delegate access across accounts only within a single partition\. For example, assume that you have an account in US West \(N\. California\) in the standard `aws` partition\. You also have an account in China \(Beijing\) in the `aws-cn` partition\. You can't use an Amazon S3 resource\-based policy in your account in China \(Beijing\) to allow access for users in your standard `aws` account\.

Cross\-account access with a resource\-based policy has some advantages over cross\-account access with a role\. With a resource that is accessed through a resource\-based policy, the principal still works in the trusted account and does not have to give up his or her permissions to receive the role permissions\. In other words, the principal continues to have access to resources in the trusted account at the same time as he or she has access to the resource in the trusting account\. This is useful for tasks such as copying information to or from the shared resource in the other account\. To learn whether principals in accounts outside of your zone of trust \(trusted organization or account\) have access to assume your roles, see [What is IAM Access Analyzer?](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)\.

The principals that you can specify in a resource based policy include accounts, IAM users, federated users, IAM roles, assumed\-role sessions, or AWS services\. For more information, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\.

The following list includes some of the AWS services that support resource\-based policies\. For a complete list of the growing number of AWS services that support attaching permission policies to resources instead of principals, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes** in the **Resource Based** column\.
+ **Amazon S3 buckets** – The policy is attached to the bucket, but the policy controls access to both the bucket and the objects in it\. For more information, go to [Access Control](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingAuthAccess.html) in the *Amazon Simple Storage Service Developer Guide*\. 

  In some cases, it may be best to use roles for cross\-account access to Amazon S3\. For more information, see the [example walkthroughs](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-walkthroughs-managing-access.html) in the *Amazon Simple Storage Service Developer Guide*\.
+ **Amazon Simple Notification Service \(Amazon SNS\) topics** – For more information, go to [Managing Access to Your Amazon SNS Topics](https://docs.aws.amazon.com/sns/latest/dg/AccessPolicyLanguage.html) in the *Amazon Simple Notification Service Developer Guide*\. 
+ **Amazon Simple Queue Service \(Amazon SQS\) queues** – For more information, go to [Appendix: The Access Policy Language](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/AccessPolicyLanguage.html) in the *Amazon Simple Queue Service Developer Guide*\. 

## About delegating AWS permissions in a resource\-based policy<a name="aboutdelegation-resourcepolicy"></a>

If a resource grants permissions to principals in your account, you can then delegate those permissions to specific IAM identities\. Identities are users, groups of users, or roles in your account\. You delegate permissions by attaching a policy to the identity\. You can grant up to the maximum permissions that are allowed by the resource\-owning account\. 

Assume that a resource\-based policy allows all principals in your account full administrative access to a resource\. Then you can delegate full access, read\-only access, or any other partial access to principals in your AWS account\. Alternatively, if the resource\-based policy allows only list permissions, then you can delegate only list access\. If you try to delegate more permissions than your account has, your principals will still have only list access\. For information about attaching a policy to an IAM identity, see [Managing IAM policies](access_policies_manage.md)\.

**Note**  
IAM roles and resource\-based policies delegate access across accounts only within a single partition\. For example, you can't add cross\-account access between an account in the standard `aws` partition and an account in the `aws-cn` partition\. 

For example, assume that you manage `AccountA` and `AccountB`\. In `AccountA`, you have the Amazon S3 bucket named `BucketA`\. You attach a resource\-based policy to `BucketA` that allows all principals in `AccountB` full access to objects in your bucket\. They can create, read, or delete any objects in that bucket\. In `AccountB`, you attach a policy to the IAM user named `User2`\. That policy allows the user read\-only access to the objects in `BucketA`\. That means that `User2` can view the objects, but not create, edit, or delete them\.

![\[Delegating access to an AWS account\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/Delegation.png)

1. `AccountA` gives `AccountB` full access to `BucketA` by naming `AccountB` as a principal in the resource\-based policy\. As a result, `AccountB` is authorized to perform any action on `BucketA`, and the `AccountB` administrator can delegate access to its users in `AccountB`\. 

1. The `AccountB` root user has all of the permissions that are granted to the account\. Therefore, the root user has full access to `BucketA`\.

1. The `AccountB` administrator does not give access to `User1`\. By default, users do not have any permissions except those that are explicitly granted\. Therefore, `User1` does not have access to `BucketA`\. 

1. The `AccountB` administrator grants `User2` read\-only access to `BucketA`\. `User2` can view the objects in the bucket\. The maximum level of access that `AccountB` can delegate is the access level that is granted to the account\. In this case, the resource\-based policy granted full access to `AccountB`, but `User2` is granted only read\-only access\.

IAM evaluates a principal's permissions at the time the principal makes a request\. Therefore, if you use wildcards \(\*\) to give users full access to your resources, principals can access any resources that your AWS account has access to\. This is true even for resources you add or gain access to after creating the user's policy\. 

In the preceding example, if `AccountB` had attached a policy to `User2` that allowed full access to all resources in all accounts, `User2` would automatically have access to any resources that `AccountB` has access to\. This includes the `BucketA` access and access to any other resources granted by resource\-based policies in `AccountA`\. 

**Important**  
Give access only to entities you trust, and give the minimum level of access necessary\. Whenever the trusted entity is another AWS account, that account can in turn delegate access to any of its IAM users\. The trusted AWS account can delegate access only to the extent that it has been granted access; it cannot delegate more access than the account itself has been granted\.

For information about permissions, policies, and the permission policy language that you use to write policies, see [Access management for AWS resources](access.md)\. 