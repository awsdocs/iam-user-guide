# Tagging IAM users<a name="id_tags_users"></a>

You can use IAM tag key\-value pairs to add custom attributes to an IAM user\. For example, to add location information to a user, you can add the tag key **location** and the tag value **us\_wa\_seattle**\. Or you could use three separate location tag key\-value pairs: **loc\-country = us**, **loc\-state = wa**, and **loc\-city = seattle**\. You can use tags to control a user's access to resources or to control what tags can be attached to a user\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

You can also use tags in AWS STS to add custom attributes when you assume a role or federate a user\. For more information, see [Passing session tags in AWS STS](id_session-tags.md)\.

## Permissions required for tagging IAM users<a name="id_tags_users_permissions"></a>

You must configure permissions to allow an IAM user to tag other users\. You can specify one or all of the following IAM tag actions in an IAM policy:
+ `iam:ListUserTags`
+ `iam:TagUser`
+ `iam:UntagUser`

**To allow an IAM user to add, list, or remove a tag for a specific user**  
Add the following statement to the permissions policy for the IAM user that needs to manage tags\. Use your account number and replace *<username>* with the name of the user whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListUserTags",
        "iam:TagUser",
        "iam:UntagUser"
    ],
    "Resource": "arn:aws:iam::<account-number>:user/<username>"
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
    "Resource": "arn:aws:iam::user/${aws:username}"
}
```

**To allow an IAM user to add a tag to a specific user**  
Add the following statement to the permissions policy for the IAM user that needs to add, but not remove, tags for a specific user\.

**Note**  
The `iam:TagUser` action requires that you also include the `iam:ListUserTags` action\.

To use this policy, replace *<username>* with the name of the user whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListUserTags",
        "iam:TagUser"
    ],
    "Resource": "arn:aws:iam::<account-number>:user/<username>"
}
```

Alternatively, you can use an AWS managed policy such as [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) to provide full access to IAM\.

## Managing tags on IAM users \(console\)<a name="id_tags_users_procs-console"></a>

You can manage tags for IAM users from the AWS Management Console\.

**To manage tags on users \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the console, choose **Users** and then choose the name of the user that you want to edit\.

1. Choose the **Tags** tab and then complete one of the following actions:
   + Choose **Add tags** if the user does not yet have tags\.
   + Choose **Edit tags** to manage the existing set of tags\.

1. Add or remove tags to complete the set of tags\. Then choose **Save changes**\.

## Managing tags on IAM users \(AWS CLI or AWS API\)<a name="id_tags_users_procs-cli-api"></a>

You can list, attach, or remove tags for IAM users\. You can use the AWS CLI or the AWS API to manage tags for IAM users\.

**To list the tags currently attached to an IAM user \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-user\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-user-tags.html)
+ AWS API: [ListUserTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListUserTags.html)

**To attach tags to an IAM user \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-user.html)
+ AWS API: [TagUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagUser.html)

**To remove tags from an IAM user \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-user](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-user.html)
+ AWS API: [UntagUser](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagUser.html)

For information about attaching tags to resources for other AWS services, see the documentation for those services\. 

For information about using tags to set more granular permissions with IAM permissions policies, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.