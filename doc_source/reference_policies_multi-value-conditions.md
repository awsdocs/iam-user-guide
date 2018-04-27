# Creating a Condition That Tests Multiple Key Values \(Set Operations\)<a name="reference_policies_multi-value-conditions"></a>

This topic discusses how to create a policy `Condition` element that lets you test multiple values for a single key in a request\. In effect, you can create a condition that uses set operations\. This type of condition is useful for creating policies that allow fine\-grained control for DynamoDB tables \(for example, allowing or denying access to particular attributes\)\.  

To create this type of condition, you can use the `ForAllValues` or `ForAnyValue` qualifier with the condition operator\. These qualifiers add set\-operation functionality to the condition operator so that you can test multiple request values against multiple condition values\. 

**Contents**
+ [Introduction](#reference_policies_multi-value-conditions-intro)
+ [Examples of Condition Set Operators](#reference_policies_multi-value-conditions-examples)
+ [Evaluation Logic for Condition Set Operators](#reference_policies_multi-value-conditions-eval)

## Introduction<a name="reference_policies_multi-value-conditions-intro"></a>

In some situations, you need to create a policy in which you test multiple values in a request against one or more values that you specify in the policy\. A good example is a request for attributes from an Amazon DynamoDB table\. Imagine an Amazon DynamoDB table named `Thread` that is used to store information about threads in a technical support forum\. The table might have attributes like `ID`, `UserName`, `PostDateTime`, `Message`, and `Tags` \(among others\)\. 

```
{	
  ID=101
  UserName=Bob
  PostDateTime=20130930T231548Z
  Message="A good resource for this question is http://aws.amazon.com/documentation/"
  Tags=["AWS", "Database", "Security"]
}
```

You might want to create a policy that allows users to see only some attributes—for example, maybe you want to let these users to see only `PostDateTime`, `Message`, and `Tags`\. If the user's request contains any of these attributes, it is allowed; but if the request contains any other attributes \(for example, `ID`\), the request is denied\. Logically speaking, you want to create a list of allowed attributes \(`PostDateTime`, `Message`, `Tags`\) and indicate in the policy that all of the user's requested attributes must be in that list of allowed attributes\.

Or you might want to make sure that users are explicitly forbidden to include some attributes in a request, such as the `ID` and `UserName` attributes\. For example, you might exclude attributes when the user is updating the DynamoDB table, because an update \(`PUT` operation\) should not change certain attributes\. In that case, you create a list of forbidden attributes \(`ID`, `UserName`\), and if any of the user's requested attributes match any of the forbidden attributes, the request is denied\. 

To support these scenarios, you can use the following modifiers to a condition operator:
+ `ForAnyValue` – The condition returns true if any one of the key values in the request matches any one of the condition values in the policy\. 
+ `ForAllValues` – The condition returns true if there's a match between every one of the specified key values in the request and at least one value in the policy\. 

For information about how set operators are used in DynamoDB to implement fine\-grained access to individual data items and attributes, see [Fine\-Grained Access Control for DynamoDB](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/FGAC_DDB.html) in the *Amazon DynamoDB Developer Guide* guide\. 

## Examples of Condition Set Operators<a name="reference_policies_multi-value-conditions-examples"></a>

The following example policy shows how to use the `ForAllValues` qualifier with the `StringLike` condition operator\. The condition allows a user to request *only* the attributes `PostDateTime`, `Message`, or `Tags` from the DynamoDB table named `Thread`\.

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "GetItem",
    "Resource": "arn:aws:dynamodb:REGION:ACCOUNT-ID-WITHOUT-HYPHENS:table/Thread",
    "Condition": {"ForAllValues:StringLike": {"dynamodb:requestedAttributes": [
      "PostDateTime",
      "Message",
      "Tags"
    ]}}
  }]
}
```

If the user makes a request to DynamoDB to get the attributes `PostDateTime` and `Message` from the `Threads` table, the request is allowed, because the user's requested attributes all match values specified in the policy\. However, if the user's request includes the `ID` attribute, the request fails, because `ID` is not within the list of allowed attributes, and the `ForAllValues` qualifier requires all requested values to be listed in the policy\. 

The following example shows how to use the `ForAnyValue` qualifier as part of a policy that denies access to the `ID` and `PostDateTime` attributes if the user tries to perform the `PutItem` action—that is, if the user tries to update either of those attributes\. Notice that the `Effect` element is set to `Deny`\.

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Deny",
    "Action": "PutItem",
    "Resource": "arn:aws:dynamodb:REGION:ACCOUNT-ID-WITHOUT-HYPHENS:table/Thread",
    "Condition": {"ForAnyValue:StringLike": {"dynamodb:requestedAttributes": [
      "ID",
      "PostDateTime"
    ]}}
  }]
}
```

Imagine that the user makes a request to update the `PostDateTime` and `Message` attributes\. The `ForAnyValue` qualifier determines whether any of the requested attributes appear in the list in the policy\. In this case, there is one match \(`PostDateTime`\), so the condition is true\. Assuming the other values in the request also match \(for example, the resource\), the overall policy evaluation returns true\. Because the policy's effect is `Deny`, the request is denied\. 

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
  "Statement": [{
    "Effect": "Allow",
    "Action": "GetItem",
    "Resource": "arn:aws:dynamodb:REGION:ACCOUNT-ID-WITHOUT-HYPHENS:table/Thread",
    "Condition": {"ForAllValues:StringLike": {"dynamodb:requestedAttributes": [
      "PostDateTime",
      "Message",
      "Tags"
    ]}}
  }]
}
```

Suppose that the user makes a request to DynamoDB to get the attributes `PostDateTime` and `UserName`\. The keys in the request and condition values in the policy are these: 


****  

| Key \(in the request\) | Condition Value \(in the policy\) | 
| --- | --- | 
| PostDateTime | PostDateTime | 
| UserName | Message | 
|   | Tags | 

The evaluation for the combination is this:


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
  "Statement": [{
    "Effect": "Deny",
    "Action": "PutItem",
    "Resource": "arn:aws:dynamodb:REGION:ACCOUNT-ID-WITHOUT-HYPHENS:table/Thread",
    "Condition": {"ForAnyValue:StringLike": {"dynamodb:requestedAttributes": [
      "ID",
      "PostDateTime"
    ]}}
  }]
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