# Tagging IAM users and roles<a name="id_tags"></a>

You can use IAM tags to add custom attributes to an IAM entity \(user or role\) using a tag key–value pair\. For example, to add location information to a user, you can add the tag key **location** and the tag value **us\_wa\_seattle**\. Or you could use three separate location tag key–value pairs: **loc\-country = us**, **loc\-state = wa**, and **loc\-city = seattle**\. You can use tags to control an entity's access to resources or to control what tags can be attached to an entity\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using IAM resource tags](access_iam-tags.md)\.

You can also use tags in AWS STS to add custom attributes when you assume a role or federate a user\. For more information, see [Passing session tags in AWS STS](id_session-tags.md)\.

## Choose an AWS tag naming convention<a name="id_tags_naming"></a>

When you begin attaching tags to your IAM users and roles, choose your tag naming convention carefully\. Apply the same convention to all of your AWS tags\. This is especially important if you use tags in policies to control access to AWS resources\. If you already use tags in AWS, review your naming convention and adjust it accordingly\. To learn more about tagging categories and strategies, see [AWS Tagging AWS Resources](https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html) in the *AWS General Reference Guide*\. To view tagging use cases and best practices, download the *[Tagging Best Practices](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf)* whitepaper\.

## Rules for tagging in IAM and AWS STS<a name="id_tags_rules"></a>

A number of conventions govern the creation and application of tags in IAM and AWS STS\.

### Naming tags<a name="id_tags_rules_creating"></a>

Observe the following conventions when formulating a tag naming convention for IAM users, IAM roles, AWS STS assume\-role sessions, and AWS STS federated user sessions:
+ Tag keys and values can include any combination of letters, numbers, spaces, and \_ \. : / = \+ \- @ \. symbols\.
+ Tag key–value pairs are not case sensitive, but case is preserved\. This means that you cannot have separate **Department** and **department** tag keys\. If you have tagged a user with the **Department=foo** tag and you add the **department=bar** tag, it replaces the first tag\. A second tag is not added\.
+ You cannot create a tag key or value that begins with the text **aws:**\. This tag prefix is reserved for AWS internal use\.
+ You can create a tag with an empty value such as **phoneNumber = **\. You cannot create an empty tag key\.
+ You cannot specify multiple values in a single tag, but you can create a custom multivalue structure in the single value\. For example, assume that the user Zhang works on the engineering team and the QA team\. If you attach the **team = Engineering** tag and then attach the **team = QA** tag, you change the value of the tag from **Engineering** to **QA**\. Instead, you can include multiple values in a single tag with a custom separator\. In this example, you could attach the **team = Engineering:QA** tag to Zhang\.
**Note**  
To control access to engineers in this example using the **team** tag, you must create a policy that allows for every configuration that might include **Engineering**, including **Engineering:QA**\. To learn more about using tags in policies, see [Controlling access to and for IAM users and roles using IAM resource tags](access_iam-tags.md)\.

### Applying and editing tags<a name="id_tags_rules_applying"></a>

