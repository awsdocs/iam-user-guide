# Tagging IAM SAML identity providers<a name="id_tags_idps_saml"></a>

You can use IAM tag key\-value pairs to add custom attributes to SAML identity providers\. For example, to identify a provider, you can add the tag key **okta** and the tag value **saml**\. You can use tags to control access to resources or to control what tags can be attached to an object\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

## Permissions required for tagging SAML identity providers<a name="id_tags_idps_saml_permissions"></a>

You must configure permissions to allow an IAM entity \(users or roles\) to tag SAML 2\.0–based Identity Providers \(IdPs\)\. You can specify one or all of the following IAM tag actions in an IAM policy:
+ `iam:ListSAMLProviderTags`
+ `iam:TagSAMLProvider`
+ `iam:UntagSAMLProvider`

**To allow an IAM entity \(user or role\) to add, list, or remove a tag for a SAML identity provider**  
Add the following statement to the permissions policy for the IAM entity that needs to manage tags\. Use your account number and replace *<SAMLProviderName>* with the name of the SAML provider whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies using the JSON editor](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListSAMLProviderTags",
        "iam:TagSAMLProvider",
        "iam:UntagSAMLProvider"
    ],
    "Resource": "arn:aws:iam::<account-number>:saml-provider/<SAMLProviderName>"
}
```

**To allow an IAM entity \(user or role\) to add a tag to a specific SAML identity provider**  
Add the following statement to the permissions policy for the IAM entity that needs to add, but not remove, tags for a specific SAML provider\.

**Note**  
The `iam:TagSAMLProvider` action requires that you also include the `iam:ListSAMLProviderTags` action\.

To use this policy, replace *<SAMLProviderName>* with the name of the SAML provider whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies using the JSON editor](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListSAMLProviderTags",
        "iam:TagSAMLProvider"
    ],
    "Resource": "arn:aws:iam::<account-number>:saml-provider/<SAMLProviderName>"
}
```

Alternatively, you can use an AWS managed policy such as [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) to provide full access to IAM\.

## Managing tags on IAM SAML identity providers \(console\)<a name="id_tags_idps_saml_procs-console"></a>

You can manage tags for IAM SAML Identity Providers from the AWS Management Console\.

**Note**  
You can manage tags using the new Identity providers console experience only\.

**To manage tags on SAML identity providers \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the console, choose **Identity providers** and then choose the name of the SAML identity provider that you want to edit\.

1. In the **Tags** section, choose **Manage tags** and then complete one of the following actions:
   + Choose **Add tag** if the SAML identity provider does not yet have tags or to add a new tag\.
   + Edit existing tag keys and values\.
   + Choose **Remove tag** to remove a tag\.

1. Add or remove tags to complete the set of tags\. Then choose **Save changes**\.

## Managing tags on IAM SAML identity providers \(AWS CLI or AWS API\)<a name="id_tags_idps_saml_procs-cli-api"></a>

You can list, attach, or remove tags for IAM SAML identity providers\. You can use the AWS CLI or the AWS API to manage tags for IAM SAML identity providers\.

**To list the tags currently attached to an SAML identity provider \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-saml\-provider\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-saml-provider-tags.html)
+ AWS API: [ListSAMLProviderTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListSAMLProviderTags.html)

**To attach tags to a SAML identity provider \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-saml\-provider](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-saml-provider.html)
+ AWS API: [TagSAMLProvider](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagSAMLProvider.html)

**To remove tags from a SAML identity provider \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-saml\-provider](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-saml-provider.html)
+ AWS API: [UntagSAMLProvider](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagSAMLProvider.html)

For information about attaching tags to resources for other AWS services, see the documentation for those services\. 

For information about using tags to set more granular permissions with IAM permissions policies, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.