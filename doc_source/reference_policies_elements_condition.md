# IAM JSON policy elements: Condition<a name="reference_policies_elements_condition"></a>

The `Condition` element \(or `Condition` *block*\) lets you specify conditions for when a policy is in effect\. The `Condition` element is optional\. In the `Condition` element, you build expressions in which you use [condition operators](reference_policies_elements_condition_operators.md) \(equal, less than, etc\.\) to match the condition keys and values in the policy against keys and values in the request context\. To learn more about the request context, see [Request](intro-structure.md#intro-structure-request)\.

```
"Condition" : { "{condition-operator}" : { "{condition-key}" : "{condition-value}" }}
```

The condition key that you specify can be a [global condition key](reference_policies_condition-keys.md) or a service\-specific condition key\. Global condition keys have the `aws:` prefix\. Service\-specific condition keys have the service's prefix\. For example, Amazon EC2 lets you write a condition using the `ec2:InstanceType` key, which is unique to that service\. To view service\-specific IAM condition keys with the `iam:` prefix, see [IAM and AWS STS condition context keys](reference_policies_iam-condition-keys.md)\.

Condition key *names* are not case\-sensitive\. For example, including the `aws:SourceIP` condition key is equivalent to testing for `AWS:SourceIp`\. Case\-sensitivity of condition key *values* depends on the [condition operator](reference_policies_elements_condition_operators.md) that you use\. For example, the following condition includes the `StringEquals` operator to ensure that only requests made by `johndoe` will match\. Users named `JohnDoe` are denied access\.

```
"Condition" : { "StringEquals" : { "aws:username" : "johndoe" }}
```

The following condition uses the [`StringEqualsIgnoreCase`](reference_policies_elements_condition_operators.md#Conditions_String) operator to match users named `johndoe` or `JohnDoe`\.

```
"Condition" : { "StringEqualsIgnoreCase" : { "aws:username" : "johndoe" }}
```

Some condition keys support key–value pairs that allow you to specify part of the key name\. Examples include the [`aws:RequestTag/tag-key`](reference_policies_condition-keys.md) global condition key, the AWS KMS [https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context), and the `ResourceTag/tag-key` condition key supported by multiple services\. If you use the `ResourceTag/tag-key` condition key for a service such as [Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys), then you must specify a key name for the `tag-key`\. **Key names are not case\-sensitive\.** This means that if you specify `"ec2:ResourceTag:TagKey1": "Value1"` in the condition element of your policy, then the condition matches a resource tag key named either `TagKey1` or `tagkey1`, but not both\. AWS services that support these attributes might allow you to create multiple key names that differ only by case\. An example is tagging an Amazon EC2 instance with `foo=bar1` and `Foo=bar2`\. When you use a condition such as `"ec2:ResourceTag:Foo": "bar1"` to allow access to that resource, the key name matches both tags, but only one value matches\. This can result in unexpected condition failures\.

**Important**  
As a best practice, make sure that members of your account follow a consistent naming convention when naming key–value pair attributes\. Examples include tags or AWS KMS encryption contexts\. You can enforce this using the [`aws:TagKeys`](reference_policies_condition-keys.md#condition-keys-tagkeys) condition key for tagging, or the [https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context-keys](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context-keys) for the AWS KMS encryption context\.
+ For a list of all of the condition operators and a description of how each one works, see [Condition Operators](reference_policies_elements_condition_operators.md)
+ Unless otherwise specified, all keys can have multiple values\. For a description of how to handle condition keys that have multiple values, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)
+ For a list of all of the globally available condition keys, see [AWS global condition context keys](reference_policies_condition-keys.md)\.
+ For conditions keys that are defined by each service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

## The request context<a name="AccessPolicyLanguage_RequestContext"></a>

When a [principal](intro-structure.md#intro-structure-principal) makes a [request](intro-structure.md#intro-structure-request) to AWS, AWS gathers the request information into a request context\. The information is used to evaluate and authorize the request\. You can use the `Condition` element of a JSON policy to test specific conditions against the request context\. For example, you can create a policy that uses the [aws:CurrentTime](reference_policies_condition-keys.md#condition-keys-currenttime) condition key to [allow a user to perform actions within only a specific range of dates](reference_policies_examples_aws-dates.md)\.

When a request is submitted, AWS evaluates each condition key in the policy returns a value of *true*, *false*, *not present*, and occasionally *null* \(an empty data string\)\. A key that is not present in the request is not considered a mismatch\. For example, the following policy allows removing your own multifactor authentication \(MFA\) device, but only if you have signed in using MFA in the last hour \(3,600 seconds\)\. 

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Sid": "AllowRemoveMfaOnlyIfRecentMfa",
        "Effect": "Allow",
        "Action": [
            "iam:DeactivateMFADevice",
            "iam:DeleteVirtualMFADevice"
        ],
        "Resource": "arn:aws:iam::*:user/${aws:username}",
        "Condition": {
            "NumericLessThanEquals": {"aws:MultiFactorAuthAge": "3600"}
        }
    }
}
```

The request context can return the following values:
+ **True** – If the requester signed in using MFA in the last one hour or less, then the condition returns *true*\. 
+ **False** – If the requester signed in using MFA more than one hour ago, then the condition returns *false*\. 
+ **Not present** – If the requester made a request using their IAM user access keys in the AWS CLI or AWS API, the key is not present\. In this case, the key is not present, and it won't match\. 
+ **Null** – For condition keys that are defined by the user, such as passing tags in a request, it is possible to include an empty string\. In this case, the value in the request context is *null*\. A null value might return true in some cases\. For example, if you use the multivalued `ForAllValues` condition operator with the `aws:TagKeys` condition key, you can experience unexpected results if the request context returns *null*\. For more information, see [aws:TagKeys](reference_policies_condition-keys.md#condition-keys-tagkeys) and [Using multiple keys and values](reference_policies_multi-value-conditions.md#reference_policies_multi-key-or-value-conditions)\.

## The condition block<a name="AccessPolicyLanguage_ConditionBlock"></a>

The following example shows the basic format of a `Condition` element:

```
"Condition": {"StringLike": {"s3:prefix": ["$janedoe/*"]}}
```

A value from the request is represented by a condition key, in this case `s3:prefix`\. The context key value is compared to a value that you specify as a literal value, such as `janedoe/*`\. The type of comparison to make is specified by the [condition operator](reference_policies_elements_condition_operators.md) \(here, `StringLike`\)\. You can create conditions that compare strings, dates, numbers, and more using typical Boolean comparisons such as equals, greater than, and less than\. When you use [string operators](reference_policies_elements_condition_operators.md#Conditions_String) or [ARN operators](reference_policies_elements_condition_operators.md#Conditions_ARN), you can also use a [policy variable](reference_policies_variables.md) in the condition value\. The following example includes the `aws:username` variable\. 

```
"Condition": {"StringLike": {"s3:prefix": ["${aws:username}/*"]}}
```

Under some circumstances, keys can contain multiple values\. For example, a request to Amazon DynamoDB might ask to return or update multiple attributes from a table\. A policy for access to DynamoDB tables can include the `dynamodb:Attributes` key, which contains all the attributes listed in the request\. You can test the multiple attributes in the request against a list of allowed attributes in a policy by using set operators in the `Condition` element\. For more information, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)\. 

When the policy is evaluated during a request, AWS replaces the key with the corresponding value from the request\. \(In this example, AWS would use the date and time of the request\.\) The condition is evaluated to return true or false, which is then factored into whether the policy as a whole allows or denies the request\. 

### Multiple values in a condition<a name="Condition-multiple-conditions"></a>

A `Condition` element can contain multiple conditions, and each condition can contain multiple key\-value pairs\. The following figure illustrates this\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Block.diagram.png)

For more information, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)\. 