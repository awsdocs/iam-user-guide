# Tagging IAM resources<a name="id_tags"></a>

A *tag* is a custom attribute label that you can assign to an AWS resource\. Each tag has two parts:
+ A *tag key* \(for example, `CostCenter`, `Environment`, `Project`, or `Purpose`\)\. Tag keys are case sensitive\.
+ An optional field known as a *tag value* \(for example, `111122223333`, `Production`, or a team name\)\. Omitting the tag value is the same as using an empty string\. Like tag keys, tag values are case sensitive\.

Together these are known as key\-value pairs\. For limits on the number of tags you can have on IAM resources, see [IAM and AWS STS quotas, name requirements, and character limits](reference_iam-quotas.md)\.

Tags help you identify and organize your AWS resources\. Many AWS services support tagging, so you can assign the same tag to resources from different services to indicate that the resources are related\. For example, you can assign the same tag to an IAM role that you assign to an Amazon S3 bucket\. For more information about tagging strategies, see [Tagging AWS resources](reference_tagging.md)\.

In addition to identifying, organizing, and tracking your IAM resources with tags, you can use tags in IAM policies to help control who can view and interact with your resources\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

You can also use tags in AWS STS to add custom attributes when you assume a role or federate a user\. For more information, see [Passing session tags in AWS STS](id_session-tags.md)\.

## Choose an AWS tag naming convention<a name="id_tags_naming"></a>

When you begin attaching tags to your IAM resources, choose your tag naming convention carefully\. Apply the same convention to all of your AWS tags\. This is especially important if you use tags in policies to control access to AWS resources\. If you already use tags in AWS, review your naming convention and adjust it accordingly\.

**Note**  
If your account is a member of AWS Organizations, see [Tag policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_tag-policies.html) in the Organizations user guide to learn more about using tags in Organizations\.

### Best practices for tag naming<a name="id_tags_naming_best_practices"></a>

These are some best practices and naming conventions for tags\.

Names for AWS tags are case sensitive so ensure that they are used consistently\. For example, the tags `CostCenter` and `costcenter` are different, so one might be configured as a cost allocation tag for financial analysis and reporting and the other one might not be\. Similarly, the `Name` tag appears in the AWS Console for many resources, but the `name` tag does not\. 

A number of tags are predefined by AWS or created automatically by various AWS services\. Many AWS\-defined tags names use all lowercase, with hyphens separating words in the name, and prefixes to identify the source service for the tag\. For example: 
+ `aws:ec2spot:fleet-request-id` identifies the Amazon EC2 Spot Instance Request that launched the instance\.
+ `aws:cloudformation:stack-name` identifies the AWS CloudFormation stack that created the resource\. 
+ `elasticbeanstalk:environment-name` identifies the application that created the resource\.

Consider naming your tags using all lowercase, with hyphens separating words, and a prefix identifying the organization name or abbreviated name\. For example, for a fictitious company named *AnyCompany*, you might define tags such as:
+ `anycompany:cost-center` to identify the internal Cost Center code 
+ `anycompany:environment-type` to identify whether the environment is development, test, or production
+ `anycompany:application-id` to identify the application the resource was created for 

The prefix ensures that tags are clearly identified as having been defined by your organization and not by AWS or a third\-party tool that you may be using\. Using all lowercase with hyphens for separators avoids confusion about how to capitalize a tag name\. For example, `anycompany:project-id` is simpler to remember than `ANYCOMPANY:ProjectID`, `anycompany:projectID`, or `Anycompany:ProjectId`\.

## Rules for tagging in IAM and AWS STS<a name="id_tags_rules"></a>

A number of conventions govern the creation and application of tags in IAM and AWS STS\.

### Naming tags<a name="id_tags_rules_creating"></a>

Observe the following conventions when formulating a tag naming convention for IAM resources, AWS STS assume\-role sessions, and AWS STS federated user sessions:

**Character requirements** – Tag keys and values can include any combination of letters, numbers, spaces, and \_ \. : / = \+ \- @ symbols\.

**Case sensitivity** – Case sensitivity for tag keys differs depending on the type of IAM resource that is tagged\. Tag key values for IAM users and roles are not case sensitive, but case is preserved\. This means that you cannot have separate **Department** and **department** tag keys\. If you have tagged a user with the **Department=finance** tag and you add the **department=hr** tag, it replaces the first tag\. A second tag is not added\.

