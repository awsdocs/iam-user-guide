# IAM Policy Actions Grouped by Access Level<a name="reference_policies_access-levels"></a>

This section lists the access levels that all AWS service actions are grouped into\. Access levels categorize AWS service actions based on their behavior\. You can use this list to help you understand policy summaries or to determine which actions are relevant to include in your IAM permission policies\.

**Important**  
AWS categorizes each AWS action into these access levels based on how closely each action matches the access level definitions in the following list\. Before you write any policies that use these access levels, review the definitions and the lists below\. Make sure that the actions that you want are categorized the way you expect\.

+  List — Permission to list resources to determine whether an object exists\. Actions with this level of access can list objects but cannot see the contents of a resource\. For example, the Amazon S3 action `ListBucket` has the **List** access level\.

+  Read — Permission to read but not edit the contents and attributes of resources\. For example, the Amazon S3 actions `GetObject` and `GetBucketLocation` have the **Read** access level\.

+  Write — Permission to create, delete, or modify resources\. For example, the Amazon S3 actions `CreateBucket`, `DeleteBucket` and `PutObject` have the **Write** access level\.

+  Permissions management — Permission to grant or modify resource permissions\. For example, most IAM and AWS Organizations actions, as well as actions like the Amazon S3 actions `PutBucketPolicy` and `DeleteBucketPolicy` have the **Permissions management** access level\.
**Tip**  
To improve the security of your AWS account, restrict or regularly monitor policies that have the **Permissions management** access level classification\.