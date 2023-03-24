# Getting started with managed policies<a name="access_policies-getting-started-managed"></a>

We recommend using policies that [grant least privilege](access_policies.md#grant-least-priv), or granting only the permissions required to perform a task\. The most secure way to grant least privilege is to write a customer managed policy with only the permissions needed by your team\. You must create a process to allow your team to request more permissions when necessary\. It takes time and expertise to [create IAM customer managed policies](access_policies_create-console.md) that provide your team with only the permissions they need\.

To get started adding permissions to your IAM identities \(users, groups of users, and roles\), you can use [AWS managed policies](access_policies_managed-vs-inline.md#aws-managed-policies)\. AWS managed policies don't grant least privilege permissions\. You must consider the security risk of granting your principals more permissions than they need to do their job\.

You can attach AWS managed policies, including job functions, to any IAM identity\. For more information, see [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md)\.

To switch to least privilege permissions, you can run AWS Identity and Access Management Access Analyzer to monitor the principals with AWS managed policies\. After learning which permissions they are using, then you can write or generate a customer managed policy with only the required permissions for your team\. This is less secure, but provides more flexibility as you learn how your team is using AWS\. For more information, see [IAM Access Analyzer policy generation](access-analyzer-policy-generation.md)\.

AWS managed policies are designed to provide permissions for many common use cases\. For more information about AWS managed policies that are designed for specific job functions, see [AWS managed policies for job functions](access_policies_job-functions.md)\.

For a list of AWS managed policies, see [AWS Managed Policy Reference Guide](https://docs.aws.amazon.com/aws-managed-policy/latest/reference/about-managed-policy-reference.html)\.