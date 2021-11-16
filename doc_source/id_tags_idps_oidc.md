# Tagging OpenID Connect \(OIDC\) identity providers<a name="id_tags_idps_oidc"></a>

You can use IAM tag key\-values to add custom attributes to IAM OpenID Connect \(OIDC\) identity providers\. For example, to identify an OIDC identity provider, you can add the tag key **google** and the tag value **oidc**\. You can use tags to control access to resources or to control what tags can be attached to an object\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

## Permissions required for tagging IAM OIDC identity providers<a name="id_tags_idps_oidc_permissions"></a>

You must configure permissions to allow an IAM entity \(user or role\) to tag IAM OIDC identity providers\. You can specify one or all of the following IAM tag actions in an IAM policy:
+ `iam:ListOpenIDConnectProviderTags`
+ `iam:TagOpenIDConnectProvider`
+ `iam:UntagOpenIDConnectProvider`

**To allow an IAM entity \(user or role\) to add, list, or remove a tag for an IAM OIDC identity provider**  
Add the following statement to the permissions policy for the IAM entity that needs to manage tags\. Use your account number and replace *<OIDCProviderName>* with the name of the OIDC provider whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListOpenIDConnectProviderTags",
        "iam:TagOpenIDConnectProvider",
        "iam:UntagOpenIDConnectProvider"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:oidc-provider/<OIDCProviderName>"
}
```

**To allow an IAM entity \(user or role\) to add a tag to a specific IAM OIDC identity provider**  
Add the following statement to the permissions policy for the IAM entity that needs to add, but not remove, tags for a specific identity provider\.

**Note**  
The `iam:TagOpenIDConnectProvider` action requires that you also include the `iam:ListOpenIDConnectProviderTags` action\.

To use this policy, replace *<OIDCProviderName>* with the name of the OIDC provider whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListOpenIDConnectProviderTags",
        "iam:TagOpenIDConnectProvider"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:oidc-provider/<OIDCProviderName>"
}
```

Alternatively, you can use an AWS managed policy such as [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) to provide full access to IAM\.

## Managing tags on IAM OIDC identity providers \(console\)<a name="id_tags_idps_oidc_procs-console"></a>

You can manage tags for IAM OIDC identity providers from the AWS Management Console\.

**Note**  
You can manage tags using the new Identity providers console experience only\.

**To manage tags on OIDC identity providers \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the console, choose **Identity providers** and then choose the name of the identity provider that you want to edit\.

1. In the **Tags** section, choose **Manage tags** and then complete one of the following actions:
   + Choose **Add tag** if the OIDC identity provider does not yet have tags or to add a new tag\.
   + Edit existing tag keys and values\.
   + Choose **Remove tag** to remove a tag\.

1. Then choose **Save changes**\.

## Managing tags on IAM OIDC identity providers \(AWS CLI or AWS API\)<a name="id_tags_idps_oidc_procs-cli-api"></a>

You can list, attach, or remove tags for IAM OIDC identity providers\. You can use the AWS CLI or the AWS API to manage tags for IAM OIDC identity providers\.

**To list the tags currently attached to an IAM OIDC identity provider \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-open\-id\-connect\-provider\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-open-id-connect-provider-tags.html)
+ AWS API: [ListOpenIDConnectProviderTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListOpenIDConnectProviderTags.html)

**To attach tags to an IAM OIDC identity provider \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-open\-id\-connect\-provider](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-open-id-connect-provider.html)
+ AWS API: [TagOpenIDConnectProvider](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagOpenIDConnectProvider.html)

**To remove tags from an IAM OIDC identity provider \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-open\-id\-connect\-provider](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-open-id-connect-provider.html)
+ AWS API: [UntagOpenIDConnectProvider](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagOpenIDConnectProvider.html)

For information about attaching tags to resources for other AWS services, see the documentation for those services\. 

For information about using tags to set more granular permissions with IAM permissions policies, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.