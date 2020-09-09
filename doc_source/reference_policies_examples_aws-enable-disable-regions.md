# AWS: Allows enabling and disabling AWS regions<a name="reference_policies_examples_aws-enable-disable-regions"></a>

This example shows how you might create a policy that allows an administrator to enable and disable the Asia Pacific \(Hong Kong\) Region \(ap\-east\-1\)\. This policy also grants the necessary permissions to complete this action on the console\. This setting appears in the **Account settings** page in the AWS Management Console\. This page includes sensitive account\-level information that should be viewed and managed only by account administrators\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

**Important**  
You cannot enable or disable regions that are enabled by default\. You can only include regions that are *disabled* by default\. For more information, see [Managing AWS Regions](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html) in the *AWS General Reference*\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "EnableDisableHongKong",
            "Effect": "Allow",
            "Action": [
                "account:EnableRegion",
                "account:DisableRegion"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {"account:TargetRegion": "ap-east-1"}
            }
        },
        {
            "Sid": "ViewConsole",
            "Effect": "Allow",
            "Action": [
                "aws-portal:ViewAccount",
                "account:ListRegions"
            ],
            "Resource": "*"
        }
    ]
}
```