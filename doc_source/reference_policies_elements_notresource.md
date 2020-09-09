# IAM JSON policy elements: NotResource<a name="reference_policies_elements_notresource"></a>

`NotResource` is an advanced policy element that explicitly matches every resource except those specified\. Using `NotResource` can result in a shorter policy by listing only a few resources that should not match, rather than including a long list of resources that will match\. This is particularly useful for policies that apply within a single AWS service\. 

For example, imagine you have a group named `HRPayroll`\. Members of `HRPayroll` should not be allowed to access any Amazon S3 resources except the `Payroll` folder in the `HRBucket` bucket\. The following policy explicitly denies access to all Amazon S3 resources other than the listed resources\. Note, however, that this policy does not grant the user access to any resources\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Deny",
    "Action": "s3:*",
    "NotResource": [
      "arn:aws:s3:::HRBucket/Payroll",
      "arn:aws:s3:::HRBucket/Payroll/*"
    ]
  }
}
```

Normally, to explicitly deny access to a resource you would write a policy that uses `"Effect":"Deny"` and that includes a `Resource` element that lists each folder individually\. However, in that case, each time you add a folder to `HRBucket`, or add a resource to Amazon S3 that should not be accessed, you must add its name to the list in `Resource`\. If you use a `NotResource` element instead, users are automatically denied access to new folders unless you add the folder names to the `NotResource` element\. 

When using `NotResource`, you should keep in mind that resources specified in this element are the *only* resources that are not limited\. This, in turn, limits all of the resources that would apply to the action\. In the example above, the policy affects only Amazon S3 actions, and therefore only Amazon S3 resources\. If the action also included Amazon EC2 actions, then the policy would not deny access to any EC2 resources\. Additionally, this policy does not deny access to S3 actions that can't be performed on a specific resource, such as `s3:ListAllMyBuckets`\. To learn which actions in a service allow specifying the ARN of a resource, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

## NotResource with other elements<a name="notresource-element-combinations"></a>

You should **never** use the `"Effect": "Allow"`, `"Action": "*"`, and `"NotResource": "arn:aws:s3:::HRBucket"` elements together\. This statement is very dangerous, because it allows all actions in AWS on all resources except the `HRBucket` S3 bucket\. This would even allow the user to add a policy to themselves that allows them to access `HRBucket`\. Do not do this\. 

Be careful using the `NotResource` element and `"Effect": "Allow"` in the same statement or in a different statement within a policy\. `NotResource` allows all services and resources that are not explicitly listed, and could result in granting users more permissions than you intended\. Using the `NotResource` element and `"Effect": "Deny"` in the same statement denies services and resources that are not explicitly listed\.