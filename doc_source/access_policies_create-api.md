# Creating IAM Policies \(AWS API\)<a name="access_policies_create-api"></a>

A [policy](access_policies.md) is an entity that, when attached to an identity or resource, defines their permissions\. You can use the AWS API to create *customer managed policies* in IAM\. Customer managed policies are standalone policies that you administer in your own AWS account\. You can then attach the policies to identities \(users, groups, and roles\) in your AWS account\.

For information about policy size limitations and other quotas, see [IAM and STS Limits](reference_iam-limits.md)\.

## Creating IAM Policies \(AWS API\)<a name="create-policies-api"></a>

You can create an IAM customer managed policy or an inline policy using the AWS API\.

**To create a customer managed policy \(AWS API\)**  
Call the following operation:
+ [CreatePolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicy.html)

**To create an inline policy for an IAM identity \(group, user, or role\) \(AWS API\)**  
Call one of the following operations:
+ [PutGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_PutGroupPolicy.html)
+ [PutRolePolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)
+ [PutUserPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_PutUserPolicy.html)

**Note**  
You can't use IAM to embed an inline policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\.