# Tagging AWS resources<a name="reference_tagging"></a>

You can assign metadata to your AWS resources in the form of *tags*\. Each tag is a label consisting of a user\-defined key and value\. Tags can help you manage, identify, organize, search for, and filter resources\. You can create tags to categorize resources by purpose, owner, environment, or other criteria\.

Each tag has two parts:
+ A *tag key* \(for example, `CostCenter`, `Environment`, or `Project`\)\. Tag keys are case sensitive\.
+ A *tag value* \(for example, `111122223333` or `Production`\)\. Like tag keys, tag values are case sensitive\.

You can use tags to categorize resources by purpose, owner, environment, or other criteria\.

You can tag resources for all cost\-accruing services in AWS\. For the following services, AWS recommends newer alternative AWS services that support tagging to better meet customer use cases\.
+ Amazon Cloud Directory
+ Amazon CloudSearch
+ Amazon Cognito Sync
+ AWS Data Pipeline
+ AWS DeepLens
+ Amazon Elastic Transcoder
+ Amazon Machine Learning
+ AWS OpsWorks Stacks
+ Amazon S3 Glacier Direct
+ Amazon SimpleDB
+ Amazon WorkSpaces Application Manager \(Amazon WAM\)

## Best practices<a name="tag-best-practices"></a>

As you create a tagging strategy for AWS resources, follow best practices:
+ Do not add personally identifiable information \(PII\) or other confidential or sensitive information in tags\. Tags are accessible to many AWS services, including billing\. Tags are not intended to be used for private or sensitive data\.
+ Use a standardized, case\-sensitive format for tags, and apply it consistently across all resource types\.
+ Consider tag guidelines that support multiple purposes, like managing resource access control, cost tracking, automation, and organization\.
+ Use automated tools to help manage resource tags\. [AWS Resource Groups](https://docs.aws.amazon.com/ARG/latest/userguide/) and the [Resource Groups Tagging API](https://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/) enable programmatic control of tags, making it easier to automatically manage, search, and filter tags and resources\.
+ Use too many tags rather than too few tags\.
+ Remember that it is easy to change tags to accommodate changing business requirements, but consider the consequences of future changes\. For example, changing access control tags means you must also update the policies that reference those tags and control access to your resources\.
+ You can automatically enforce the tagging standards that your organization chooses to adopt by creating and deploying tag policies using AWS Organizations\. Tag policies let you specify tagging rules that define valid key names and the values that are valid for each key\. You can choose to only monitor, giving you an opportunity to evaluate and clean up your existing tags\. Once your tags are in compliance with your chosen standards, you can then turn on enforcement in the tag policies to prevent non\-compliant tags from being created\. For more information, see [Tag policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_tag-policies.html) in the *AWS Organizations User Guide*\.

## Tagging categories<a name="tag-categories"></a>

Companies that are most effective in their use of tags typically create business\-relevant tag groupings to organize their resources along technical, business, and security dimensions\. Companies that use automated processes to manage their infrastructure also include additional, automation\-specific tags\.


| Technical tags | Tags for automation | Business tags | Security tags | 
| --- | --- | --- | --- | 
|  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_tagging.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_tagging.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_tagging.html)  |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_tagging.html)  | 

## Tag naming limits and requirements<a name="tag-conventions"></a>

The following basic naming and usage requirements apply to tags:
+ Each resource can have a maximum of 50 user created tags\. 
+ System created tags that begin with `aws:` are reserved for AWS use, and do not count against this limit\. You can't edit or delete a tag that begins with the `aws:` prefix\.
+ For each resource, each tag key must be unique, and each tag key can have only one value\.
+ The tag key must be a minimum of 1 and a maximum of 128 Unicode characters in UTF\-8\.
+ The tag value must be a minimum of 0 and a maximum of 256 Unicode characters in UTF\-8\.
+ Allowed characters can vary by AWS service\. For information about what characters you can use to tag resources in a particular AWS service, see its documentation\. In general, the allowed characters are letters, numbers, spaces representable in UTF\-8, and the following characters: \_ \. : / = \+ \- @\.
+ Tag keys and values are case sensitive\. As a best practice, decide on a strategy for capitalizing tags, and consistently implement that strategy across all resource types\. For example, decide whether to use `Costcenter`, `costcenter`, or `CostCenter`, and use the same convention for all tags\. Avoid using similar tags with inconsistent case treatment\. 

## Common tagging strategies<a name="tag-strategies"></a>

Use the following tagging strategies to help identify and manage AWS resources\.

