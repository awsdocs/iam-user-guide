# Tagging IAM roles<a name="id_tags_roles"></a>

You can use IAM tag key\-value pairs to add custom attributes to an IAM role\. For example, to add location information to a role, you can add the tag key **location** and the tag value **us\_wa\_seattle**\. Or you could use three separate location tag key\-value pairs: **loc\-country = us**, **loc\-state = wa**, and **loc\-city = seattle**\. You can use tags to control a role's access to resources or to control what tags can be attached to a role\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

You can also use tags in AWS STS to add custom attributes when you assume a role or federate a user\. For more information, see [Passing session tags in AWS STS](id_session-tags.md)\.

## Permissions required for tagging IAM roles<a name="id_tags_roles_permissions"></a>

You must configure permissions to allow an IAM role to tag other entities \(users or roles\)\. You can specify one or all of the following IAM tag actions in an IAM policy:
+ `iam:ListRoleTags`
+ `iam:TagRole`
+ `iam:UntagRole`
+ `iam:ListUserTags`
+ `iam:TagUser`
+ `iam:UntagUser`

**To allow an IAM role to add, list, or remove a tag for a specific user**  
Add the following statement to the permissions policy for the IAM role that needs to manage tags\. Use your account number and replace *<username>* with the name of the user whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

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

**To allow an IAM role to add a tag to a specific user**  
Add the following statement to the permissions policy for the IAM role that needs to add, but not remove, tags for a specific user\.

**Note**  
The `iam:TagRole` action requires that you also include the `iam:ListRoleTags` action\.

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

**To allow an IAM role to add, list, or remove a tag for a specific role**  
Add the following statement to the permissions policy for the IAM role that needs to manage tags\. Replace *<rolename>* with the name of the role whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListRoleTags",
        "iam:TagRole",
        "iam:UntagRole"
    ],
    "Resource": "arn:aws:iam::<account-number>:role/<rolename>"
}
```

Alternatively, you can use an AWS managed policy such as [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) to provide full access to IAM\.

## Managing tags on IAM roles \(console\)<a name="id_tags_roles_procs-console"></a>

You can manage tags for IAM roles from the AWS Management Console\.

**To manage tags on roles \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the console, choose **Roles** and then choose the name of the role that you want to edit\.

1. Choose the **Tags** tab and then complete one of the following actions:
   + Choose **Add new tag** if the role does not yet have tags\.
   + Choose **Manage tags** to manage the existing set of tags\.

1. Add or remove tags to complete the set of tags\. Then, choose **Save changes**\.

## Managing tags on IAM roles \(AWS CLI or AWS API\)<a name="id_tags_roles_procs-cli-api"></a>

You can list, attach, or remove tags for IAM roles\. You can use the AWS CLI or the AWS API to manage tags for IAM roles\.

**To list the tags currently attached to an IAM role \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-role\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-role-tags.html)
+ AWS API: [ListRoleTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRoleTags.html)

**To attach tags to an IAM role \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-role.html)
+ AWS API: [TagRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagRole.html)

**To remove tags from an IAM role \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-role.html)
+ AWS API: [UntagRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagRole.html)

For information about attaching tags to resources for other AWS services, see the documentation for those services\. 

For information about using tags to set more granular permissions with IAM permissions policies, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.