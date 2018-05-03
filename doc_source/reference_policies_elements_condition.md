# IAM JSON Policy Elements: Condition<a name="reference_policies_elements_condition"></a>

The `Condition` element \(or `Condition` *block*\) lets you specify conditions for when a policy is in effect\. The `Condition` element is optional\. In the `Condition` element, you build expressions in which you use [condition operators](reference_policies_elements_condition_operators.md) \(equal, less than, etc\.\) to match the condition in the policy against values in the request\. Condition values can include date, time, the IP address of the requester, the ARN of the request source, the user name, user ID, and the user agent of the requester\. Some services let you specify additional values in conditions; for example, Amazon S3 lets you write a condition using the `s3:VersionId` key, which is unique to that service\.
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

A value from the request is represented by a key, in this case `aws:CurrentTime`\. The key value is compared to a value that you specify either as a literal value \(`2013-08-16T12:00:00Z`\) or as a policy variable, as explained later\. The type of comparison to make is specified by the [condition operator](reference_policies_elements_condition_operators.md) \(here, `DateGreaterThan`\)\. You can create conditions that compare strings, dates, numbers, and so on, using typical boolean comparisons like equals, greater than, and less than\. 

Under some circumstances, keys can contains multiple values\. For example, a request to DynamoDB might ask to return or update multiple attributes from a table\. A policy for access to DynamoDB tables can include the `dynamodb:Attributes` key, which contains all the attributes listed in the request\. You can test the multiple attributes in the request against a list of allowed attributes in a policy by using set operators in the `Condition` element\. For more information, see [Creating a Condition That Tests Multiple Key Values \(Set Operations\)](reference_policies_multi-value-conditions.md)\. 

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
+ The request \(IAM or SQS\) or message \(SNS\) comes from an IP address within the range 192\.0\.2\.0 to 192\.0\.2\.255 *or* 203\.0\.113\.0 to 203\.0\.113\.255\.

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

Finally, under some circumstances, individual keys in a policy can contain multiple values, and you can use *condition set operators* to test these multi\-valued keys against one or more values listed in the policy\. For more information, see [Creating a Condition That Tests Multiple Key Values \(Set Operations\)](reference_policies_multi-value-conditions.md)\. 