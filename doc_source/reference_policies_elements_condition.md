# IAM JSON Policy Elements: Condition<a name="reference_policies_elements_condition"></a>

The `Condition` element \(or `Condition` *block*\) lets you specify conditions for when a policy is in effect\. The `Condition` element is optional\. In the `Condition` element, you build expressions in which you use [condition operators](reference_policies_elements_condition_operators.md) \(equal, less than, etc\.\) to match the condition in the policy against values in the request\. For example, you can use the date or the IP address of the requester in the condition value\. Some services let you specify additional values in conditions; for example, Amazon EC2 lets you write a condition using the `ec2:InstanceType` key, which is unique to that service\.

Condition key *names* are not case\-sensitive\. For example, including the `aws:SourceIP` condition key is equivalent to testing for `AWS:SourceIp`\. Case\-sensitivity of condition key *values* depends on the [condition operator](reference_policies_elements_condition_operators.md) that you use\. For example, the following condition includes the `StringEquals` operator to ensure that only requests made by `johndoe` will match\. Users named `JohnDoe` are denied access\.

```
"Condition" : { "StringEquals" : { "aws:username" : "johndoe" }}
```

The following condition uses the [`StringEqualsIgnoreCase`](reference_policies_elements_condition_operators.md#Conditions_String) operator to match users named `johndoe` or `JohnDoe`\.

```
"Condition" : { "StringEqualsIgnoreCase" : { "aws:username" : "johndoe" }}
```

Some condition keys support key–value pairs that allow you to specify part of the key name\. Examples include the [`aws:RequestTag/tag-key`](reference_policies_condition-keys.md) global condition key, the AWS KMS [https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context), and the `ResourceTag/tag-key` condition key supported by multiple services\. If you use the `ResourceTag/tag-key` condition key for a service such as [Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys), then you must specify a key name for the `tag-key`\. **Key names are not case\-sensitive\.** This means that if you specify `"ec2:ResourceTag:TagKey1": "Value1"` in the condition element of your policy, then the condition matches a resource tag key named either `TagKey1` or `tagkey1`, but not both\. AWS services that support these attributes might allow you to create multiple key names that differ only by case, such as tagging an Amazon EC2 instance with `foo=bar1` and `Foo=bar2`\. When you use a condition such as `"ec2:ResourceTag:Foo": "bar1"` to allow access to that resource, the key name matches both tags, but only one value matches\. This can result in unexpected condition failures\.

**Important**  
As a best practice, make sure that members of your account follow a consistent naming convention when naming key–value pair attributes, such as tags or AWS KMS encryption contexts\. You can enforce this using the [`aws:TagKeys`](reference_policies_condition-keys.md#condition-keys-tagkeys) condition key for tagging, or the [https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context-keys](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context-keys) for the AWS KMS encryption context\.
+ For a list of all of the condition operators and a description of how each one works, see [Condition Operators](reference_policies_elements_condition_operators.md)
+ For a description of how to handle condition keys that have multiple values, see [Creating a Condition That Tests Multiple Key Values \(Set Operations\)](reference_policies_multi-value-conditions.md)
+ For a list of all of the globally available condition keys, see [AWS Global Condition Context Keys](reference_policies_condition-keys.md)\.
+ For conditions keys that are defined by each service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\.

## The Condition Block<a name="AccessPolicyLanguage_ConditionBlock"></a>

The following example shows the basic format of a `Condition` element:

```
"Condition": {
  "DateGreaterThan" : {
     "aws:CurrentTime" : "2013-12-15T12:00:00Z"
   }
}
```

A value from the request is represented by a key, in this case `aws:CurrentTime`\. The key value is compared to a value that you specify either as a literal value \(`2013-08-16T12:00:00Z`\) or as a policy variable, as explained later\. The type of comparison to make is specified by the [condition operator](reference_policies_elements_condition_operators.md) \(here, `DateGreaterThan`\)\. You can create conditions that compare strings, dates, numbers, and so on, using typical Boolean comparisons like equals, greater than, and less than\. 

Under some circumstances, keys can contain multiple values\. For example, a request to Amazon DynamoDB might ask to return or update multiple attributes from a table\. A policy for access to DynamoDB tables can include the `dynamodb:Attributes` key, which contains all the attributes listed in the request\. You can test the multiple attributes in the request against a list of allowed attributes in a policy by using set operators in the `Condition` element\. For more information, see [Creating a Condition That Tests Multiple Key Values \(Set Operations\)](reference_policies_multi-value-conditions.md)\. 

When the policy is evaluated during a request, AWS replaces the key with the corresponding value from the request\. \(In this example, AWS would use the date and time of the request\.\) The condition is evaluated to return true or false, which is then factored into whether the policy as a whole allows or denies the request\. 

### Multiple Values in a Condition<a name="Condition-multiple-conditions"></a>

A `Condition` element can contain multiple conditions, and each condition can contain multiple key\-value pairs\. The following figure illustrates this\. Unless otherwise specified, all keys can have multiple values\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Block.diagram.png)

Let's say you want to let John use a resource only if a numeric value *foo* equals either A or B, and another numeric value *bar* equals C\. You would create a condition block that looks like the following figure\.

![\[Condition block that includes two NumericEquals conditions\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Example1.diagram.png)

Let's say you also want to restrict John's access to after January 1, 2009\. You would add another condition, `DateGreaterThan`, with a date equal to January 1, 2009\. The condition block would then look like the following figure\.

![\[Condition block that includes DateGreaterThan condition\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Example2.diagram.png)

If there are multiple condition operators, or if there are multiple keys attached to a single condition operator, the conditions are evaluated using a logical `AND`\. If a single condition operator includes multiple values for one key, that condition operator is evaluated using a logical `OR`\. All condition operators must be met for an allow or an explicit deny decision\. If any one condition operator isn't met, the result is a deny\.

![\[Condition block showing how AND and OR are applied to multiple values\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Block_AND.diagram.png)

As noted, AWS has predefined condition operators and keys \(like `aws:CurrentTime`\)\. Individual AWS services also define service\-specific keys\.

As an example, let's say you want to let user John access your Amazon SQS queue under the following conditions:
+ The time is after 12:00 noon on 8/16/2013
+ The time is before 3:00 p\.m\. on 8/16/2013
+ The request \(IAM or Amazon SQS\) or message \(Amazon SNS\) comes from an IP address within the range 192\.0\.2\.0 to 192\.0\.2\.255 *or* 203\.0\.113\.0 to 203\.0\.113\.255\.

Your condition block has three separate condition operators, and all three of them must be met for John to have access to your queue, topic, or resource\.

The following shows what the condition block looks like in your policy\. The two values for `aws:SourceIp` are evaluated using OR\. The three separate condition operators are evaluated using AND\.

```
 1. "Condition" :  {
 2.       "DateGreaterThan" : {
 3.          "aws:CurrentTime" : "2013-08-16T12:00:00Z"
 4.        },
 5.       "DateLessThan": {
 6.          "aws:CurrentTime" : "2013-08-16T15:00:00Z"
 7.        },
 8.        "IpAddress" : {
 9.           "aws:SourceIp" : ["192.0.2.0/24", "203.0.113.0/24"]
10.       }
11. }
```

Finally, under some circumstances, individual keys in a policy can contain multiple values\. You can use *condition set operators* to test these multivalued keys against one or more values listed in the policy\. For more information, see [Creating a Condition That Tests Multiple Key Values \(Set Operations\)](reference_policies_multi-value-conditions.md)\. 