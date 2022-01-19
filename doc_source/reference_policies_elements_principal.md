# AWS JSON policy elements: Principal<a name="reference_policies_elements_principal"></a>

Use the `Principal` element in a resource\-based JSON policy to specify the principal that is allowed or denied access to a resource\. 

You can use the `Principal` element in [resource\-based policies](access_policies_identity-vs-resource.md)\. Several services support resource\-based policies, including IAM\. The IAM resource\-based policy type is a role trust policy\. In IAM roles, use the `Principal` element in the role trust policy to specify who can assume the role\. For cross\-account access, you must specify the 12\-digit identifier of the trusted account\. To learn whether principals in accounts outside of your zone of trust \(trusted organization or account\) have access to assume your roles, see [What is IAM Access Analyzer?](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)\.

**Note**  
After you create the role, you can change the account to "\*" to allow everyone to assume the role\. If you do this, we strongly recommend that you limit who can access the role through other means, such as a `Condition` element that limits access to only certain IP addresses\. Do not leave your role accessible to everyone\!

Other examples of resources that support resource\-based policies include an Amazon S3 bucket or an AWS KMS key\.

You cannot use the `Principal` element in an identity\-based policy\. Identity\-based policies are permissions policies that you attach to IAM identities \(users, groups, or roles\)\. In those cases, the principal is implicitly the identity where the policy is attached\.

## Specifying a principal<a name="Principal_specifying"></a>

