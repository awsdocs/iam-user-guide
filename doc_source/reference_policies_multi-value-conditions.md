# Creating a Condition That Tests Multiple Key Values \(Set Operations\)<a name="reference_policies_multi-value-conditions"></a>

You can use the `Condition` element of a policy to test multiple values for a single key in a request\. When you make a request to AWS, either programmatically or through the AWS Management Console, you include information in the request\. You can use condition keys to test the values of the matching keys in the request\. For example, you can use a condition key to control access to specific attributes of a DynamoDB table, or to an Amazon EC2 instance based on tags\.

For requests that include multiple values for a single key, test whether the entire set of request values matches the entire set of condition key values using the `ForAllValues` qualifier\. To test whether at least one member of the set of request values matches at least one member of the set of condition key values, use the `ForAnyValue` qualifier\. These qualifiers add set\-operation functionality to the condition operator so that you can test multiple request values against multiple condition values\. 

When someone makes a request, AWS evaluates the policy to determine whether the condition is true or false\. For requests with multiple key values, AWS evaluates the condition based on the qualifier:
+ `ForAllValues` – The condition returns true if there's a match between every one of the specified key values in the request and at least one value in the policy\. It also returns true if there is no matching key in the request, or if the key values resolve to an empty data set, such as an empty string\.
+ `ForAnyValue` – The condition returns true if any one of the key values in the request matches any one of the condition values in the policy\. For no matching key or an empty data set, the condition returns false\.

**Contents**
+ [Examples of Condition Set Operators](#reference_policies_multi-value-conditions-examples)
+ [Evaluation Logic for Condition Set Operators](#reference_policies_multi-value-conditions-eval)

## Examples of Condition Set Operators<a name="reference_policies_multi-value-conditions-examples"></a>

You can create a policy to test multiple values in a request against one or more values that you specify in the policy\. Assume that you have an Amazon DynamoDB table named `Thread` that is used to store information about threads in a technical support forum\. The table might as attributes named `ID`, `UserName`, `PostDateTime`, `Message`, and `Tags`\. 

```
{	
  ID=101
  UserName=Bob
  PostDateTime=20130930T231548Z
  Message="A good resource for this question is docs.aws.amazon.com"
  Tags=["AWS", "Database", "Security"]
}
```

For information about how set operators are used in DynamoDB to implement fine\-grained access to individual data items and attributes, see [Fine\-Grained Access Control for DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/FGAC_DDB.html) in the *Amazon DynamoDB Developer Guide* guide\. 

You can create a policy that allows users to see only the `PostDateTime`, `Message`, and `Tags` attribures\. If the user's request contains any of these attributes, it is allowed; but if the request contains any other attributes \(for example, `ID`\), the request is denied\. Logically speaking, you want to create a list of allowed attributes \(`PostDateTime`, `Message`, `Tags`\) and indicate in the policy that all of the user's requested attributes must be in that list of allowed attributes\.

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

If the user makes a request to DynamoDB to get the attributes `Message` and `Tags` from the `Thread` table, the request is allowed, because the user's requested attributes all match values specified in the policy\. The `GetItem` operation requires the user to pass the `ID` attribute as the database table key, which is also allowed in the policy\. However, if the user's request includes the `UserName` attribute, the request fails, because `UserName` is not within the list of allowed attributes and the `ForAllValues` qualifier requires all requested values to be listed in the policy\.

**Important**  
If you use `dynamodb:Attributes`, you must specify the names of all of the primary key and index key attributes for the table and any secondary indexes that are listed in the policy\. Otherwise, DynamoDB can't use these key attributes to perform the requested action\.

Alternatively, you might want to make sure that users are explicitly forbidden to include some attributes in a request, such as the `ID` and `UserName` attributes\. For example, you might exclude attributes when the user is updating the DynamoDB table, because an update \(`PUT` operation\) should not change certain attributes\. In that case, you create a list of forbidden attributes \(`ID`, `UserName`\), and if any of the user's requested attributes match any of the forbidden attributes, the request is denied\. 

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

## Evaluation Logic for Condition Set Operators<a name="reference_policies_multi-value-conditions-eval"></a>

This section discusses the specifics of the evaluation logic used with the `ForAllValues` and `ForAnyValue` qualifiers\. The following table illustrates possible keys that might be included in a request \(`PostDateTime` and `UserName`\) and a policy condition that includes the values `PostDateTime`, `Message`, and `Tags`\. 


****  

| Key \(in the request\) | Condition Value \(in the policy\) | 
| --- | --- | 
| `PostDateTime` | `PostDateTime` | 
| `UserName` | `Message` | 
|   | `Tags` | 

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
| `PostDateTime` matches `Message`? |  `False`  | 
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
If the key values in the request resolve to an empty data set \(for example, an empty string\), a condition operator modified by `ForAllValues` returns true, and a condition operator modified by `ForAnyValue` returns false\. 