# Cross\-Account Policy Evaluation Logic<a name="reference_policies_evaluation-logic-cross-account"></a>

You can allow a principal in one account to access resources in a second account\. This is called cross\-account access\. When you allow cross\-account access, the account where the principal exists is called the *trusted* account\. The account where the resource exists is the *trusting* account\. 

To allow cross\-account access, you attach a resource\-based policy to the resource that you want to share\. You must also attach an identity\-based policy to the identity that acts the principal in the request\. The resource\-based policy in the trusting account must specify the principal of the trusted account that will have access the resource\. You can specify the entire account or its IAM users, federated users, IAM roles, or assumed\-role sessions\. You can also specify an AWS service as a principal\. For more information, see [Specifying a Principal](reference_policies_elements_principal.md#Principal_specifying)\. 

The principal's identity\-based policy must allow the requested access to the resource in the trusting service\. You can do this by specifying the ARN of the resource or by allowing access to all resources \(`*`\)\.

In IAM, you can attach a resource\-based policy to an IAM role to allow principals in other accounts to assume that role\. The role's resource\-based policy is called a role trust policy\. After assuming that role, the allowed principals can use the resulting temporary credentials to access multiple resources in your account\. This access is defined in the role's identity\-based permissions policy\. For more information, see [ Roles Terms and ConceptsTerms and Concepts  Learn basic terms and concepts related to IAM roles\.   Here are some basic terms to help you get started with roles\.  

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
A special type of service role that an application running on an Amazon EC2 instance can assume to perform actions in your account\. This role is assigned to the EC2 instance when it is launched\. Applications running on that instance can retrieve temporary security credentials and perform actions that the role allows\. For details about using a service role for an EC2 instance, see [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)\. 

****AWS service\-linked role****  <a name="iam-term-service-linked-role"></a>
A unique type of service role that is linked directly to an AWS service\. Service\-linked roles are predefined by the service and include all the permissions that the service requires to call other AWS services on your behalf\. The linked service also defines how you create, modify, and delete a service\-linked role\. A service might automatically create or delete the role\. It might allow you to create, modify, or delete the role as part of a wizard or process in the service\. Or it might require that you use IAM to create or delete the role\. Regardless of the method, service\-linked roles make setting up a service easier because you don’t have to manually add the necessary permissions\.  
If you are already using a service when it begins supporting service\-linked roles, you might receive an email announcing a new role in your account\. In this case, the service automatically created the service\-linked role in your account\. You don't need to take any action to support this role, and you should not manually delete it\. For more information, see [A New Role Appeared in My AWS Account](troubleshoot_roles.md#troubleshoot_roles_new-role-appeared)\.
For information about which services support using service\-linked roles, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\. If the service does not include documentation for creating, modifying, or deleting the service\-linked role, then you can use the IAM console, AWS CLI, or API\. For more information, see [Using Service\-Linked Roles](using-service-linked-roles.md)\. 

****Role chaining****  <a name="iam-term-role-chaining"></a>
Role chaining occurs when you use a role to assume a second role through the AWS CLI or API\. For example, assume that `User1` has permission to assume `RoleA` and `RoleB`\. Additionally, `RoleA` has permission to assume `RoleB`\. You can assume `RoleA` by using `User1`'s long\-term user credentials in the `AssumeRole` API operation\. This operation returns `RoleA` short\-term credentials\. To engage in role chaining, you can use `RoleA`'s short\-term credentials to assume `RoleB`\.   
When you assume a role, you can pass a session tag and set the tag as transitive\. Transitive session tags are passed to all subsequent sessions in a role chain\. To learn more about session tags, see [Passing Session Tags in AWS STS](id_session-tags.md)\.  
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
An advanced feature in which you use policies to limit the maximum permissions that an identity\-based policy can grant to a role\. You cannot apply a permissions boundary to a service\-linked role\. For more information, see [Permissions Boundaries for IAM Entities](access_policies_boundaries.md)\. 

****Principal****  
An entity in AWS that can perform actions and access resources\. A principal can be an AWS account root user, an IAM user, or a role\. You can grant permissions to access a resource in one of two ways:  
+ You can attach a permissions policy to a user \(directly, or indirectly through a group\) or to a role\.
+ For those services that support [resource\-based policies](introduction_access-management.md#intro-access-resource-based-policies), you can identify the principal in the `Principal` element of a policy attached to the resource\.
If you reference an AWS account as principal, it generally means any principal defined within that account\.  
You cannot use a wildcard \(\*\) in the `Principal` element in a role's trust policy\. 

****Role for cross\-account access****  
A role that grants access to resources in one account to a trusted principal in a different account\. Roles are the primary way to grant cross\-account access\. However, some AWS services allow you to attach a policy directly to a resource \(instead of using a role as a proxy\)\. These are called resource\-based policies, and you can use them to grant principals in another AWS account access to the resource\. Some of these resources include Amazon Simple Storage Service \(S3\) buckets, S3 Glacier vaults, Amazon Simple Notification Service \(SNS\) topics, and Amazon Simple Queue Service \(SQS\) queues\. To learn which services support resource\-based policies, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md)\. For more information about resource\-based policies, see [How IAM Roles Differ from Resource\-based Policies](id_roles_compare-resource-policies.md)\.  ](id_roles_terms-and-concepts.md#term_trust-policy)\. To learn how allowing cross\-account access using roles is different from allowing cross\-account access using other resource\-based policies, see [How IAM Roles Differ from Resource\-based Policies](id_roles_compare-resource-policies.md)\. 

**Important**  
Other services can affect the policy evaluation logic\. For example, AWS Organizations supports [service control policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html) that can be applied to principals one or more accounts\. AWS Resource Access Manager supports [policy fragments](https://docs.aws.amazon.com/ram/latest/userguide/permissions.html) that control which actions that principals are allowed to perform on resources that are shared with them\.

## Determining Whether a Cross\-Account Request Is Allowed<a name="policy-eval-cross-account"></a>

For cross\-account requests, the requester in the trusted `AccountA` must have an identity\-based policy\. That policy must allow them to make a request to the resource in the trusting `AccountB`\. Additionally, the resource\-based policy in `AccountB` must allow the requester in `AccountA` to access the resource\.

When you make a cross\-account request, AWS performs two evaluations\. AWS evaluates the request in the trusting account and the trusted account\. For more information about how a request is evaluated within a single account, see [Determining Whether a Request Is Allowed or Denied Within an Account](reference_policies_evaluation-logic.md#policy-eval-denyallow)\. The request is allowed only if both evaluations return a decision of `Allow`\.

![\[Cross-account evalusation\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_cross-account-eval-simple.png)

1. When a principal in one account makes a request to access a resource in another account, this is a cross\-account request\.

1. The requesting principal exists in the trusted account \(`AccountA`\)\. When AWS evaluates this account, it checks the identity\-based policy and any policies that can limit an identity\-based policy\. For more information, see [Evaluating Policies Within a Single Account](reference_policies_evaluation-logic.md#policy-eval-basics)\.

1. The requested resource exists in the trusting account \(`AccountB`\)\. When AWS evaluates this account, it checks the resource\-based policy that is attached to the requested resource and any policies that can limit a resource\-based policy\. For more information, see [Evaluating Policies Within a Single Account](reference_policies_evaluation-logic.md#policy-eval-basics)\.

1. AWS allows the request only if both account policy evaluations allow the request\.

## Example Cross\-Account Policy Evaluation<a name="policies_evaluation_example-cross-account"></a>

The following example demonstrates a scenario where a user in one account is granted permissions by a resource\-based policy in a second account\.

Assume that Carlos is a developer with an IAM user named `carlossalazar` in account 111111111111\. He wants to save a file to the `Production-logs` Amazon S3 bucket in account 222222222222\. 

Also assume that the following policy is attached to the `carlossalazar` IAM user\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowS3ListRead",
            "Effect": "Allow",
            "Action": "s3:ListAllMyBuckets",
            "Resource": "*"
        },
        {
            "Sid": "AllowS3ProductionObjectActions",
            "Effect": "Allow",
            "Action": "s3:*Object*",
            "Resource": "arn:aws:s3:::Production/*"
        },
        {
            "Sid": "DenyS3Logs",
            "Effect": "Deny",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::*log*",
                "arn:aws:s3:::*log*/*"
            ]
        }
    ]
}
```

The `AllowS3ListRead` statement in this policy allows Carlos to view a list of all of the buckets in Amazon S3\. The `AllowS3ProductionObjectActions` statement allows Carlos full access to objects in the `Production` bucket\. The `DenyS3Logs` statement denies Carlos access to any S3 bucket with `log` in its name\. It also denies access to all objects in those buckets\.

Additionally, the following resource\-based policy \(called a bucket policy\) is attached to the `Production` bucket in account 222222222222\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject*",
                "s3:PutObject*",
                "s3:ReplicateObject",
                "s3:RestoreObject"
            ],
            "Principal": { "AWS": "arn:aws:iam::111111111111:user/carlossalazar" },
            "Resource": "arn:aws:s3:::Production/*"
        }
    ]
}
```

This policy allows the `carlossalazar` user to access objects in the `Production` bucket\. He can create and edit, but not delete the objects in the bucket\. He can't manage the bucket itself\.

When Carlos makes his request to save a file to the `Production-logs` bucket, AWS determines what policies apply to the request\. In this case, the identity\-based policy attached to the `carlossalazar` user is the only policy that applies in account `111111111111`\. In account `222222222222`, there is no resource\-based policy attached to the `Production-logs` bucket\. When AWS evaluates account `111111111111`, it returns a decision of `Deny`\. This is because the `DenyS3Logs` statement in the identity\-based policy explicitly denies access to any log buckets\. For more information about how a request is evaluated within a single account, see [Determining Whether a Request Is Allowed or Denied Within an Account](reference_policies_evaluation-logic.md#policy-eval-denyallow)\.

Because the request is explicitly denied within one of the accounts, the final decision is to deny the request\.

![\[Request to Production-logs bucket\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_cross-account-eval-example.png)

Assume that Carlos then realizes his mistake and tries to save the file to the `Production` bucket\. AWS first checks account `111111111111` to determine if the request is allowed\. Only the identity\-based policy applies, and it allows the request\. AWS then checks account `222222222222`\. Only the resource\-based policy attached to the `Production` bucket applies, and it allows the request\. Because both accounts allow the request, the final decision is to allow the request\.

![\[Request to Production bucket\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_cross-account-eval-example-correct.png)