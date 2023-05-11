# Amazon S3: Restrict management to a specific S3 bucket<a name="reference_policies_examples_s3_deny-except-bucket"></a>

This example shows how you might create an identity\-based policy that restricts management of an Amazon S3 bucket to that specific bucket\. This policy grants permission to perform all Amazon S3 actions, but deny access to every AWS service except Amazon S3\. See the following example\. According to this policy, you can only access Amazon S3 actions that you can perform on an S3 bucket or S3 object resource\. This policy grants the permissions necessary to complete this action programmatically from the AWS API or AWS CLI\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

If this policy is used in combination with other policies \(such as the [AmazonS3FullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AmazonS3FullAccess) or [AmazonEC2FullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AmazonEC2FullAccess) AWS managed policies\) that allow actions denied by this policy, then access is denied\. This is because an explicit deny statement takes precedence over allow statements\. For more information, see [Determining whether a request is allowed or denied within an account](reference_policies_evaluation-logic.md#policy-eval-denyallow)\.

**Warning**  
[`NotAction`](reference_policies_elements_notaction.md) and [`NotResource`](reference_policies_elements_notresource.md) are advanced policy elements that must be used with care\. This policy denies access to every AWS service except Amazon S3\. If you attach this policy to a user, any other policies that grant permissions to other services are ignored and access is denied\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::bucket-name",
                "arn:aws:s3:::bucket-name/*"
            ]
        },
        {
            "Effect": "Deny",
            "NotAction": "s3:*",
            "NotResource": [
                "arn:aws:s3:::bucket-name",
                "arn:aws:s3:::bucket-name/*"
            ]
        }
    ]
}
```