# AWS JSON policy elements: Principal<a name="reference_policies_elements_principal"></a>

Use the `Principal` element in a policy to specify the principal that is allowed or denied access to a resource\. You cannot use the `Principal` element in an IAM identity\-based policy\. You can use it in the trust policies for IAM roles and in resource\-based policies\. Resource\-based policies are policies that you embed directly in an IAM resource\. For example, you can embed policies in an Amazon S3 bucket or an AWS KMS customer master key \(CMK\)\.

You can specify any of the following principals in a policy:
+ AWS account and root user
+ IAM users
+ Federated users \(using web identity or SAML federation\)
+ IAM roles
+ Assumed\-role sessions
+ AWS services
+ Anonymous users \(not recommended\)

Use the `Principal` element in these ways:
+ In IAM roles, use the `Principal` element in the role's trust policy to specify who can assume the role\. For cross\-account access, you must specify the 12\-digit identifier of the trusted account\. To learn whether principals in accounts outside of your zone of trust \(trusted organization or account\) have access to assume your roles, see [What is IAM Access Analyzer?](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)\.
**Note**  
After you create the role, you can change the account to "\*" to allow everyone to assume the role\. If you do this, we strongly recommend that you limit who can access the role through other means, such as a `Condition` element that limits access to only certain IP addresses\. Do not leave your role accessible to everyone\!
+ In resource\-based policies, use the `Principal` element to specify the accounts or users who are allowed to access the resource\. 

Do not use the `Principal` element in policies that you attach to IAM users and groups\. Similarly, you do not specify a principal in the permission policy for an IAM role\. In those cases, the principal is implicitly the user that the policy is attached to \(for IAM users\) or the user who assumes the role \(for role access policies\)\. When the policy is attached to an IAM group, the principal is the IAM user in that group who is making the request\. 

## Specifying a principal<a name="Principal_specifying"></a>

