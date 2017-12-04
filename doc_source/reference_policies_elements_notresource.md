# IAM JSON Policy Elements: NotResource<a name="reference_policies_elements_notresource"></a>

`NotResource` is an advanced policy element that explicitly matches everything except the specified list of resources\. Using `NotResource` can result in a shorter policy by listing only a few resources that should not match, rather than including a long list of resources that will match\. When using `NotResource`, you should keep in mind that resources specified in this element are the *only* resources that are limited\. This, in turn, means that all of the resources, including the resources in all other services, that are not listed are allowed if you use the `Allow` effect, or are denied if you use the `Deny` effect\. Statements must include either a `Resource` or a `NotResource` element that specifies a resource using an ARN\. \(For more information about the format of ARNs, see [Amazon Resource Names \(ARNs\) and AWS Service Namespaces](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html)\.\) 

Be careful using the `NotResource` element and `"Effect": "Allow"` in the same statement or in a different statement within a policy\. `NotResource` allows all services and resources that are not explicitly listed, and could result in granting users more permissions than you intended\. Using the `NotResource` element and `"Effect": "Deny"` in the same statement denies services and resources that are not explicitly listed\.

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