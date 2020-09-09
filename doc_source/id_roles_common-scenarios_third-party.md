# Providing access to AWS accounts owned by third parties<a name="id_roles_common-scenarios_third-party"></a>

When third parties require access to your organization's AWS resources, you can use roles to delegate access to them\. For example, a third party might provide a service for managing your AWS resources\. With IAM roles, you can grant these third parties access to your AWS resources without sharing your AWS security credentials\. Instead, the third party can access your AWS resources by assuming a role that you create in your AWS account\. To learn whether principals in accounts outside of your zone of trust \(trusted organization or account\) have access to assume your roles, see [What is IAM Access Analyzer?](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)\.

Third parties must provide you with the following information for you to create a role that they can assume:
+ The third party's AWS account ID\. You specify their AWS account ID as the principal when you define the trust policy for the role\.
+ An external ID to uniquely associate with the role\. The external ID can be any secret identifier that is known by you and the third party\. For example, you can use an invoice ID between you and the third party, but do not use something that can be guessed, like the name or phone number of the third party\. You must specify this ID when you define the trust policy for the role\. The third party must provide this ID when they assume the role\. For more information about the external ID, see [How to use an external ID when granting access to your AWS resources to a third party](id_roles_create_for-user_externalid.md)\.
+ The permissions that the third party requires to work with your AWS resources\. You must specify these permissions when defining the role's permission policy\. This policy defines what actions they can take and what resources they can access\.

After you create the role, you must provide the role's Amazon Resource Name \(ARN\) to the third party\. They require your role's ARN in order to assume the role\.

For details about creating a role to delegate access to a third party, see [How to use an external ID when granting access to your AWS resources to a third party](id_roles_create_for-user_externalid.md)\.

**Important**  
When you grant third parties access to your AWS resources, they can access any resource that you specify in the policy\. Their use of your resources is billed to you\. Ensure that you limit their use of your resources appropriately\.