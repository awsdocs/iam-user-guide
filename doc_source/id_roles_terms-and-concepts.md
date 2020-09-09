# Roles terms and concepts<a name="id_roles_terms-and-concepts"></a>

Here are some basic terms to help you get started with roles\.

**Role**  <a name="iam-term-role"></a>
An IAM identity that you can create in your account that has specific permissions\. An IAM role has some similarities to an IAM user\. Roles and users are both AWS identities with permissions policies that determine what the identity can and cannot do in AWS\. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it\. Also, a role does not have standard long\-term credentials such as a password or access keys associated with it\. Instead, when you assume a role, it provides you with temporary security credentials for your role session\.  
Roles can be used by the following:  
+ An IAM user in the same AWS account as the role
+ An IAM user in a different AWS account than the role
+ A web service offered by AWS such as Amazon Elastic Compute Cloud \(Amazon EC2\)
+ An external user authenticated by an external identity provider \(IdP\) service that is compatible with SAML 2\.0 or OpenID Connect, or a custom\-built identity broker\.

****AWS service role****  <a name="iam-term-service-role"></a>
A role that a service assumes to perform actions in your account on your behalf\. When you set up some AWS service environments, you must define a role for the service to assume\. This service role must include all the permissions required for the service to access the AWS resources that it needs\. Service roles vary from service to service, but many allow you to choose your permissions, as long as you meet the documented requirements for that service\. Service roles provide access only within your account and cannot be used to grant access to services in other accounts\. You can create, modify, and delete a service role from within IAM\.

****AWS service role for an EC2 instance****  <a name="iam-term-service-role-ec2"></a>
A special type of service role that an application running on an Amazon EC2 instance can assume to perform actions in your account\. This role is assigned to the EC2 instance when it is launched\. Applications running on that instance can retrieve temporary security credentials and perform actions that the role allows\. For details about using a service role for an EC2 instance, see [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](id_roles_use_switch-role-ec2.md)\.

****AWS service\-linked role****  <a name="iam-term-service-linked-role"></a>
A unique type of service role that is linked directly to an AWS service\. Service\-linked roles are predefined by the service and include all the permissions that the service requires to call other AWS services on your behalf\. The linked service also defines how you create, modify, and delete a service\-linked role\. A service might automatically create or delete the role\. It might allow you to create, modify, or delete the role as part of a wizard or process in the service\. Or it might require that you use IAM to create or delete the role\. Regardless of the method, service\-linked roles make setting up a service easier because you don't have to manually add the necessary permissions\.  
If you are already using a service when it begins supporting service\-linked roles, you might receive an email announcing a new role in your account\. In this case, the service automatically created the service\-linked role in your account\. You don't need to take any action to support this role, and you should not manually delete it\. For more information, see [A new role appeared in my AWS account](troubleshoot_roles.md#troubleshoot_roles_new-role-appeared)\.
For information about which services support using service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\. If the service does not include documentation for creating, modifying, or deleting the service\-linked role, then you can use the IAM console, AWS CLI, or API\. For more information, see [Using service\-linked roles](using-service-linked-roles.md)\.

