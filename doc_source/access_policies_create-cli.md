# Creating IAM Policies \(AWS CLI\)<a name="access_policies_create-cli"></a>

A [policy](access_policies.md) is an entity that, when attached to an identity or resource, defines their permissions\. You can use the AWS CLI to create *customer managed policies* in IAM\. Customer managed policies are standalone policies that you administer in your own AWS account\. You can then attach the policies to identities \(users, groups, and roles\) in your AWS account\.

For information about policy size limitations and other quotas, see [IAM and STS Limits](reference_iam-limits.md)\.

## Creating IAM Policies \(AWS CLI\)<a name="create-policies-cli-api"></a>

You can create an IAM customer managed policy or an inline policy using the AWS Command Line Interface \(AWS CLI\)\. 

**To create a customer managed policy \(AWS CLI\)**  
Use the following command:
+ [create\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/create-policy.html)

**To create an inline policy for an IAM identity \(group, user or role\) \(AWS CLI\)**  
Use one of the following commands:
+ [put\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/put-group-policy.html)
+ [put\-role\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)
+ [put\-user\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/put-user-policy.html)

**Note**  
You can't use IAM to embed an inline policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*\.