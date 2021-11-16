# Tagging virtual MFA devices<a name="id_tags_virtual-mfa"></a>

You can use IAM tag key\-value pairs to add custom attributes to a virtual MFA device\. For example, to add cost center information for a user's virtual MFA device, you can add the tag key **CostCenter** and the tag value **1234**\. You can use tags to control access to resources or to control what tags can be attached to an object\. To learn more about using tags to control access, see [Controlling access to and for IAM users and roles using tags](access_iam-tags.md)\.

You can also use tags in AWS STS to add custom attributes when you assume a role or federate a user\. For more information, see [Passing session tags in AWS STS](id_session-tags.md)\.

## Permissions required for tagging virtual MFA devices<a name="id_tags_virtual-mfa_permissions"></a>

You must configure permissions to allow an IAM entity \(user or role\) to tag virtual MFA devices\. You can specify one or all of the following IAM tag actions in an IAM policy:
+ `iam:ListMFADeviceTags`
+ `iam:TagMFADevice`
+ `iam:UntagMFADevice`

**To allow an IAM entity \(user or role\) to add, list, or remove a tag for a virtual MFA device**  
Add the following statement to the permissions policy for the IAM entity that needs to manage tags\. Use your account number and replace *<MFATokenID>* with the name of the virtual MFA device whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListMFADeviceTags",
        "iam:TagMFADevice",
        "iam:UntagMFADevice"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:mfa/<MFATokenID>"
}
```

**To allow an IAM entity \(user or role\) to add a tag to a specific virtual MFA device**  
Add the following statement to the permissions policy for the IAM entity that needs to add, but not remove, tags for a specific MFA device\.

**Note**  
The `iam:TagMFADevice` action requires that you also include the `iam:ListMFADeviceTags` action\.

To use this policy, replace *<MFATokenID>* with the name of the virtual MFA device whose tags need to be managed\. To learn how to create a policy using this example JSON policy document, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListMFADeviceTags",
        "iam:TagMFADevice"
    ],
    "Resource": "arn:aws:iam:*:<account-number>:mfa/<MFATokenID>"
}
```

Alternatively, you can use an AWS managed policy such as [IAMFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/IAMFullAccess) to provide full access to IAM\.

## Managing tags on virtual MFA devices \(AWS CLI or AWS API\)<a name="id_tags_virtual-mfa_procs-cli-api"></a>

You can list, attach, or remove tags for a virtual MFA device\. You can use the AWS CLI or the AWS API to manage tags for a virtual MFA device\.

**To list the tags currently attached to a virtual MFA device \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam list\-mfa\-device\-tags](https://docs.aws.amazon.com/cli/latest/reference/iam/list-mfa-device-tags.html)
+ AWS API: [ListMFADeviceTags](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListMFADeviceTags.html)

**To attach tags to a virtual MFA device \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam tag\-mfa\-device](https://docs.aws.amazon.com/cli/latest/reference/iam/tag-mfa-device.html)
+ AWS API: [TagMFADevice](https://docs.aws.amazon.com/IAM/latest/APIReference/API_TagMFADevice.html)

**To remove tags from a virtual MFA device \(AWS CLI or AWS API\)**
+ AWS CLI: [aws iam untag\-mfa\-device](https://docs.aws.amazon.com/cli/latest/reference/iam/untag-mfa-device.html)
+ AWS API: [UntagMFADevice](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UntagMFADevice.html)

For information about attaching tags to resources for other AWS services, see the documentation for those services\. 

For information about using tags to set more granular permissions with IAM permissions policies, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.