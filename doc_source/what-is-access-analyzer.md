# Using AWS IAM Access Analyzer<a name="what-is-access-analyzer"></a>

AWS IAM Access Analyzer provides the following capabilities:
+ Access Analyzer helps [identify resources](#what-is-access-analyzer-resource-identification) in your organization and accounts that are shared with an external entity\.
+ Access Analyzer [validates IAM policies](#what-is-access-analyzer-policy-validation) against policy grammar and best practices\.
+ Access Analyzer [generates IAM policies](#what-is-access-analyzer-policy-generation) based on access activity in your AWS CloudTrail logs\.

## Identifying resources shared with an external entity<a name="what-is-access-analyzer-resource-identification"></a>

Access Analyzer helps you identify the resources in your organization and accounts, such as Amazon S3 buckets or IAM roles, shared with an external entity\. This lets you identify unintended access to your resources and data, which is a security risk\. Access Analyzer identifies resources shared with external principals by using logic\-based reasoning to analyze the resource\-based policies in your AWS environment\. For each instance of a resource shared outside of your account, Access Analyzer generates a finding\. Findings include information about the access and the external principal granted to it\. You can review findings to determine whether the access is intended and safe or the access is unintended and a security risk\. In addition to helping you identify resources shared with an external entity, you can use Access Analyzer findings to preview how your policy affects public and cross\-account access to your resource before deploying resource permissions\.

**Note**  
An external entity can be another AWS account, a root user, an IAM user or role, a federated user, an AWS service, an anonymous user, or other entity that you can use to create a filter\. For more information, see [AWS JSON Policy Elements: Principal](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html)\.

When you enable Access Analyzer, you create an analyzer for your entire organization or your account\. The organization or account you choose is known as the zone of trust for the analyzer\. The analyzer monitors all of the [supported resources](access-analyzer-resources.md) within your zone of trust\. Any access to resources by principals within your zone of trust is considered trusted\. Once enabled, Access Analyzer analyzes the policies applied to all of the supported resources in your zone of trust\. After the first analysis, Access Analyzer analyzes these policies periodically\. If you add a new policy , or change an existing policy, Access Analyzer analyzes the new or updated policy within about 30 minutes\.

When analyzing the policies, if Access Analyzer identifies one that grants access to an external principal that isn't within your zone of trust, it generates a finding\. Each finding includes details about the resource, the external entity with access to it, and the permissions granted so that you can take appropriate action\. You can view the details included in the finding to determine whether the resource access is intentional or a potential risk that you should resolve\. When you add a policy to a resource, or update an existing policy, Access Analyzer analyzes the policy\. Access Analyzer also analyzes all resource\-based policies periodically\.

On rare occasions under certain conditions, Access Analyzer does not receive notification of an added or updated policy\. Access Analyzer can take up to 6 hours to generate or resolve findings if you create or delete a multi\-region access point associated with an S3 bucket, or update the policy for the multi\-region access point\. Also, if there is a delivery issue with AWS CloudTrail log delivery, the policy change does not trigger a rescan of the resource reported in the finding\. When this happens, Access Analyzer analyzes the new or updated policy during the next periodic scan, which is within 24 hours\. If you want to confirm a change you make to a policy resolves an access issue reported in a finding, you can rescan the resource reported in a finding by using the **Rescan** link in the **Findings** details page, or by using the [https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_StartResourceScan.html](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_StartResourceScan.html) operation of the Access Analyzer API\. To learn more, see [Resolving findings](access-analyzer-findings-remediate.md)\.

**Important**  
Access Analyzer analyzes only policies applied to resources in the same AWS Region where it's enabled\. To monitor all resources in your AWS environment, you must create an analyzer to enable Access Analyzer in each Region where you're using supported AWS resources\.

Access Analyzer analyzes the following resource types:
+ [Amazon Simple Storage Service buckets](access-analyzer-resources.md#access-analyzer-s3)
+ [AWS Identity and Access Management roles](access-analyzer-resources.md#access-analyzer-iam-role)
+ [AWS Key Management Service keys](access-analyzer-resources.md#access-analyzer-kms-key)
+ [AWS Lambda functions and layers](access-analyzer-resources.md#access-analyzer-lambda)
+ [Amazon Simple Queue Service queues](access-analyzer-resources.md#access-analyzer-sqs)
+ [AWS Secrets Manager secrets](access-analyzer-resources.md#access-analyzer-secrets-manager)

## Validating policies<a name="what-is-access-analyzer-policy-validation"></a>

You can validate your policies using Access Analyzer policy checks\. You can create or edit a policy using the AWS CLI, AWS API, or JSON policy editor in the IAM console\. Access Analyzer validates your policy against IAM [policy grammar](reference_policies_grammar.md) and [best practices](best-practices.md)\. You can view policy validation check findings that include security warnings, errors, general warnings, and suggestions for your policy\. These findings provide actionable recommendations that help you author policies that are functional and conform to security best practices\. To learn more about validating policies using Access Analyzer, see [Access Analyzer policy validation](access-analyzer-policy-validation.md)\.

## Generating policies<a name="what-is-access-analyzer-policy-generation"></a>

Access Analyzer analyzes your AWS CloudTrail logs to identify actions and services that have been used by an IAM entity \(user or role\) within your specified date range\. It then generates an IAM policy that is based on that access activity\. You can use the generated policy to refine an entity's permissions by attaching it to an IAM user or role\. To learn more about generating policies using Access Analyzer, see [IAM Access Analyzer policy generation](access-analyzer-policy-generation.md)\.