****Role chaining****  <a name="iam-term-role-chaining"></a>
Role chaining occurs when you use a role to assume a second role through the AWS CLI or API\. For example, assume that `User1` has permission to assume `RoleA` and `RoleB`\. Additionally, `RoleA` has permission to assume `RoleB`\. You can assume `RoleA` by using `User1`'s long\-term user credentials in the `AssumeRole` API operation\. This operation returns `RoleA` short\-term credentials\. To engage in role chaining, you can use `RoleA`'s short\-term credentials to assume `RoleB`\.   
When you assume a role, you can pass a session tag and set the tag as transitive\. Transitive session tags are passed to all subsequent sessions in a role chain\. To learn more about session tags, see [Passing session tags in AWS STS](id_session-tags.md)\.  
Role chaining limits your AWS CLI or AWS API role session to a maximum of one hour\. When you use the [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API operation to assume a role, you can specify the duration of your role session with the `DurationSeconds` parameter\. You can specify a parameter value of up to 43200 seconds \(12 hours\), depending on the [maximum session duration setting](id_roles_use.md#id_roles_use_view-role-max-session) for your role\. However, if you assume a role using role chaining and provide a `DurationSeconds` parameter value greater than one hour, the operation fails\.  
AWS does not treat using roles to [grant permissions to applications that run on EC2 instances](id_roles_use_switch-role-ec2.md) as role chaining\.

****Delegation****  <a name="delegation"></a>
The granting of permissions to someone to allow access to resources that you control\. Delegation involves setting up a trust between two accounts\. The first is the account that owns the resource \(the trusting account\)\. The second is the account that contains the users that need to access the resource \(the trusted account\)\. The trusted and trusting accounts can be any of the following:  
+ The same account\.
+ Separate accounts that are both under your organization's control\.
+ Two accounts owned by different organizations\.
To delegate permission to access a resource, you [create an IAM role](id_roles_create_for-user.md) in the trusting account that has two [policies](#term_policy) attached\. The *permissions policy* grants the user of the role the needed permissions to carry out the intended tasks on the resource\. The *trust policy* specifies which trusted account members are allowed to assume the role\.  
When you create a trust policy, you cannot specify a wildcard \(\*\) as a principal\. The trust policy is attached to the role in the trusting account, and is one\-half of the permissions\. The other half is a permissions policy attached to the user in the trusted account that [allows that user to switch to, or assume the role](id_roles_use_permissions-to-switch.md)\. A user who assumes a role temporarily gives up his or her own permissions and instead takes on the permissions of the role\. When the user exits, or stops using the role, the original user permissions are restored\. An additional parameter called [external ID](id_roles_create_for-user_externalid.md) helps ensure secure use of roles between accounts that are not controlled by the same organization\.

****Federation****  
The creation of a trust relationship between an external identity provider and AWS\. Users can sign in to a web identity provider, such as **Login with Amazon**, **Facebook**, **Google**, or any IdP that is compatible with **OpenID Connect** \(OIDC\)\. Users can also sign in to an enterprise identity system that is compatible with Security Assertion Markup Language \(SAML\) 2\.0, such as Microsoft Active Directory Federation Services\. When you use OIDC and SAML 2\.0 to configure a trust relationship between these external identity providers and AWS, the user is assigned to an IAM role\. The user also receives temporary credentials that allow the user to access your AWS resources\. 

****Federated user****  <a name="term_federated-user"></a>
Instead of creating an IAM user, you can use existing identities from AWS Directory Service, your enterprise user directory, or a web identity provider\. These are known as *federated users*\. AWS assigns a role to a federated user when access is requested through an [identity provider](id_roles_providers.md)\. For more information about federated users, see [Federated Users and Roles](introduction_access-management.md#intro-access-roles) in the *IAM User Guide*\.

****Trust policy****  <a name="term_trust-policy"></a>
A [JSON policy document](reference_policies_grammar.md) in which you define the principals that you *trust* to assume the role\. A role trust policy is a required [resource\-based policy](access_policies.md#policies_resource-based) that is attached to a role in IAM\. The [principals](reference_policies_elements_principal.md) that you can specify in the trust policy include users, roles, accounts, and services\.

****Permissions policy****  <a name="term_policy"></a>
A permissions document in [JSON](http://www.json.org) format in which you define what actions and resources the role can use\. The document is written according to the rules of the [IAM policy language](reference_policies.md)\.

****Permissions boundary****  
An advanced feature in which you use policies to limit the maximum permissions that an identity\-based policy can grant to a role\. You cannot apply a permissions boundary to a service\-linked role\. For more information, see [Permissions boundaries for IAM entities](access_policies_boundaries.md)\.

****Principal****  
An entity in AWS that can perform actions and access resources\. A principal can be an AWS account root user, an IAM user, or a role\. You can grant permissions to access a resource in one of two ways:  
+ You can attach a permissions policy to a user \(directly, or indirectly through a group\) or to a role\.
+ For those services that support [resource\-based policies](introduction_access-management.md#intro-access-resource-based-policies), you can identify the principal in the `Principal` element of a policy attached to the resource\.
If you reference an AWS account as principal, it generally means any principal defined within that account\.  
You cannot use a wildcard \(\*\) in the `Principal` element in a role's trust policy\.

****Role for cross\-account access****  
A role that grants access to resources in one account to a trusted principal in a different account\. Roles are the primary way to grant cross\-account access\. However, some AWS services allow you to attach a policy directly to a resource \(instead of using a role as a proxy\)\. These are called resource\-based policies, and you can use them to grant principals in another AWS account access to the resource\. Some of these resources include Amazon Simple Storage Service \(S3\) buckets, S3 Glacier vaults, Amazon Simple Notification Service \(SNS\) topics, and Amazon Simple Queue Service \(SQS\) queues\. To learn which services support resource\-based policies, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. For more information about resource\-based policies, see [How IAM roles differ from resource\-based policies](id_roles_compare-resource-policies.md)\.