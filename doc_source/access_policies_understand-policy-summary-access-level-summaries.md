# Understanding Access Level Summaries Within Policy Summaries<a name="access_policies_understand-policy-summary-access-level-summaries"></a>

Policy summaries include an access level summary that describes the action permissions defined for each service that is mentioned in the policy\. To learn about policy summaries, see [Understanding Permissions Granted by a Policy](access_policies_understand.md)\. Access level summaries indicate whether the actions in each access level \(`List`, `Read`, `Write`, and `Permissions management`\) have `Full` or `Limited` permissions defined in the policy\. To view the access level classification that is assigned to each action in a service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\.

The following example describes the access provided by a policy for the given services\. For examples of full JSON policy documents and their related summaries, see [Examples of Policy Summaries](access_policies_policy-summary-examples.md)\.


****  

| Service | Access level | This policy provides: | 
| --- | --- | --- | 
| IAM | Full access | Access to all actions within the IAM service | 
| CloudWatch | Full: List | Access to all CloudWatch actions in the List access level, but no access to actions with the Read, Write, or Permissions management access level classification | 
| Data Pipeline | Limited: List, Read | Access to at least one but not all AWS Data Pipeline actions in the List and Read access level, but not the Write or Permissions management actions | 
| EC2 | Full: List, Read Limited: Write | Access to all Amazon EC2 List and Read actions and access to at least one but not all Amazon EC2 Write actions, but no access to actions with the Permissions management access level classification | 
| S3 | Limited: Read, Write, Permissions management | Access to at least one but not all Amazon S3 Read, Write and Permissions management actions | 
| codedploy | \(empty\) | Unknown access, because IAM does not recognize this service | 
| API Gateway | None | No access is defined in the policy | 
| CodeBuild | ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) No actions are defined\. | No access because no actions are defined for the service\. To learn how to understand and troubleshoot this issue, see [My Policy Does Not Grant the Expected Permissions](troubleshoot_policies.md#policy-summary-not-grant-permissions) | 

As [previously mentioned](access_policies_understand-policy-summary.md#full-vs-limited-access-summary), **Full access** indicates that the policy provides access to all the actions within the service\. Policies that provide access to some but not all actions within a service are further grouped according to the access level classification\. This is indicated by one of the following access\-level groupings:
+ **Full**: The policy provides access to all actions within the specified access level classification\.
+ **Limited**: The policy provides access to one or more but not all actions within the specified access level classification\.
+ **None**: The policy provides no access\.
+ \(empty\): IAM does not recognize this service\. If the service name includes a typo, then the policy provides no access to the service\. If the service name is correct, then the service might not support policy summaries or might be in preview\. In this case, the policy might provide access, but that access cannot be shown in the policy summary\. To request policy summary support for a generally available \(GA\) service, see [Service Does Not Support IAM Policy Summaries](troubleshoot_policies.md#unsupported-services-actions)\.

Access level summaries that include partial access to actions are grouped using the following access level classifications:
+ **List**: Permission to list resources within the service to determine whether an object exists\. Actions with this level of access can list objects but cannot see the contents of a resource\. For example, the Amazon S3 action `ListBucket` has the **List** access level\. 
+ **Read**: Permission to read but not edit the contents and attributes of resources in the service\. For example, the Amazon S3 actions `GetObject` and `GetBucketLocation` have the **Read** access level\.
+ **Write**: Permission to create, delete, or modify resources in the service\. For example, the Amazon S3 actions `CreateBucket`, `DeleteBucket` and `PutObject` have the **Write** access level\.
+ **Permissions management**: Permission to grant or modify resource permissions in the service\. For example, most IAM and AWS Organizations actions, as well as actions like the Amazon S3 actions `PutBucketPolicy` and `DeleteBucketPolicy` have the **Permissions management** access level\.
**Tip**  
To improve the security of your AWS account, restrict or regularly monitor policies that include the **Permissions management** access level classification\.