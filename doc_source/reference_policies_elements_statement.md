# IAM JSON policy elements: Statement<a name="reference_policies_elements_statement"></a>

The `Statement` element is the main element for a policy\. This element is required\. The `Statement` element can contain a single statement or an array of individual statements\. Each individual statement block must be enclosed in curly braces \{ \}\. For multiple statements, the array must be enclosed in square brackets \[ \]\.

```
"Statement": [{...},{...},{...}]
```

The following example shows a policy that contains an array of three statements inside a single `Statement` element\. \(The policy allows you to access your own "home folder" in the Amazon S3 console\.\) The policy includes the `aws:username` variable, which is replaced during policy evaluation with the user name from the request\. For more information, see [Introduction](reference_policies_variables.md#policy-vars-intro)\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets",
        "s3:GetBucketLocation"
      ],
      "Resource": "arn:aws:s3:::*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::BUCKET-NAME",
      "Condition": {"StringLike": {"s3:prefix": [
        "",
        "home/",
        "home/${aws:username}/"
      ]}}
    },
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::BUCKET-NAME/home/${aws:username}",
        "arn:aws:s3:::BUCKET-NAME/home/${aws:username}/*"
      ]
    }
  ]
}
```