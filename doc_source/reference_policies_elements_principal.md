# IAM JSON Policy Elements: Principal<a name="reference_policies_elements_principal"></a>

Use the `Principal` element to specify the user \(IAM user, federated user, or assumed\-role user\), AWS account, AWS service, or other principal entity that is allowed or denied access to a resource\. You use the `Principal` element in the trust policies for IAM roles and in resource\-based policies—that is, in policies that you embed directly in a resource\. For example, you can embed such policies in an Amazon S3 bucket, an Amazon Glacier vault, an Amazon SNS topic, an Amazon SQS queue, or an AWS KMS customer master key \(CMK\)\.

Use the `Principal` element in these ways:
+ In IAM roles, use the `Principal` element in the role's trust policy to specify who can assume the role\. For cross\-account access, you must specify the 12\-digit identifier of the trusted account\. 
**Note**  
After you create the role, you can change the account to "\*" to allow everyone to assume the role\. If you do this, we strongly recommend that you limit who can access the role through other means, such as a `Condition` element that limits access to only certain IP addresses\. Do not leave your role accessible to everyone\!
+ In resource\-based policies, use the `Principal` element to specify the accounts or users who are allowed to access the resource\. 

Do not use the `Principal` element in policies that you attach to IAM users and groups\. Similarly, you do not specify a principal in the permission policy for an IAM role\. In those cases, the principal is implicitly the user that the policy is attached to \(for IAM users\) or the user who assumes the role \(for role access policies\)\. When the policy is attached to an IAM group, the principal is the IAM user in that group who is making the request\. 

## Specifying a Principal<a name="Principal_specifying"></a>

You specify a principal using the [*Amazon Resource Name* \(ARN\)](reference_identifiers.md#identifiers-arns) of the AWS account, IAM user, IAM role, federated user, or assumed\-role user\. You cannot specify IAM groups as principals\. 

The following examples show various ways in which principals can be specified\.

**Specific AWS accounts**

When you use an AWS account identifier as the principal in a policy, the permissions in the policy statement can be granted to all identities contained in that account\. This includes IAM users and roles in that account\. When you specify an AWS account, you can use the account ARN \(arn:aws:iam::*AWS\-account\-ID*:root\), or a shortened form that consists of the `AWS:` prefix followed by the account ID\.

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

**Individual IAM user or users**

You can specify an individual IAM user \(or array of users\) as the principal, as in the following examples\. 

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

**Federated users \(using web identity federation\)** 

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

**Federated users \(using a SAML identity provider\)**

```
"Principal": { "Federated": "arn:aws:iam::AWS-account-ID:saml-provider/provider-name" }
```

**IAM role**

```
"Principal": { "AWS": "arn:aws:iam::AWS-account-ID:role/role-name" }
```

**Important**  
If your `Principal` element in a role trust policy contains an ARN that points to a specific IAM role, then that ARN is transformed to the role's unique principal ID when the policy is saved\. This helps mitigate the risk of someone escalating their privileges by removing and recreating the role\. You don't normally see this ID in the console, because there is also a reverse transformation back to the role's ARN when the trust policy is displayed\. However, if you delete the role, then the relationship is broken\. The policy no longer applies, even if you recreate the role because the new role has a new principal ID that does not match the ID stored in the trust policy\. When this happens, the principal ID shows up in the console because AWS can no longer map it back to a valid ARN\. The end result is that if you delete and recreate a role referenced in a trust policy's `Principal` element, you must edit the role to replace the now incorrect principal ID with the correct ARN\. The ARN will once again be transformed into the role's new principal ID when you save the policy\.

**Specific assumed\-role user**

```
"Principal": { "AWS": "arn:aws:sts::AWS-account-ID:assumed-role/role-name/role-session-name" }
```

**AWS service**

IAM roles that can be assumed by an AWS service are called *[service roles](id_roles_terms-and-concepts.md#iam-term-service-role)*\. Service roles must include a trust policy\. *Trust policies* are resource\-based policies that are attached to a role that define which principals can assume the role\. Some service role have predefined trust policies\. However, in some cases, you must specify the service principal in the trust policy\. A *service principal* is an identifier that is used to grant permissions to a service\. The identifier includes the long version of a service name, and is usually in the following format:

`long_service-name.amazonaws.com`

The service principal is defined by the service\. To learn the service principal for a service, see the documentation for that service\. 

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

Some AWS services support additional options for specifying a principal\. For example, Amazon S3 lets you specify a [canonical user ID](http://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html#FindingCanonicalId) using the following format:

```
"Principal": { "CanonicalUser": "79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be" }
```

**Everyone \(anonymous users\)** 

The following are equivalent:

```
"Principal": "*"
```

```
"Principal" : { "AWS" : "*" }
```

**Note**  
In these examples, the asterisk \(\*\) is used as a placeholder for Everyone/Anonymous\. You cannot use it as a wildcard to match part of a name or an ARN\. We also strongly recommend that you do not use a wildcard in the `Principal` element in a role's trust policy unless you otherwise restrict access through a `Condition` element in the policy\. Otherwise, any IAM user in any account can access the role\.

## More Information<a name="Principal_more-info"></a>

For more information, see the following:
+ [Bucket Policy Examples](http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) in the *Amazon Simple Storage Service Developer Guide*
+ [Example Policies for Amazon SNS](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html#ExamplePolicies_SNS) in the *Amazon Simple Notification Service Developer Guide*
+ [Amazon SQS Policy Examples](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/SQSExamples.html) in the *Amazon Simple Queue Service Developer Guide*
+ [Key Policies](http://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html) in the *AWS Key Management Service Developer Guide*
+ [Account Identifiers](http://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *AWS General Reference*
+ [About Web Identity Federation](id_roles_providers_oidc.md)