**Topics**
+ [Tags for resource organization](#tag-strategies-console)
+ [Tags for cost allocation](#tag-strategies-cost-allocation)
+ [Tags for automation](#tag-strategies-automation)
+ [Tags for access control](#tag-strategies-access-control)

### Tags for resource organization<a name="tag-strategies-console"></a>

Tags are a good way to organize AWS resources in the AWS Management Console\. You can configure tags to be displayed with resources, and can search and filter by tag\. With the AWS Resource Groups service, you can create groups of AWS resources based on one or more tags or portions of tags\. You can also create groups based on their occurrence in an AWS CloudFormation stack\. Using Resource Groups and Tag Editor, you can consolidate and view data for applications that consist of multiple services, resources, and Regions in one place\.

### Tags for cost allocation<a name="tag-strategies-cost-allocation"></a>

AWS Cost Explorer and detailed billing reports let you break down AWS costs by tag\. Typically, you use business tags such as *cost center/business unit*, *customer*, or *project* to associate AWS costs with traditional cost\-allocation dimensions\. But a cost allocation report can include any tag\. This lets you associate costs with technical or security dimensions, such as specific applications, environments, or compliance programs\. The following is an example of a partial cost allocation report\.

![\[Sample tag-based cost allocation report\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/tagging-sample-cost-report.png)

For some services, you can use an AWS\-generated `createdBy` tag for cost allocation purposes, to help account for resources that might otherwise go uncategorized\. The `createdBy` tag is available only for supported AWS services and resources\. Its value contains data associated with specific API or console events\. For more information, see [AWS\-Generated Cost Allocation Tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/aws-tags.html) in the *AWS Billing and Cost Management User Guide*\.

### Tags for automation<a name="tag-strategies-automation"></a>

Resource or service\-specific tags are often used to filter resources during automation activities\. Automation tags are used to opt in or opt out of automated tasks or to identify specific versions of resources to archive, update, or delete\. For example, you can run automated `start` or `stop` scripts that turn off development environments during non\-business hours to reduce costs\. In this scenario, Amazon Elastic Compute Cloud \(Amazon EC2\) instance tags are a simple way to identify instances to opt out of this action\. For scripts that find and delete stale, out\-of\-date, or rolling Amazon EBS snapshots, snapshot tags can add an extra dimension of search criteria\.

### Tags for access control<a name="tag-strategies-access-control"></a>

IAM policies support tag\-based conditions, letting you constrain IAM permissions based on specific tags or tag values\. For example, IAM user or role permissions can include conditions to limit EC2 API calls to specific environments \(such as development, test, or production\) based on their tags\. The same strategy can be used to limit API calls to specific Amazon Virtual Private Cloud \(Amazon VPC\) networks\. Support for tag\-based, resource\-level IAM permissions is service specific\. When you use tag\-based conditions for access control, be sure to define and restrict who can modify the tags\. For more information about using tags to control API access to AWS resources, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

## Tagging governance<a name="tag-strategies-governance"></a>

An effective tagging strategy uses standardized tags and applies them consistently and programmatically across AWS resources\. You can use both reactive and proactive approaches for governing tags in your AWS environment\.
+ **Reactive governance** is for finding resources that are not properly tagged using tools such as the Resource Groups Tagging API, AWS Config Rules, and custom scripts\. To find resources manually, you can use Tag Editor and detailed billing reports\.
+ **Proactive governance** uses tools such as AWS CloudFormation, Service Catalog, tag policies in AWS Organizations, or IAM resource\-level permissions to ensure standardized tags are consistently applied at resource creation\.

  For example, you can use the AWS CloudFormation `Resource Tags` property to apply tags to resource types\. In Service Catalog, you can add portfolio and product tags that are combined and applied to a product automatically when it is launched\. More rigorous forms of proactive governance include automated tasks\. For example, you can use the Resource Groups Tagging API to search an AWS environment’s tags, or run scripts to quarantine or delete improperly tagged resources\.

## Learn more<a name="more-info-tagging"></a>

For more information about tagging resources in a particular AWS service, see its documentation\. The following are also good sources of more information about tagging:
+ For information about the AWS Resource Groups Tagging API, see the [https://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/Welcome.html](https://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/Welcome.html)\.
+ For information about Tag Editor, see [Working with Tag Editor](https://docs.aws.amazon.com/ARG/latest/userguide/tag-editor.html) in the *AWS Resource Groups User Guide*\.
+ For information about identifying, organizing, and tracking your IAM resources with tags, see [Tagging IAM resources](id_tags.md)\.
+ For information about using tags in IAM policies to help control who can view and interact with your AWS resources, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.