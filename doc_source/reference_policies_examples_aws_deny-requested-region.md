# AWS: Denies access to AWS based on the requested Region<a name="reference_policies_examples_aws_deny-requested-region"></a>

This example shows how you might create a policy that denies access to any actions outside the Regions specified using `aws:RequestedRegion`, except for actions in the services specified using `NotAction`\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

This policy uses the `NotAction` element with the `Deny` effect, which explicitly denies access to all of the actions *not* listed in the statement\. Actions in the CloudFront, IAM, Route 53, and AWS Support services should not be denied because these are popular AWS global services with a single endpoint that is physically located in the `us-east-1` Region\. Because all requests to these services are made to the `us-east-1` Region, the requests would be denied without the `NotAction` element\. Edit this element to include actions for other AWS global services that you use, such as `budgets`, `globalaccelerator`, `importexport`, `organizations`, or `waf`\. To learn about all of the services that have a single global endpoint, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *AWS General Reference*\. For more information about using the `NotAction` element with the `Deny` effect, see [IAM JSON policy elements: NotAction](reference_policies_elements_notaction.md)\. 

**Important**  
This policy does not allow any actions\. Use this policy in combination with other policies that allow specific actions\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "DenyAllOutsideRequestedRegions",
            "Effect": "Deny",
            "NotAction": [
                "cloudfront:*",
                "iam:*",
                "route53:*",
                "support:*"
            ],
            "Resource": "*",
            "Condition": {
                "StringNotEquals": {
                    "aws:RequestedRegion": [
                        "eu-central-1",
                        "eu-west-1",
                        "eu-west-2",
                        "eu-west-3"
                    ]
                }
            }
        }
    ]
}
```