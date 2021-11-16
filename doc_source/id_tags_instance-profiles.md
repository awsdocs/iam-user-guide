# Tagging instance profiles for Amazon EC2 roles<a name="id_tags_instance-profiles"></a>

When you launch an Amazon EC2 instance, you specify an IAM role to associate with the instance\. An instance profile is a container for an IAM role that you can use to pass role information to an Amazon EC2 instance when the instance starts\. You can tag instance profiles when you use the AWS CLI or AWS API\.

You can use IAM tag key\-value pairs to add custom attributes to an instance profile\. For example, to add department information to an instance profile, you can add the tag key **access\-team** and the tag value **eng**\. Doing this gives principals with matching tags access to instance profiles with the same tag\. You could use multiple tag key\-value pairs to specify a team and project: **access\-team = eng **, and **project = peg**\. You can use tags to control a user's access to resources or to control what tags can be attached to a user\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

You can also use tags in AWS STS to add custom attributes when you assume a role or federate a user\. For more information, see [Passing session tags in AWS STS](id_session-tags.md)\.

## Permissions required for tagging instance profiles<a name="id_tags_instance-profiles_permissions"></a>

You must configure permissions to allow an IAM entity \(user or role\) to tag instance profiles\. You can specify one or all of the following IAM tag actions in an IAM policy:
+ `iam:ListInstanceProfileTags`
+ `iam:TagInstanceProfile`
+ `iam:UntagInstanceProfile`

**To allow an IAM entity \(user or role\) to add, list, or remove a tag for an instance profile**  
Add the following statement to the permissions policy for the IAM entity that needs to manage tags\. Use your account number and replace *<InstanceProfileName>* with the name of the instance profile whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListInstanceProfileTags",
        "iam:TagInstanceProfile",
        "iam:UntagInstanceProfile"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:instance-profile/<InstanceProfileName>"
}
```

**To allow an IAM entity \(user or role\) to add a tag to a specific instance profile**  
Add the following statement to the permissions policy for the IAM entity that needs to add, but not remove, tags for a specific instance profile\. 

**Note**  
The `iam:TagInstanceProfile` action requires that you also include the `iam:ListInstanceProfileTags` action\.

To use this policy, replace *<InstanceProfileName>* with the name of the instance profile whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListInstanceProfileTags",
        "iam:TagInstanceProfile"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:instance-profile/<InstanceProfileName>"
}
```

Alternatively, you can use an AWS managed policy such as [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) to provide full access to IAM\.

## Managing tags on instance profiles \(AWS CLI or AWS API\)<a name="id_tags_instance-profile_procs-cli-api"></a>

You can list, attach, or remove tags for instance profiles\. You can use the AWS CLI or the AWS API to manage tags for instance profiles\.

**To list the tags currently attached to an instance profile \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-instance\-profile\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-instance-profile-tags.html)
+ AWS API: [ListInstanceProfileTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListInstanceProfileTags.html)

**To attach tags to an instance profile \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-instance\-profile](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-instance-profile.html)
+ AWS API: [TagInstanceProfile](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagInstanceProfile.html)

**To remove tags from an instance profile \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-instance\-profile](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-instance-profile.html)
+ AWS API: [UntagInstanceProfile](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagInstanceProfile.html)

For information about attaching tags to resources for other AWS services, see the documentation for those services\. 

For information about using tags to set more granular permissions with IAM permissions policies, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.