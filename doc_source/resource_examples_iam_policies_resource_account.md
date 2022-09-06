# AWS: Deny access to resources outside your account except AWS managed IAM policies<a name="resource_examples_iam_policies_resource_account"></a>

Using `aws:ResourceAccount` in your identity\-based policies can impact the user or the role's ability to utilize some services that require interaction with resources in accounts owned by a service\.

You can create a policy with an exception to allow for AWS managed IAM policies\. A service\-managed account outside of your AWS Organizations owns Managed IAM Policies\. There are four IAM actions that list and retrieve AWS\-managed policies\. Use these actions in the [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_notaction.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_notaction.html) element of the statement\. `AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService1` in the policy\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowAccessToResourcesInSpecificAccountsAndSpecificService1",
      "Effect": "Deny",
      "NotAction": [
        "iam:GetPolicy",
        "iam:GetPolicyVersion",
        "iam:ListEntitiesForPolicy",
        "iam:ListPolicies"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "111122223333"
          ]
        }
      }
    }
  ]
}
```