You specify a principal in the `Principal` element of a resource\-based policy or in condition keys that support principals\. For example, you can specify a principal [*Amazon Resource Name* \(ARN\)](reference_identifiers.md#identifiers-arns) in the `aws:PrincipalArn` condition key\. 

You can specify any of the following principals in a policy:
+ AWS account and root user
+ IAM roles
+ Role sessions 
+ IAM users
+ Federated user sessions
+ AWS services
+ All principals

You can specify more than one principal for each of the principal types in following sections using an array\. Arrays can take one or more values\. When you specify more than one principal in an element, you grant permissions to each principal\. This is a logical `OR` and not a logical `AND`, because you authenticate as one principal at a time\. If you include more than one value, use square brackets \(`[` and `]`\) and comma\-delimit each entry for the array\. The following example policy defines permissions for the 123456789012 account or the 555555555555 account\.

```
"Principal" : { 
"AWS": [ 
  "123456789012",
  "555555555555" 
  ]
}
```

**Note**  
You cannot use a wildcard to match part of a principal name or ARN\. 

## AWS account principals<a name="principal-accounts"></a>

You can specify AWS account identifiers in the `Principal` element of a resource\-based policy or in condition keys that support principals\. This delegates authority to the account\. When you allow access to a different account, an administrator in that account must then grant access to an identity \(IAM user or role\) in that account\. When you specify an AWS account, you can use the account ARN \(arn:aws:iam::*account\-ID*:root\), or a shortened form that consists of the `"AWS":` prefix followed by the account ID\.

For example, given an account ID of `123456789012`, you can use either of the following methods to specify that account in the `Principal` element:

```
"Principal": { "AWS": "arn:aws:iam::123456789012:root" }
```

```
"Principal": { "AWS": "123456789012" }
```

The account ARN and the shortened account ID behave the same way\. Both delegate permissions to the account\. Using the account ARN in the `Principal` element does not limit permissions to only the root user of the account\. 

**Note**  
When you save a resource\-based policy that includes the shortened account ID, the service might convert it to the principal ARN\. This does not change the functionality of the policy\.

Some AWS services support additional options for specifying an account principal\. For example, Amazon S3 lets you specify a [canonical user ID](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html#FindingCanonicalId) using the following format:

```
"Principal": { "CanonicalUser": "79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be" }
```

You can also specify more than one AWS account, \(or canonical user ID\) as a principal using an array\. For example, you can specify a principal in a bucket policy using all three methods\.

```
"Principal": { 
  "AWS": [
    "arn:aws:iam::123456789012:root",
    "999999999999"
  ],
  "CanonicalUser": "79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be"
}
```

## IAM role principals<a name="principal-roles"></a>

You can specify IAM role principal ARNs in the `Principal` element of a resource\-based policy or in condition keys that support principals\. IAM roles are identities\. In IAM, identities are resources to which you can assign permissions\. Roles trust another authenticated identity to assume that role\. This includes a principal in AWS or a user from an external identity provider \(IdP\)\. When a principal or identity assumes a role, they receive temporary security credentials with the assumed role’s permissions\. When they use those session credentials to perform operations in AWS, they become a *role session principal*\. 

IAM roles are identities that exist in IAM\. Roles trust another authenticated identity, such as a principal in AWS or a user from an external identity provider\. When a principal or identity assumes a role, they receive temporary security credentials\. They can then use those credentials as a role session principal to perform operations in AWS\. 

When you specify a role principal in a resource\-based policy, the effective permissions for the principal are limited by any policy types that limit permissions for the role\. This includes session policies and permissions boundaries\. For more information about how the effective permissions for a role session are evaluated, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.

To specify the role ARN in the `Principal` element, use the following format:

```
"Principal": { "AWS": "arn:aws:iam::AWS-account-ID:role/role-name" }
```

**Important**  
If your `Principal` element in a role trust policy contains an ARN that points to a specific IAM role, then that ARN transforms to the role unique principal ID when you save the policy\. This helps mitigate the risk of someone escalating their privileges by removing and recreating the role\. You don't normally see this ID in the console, because IAM uses a reverse transformation back to the role ARN when the trust policy is displayed\. However, if you delete the role, then you break the relationship\. The policy no longer applies, even if you recreate the role because the new role has a new principal ID that does not match the ID stored in the trust policy\. When this happens, the principal ID shows up in the console because AWS can no longer map it back to a valid ARN\. The end result is that if you delete and recreate a role referenced in a trust policy's `Principal` element, you must edit the role to replace the now incorrect principal ID with the correct ARN\. The ARN once again transforms into the role's new principal ID when you save the policy\.

Alternatively, you can specify the role principal as the principal in a resource\-based policy or [create a broad\-permission policy](#principal-anonymous) that uses the `aws:PrincipalArn` condition key\. When you use this key, the role session principal is granted the permissions based on the ARN of role that was assumed, and not the ARN of the resulting session\. Because AWS does not convert condition key ARNs to IDs, permissions granted to the role ARN persist if you delete the role and then create a new role with the same name\. Permissions granted using the `aws:PrincipalArn` condition key are not limited by Identity\-based policy types such as permissions boundaries or session policies\.

## Role session principals<a name="principal-role-session"></a>

You can specify role sessions in the `Principal` element of a resource\-based policy or in condition keys that support principals\. When a principal or identity assumes a role, they receive temporary security credentials with the assumed role’s permissions\. When they use those session credentials to perform operations in AWS, they become a *role session principal*\.

The format that you use for a role session principal depends on the AWS STS operation that was used to assume the role\.

Additionally, administrators can design a process to control how role sessions are issued\. For example, they can provide a one\-click solution for their users that creates a predictable session name\. If your administrator does this, you can use role session principals in your policies or condition keys\. Otherwise, you can specify the role ARN as a principal or in the `aws:PrincipalArn` condition key\. How you specify the role as a principal can change the effective permissions for the resulting session\. For more information, see [IAM role principals](#principal-roles)\. 

### Assumed\-role session principals<a name="principal-sessions"></a>

An *assumed\-role session principal* is a session principal that results from using the AWS STS `AssumeRole` operation\. For more information about which principals can assume a role using this operation, see [Comparing the AWS STS API operations](id_credentials_temp_request.md#stsapi_comparison)\.

To specify the assumed\-role session ARN in the `Principal` element, use the following format:

```
"Principal": { "AWS": "arn:aws:sts::AWS-account-ID:assumed-role/role-name/role-session-name" }
```

When you specify an assumed\-role session in a `Principal` element, you cannot use a wildcard "\*" to mean all sessions\. Principals must always name a specific session\.

### Web identity session principals<a name="principal-federated-web-identity"></a>

A *web identity session principal* is a session principal that results from using the AWS STS `AssumeRoleWithWebIdentity` operation\. You can use an external web identity provider \(IdP\) to sign in, and then assume an IAM role using this operation\. This leverages identity federation and issues a role session\. For more information about which principals can assume a role using this operation, see [Comparing the AWS STS API operations](id_credentials_temp_request.md#stsapi_comparison)\.

When you issue a role from a web identity provider, you get this special type of session principal that includes information about the web identity provider\. 

Use this principal type in your policy to allow or deny access based on the trusted web identity provider\. To specify the web identity role session ARN in the `Principal` element of a role trust policy, use the following format:

```
"Principal": { "Federated": "cognito-identity.amazonaws.com" }
```

```
"Principal": { "Federated": "www.amazon.com" }
```

```
"Principal": { "Federated": "graph.facebook.com" }
```

```
"Principal": { "Federated": "accounts.google.com" }
```

### SAML session principals<a name="principal-saml"></a>

A *SAML session principal* is a session principal that results from using the AWS STS `AssumeRoleWithSAML` operation\. You can use an external SAML identity provider \(IdP\) to sign in, and then assume an IAM role using this operation\. This leverages identity federation and issues a role session\. For more information about which principals can assume a role using this operation, see [Comparing the AWS STS API operations](id_credentials_temp_request.md#stsapi_comparison)\.

When you issue a role from a SAML identity provider, you get this special type of session principal that includes information about the SAML identity provider\.

Use this principal type in your policy to allow or deny access based on the trusted SAML identity provider\. To specify the web identity role session ARN in the `Principal` element of a role trust policy, use the following format:

```
"Principal": { "Federated": "arn:aws:iam::AWS-account-ID:saml-provider/provider-name" }
```

## IAM user principals<a name="principal-users"></a>

You can specify IAM users in the `Principal` element of a resource\-based policy or in condition keys that support principals\.

**Note**  
In a `Principal` element, the user name part of the [*Amazon Resource Name* \(ARN\)](reference_identifiers.md#identifiers-arns) is case sensitive\.

```
"Principal": { "AWS": "arn:aws:iam::AWS-account-ID:user/user-name" }
```

```
"Principal": {
  "AWS": [
    "arn:aws:iam::AWS-account-ID:user/user-name-1", 
    "arn:aws:iam::AWS-account-ID:user/user-name-2"
  ]
}
```

When you specify users in a `Principal` element, you cannot use a wildcard \(`*`\) to mean "all users"\. Principals must always name specific users\. 

**Important**  
If your `Principal` element in a role trust policy contains an ARN that points to a specific IAM user, then IAM transforms the ARN to the user's unique principal ID when you save the policy\. This helps mitigate the risk of someone escalating their privileges by removing and recreating the user\. You don't normally see this ID in the console, because there is also a reverse transformation back to the user's ARN when the trust policy is displayed\. However, if you delete the user, then you break the relationship\. The policy no longer applies, even if you recreate the user\. That's because the new user has a new principal ID that does not match the ID stored in the trust policy\. When this happens, the principal ID shows up in the console because AWS can no longer map it back to a valid ARN\. The result is that if you delete and recreate a user referenced in a trust policy `Principal` element, you must edit the role to replace the now incorrect principal ID with the correct ARN\. IAM once again transforms ARN into the user's new principal ID when you save the policy\.

## AWS STS federated user session principals<a name="sts-session-principals"></a>

You can specify *federated user sessions* in the `Principal` element of a resource\-based policy or in condition keys that support principals\.

**Important**  
AWS recommends that you use AWS STS federated user sessions only when necessary, such as when [root user access is required](https://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html#aws_tasks-that-require-root)\. Instead, [use roles to delegate permissions](best-practices.md#delegate-using-roles)\.

An *AWS STS federated user session principal* is a session principal that results from using the AWS STS `GetFederationToken` operation\. In this case, AWS STS uses [identity federation](https://aws.amazon.com/identity/federation/) as the method to obtain temporary access tokens instead of using IAM roles\. 

In AWS, IAM users or an AWS account root user can authenticate using long\-term access keys\. For more information about which principals can federate using this operation, see [Comparing the AWS STS API operations](id_credentials_temp_request.md#stsapi_comparison)\. 
+ **IAM federated user** – An IAM user federates using the `GetFederationToken` operation that results in a federated user session principal for that IAM user\.
+ **Federated root user** – A root user federates using the `GetFederationToken` operation that results in a federated user session principal for that root user\.

When an IAM user or root user requests temporary credentials from AWS STS using this operation, they begin a temporary federated user session\. This session’s ARN is based on the original identity that was federated\.

To specify the federated user session ARN in the `Principal` element, use the following format:

```
"Principal": { "AWS": "arn:aws:sts::AWS-account-ID:federated-user/user-name" }
```

## AWS service principals<a name="principal-services"></a>

You can specify AWS services in the `Principal` element of a resource\-based policy or in condition keys that support principals\. A *service principal* is an identifier for a service\. 

IAM roles that can be assumed by an AWS service are called *[service roles](id_roles_terms-and-concepts.md#iam-term-service-role)*\. Service roles must include a trust policy\. *Trust policies* are resource\-based policies attached to a role that defines which principals can assume the role\. Some service roles have predefined trust policies\. However, in some cases, you must specify the service principal in the trust policy\.

The identifier for a service principal includes the service name, and is usually in the following format:

`service-name.amazonaws.com`

The service principal is defined by the service\. You can find the service principal for some services by opening [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md), checking whether the service has **Yes **in the **Service\-linked role** column, and opening the **Yes** link to view the service\-linked role documentation for that service\. Find the **Service\-Linked Role Permissions** section for that service to view the service principal\.

The following example shows a policy that can be attached to a service role\. The policy enables two services, Amazon ECS and Elastic Load Balancing, to assume the role\. The services can then perform any tasks granted by the permissions policy assigned to the role \(not shown\)\. To specify multiple service principals, you do not specify two `Service` elements; you can have only one\. Instead, you use an array of multiple service principals as the value of a single `Service` element\.

```
"Principal": {
    "Service": [
        "ecs.amazonaws.com",
        "elasticloadbalancing.amazonaws.com"
   ]
}
```

## All principals<a name="principal-anonymous"></a>

You can use a wildcard \(\*\) to specify all principals in the `Principal` element of a resource\-based policy or in condition keys that support principals\. As a best practice, do this only with the `Condition` element and a condition key such as `aws:PrincipalArn` to limit those broad permissions\.

For resource\-based policies, such as Amazon S3 bucket policies, a wildcard \(\*\) in the principal element specifies all users or public access\. For example, you can use either of the following methods to specify all principals in the `Principal` element:

```
"Principal": "*"
```

```
"Principal" : { "AWS" : "*" }
```

Using `"Principal": "*"` with an `Allow` effect in a resource\-based policy allows anyone, even if they’re not signed in to AWS, to access your resource\. 

Using `"Principal" : { "AWS" : "*" }` with an `Allow` effect in a resource\-based policy allows any root user, IAM user, assumed\-role session, or federated user in any account in the same [partition](reference_identifiers.md#identifiers-arns) to access your resource\. For IAM user and role principals within your account, no other permissions are required\. For principals in other accounts, they must also have identity\-based permissions in their account that allow them to access your resource\. This is called [cross\-account access](reference_policies_evaluation-logic-cross-account.md)\. This method does not allow web identity session principals, SAML session principals, or service principals to access your resource\. 

**Important**  
Because anyone can create an AWS account, the **security level** of these two methods is equivalent, even though they function differently\.

You cannot use a wildcard to match part of a principal name or ARN\.

## More information<a name="Principal_more-info"></a>

For more information, see the following:
+ [Bucket Policy Examples](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) in the *Amazon Simple Storage Service User Guide*
+ [Example Policies for Amazon SNS](https://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#ExamplePolicies_SNS) in the *Amazon Simple Notification Service Developer Guide*
+ [Amazon SQS Policy Examples](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSExamples.html) in the *Amazon Simple Queue Service Developer Guide*
+ [Key Policies](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html) in the *AWS Key Management Service Developer Guide*
+ [Account Identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *AWS General Reference*
+ [About web identity federation](id_roles_providers_oidc.md)Web identity federation
