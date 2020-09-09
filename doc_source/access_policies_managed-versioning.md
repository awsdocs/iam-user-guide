# Versioning IAM policies<a name="access_policies_managed-versioning"></a>

When you make changes to an IAM customer managed policy, and when AWS makes changes to an AWS managed policy, the changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new *version* of the managed policy\. IAM stores up to five versions of your customer managed policies\. IAM does not support versioning for inline policies\. 

The following diagram illustrates versioning for a customer managed policy\. 

![\[Changes to managed policies become new versions of the policy\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[Changes to managed policies become new versions of the policy\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

A policy version is different from a `Version` policy element\. The `Version` policy element is used within a policy and defines the version of the policy language\. To learn more about the `Version` policy element see [IAM JSON policy elements: Version](reference_policies_elements_version.md)\.

You can use versions to track changes to a managed policy\. For example, you might make a change to a managed policy and then discover that the change had unintended effects\. In this case, you can roll back to a previous version of the managed policy by setting the previous version as the *default* version\. 

The following sections explain how you can use versioning for managed policies\.

**Topics**
+ [Permissions for setting the default version of a policy](#policy-version-permissions)
+ [Setting the default version of customer managed policies](#default-version)
+ [Using versions to roll back changes](#versions-roll-back)
+ [Version limits](#version-limits)

## Permissions for setting the default version of a policy<a name="policy-version-permissions"></a>

The permissions that are required to set the default version of a policy correspond to the AWS API operations for the task\. You can use the `CreatePolicyVersion` or `SetDefaultPolicyVersion` API operations to set the default version of a policy\. To allow someone to set the default policy version of an existing policy, you can allow access to either the `iam:CreatePolicyVersion` action or the `iam:SetDefaultPolicyVersion` action\. The `iam:CreatePolicyVersion` action allows them to create a new version of the policy and to set that version as the default\. The `iam:SetDefaultPolicyVersion` action allows them to set any existing version of the policy as the default\.

**Important**  
Denying the `iam:SetDefaultPolicyVersion` action in a user's policy does not stop the user from creating a new policy version and setting it as the default\.

You can use the following policy to deny a user access to change an existing customer managed policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": [
                "iam:CreatePolicyVersion",
                "iam:SetDefaultPolicyVersion"
            ],
            "Resource": "arn:aws:iam::*:policy/POLICY-NAME"
        }
    ]
}
```

## Setting the default version of customer managed policies<a name="default-version"></a>

One of the versions of a managed policy is set as the *default* version\. The policy's default version is the operative version—that is, it's the version that is in effect for all of the principal entities \(users, groups, and roles\) that the managed policy is attached to\. 

When you create a customer managed policy, the policy begins with a single version identified as v1\. For managed policies with only a single version, that version is automatically set as the default\. For customer managed policies with more than one version, you choose which version to set as the default\. For AWS managed policies, the default version is set by AWS\. The following diagrams illustrate this concept\. 

![\[Managed policy with a single version, which is the default version\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-managed-policies-versions-default-one.diagram.png)

![\[Customer managed policy with three versions, where version v2 is the default version.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-managed-policies-versions-default-multiple.diagram.png)

### <a name="set-default-version-managed-policy-console"></a>

You can set the default version of a customer managed policy to apply that version to every IAM identity \(user, group, and role\) where the policy is attached\. You cannot set the default version for an AWS managed policy or an inline policy\.

**To set the default version of a customer managed policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. In the list of policies, choose the policy name of the policy to set the default version of\. You can use the **Filter** menu and the search box to filter the list of policies\.

1. Choose the **Policy versions** tab\. Select the check box next to the version that you want to set as the default version, and then choose **Set as default**\.

To learn how to set the default version of a customer managed policy from the AWS Command Line Interface or the AWS API, see [Editing customer managed policies \(AWS CLI\)](access_policies_manage-edit.md#edit-policies-cli-api)\. 

## Using versions to roll back changes<a name="versions-roll-back"></a>

You can set the default version of a customer managed policy to roll back your changes\. For example, consider the following scenario:

You create a customer managed policy that allows users to administer a particular Amazon S3 bucket using the AWS Management Console\. Upon creation, your customer managed policy has only one version, identified as v1, so that version is automatically set as the default\. The policy works as intended\. 

Later, you update the policy to add permission to administer a second Amazon S3 bucket\. IAM creates a new version of the policy, identified as v2, that contains your changes\. You set version v2 as the default, and a short time later your users report that they lack permission to use the Amazon S3 console\. In this case, you can roll back to version v1 of the policy, which you know works as intended\. To do this, you set version v1 as the default version\. Your users are now able to use the Amazon S3 console to administer the original bucket\. 

Later, after you determine the error in version v2 of the policy, you update the policy again to add permission to administer the second Amazon S3 bucket\. IAM creates another new version of the policy, identified as v3\. You set version v3 as the default, and this version works as intended\. At this point, you delete version v2 of the policy\.

## Version limits<a name="version-limits"></a>

A managed policy can have up to five versions\. If you need to make changes to a managed policy beyond five versions from the AWS Command Line Interface, or the AWS API, you must first delete one or more existing versions\. If you use the AWS Management Console, you do not have to delete a version before editing your policy\. When you save a sixth version, a dialog box appears that prompts you to delete one or more nondefault versions of your policy\. You can view the JSON policy document for each version to help you decide\. For details about this dialog box, see [Editing IAM policies](access_policies_manage-edit.md)\.

You can delete any version of the managed policy that you want, except for the default version\. When you delete a version, the version identifiers for the remaining versions do not change\. As a result, version identifiers might not be sequential\. For example, if you delete versions v2 and v4 of a managed policy and add two new versions, the remaining version identifiers might be v1, v3, v5, v6, and v7\. 