For other IAM resource types, tag key values are case sensitive\. That means you can have separate **Costcenter** and **costcenter** tag keys\. For example, if you have tagged a customer managed policy with the **Costcenter = 1234** tag and you add the **costcenter = 5678** tag, the policy will have both the **Costcenter** and **costcenter** tag keys\.

As a best practice, we recommend that you avoid using similar tags with inconsistent case treatment\. We recommend that you decide on a strategy for capitalizing tags, and consistently implement that strategy across all resource types\. To learn more about best practices for tagging, see [Tagging AWS Resources](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html) in the AWS General Reference\.

The following lists show the differences in case sensitivity for tag keys that are attached to IAM resources\.

Tag key values are **not** case sensitive:
+ IAM roles
+ IAM users

Tag key values are case sensitive:
+ Customer managed policies
+ Instance profiles
+ OpenID Connect identity providers
+ SAML identity providers
+ Server certificates
+ Virtual MFA devices

Additionally, the following rules apply:
+ You cannot create a tag key or value that begins with the text **aws:**\. This tag prefix is reserved for AWS internal use\.
+ You can create a tag with an empty value such as **phoneNumber = **\. You cannot create an empty tag key\.
+ You cannot specify multiple values in a single tag, but you can create a custom multivalue structure in the single value\. For example, assume that the user Zhang works on the engineering team and the QA team\. If you attach the **team = Engineering** tag and then attach the **team = QA** tag, you change the value of the tag from **Engineering** to **QA**\. Instead, you can include multiple values in a single tag with a custom separator\. In this example, you could attach the **team = Engineering:QA** tag to Zhang\.
**Note**  
To control access to engineers in this example using the **team** tag, you must create a policy that allows for every configuration that might include **Engineering**, including **Engineering:QA**\. To learn more about using tags in policies, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

### Applying and editing tags<a name="id_tags_rules_applying"></a>

Observe the following conventions when attaching tags to IAM resources:
+ You can tag most IAM resources, but not groups, assumed roles, access reports, or hardware\-based MFA devices\.
+ You cannot use Tag Editor to tag IAM resources\. Tag Editor does not support IAM tags\. For information about using Tag Editor with other services, see [Working with Tag Editor](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/tag-editor.html) in the *AWS Resource Groups User Guide*\.
+ To tag an IAM resource, you must have specific permissions\. To tag or untag resources, you must also have permission to list tags\. For more information, see the list of topics for each IAM resource at the end of this page\. 
+ The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and AWS STS quotas, name requirements, and character limits](reference_iam-quotas.md)\.
+ You can apply the same tag to multiple IAM resources\. For example, suppose you have a department named `AWS_Development` with 12 members\. You can have 12 users and a role with the tag key of **department** and a value of **awsDevelopment** \(**department = awsDevelopment**\)\. You can also use the same tag on resources in other [services that support tagging](reference_aws-services-that-work-with-iam.md)\.
+ IAM entities \(users or roles\) cannot have multiple instances of the same tag key\. For example, if you have a user with the tag key\-value pair **costCenter = 1234**, you can then attach the tag key\-value pair **costCenter = 5678**\. IAM updates the value of the **costCenter** tag to **5678**\.
+ To edit a tag that is attached to an IAM entity \(user or role\), attach a tag with a new value to overwrite the existing tag\. For example, assume that you have a user with the tag key\-value pair **department = Engineering**\. If you need to move the user to the QA department, then you can attach the **department = QA** tag key\-value pair to the user\. This results in the **Engineering** value of the **department** tag key being replaced with the **QA** value\.

**Topics**
+ [Choose an AWS tag naming convention](#id_tags_naming)
+ [Rules for tagging in IAM and AWS STS](#id_tags_rules)
+ [Tagging IAM users](id_tags_users.md)
+ [Tagging IAM roles](id_tags_roles.md)
+ [Tagging customer managed policies](id_tags_customer-managed-policies.md)
+ [Tagging IAM identity providers](id_tags_idps.md)
+ [Tagging instance profiles for Amazon EC2 roles](id_tags_instance-profiles.md)
+ [Tagging server certificates](id_tags_server-certificates.md)
+ [Tagging virtual MFA devices](id_tags_virtual-mfa.md)
+ [Passing session tags in AWS STS](id_session-tags.md)