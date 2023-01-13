# AWS: Deny access to Amazon S3 resources outside your account except AWS Data Exchange<a name="reference_policies_examples_resource_account_data_exch"></a>

This example shows how you might create an identity\-based policy that denies access to all resources in AWS that don't belong to your account, except for the resources that AWS Data Exchange requires for normal operation\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

You can create a similar policy to restrict access to resources within an organization or an organizational unit, while accounting for AWS Data Exchange owned resources by using the condition keys `aws:ResourceOrgPaths` and `aws:ResourceOrgID`\.

If you use AWS Data Exchange in your environment, the service creates and interacts with resources such as Amazon S3 buckets owned by the service account\. For example, AWS Data Exchange sends requests to Amazon S3 buckets owned by the AWS Data Exchange service on behalf of the IAM principal \(user or role\) invoking the AWS Data Exchange APIs\. In that case, using `aws:ResourceAccount`, `aws:ResourceOrgPaths`, or `aws:ResourceOrgID` in a policy, without accounting for AWS Data Exchange owned resources, denies access to the buckets owned by the service account\.
+ The statement, `DenyAllAwsResourcesOutsideAccountExceptS3`, uses the `NotAction` element with the [Deny](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_effect.html) effect which explicitly denies access to every action not listed in the statement that also do not belong to the listed account\. The `NotAction` element indicates the exceptions to this statement\. These actions are the exception to this statement because if the actions are performed on resources created by AWS Data Exchange, the policy denies them\.
+ The statement, `DenyAllS3ResoucesOutsideAccountExceptDataExchange`, uses a combination of the `ResourceAccount` and `CalledVia` conditions to deny access to the three Amazon S3 actions excluded in the previous statement\. The statement denies the actions if resources do not belong in the listed account and if the calling service is not AWS Data Exchange\. The statement does not deny the actions if either the resource belongs to the listed account or the listed service principal, `dataexchange.amazonaws.com`, performs the operations\.

**Important**  
This policy does not allow any actions\. It uses the `Deny` effect which explicitly denies access to all of the resources listed in the statement that do not belong to the listed account\. Use this policy in combination with other policies that allow access to specific resources\.

The following example shows how you can configure the policy to allow access to the required Amazon S3 buckets\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyAllAwsReourcesOutsideAccountExceptAmazonS3",
      "Effect": "Deny",
      "NotAction": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:PutObjectAcl"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "111122223333"
          ]
        }
      }
    },
    {
      "Sid": "DenyAllS3ResourcesOutsideAccountExceptDataExchange",
      "Effect": "Deny",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:PutObjectAcl"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "111122223333"
          ]
        },
        "ForAllValues:StringNotEquals": {
          "aws:CalledVia": [
            "dataexchange.amazonaws.com"
          ]
        }
      }
    }
  ]
}
```