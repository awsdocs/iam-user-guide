# How IAM Roles Differ from Resource\-based Policies<a name="id_roles_compare-resource-policies"></a>

For some AWS services, you can grant cross\-account access to your resources\. To do this, you attach a policy directly to the resource that you want to share, instead of using a role as a proxy\. The resource that you want to share must support [resource\-based policies](access_policies_identity-vs-resource.md)\. Unlike a user\-based policy, a resource\-based policy specifies who \(in the form of a list of AWS account ID numbers\) can access that resource\. 

Cross\-account access with a resource\-based policy has an advantage over a role\. With a resource that is accessed through a resource\-based policy, the user still works in the trusted account and does not have to give up his or her user permissions in place of the role permissions\. In other words, the user continues to have access to resources in the trusted account at the same time as he or she has access to the resource in the trusting account\. This is useful for tasks such as copying information to or from the shared resource in the other account\. 

The disadvantage is that not all services support resource\-based policies\. A few of the AWS services that support resource\-based policies are listed here:
+ **Amazon S3 buckets** – The policy is attached to the bucket, but the policy controls access to both the bucket and the objects in it\. For more information, go to [Access Control](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingAuthAccess.html) in the *Amazon Simple Storage Service Developer Guide*\. 
+ **Amazon Simple Notification Service \(Amazon SNS\) topics** – For more information, go to [Managing Access to Your Amazon SNS Topics](http://docs.aws.amazon.com/sns/latest/dg/AccessPolicyLanguage.html) in the *Amazon Simple Notification Service Developer Guide*\. 
+ **Amazon Simple Queue Service \(Amazon SQS\) queues** – For more information, go to [Appendix: The Access Policy Language](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/AccessPolicyLanguage.html) in the *Amazon Simple Queue Service Developer Guide*\. 

For a complete list of the growing number of AWS services that support attaching permission policies to resources instead of principals, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes** in the **Resource Based** column\.

## About Delegating AWS Permissions in a Resource\-based Policy<a name="aboutdelegation-resourcepolicy"></a>

After a resource grants your AWS account permissions as a principal in its resource\-based policy, you can then delegate permissions to specific users or groups under your AWS account\. You attach a policy to the user or group that you want to delegate the permissions to\. Note that you can only delegate permissions equivalent to, or less than, the permissions granted to your account by the resource owning account\. For example, if your account is granted full access to the resources of another AWS account, then you can delegate full access, list access, or any other partial access to users under your AWS account\. If, on the other hand, your account is granted list access only, then you can delegate only list access\. If you try to delegate more permissions than your account has, your users will still have only list access only\. This is illustrated in the following figure\. For information about attaching a policy to a user or group, see [Managing IAM Policies](access_policies_manage.md)\.

![\[Delegating access to an AWS account\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/Delegation.diagram.png)

1. Account A gives account B full access to account A's S3 bucket by naming account B as a principal in the policy\. As a result, account B is authorized to perform any action on account A's bucket, and the account B administrator can delegate access to its users in account B\. 

1. The account B administrator grants user 1 read\-only access to account A's S3 bucket\. User 1 can view the objects in account A's bucket\. The level of access account B can delegate is equivalent to, or less than, the access the account has\. In this case, the full access granted to account B is filtered to read only for user 1\.

1. The account B administrator does not give access to user 2\. Because users by default do not have any permissions except those that are explicitly granted, user 2 does not have access to account A's Amazon S3 bucket\. 

**Important**  
In the preceding example, if account B had used wildcards \(\*\) to give user 1 full access to all its resources, user 1 would automatically have access to any resources that account B has access to, including access granted by other accounts to those accounts' resources\. In this case, user 1 would have access to any Account A resources granted to account B, in addition to those explicitly granted to user 1\.   
IAM evaluates a user's permissions at the time the user makes a request\. Therefore, if you use wildcards \(\*\) to give users full access to your resources, users are able to access any resources that your AWS account has access to, even resources you add or gain access to after creating the user's policy\. 

For information about permissions, policies, and the permission policy language that you use to write policies, see [Access Management](access.md)\. 

**Important**  
Give access only to entities you trust, and give the minimum amount of access necessary\. Whenever the trusted entity is another AWS account, that account can in turn delegate access to any of its IAM users\. The trusted AWS account can delegate access only to the extent that it has been granted access; it cannot delegate more access than the account itself has been granted\.