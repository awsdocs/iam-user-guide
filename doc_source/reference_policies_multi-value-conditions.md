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

If your policy has multiple [condition operators](reference_policies_elements_condition_operators.md) or multiple keys attached to a single condition operator, the conditions are evaluated using a logical `AND`\. If a single condition operator includes multiple values for one key, that condition operator is evaluated using a logical `OR`\. All conditions must resolve to true to invoke the desired `Allow` or `Deny` effect\.

![\[Condition block showing how AND and OR are applied to multiple values\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Condition_Block_AND.diagram.png)

For example, the following condition block shows how the figure above presents in a policy\. The condition block uses condition operators `StringEqualsIgnoreCase` and `StringEquals`, and condition keys `aws:PrincipalTag` and `aws:PrincipalAccount`\. To invoke the desired `Allow` or `Deny` effect, all conditions must resolve to true\. The user making the request must have both principal tag keys, *department* and *role*, that include one of the tag key values specified in the policy\. Also, the user making the request must belong to the AWS account identifier specified in the policy\.

```
"Condition": {
  "StringEqualsIgnoreCase": {
    "aws:PrincipalTag/department": [ "finance", "hr", "legal" ],
    "aws:PrincipalTag/role": [ "audit", "security" ]
  },
  "StringEquals": {
    "aws:PrincipalAccount": "123456789012"
  }
}
```

**Note**  
When multiple values are listed in a policy for negated matching condition operators such as `StringNotEquals` and `DateNotEquals`, the effective permissions work like a logical `AND`\. For example, if there are multiple `aws:PrincipalAccount` values in a `StringNotEquals` condition operator, the string cannot match any of the `aws:PrincipalAccount` values listed to resolve the condition to true\.

## Using multiple keys and values<a name="reference_policies_multi-key-or-value-conditions"></a>

To compare your condition against a [request context](intro-structure.md#intro-structure-request) with multiple key values, you must use the `ForAllValues` or `ForAnyValue` set operators\. These set operators are used to compare two sets of values\.

When a policy condition compares two sets of values, such as the set of tags in a request and the set of tags in a policy condition, you need to tell AWS how to compare the sets\. IAM defines two set operators, `ForAnyValue` and `ForAllValues`\. You must use set operators with *multivalued* condition keys\. Do not use set operators with *single\-valued* condition keys\.

To determine whether an AWS condition key is single\-valued or multivalued, review its data type\. To view the condition key data types for a service, see [Actions, Resources, and Condition Keys for AWS Services](https://docs.aws.amazon.com/service-authorization/latest/reference/reference_policies_actions-resources-contextkeys.html) and choose the service whose condition keys you want to view\. If the condition **Type** field includes the `ArrayOf` prefix, the condition key is multivalued\. For example, [AWS Key Management Service](https://docs.aws.amazon.com/service-authorization/latest/reference/list_awskeymanagementservice.html) supports condition keys with the `String` single\-valued data type and the `ArrayOfString` multivalued data type\.
+ *Single\-valued* condition keys have at most one value in the request context\. For example, you can tag resources in AWS\. Resource tags are stored as tag key\-value pairs\. A resource tag key can have a single tag value\. Therefore, [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag) is a single\-valued condition key\. Do not use a set operator with a single\-valued condition key\.
+ *Multivalued* condition keys can have multiple values in the request context\. For example, you can tag resources in AWS and include multiple tag key\-value pairs in a request\. Therefore, [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys) is a multivalued condition key\. Multivalued condition keys require a set operator\.

The `ForAllValues` and `ForAnyValue` qualifiers add set\-operation functionality to the condition operator so that you can test multiple request values against multiple condition values\. Additionally, if you include a multivalued string key in your policy with a wildcard or a variable, you must also use the `StringLike` [condition operator](reference_policies_elements_condition_operators.md#Conditions_String)\. For requests that include multiple values for a single key, you must enclose the condition key values within brackets like an [array](reference_policies_grammar.md#policies-grammar-json)\. For example, `"Key2":["Value2A", "Value2B"]`\.
+ `ForAllValues` – Use with multivalued condition keys\. Tests whether the value of every member of the request set is a subset of the condition key set\. The condition returns true if every key value in the request matches at least one value in the policy\. It also returns true if there are no keys in the request, or if the key values resolve to a null data set, such as an empty string\. Do not use `ForAllValues` with an `Allow` effect because it can be overly permissive\.
+ `ForAnyValue` – Use with multivalued condition keys\. Tests whether at least one member of the set of request values matches at least one member of the set of condition key values\. The condition returns true if any one of the key values in the request matches any one of the condition values in the policy\. For no matching key or a null dataset, the condition returns false\.
**Note**  
The difference between single\-valued and multivalued condition keys depends on the number of values in the request context, not the number of values in the policy condition\.

## Examples of using multiple values with condition set operators<a name="reference_policies_multi-value-conditions-examples"></a>

You can create a policy to test multiple values in a request against one or more values that you specify in the policy\. Assume that you have an Amazon DynamoDB table named `Thread` that is used to store information about threads in a technical support forum\. The table has a partition key attribute named `ID` and each item has the following attributes: `UserName`, `PostDateTime`, `Message`, and `Tags`\.  Here's how an item in such a table would look like:

```
{	
    "ID": { "S": "101" },
    "UserName": { "S": "Bob" },
    "PostDateTime": { "S": "2023-03-17T21:20:00Z" },
    "Message": { "S": "A good resource for this question is docs.aws.amazon.com" },
    "Tags": { "SS": ["AWS", "Database", "Security"] }
}
```

You can create a policy that allows the [GetItem](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_GetItem.html) operation to obtain only the `PostDateTime`, `Message`, and `Tags` attributes\. If the user's request contains any of these attributes, it is allowed\. But if the request contains any other attributes \(for example, `UserName`\) or implicitly requests all attributes by omitting the [ProjectionExpression](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_GetItem.html#DDB-GetItem-request-ProjectionExpression) parameter, the request is denied\. The following example policy shows how to use the `ForAllValues` qualifier with the `StringEquals` condition operator to achieve this:

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
                        "PostDateTime",
                        "Message",
                        "Tags"
                    ]
                },
                "StringEquals": {
                    "dynamodb:Select": "SPECIFIC_ATTRIBUTES"
                }
            }
        }
    ]
}
```

Assume the user invokes the `GetItem` operation with the following input:

```
{
    "Key": {
        "ID": { "S": "101" }
    },
    "ProjectionExpression": "Message, Tags"
}
```

The relevant request context key values would be:

```
{
    "dynamodb:Attributes": ["ID", "Message", "Tags"],
    "dynamodb:Select": "SPECIFIC_ATTRIBUTES"
}
```

In this case, the request is allowed because the user's requested attributes all match values specified in the policy\. The `GetItem` operation requires the user to pass the `ID` attribute as the item's primary key, which is also allowed in the policy\. However, if the user's request includes the `UserName` attribute, the request would be denied\. The reason is that `UserName` is not within the list of allowed attributes and the `ForAllValues` qualifier requires all requested values to be listed in the policy\.

On the other hand, if the user attempts to implicitly obtain all attributes by invoking the `GetItem` operation with the following input:

```
{
    "Key": {
        "ID": { "S": "101" }
    }
}
```

The request context key values would be:

```
{
    "dynamodb:Attributes": ["ID"],
    "dynamodb:Select": "ALL_ATTRIBUTES"
}
```

In this case, the user's requested attributes all match values specified in the policy\. However, the `dynamodb:Select` context key does not match, which causes the request to be implicitly denied.

**Important**  
If you use `dynamodb:Attributes`, you must specify the names of all of the primary key and index key attributes for the table\. You must also specify any secondary indexes that are listed in the policy\. Otherwise, DynamoDB can't use these key attributes to perform the requested action\.

**Warning**  
When you use the `ForAllValues` condition operator, it returns true if there are no keys in the request, or if the key values resolve to a null data set, such as an empty string\. To require that the request context key exists, you must use the [Null](reference_policies_elements_condition_operators.md#Conditions_Null) operator. To require that the request context key includes at least one value, you must use another condition in the policy\. For an example, see [Controlling access during AWS requests](access_tags.md#access_tags_control-requests)\.

Alternatively, you might want to make sure that users are explicitly forbidden to include some attributes in a request, such as the `PostDateTime` and `UserName` attributes\. For example, you might exclude attributes when the user is updating the DynamoDB table, since an [UpdateItem](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_UpdateItem.html) invocation should not change certain attributes\. In that case, you create a list of forbidden attributes \(`PostDateTime`, `UserName`\)\. If any of the user's requested attributes match any of the forbidden attributes, the request is denied\. 

The following example shows how to use the `ForAnyValue` qualifier to deny access to the `PostDateTime` and `UserName` attributes if the user tries to perform the `UpdateItem` action\. That is, if the user tries to update either of those attributes in the `Thread` table\. Notice that the `Effect` element is set to `Deny`\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Deny",
        "Action": "dynamodb:UpdateItem",
        "Resource": "arn:aws:dynamodb:*:*:table/Thread",
        "Condition": {
            "ForAnyValue:StringEquals": {
                "dynamodb:Attributes": [
                    "PostDateTime",
                    "UserName"
                ]
            }
        }
    }
}
```

Assume that the user makes a request to update the `PostDateTime` and `Message` attributes of the `Thread` table\. The `ForAnyValue` qualifier determines whether any of the requested attributes appear in the list in the policy\. In this case, there is one match \(`PostDateTime`\), so the condition is true\. Assuming the other values in the request also match \(for example, the `Resource`\), the overall policy evaluation returns true\. Because the policy's effect is `Deny`, the request is denied\. 

Imagine the user instead makes a request to perform `UpdateItem` with just the `Message` attribute\. None of the attributes in the request \(`ID`, `Message`\) match any of attributes listed in the policy \(`PostDateTime`, `UserName`\)\. The condition returns false, so the effect of the policy \(`Deny`\) is also false, and the request is not denied by this policy\. However, for the request to succeed, it must be explicitly allowed by a different policy\. Keep in mind that all requests are implicitly denied by default\.

For more information about how set operators are used in DynamoDB to implement fine\-grained access to individual data items and attributes, see [Using IAM policy conditions for fine\-grained access control](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html) in the *Amazon DynamoDB Developer Guide*\.

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
If the key values in the request resolve to an empty data set, such as an empty list, a condition operator modified by `ForAllValues` returns true\. A condition operator modified by `ForAnyValue` returns false\. 
