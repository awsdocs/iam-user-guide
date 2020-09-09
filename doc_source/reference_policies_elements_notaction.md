# IAM JSON policy elements: NotAction<a name="reference_policies_elements_notaction"></a>

`NotAction` is an advanced policy element that explicitly matches everything *except* the specified list of actions\. Using `NotAction` can result in a shorter policy by listing only a few actions that should not match, rather than including a long list of actions that will match\. When using `NotAction`, you should keep in mind that actions specified in this element are the *only* actions in that are limited\. This, in turn, means that all of the applicable actions or services that are not listed are allowed if you use the `Allow` effect\. In addition, such unlisted actions or services are denied if you use the `Deny` effect\. When you use `NotAction` with the `Resource` element, you provide scope for the policy\. This is how AWS determines which actions or services are applicable\. For more information, see the following example policy\. 

**NotAction with Allow** 

You can use the `NotAction` element in a statement with `"Effect": "Allow"` to provide access to all of the actions in an AWS service, except for the actions specified in `NotAction`\. You can use it with the `Resource` element to provide scope for the policy, limiting the allowed actions to the actions that can be performed on the specified resource\.

The following example allows users to access all of the Amazon S3 actions that can be performed on any S3 resource *except* for deleting a bucket\. This does not allow users to use the `ListAllMyBuckets` S3 API operation, because that action requires the "\*" resource\. This policy also does not allow actions in other services, because other service actions are not applicable to the S3 resources\.

```
"Effect": "Allow",
"NotAction": "s3:DeleteBucket",
"Resource": "arn:aws:s3:::*",
```

Sometimes, you might want to allow access to a large number of actions\. By using the `NotAction` element you effectively reverse the statement, resulting in a shorter list of actions\. For example, because AWS has so many services, you might want to create a policy that allows the user to do everything except access IAM actions\.

The following example allows users to access every action in every AWS service except for IAM\.

```
"Effect": "Allow",
"NotAction": "iam:*",
"Resource": "*"
```

Be careful using the `NotAction` element and `"Effect": "Allow"` in the same statement or in a different statement within a policy\. `NotAction` matches all services and actions that are not explicitly listed or applicable to the specified resource, and could result in granting users more permissions than you intended\.

**NotAction with Deny**

You can use the `NotAction` element in a statement with `"Effect": "Deny"` to deny access to all of the listed resources except for the actions specified in the `NotAction` element\. This combination does not allow the listed items, but instead explicitly denies the actions not listed\. You must still allow actions that you want to allow\.

The following conditional example denies access to non\-IAM actions if the user is not signed in using MFA\. If the user is signed in with MFA, then the `"Condition"` test fails and the final `"Deny"` statement has no effect\. Note, however, that this would not grant the user access to any actions; it would only explicitly deny all other actions except IAM actions\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Sid": "DenyAllUsersNotUsingMFA",
        "Effect": "Deny",
        "NotAction": "iam:*",
        "Resource": "*",
        "Condition": {"BoolIfExists": {"aws:MultiFactorAuthPresent": "false"}}
    }]
}
```

For an example policy that denies access to actions outside of specific Regions, except for actions from specific services, see [AWS: Denies access to AWS based on the requested Region](reference_policies_examples_aws_deny-requested-region.md)\.