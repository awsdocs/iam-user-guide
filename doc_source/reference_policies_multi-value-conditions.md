# Creating a condition with multiple keys or values<a name="reference_policies_multi-value-conditions"></a>

You can use the `Condition` element of a policy to test multiple keys or multiple values for a single key in a request\. When you make a request to AWS, either programmatically or through the AWS Management Console, your request includes information about your principal, operation, tags, and more\. To learn about information and data included in a request, see [Request](intro-structure.md#intro-structure-request)\. You can use condition keys to test the values of the matching keys in the request\. For example, you can use a condition key to control access to specific attributes of a DynamoDB table or to an Amazon EC2 instance based on tags\.

A `Condition` element can contain multiple conditions, and each condition can contain multiple key\-value pairs\. Most condition keys support using multiple values\. The following figure illustrates this\. Unless otherwise specified, all keys can have multiple values\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Block.diagram.png)

**Topics**
+ [Evaluation logic for conditions with multiple keys or values](#reference_policies_multiple-conditions-eval)
+ [Using multiple keys and values](#reference_policies_multi-key-or-value-conditions)
+ [Examples of using multiple values with condition set operators](#reference_policies_multi-value-conditions-examples)
+ [Evaluation logic for multiple values with condition set operators](#reference_policies_multi-value-conditions-eval)

## Evaluation logic for conditions with multiple keys or values<a name="reference_policies_multiple-conditions-eval"></a>

If your policy has multiple condition operators or multiple keys attached to a single condition operator, the conditions are evaluated using a logical `AND`\. If a single condition operator includes multiple values for one key, that condition operator is evaluated using a logical `OR`\. All conditions must resolve to true to trigger the desired `Allow` or `Deny` effect\.

![\[Condition block showing how AND and OR are applied to multiple values\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Block_AND.diagram.png)

## Using multiple keys and values<a name="reference_policies_multi-key-or-value-conditions"></a>

For requests that include multiple values for a single key, you must enclose the conditions within brackets like an array \("Key2":\["Value2A", "Value2B"\]\)\. You must also use the `ForAllValues` or `ForAnyValue` set operators with the `StringLike` [condition operator](reference_policies_elements_condition_operators.md#Conditions_String)\. These qualifiers add set\-operation functionality to the condition operator so that you can test multiple request values against multiple condition values\.
+ `ForAllValues` – Tests whether the value of every member of the request set is a subset of the condition key set\. The condition returns true if every key value in the request matches at least one value in the policy\. It also returns true if there are no keys in the request, or if the key values resolve to a null data set, such as an empty string\.
+ `ForAnyValue` – Tests whether at least one member of the set of request values matches at least one member of the set of condition key values\. The condition returns true if any one of the key values in the request matches any one of the condition values in the policy\. For no matching key or a null dataset, the condition returns false\.

Assume that you want to let John use a resource only if a numeric value *foo* equals either A or B, and another numeric value *bar* equals C\. You would create a condition block that looks like the following figure\.

![\[Condition block that includes two NumericEquals conditions\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Example1.diagram.png)

Assume that you also want to restrict John's access to after January 1, 2019\. You would add another condition, `DateGreaterThan`, with a date equal to January 1, 2019\. The condition block would then look like the following figure\.

![\[Condition block that includes DateGreaterThan condition\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Example2.diagram.png)

AWS has predefined condition operators and keys \(like `aws:CurrentTime`\)\. Individual AWS services also define service\-specific keys\.

As an example, assume that you want to let user John access your Amazon SQS queue under the following conditions:
+ The time is after 12:00 p\.m\. on 7/16/2019
+ The time is before 3:00 p\.m\. on 7/16/2019
+ The request comes from an IP address within the range 192\.0\.2\.0 to 192\.0\.2\.255 *or* 203\.0\.113\.0 to 203\.0\.113\.255\.

Your condition block has three separate condition operators, and all three of them must be met for John to have access to your queue, topic, or resource\.

The following shows what the condition block looks like in your policy\. The two values for `aws:SourceIp` are evaluated using `OR`\. The three separate condition operators are evaluated using `AND`\.

```
 1. "Condition" :  {
 2.       "DateGreaterThan" : {
 3.          "aws:CurrentTime" : "2019-07-16T12:00:00Z"
 4.        },
 5.       "DateLessThan": {
 6.          "aws:CurrentTime" : "2019-07-16T15:00:00Z"
 7.        },
 8.        "IpAddress" : {
 9.           "aws:SourceIp" : ["192.0.2.0/24", "203.0.113.0/24"]
10.       }
11. }
```

## Examples of using multiple values with condition set operators<a name="reference_policies_multi-value-conditions-examples"></a>

You can create a policy to test multiple values in a request against one or more values that you specify in the policy\. Assume that you have an Amazon DynamoDB table named `Thread` that is used to store information about threads in a technical support forum\. The table has attributes named `ID`, `UserName`, `PostDateTime`, `Message`, and `Tags`\. 

```
{	
  ID=101
  UserName=Bob
  PostDateTime=20130930T231548Z
  Message="A good resource for this question is docs.aws.amazon.com"
  Tags=["AWS", "Database", "Security"]
}
```

For information about how set operators are used in DynamoDB to implement fine\-grained access to individual data items and attributes, see [Fine\-Grained Access Control for DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/FGAC_DDB.html) in the *Amazon DynamoDB Developer Guide*\. 

You can create a policy that allows users to see only the `PostDateTime`, `Message`, and `Tags` attributes\. If the user's request contains any of these attributes, it is allowed\. But if the request contains any other attributes \(for example, `ID`\), the request is denied\. Logically speaking, you want to create a list of allowed attributes \(`PostDateTime`, `Message`, `Tags`\)\. You also want to indicate in the policy that all of the user's requested attributes must be in that list of allowed attributes\.

The following example policy shows how to use the `ForAllValues` qualifier with the `StringEquals` condition operator\. The condition allows a user to request *only* the attributes `ID`, `Message`, or `Tags` from the DynamoDB table named `Thread`\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "dynamodb:GetItem",
            "Resource": "arn:aws:dynamodb:*:*:table/Thread",
            "Condition": {
                "ForAllValues:StringEquals": {
                    "dynamodb:Attributes": [
                        "ID",
                        "Message",
                        "Tags"
                    ]
                }
            }
        }
    ]
}
```

Assume the user makes a request to DynamoDB to get the attributes `Message` and `Tags` from the `Thread` table\. In that case, the request is allowed because the user's requested attributes all match values specified in the policy\. The `GetItem` operation requires the user to pass the `ID` attribute as the database table key, which is also allowed in the policy\. However, if the user's request includes the `UserName` attribute, the request fails\. The reason is that `UserName` is not within the list of allowed attributes and the `ForAllValues` qualifier requires all requested values to be listed in the policy\.

**Important**  
If you use `dynamodb:Attributes`, you must specify the names of all of the primary key and index key attributes for the table\. You must also specify any secondary indexes that are listed in the policy\. Otherwise, DynamoDB can't use these key attributes to perform the requested action\.

Alternatively, you might want to make sure that users are explicitly forbidden to include some attributes in a request, such as the `ID` and `UserName` attributes\. For example, you might exclude attributes when the user is updating the DynamoDB table, because an update \(`PUT` operation\) should not change certain attributes\. In that case, you create a list of forbidden attributes \(`ID`, `UserName`\)\. If any of the user's requested attributes match any of the forbidden attributes, the request is denied\. 

The following example shows how to use the `ForAnyValue` qualifier to deny access to the `ID` and `PostDateTime` attributes if the user tries to perform the `PutItem` action\. That is, if the user tries to update either of those attributes in the `Thread` table\. Notice that the `Effect` element is set to `Deny`\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Deny",
        "Action": "dynamodb:PutItem",
        "Resource": "arn:aws:dynamodb:*:*:table/Thread",
        "Condition": {
            "ForAnyValue:StringEquals": {
                "dynamodb:Attributes": [
                    "ID",
                    "PostDateTime"
                ]
            }
        }
    }
}
```

Assume that the user makes a request to update the `PostDateTime` and `Message` attributes of the `Thread` table\. The `ForAnyValue` qualifier determines whether any of the requested attributes appear in the list in the policy\. In this case, there is one match \(`PostDateTime`\), so the condition is true\. Assuming the other values in the request also match \(for example, the resource\), the overall policy evaluation returns true\. Because the policy's effect is `Deny`, the request is denied\. 

Imagine the user instead makes a request to perform `PutItem` with just the `UserName` attribute\. None of the attributes in the request \(just `UserName`\) match any of attributes listed in the policy \(`ID`, `PostDateTime`\)\. The condition returns false, so the effect of the policy \(`Deny`\) is also false, and the request is not denied by this policy\. \(For the request to succeed, it must be explicitly allowed by a different policy\. It is not explicitly denied by this policy, but all requests are implicitly denied\.\)

**Warning**  
When you use the `ForAllValues` condition operator, it returns true if there are no keys in the request, or if the key values resolve to a null data set, such as an empty string\. To require that the request includes at least one value, you must use another condition in the policy\. For an example, see [Controlling access during AWS requests](access_tags.md#access_tags_control-requests)\.

## Evaluation logic for multiple values with condition set operators<a name="reference_policies_multi-value-conditions-eval"></a>

This section discusses the specifics of the evaluation logic used with the `ForAllValues` and `ForAnyValue` operators\. The following table illustrates possible keys that might be included in a request \(`PostDateTime` and `UserName`\) and a policy condition that includes the values `PostDateTime`, `Message`, and `Tags`\. 


****  

|  Key \(in the request\)  |  Condition value \(in the policy\)  | 
| --- | --- | 
|  `PostDateTime`  |  `PostDateTime`  | 
|  `UserName`  |  `Message`  | 
|     |  `Tags`  | 

The evaluation for the combination is this:


****  

|  | 
| --- |
|  `PostDateTime` matches `PostDateTime`?  | 
|  `PostDateTime` matches `Message`?  | 
|  `PostDateTime` matches `Tags`?  | 
|  `UserName` matches `PostDateTime`?  | 
|  `UserName` matches `Message`?  | 
|  `UserName` matches `Tags`?  | 

The result of the condition operator depends on which modifier is used with the policy condition:
+ `ForAllValues`\. If every key in the request \(`PostDateTime` or `UserName`\) matches at least one condition value in the policy \(`PostDateTime`, `Message`, `Tags`\), the condition operator returns true\. Stated another way, in order for the condition to be true, \(`PostDateTime` must equal `PostDateTime`, `Message`, or `Tags`\) *and* \(`UserName` must equal `PostDateTime`, `Message`, or `Tags`\)\. 
+ `ForAnyValue`\. If any combination of request value and policy value \(any one of the six in the example\) returns true, the condition operator returns true\. 

The following policy includes a `ForAllValues` qualifier: 

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": "dynamodb:GetItem",
        "Resource": "arn:aws:dynamodb:*:*:table/Thread",
        "Condition": {
            "ForAllValues:StringEquals": {
                "dynamodb:Attributes": [
                    "PostDateTime",
                    "Message",
                    "Tags"
                ]
            }
        }
    }
}
```

Suppose that the user makes a request to DynamoDB to get the attributes `PostDateTime` and `UserName`\. The evaluation for the combination is this:


****  

|  |  | 
| --- |--- |
|  `PostDateTime` matches `PostDateTime`?  |  `True`  | 
|  `PostDateTime` matches `Message`?  |  `False`  | 
|  `PostDateTime` matches `Tags`?  |  `False`  | 
|  `UserName` matches `PostDateTime`?  |  `False`  | 
|  `UserName` matches `Message`?  |  `False`  | 
|  `UserName` matches `Tags`?  |  `False`  | 

The policy includes the `ForAllValues` condition operator modifier, meaning that there must be at least one match for `PostDateTime` and one match for `UserName`\. There's no match for `UserName`, so the condition operator returns false, and the policy does not allow the request\. 

The following policy includes a `ForAnyValue` qualifier: 

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Deny",
        "Action": "dynamodb:PutItem",
        "Resource": "arn:aws:dynamodb:*:*:table/Thread",
        "Condition": {
            "ForAnyValue:StringEquals": {
                "dynamodb:Attributes": [
                    "ID",
                    "PostDateTime"
                ]
            }
        }
    }
}
```

Notice that the policy includes `"Effect":"Deny"` and the action is `PutItem`\. Imagine that the user makes a `PutItem` request that includes the attributes `UserName`, `Message`, and `PostDateTime`\. The evaluation is this: 


****  

|  |  | 
| --- |--- |
|  `UserName` matches `ID`?  |  `False`  | 
|  `UserName` matches `PostDateTime`?  |  `False`  | 
|  `Messages` matches `ID`?  |  `False`  | 
|  `Message` matches `PostDateTime`?  |  `False`  | 
|  `PostDateTime` matches `ID`?  |  `False`  | 
|  `PostDateTime` matches `PostDateTime`?  |  `True`  | 

With the modifier `ForAnyValue`, if any one of these tests returns true, the condition returns true\. The last test returns true, so the condition is true; because the `Effect` element is set to `Deny`, the request is denied\. 

**Note**  
If the key values in the request resolve to an empty data set \(for example, an empty string\), a condition operator modified by `ForAllValues` returns true\. In addition, a condition operator modified by `ForAnyValue` returns false\. 