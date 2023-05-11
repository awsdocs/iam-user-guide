# Tagging server certificates<a name="id_tags_server-certificates"></a>

If you use IAM to manage SSL/TLS certificates, you can tag server certificates in IAM using the AWS CLI or AWS API\. For certificates in a Region supported by AWS Certificate Manager \(ACM\), we recommend that you use ACM instead of IAM to provision, manage, and deploy your server certificates\. In unsupported Regions, you must use IAM as a certificate manager\. To learn which Regions ACM supports, see [AWS Certificate Manager endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/acm.html) in the *AWS General Reference*\.

You can use IAM tag key\-value pairs to add custom attributes to a server certificate\. For example, to add information about the owner or administrator of a server certificate, add the tag key **owner** and the tag value **net\-eng**\. Or you can specify a cost center by adding the tag key **CostCenter** and the tag value **1234**\. You can use tags to control access to resources or to control what tags can be attached to resources\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

You can also use tags in AWS STS to add custom attributes when you assume a role or federate a user\. For more information, see [Passing session tags in AWS STS](id_session-tags.md)\.

## Permissions required for tagging server certificates<a name="id_tags_server-certificates_permissions"></a>

You must configure permissions to allow an IAM entity \(user or role\) to tag server certificates\. You can specify one or all of the following IAM tag actions in an IAM policy:
+ `iam:ListServerCertificateTags`
+ `iam:TagServerCertificate`
+ `iam:UntagServerCertificate`

**To allow an IAM entity \(user or role\) to add, list, or remove a tag for a server certificate**  
Add the following statement to the permissions policy for the IAM entity that needs to manage tags\. Use your account number and replace *<CertificateName>* with the name of the server certificate whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies using the JSON editor](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListServerCertificateTags",
        "iam:TagServerCertificate",
        "iam:UntagServerCertificate"
    ],
    "Resource": "arn:aws:iam::<account-number>:server-certificate/<CertificateName>"
}
```

**To allow an IAM entity \(user or role\) to add a tag to a specific server certificate**  
Add the following statement to the permissions policy for the IAM entity that needs to add, but not remove, tags for a specific server certificate\.

**Note**  
The `iam:TagServerCertificate` action requires that you also include the `iam:ListServerCertificateTags` action\.

To use this policy, replace *<CertificateName>* with the name of the server certificate whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies using the JSON editor](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListServerCertificateTags",
        "iam:TagServerCertificate"
    ],
    "Resource": "arn:aws:iam::<account-number>:server-certificate/<CertificateName>"
}
```

Alternatively, you can use an AWS managed policy such as [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) to provide full access to IAM\.

## Managing tags on server certificates \(AWS CLI or AWS API\)<a name="id_tags_server-certificates_procs-cli-api"></a>

You can list, attach, or remove tags for server certificates\. You can use the AWS CLI or the AWS API to manage tags for server certificates\.

**To list the tags currently attached to a server certificate \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-server\-certificate\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-server-certificate-tags.html)
+ AWS API: [ListServerCertificateTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListServerCertificateTags.html)

**To attach tags to a server certificate\(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-server\-certificate](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-server-certificate.html)
+ AWS API: [TagServerCertificate](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagServerCertificate.html)

**To remove tags from a server certificate \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-server\-certificate](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-server-certificate.html)
+ AWS API: [UntagServerCertificate](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagServerCertificate.html)

For information about attaching tags to resources for other AWS services, see the documentation for those services\. 

For information about using tags to set more granular permissions with IAM permissions policies, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.