You specify a principal using the [*Amazon Resource Name* \(ARN\)](reference_identifiers.md#identifiers-arns) or other identifier of the principal\. You cannot specify IAM groups and instance profiles as principals\. 

The following examples show different methods for specifying principals\.

### Specific AWS accounts<a name="principal-accounts"></a>

When you use an AWS account identifier as the principal in a policy, you delegate authority to the account\. All identities inside the account can access the resource if they have the appropriate IAM permissions attached to explicitly allow access\. This includes IAM users and roles in that account\. When you specify an AWS account, you can use the account ARN \(arn:aws:iam::*AWS\-account\-ID*:root\), or a shortened form that consists of the `AWS:` prefix followed by the account ID\.

For example, given an account ID of `123456789012`, you can use either of the following methods to specify that account in the `Principal` element:

```
"Principal": { "AWS": "arn:aws:iam::123456789012:root" }
```

```
"Principal": { "AWS": "123456789012" }
```

You can also specify more than one AWS account as a principal using an array, with any combination of the methods that we previously mentioned\.

```
"Principal": { 
  "AWS": [
    "arn:aws:iam::123456789012:root",
    "999999999999"
  ]
}
```

Some AWS services support additional options for specifying an account principal\. For example, Amazon S3 lets you specify a [canonical user ID](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html#FindingCanonicalId) using the following format:

```
"Principal": { "CanonicalUser": "79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be" }
```

### Individual IAM users<a name="principal-users"></a>

You can specify an individual IAM user \(or array of users\) as the principal, as in the following examples\. When you specify more than one principal in the element, you grant permissions to each principal\. This is a logical `OR` and not a logical `AND`, because you are authenticated as one principal at a time\. 

**Note**  
In a `Principal` element, the user name is case sensitive\.

```
"Principal": { "AWS": "arn:aws:iam::AWS-account-ID:user/user-name" }
```

```
"Principal": {
  "AWS": [
    "arn:aws:iam::AWS-account-ID:user/user-name-1", 
    "arn:aws:iam::AWS-account-ID:user/UserName2"
  ]
}
```

When you specify users in a `Principal` element, you cannot use a wildcard \(`*`\) to mean "all users"\. Principals must always name a specific user or users\. 

**Important**  
If your `Principal` element in a role trust policy contains an ARN that points to a specific IAM user, then that ARN is transformed to the user's unique principal ID when the policy is saved\. This helps mitigate the risk of someone escalating their privileges by removing and recreating the user\. You don't normally see this ID in the console, because there is also a reverse transformation back to the user's ARN when the trust policy is displayed\. However, if you delete the user, then the relationship is broken\. The policy no longer applies, even if you recreate the user\. That's because the new user has a new principal ID that does not match the ID stored in the trust policy\. When this happens, the principal ID shows up in the console because AWS can no longer map it back to a valid ARN\. The result is that if you delete and recreate a user referenced in a trust policy's `Principal` element, you must edit the role to replace the now incorrect principal ID with the correct ARN\. The ARN is once again transformed into the user's new principal ID when you save the policy\.

### Federated web identity users<a name="principal-federated-web-identity"></a>

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

### Federated SAML users<a name="principal-saml"></a>

```
"Principal": { "Federated": "arn:aws:iam::AWS-account-ID:saml-provider/provider-name" }
```

### IAM roles<a name="principal-roles"></a>

```
"Principal": { "AWS": "arn:aws:iam::AWS-account-ID:role/role-name" }
```

**Important**  
If your `Principal` element in a role trust policy contains an ARN that points to a specific IAM role, then that ARN is transformed to the role's unique principal ID when the policy is saved\. This helps mitigate the risk of someone escalating their privileges by removing and recreating the role\. You don't normally see this ID in the console, because there is also a reverse transformation back to the role's ARN when the trust policy is displayed\. However, if you delete the role, then the relationship is broken\. The policy no longer applies, even if you recreate the role because the new role has a new principal ID that does not match the ID stored in the trust policy\. When this happens, the principal ID shows up in the console because AWS can no longer map it back to a valid ARN\. The end result is that if you delete and recreate a role referenced in a trust policy's `Principal` element, you must edit the role to replace the now incorrect principal ID with the correct ARN\. The ARN will once again be transformed into the role's new principal ID when you save the policy\.

### Specific assumed\-role sessions<a name="principal-sessions"></a>

```
"Principal": { "AWS": "arn:aws:sts::AWS-account-ID:assumed-role/role-name/role-session-name" }
```

When you specify an assumed\-role session in a `Principal` element, you cannot use a wildcard \(\*\) to mean "all sessions"\. Principals must always name a specific session\.

### AWS services<a name="principal-services"></a>

IAM roles that can be assumed by an AWS service are called *[service roles](id_roles_terms-and-concepts.md#iam-term-service-role)*\. Service roles must include a trust policy\. *Trust policies* are resource\-based policies that are attached to a role that define which principals can assume the role\. Some service roles have predefined trust policies\. However, in some cases, you must specify the service principal in the trust policy\. A *service principal* is an identifier that is used to grant permissions to a service\. The identifier includes the long version of a service name, and is usually in the following format:

`long_service-name.amazonaws.com`

The service principal is defined by the service\. To learn the service principal for a service, see the documentation for that service\. For some services, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\. View the **Service\-Linked Role Permissions** section for that service to view the service principal\.

The following example shows a policy that can be attached to a service role\. The policy enables two services, Amazon EMR and AWS Data Pipeline, to assume the role\. The services can then perform any tasks granted by the permissions policy assigned to the role \(not shown\)\. To specify multiple service principals, you do not specify two `Service` elements; you can have only one\. Instead, you use an array of multiple service principals as the value of a single `Service` element\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": [
          "elasticmapreduce.amazonaws.com",
          "datapipeline.amazonaws.com"
        ]
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

### Anonymous users \(public\)<a name="principal-anonymous"></a>

For resource\-based policies, such as Amazon S3 bucket policies, a wildcard \(\*\) in the principal element specifies all users or public access\. The following elements are equivalent:

```
"Principal": "*"
```

```
"Principal" : { "AWS" : "*" }
```

You cannot use a wildcard to match part of a name or an ARN\. 

We strongly recommend that you do not use a wildcard in the `Principal` element in a role's trust policy unless you otherwise restrict access through a `Condition` element in the policy\. Otherwise, any IAM user in any account in your [partition](reference_identifiers.md#identifiers-arns) can access the role\.

## More information<a name="Principal_more-info"></a>

For more information, see the following:
+ [Bucket Policy Examples](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) in the *Amazon Simple Storage Service Developer Guide*
+ [Example Policies for Amazon SNS](https://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#ExamplePolicies_SNS) in the *Amazon Simple Notification Service Developer Guide*
+ [Amazon SQS Policy Examples](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSExamples.html) in the *Amazon Simple Queue Service Developer Guide*
+ [Key Policies](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html) in the *AWS Key Management Service Developer Guide*
+ [Account Identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *AWS General Reference*
+ [About web identity federation](id_roles_providers_oidc.md)