Observe the following conventions when attaching tags to IAM entities \(users or roles\):
+ You can tag users or roles but not groups or policies\.
+ You cannot use Tag Editor to tag IAM entities\. Tag Editor does not support IAM tags\. For information about using Tag Editor with other services, see [Working with Tag Editor](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/tag-editor.html) in the *AWS Management Console User Guide*\.
+ To tag an IAM entity, you must have specific permissions\. To tag or untag roles and users, you must also have permission to list tags\. For more information, see [Permissions required for tagging IAM entities](#id_tags_permissions) following\.
+ The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\.
+ You can apply the same tag to multiple IAM entities\. For example, suppose you have a department named AWS\_Development with 12 members\. You can have 12 users and a role with the tag key of **department** and a value of **awsDevelopment** \(**department = awsDevelopment**\)\. You can also use the same tag on resources in other [services that support tagging](reference_aws-services-that-work-with-iam.md)\.
+ An IAM entity cannot have multiple instances of the same tag key\. For example, if you have a user with the tag key–value pair **costCenter = 1234**, you can then attach the tag key–value pair **costCenter = 5678**\. IAM updates the value of the **costCenter** tag to **5678**\.
+ To edit a tag that is attached to an IAM user or role, attach a tag with a new value to overwrite the existing tag\. For example, assume that you have a user with the tag key–value pair **department = Engineering**\. If you need to move the user to the QA department, then you can attach the **department = QA** tag key–value pair to the user\. This results in the **Engineering** value of the **department** tag key being replaced with the **QA** value\.

## Permissions required for tagging IAM entities<a name="id_tags_permissions"></a>

You must configure permissions to allow an IAM entity \(user or role\) to tag other entities\. You can specify one or all of the following IAM tag actions in an IAM policy:
+ `iam:ListRoleTags`
+ `iam:ListUserTags`
+ `iam:TagRole`
+ `iam:TagUser`
+ `iam:UntagRole`
+ `iam:UntagUser`

**To allow an IAM entity to add, list, or remove a tag for a specific user**

Add the following statement to the permissions policy for the IAM entity that needs to manage tags\. Use your account number and replace *<username>* with the name of the user that needs to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListUserTags",
        "iam:TagUser",
        "iam:UntagUser"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:user/<username>"
}
```

**To allow an IAM user to self\-manage tags**

Add the following statement to the permissions policy for users to allow users to manage their own tags\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListUserTags",
        "iam:TagUser",
        "iam:UntagUser"
    ],
    "Resource": "arn:aws:iam:*:user/${aws:username}"
}
```

**To allow an IAM entity to add a tag to a specific user**

Add the following statement to the permissions policy for the IAM entity that needs to add, but not remove, tags for a specific user\. 

**Note**  
The `iam:AddRoleTags` and `iam:AddUserTags` actions require that you also include the `iam:ListRoleTags` and `iam:ListUserTags` actions\.

To use this policy, replace *<username>* with the name of the user that needs to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListUserTags",
        "iam:TagUser"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:user/<username>"
}
```

**To allow an IAM entity to add, list, or remove a tag for a specific role**

Add the following statement to the permissions policy for the IAM entity that needs to manage tags\. Replace *<rolename>* with the name of the role that needs to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListRoleTags",
        "iam:TagRole",
        "iam:UntagRole"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:role/<rolename>"
}
```

Alternatively, you can use an AWS managed policy such as [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) to provide full access to IAM\.

## Managing tags on IAM entities \(console\)<a name="id_tags_procs-console"></a>

You can manage tags for IAM users or roles from the AWS Management Console\.

**To manage tags on users or roles \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the console, choose **Roles** or **Users** and then choose the name of the entity that you want to edit\.

1. Choose the **Tags** tab and then complete one of the following actions:
   + Choose **Add tags** if the entity does not yet have tags\.
   + Choose **Edit tags** to manage the existing set of tags\.

1. Add or remove tags to complete the set of tags\. Then choose **Save changes**\.

## Managing tags on IAM entities \(AWS CLI or AWS API\)<a name="id_tags_procs-cli-api"></a>

You can list, attach, or remove tags for IAM users and roles\. You can use the AWS CLI or the AWS API to manage tags for IAM users and roles\.

**To list the tags currently attached to an IAM role \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-role\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-role-tags.html)
+ AWS API: [ListRoleTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRoleTags.html)

**To list the tags currently attached to an IAM user \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-user\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-user-tags.html)
+ AWS API: [ListUserTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserTags.html)

**To attach tags to an IAM role \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-role.html)
+ AWS API: [TagRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagRole.html)

**To attach tags to an IAM user \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-user.html)
+ AWS API: [TagUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagUser.html)

**To remove tags from an IAM role \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-role.html)
+ AWS API: [UntagRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagRole.html)

**To remove tags from an IAM user \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-user.html)
+ AWS API: [UntagUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagUser.html)

For information about attaching tags to resources for other AWS services, see the documentation for those services\. 

For information about using tags to set more granular permissions with IAM permissions policies, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.