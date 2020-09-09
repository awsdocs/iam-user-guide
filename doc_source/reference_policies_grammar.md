# Grammar of the IAM JSON policy language<a name="reference_policies_grammar"></a>

This page presents a formal grammar for the language used to create JSON policies in IAM\. We present this grammar so that you can understand how to construct and validate policies\.

For examples of policies, see the following topics:
+ [Policies and permissions in IAM](access_policies.md)
+ [Example IAM identity\-based policies](access_policies_examples.md)
+ [Example Policies for Working in the Amazon EC2 Console](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policies-ec2-console.html) and [Example Policies for Working With the AWS CLI, the Amazon EC2 CLI, or an AWS SDK](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ExamplePolicies_EC2.html) in the *Amazon EC2 User Guide for Linux Instances*\. 
+  [Bucket Policy Examples](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html) and [User Policy Examples](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-policies-s3.html) in the *Amazon Simple Storage Service Developer Guide*\. 

For examples of policies used in other AWS services, go to the documentation for those services\.

**Topics**
+ [The policy language and JSON](#policies-grammar-json)
+ [Conventions used in this grammar](#policies-grammar-conventions)
+ [Grammar](#policies-grammar-bnf)
+ [Policy grammar notes](#policies-grammar-notes)

## The policy language and JSON<a name="policies-grammar-json"></a>

Policies are expressed in JSON\. When a policy is submitted to IAM, it is first validated to make sure that the JSON syntax is correct\. In this document, we do not provide a complete description of what constitutes valid JSON\. However, here are some basic JSON rules:
+ White space between individual entities is allowed\.
+ Values are enclosed in quotation marks\. Quotation marks are optional for numeric and Boolean values\.
+ Many elements \(for example, `action_string_list` and `resource_string_list`\) can take a JSON array as a value\. Arrays can take one or more values\. If more than one value is included, the array is in square brackets \(`[` and `]`\) and comma\-delimited, as in the following example: 

  `"Action" : ["ec2:Describe*","ec2:List*"]`
+ Basic JSON data types \(Boolean, number, and string\) are defined in [RFC 7159](http://tools.ietf.org/html/rfc7159)\.

You can use a JSON validator to check the syntax of a policy\. You can find a validator online, and many code editors and XML\-editing tools include JSON validation features\.

## Conventions used in this grammar<a name="policies-grammar-conventions"></a>

The following conventions are used in this grammar:
+ The following characters are JSON tokens and *are* included in policies:

  `{ } [ ] " , :`
+ The following characters are special characters in the grammar and are *not* included in policies: 

  `= < > ( ) |`
+ If an element allows multiple values, it is indicated using repeated values, a comma delimiter, and an ellipsis \(`...`\)\. Examples:

  `[<action_string>, <action_string>, ...]`

  `<principal_map> = { <principal_map_entry>, <principal_map_entry>, ... }`

  If multiple values are allowed, it is also valid to include only one value\. For only one value, the trailing comma must be omitted\. If the element takes an array \(marked with \[ and \]\) but only one value is included, the brackets are optional\. Examples:

  `"Action": [<action_string>]`

  `"Action": <action_string>`
+ A question mark \(`?`\) following an element indicates that the element is optional\. Example: 

  <`version_block?>`

  However, be sure to refer to the notes that follow the grammar listing for details about optional elements\. 
+ A vertical line \(`|`\) between elements indicates alternatives\. In the grammar, parentheses define the scope of the alternatives\. Example:

  `("Principal" | "NotPrincipal")` 
+ Elements that must be literal strings are enclosed in double quotation marks \(`"`\)\. Example:

  `<version_block> = "Version" : ("2008-10-17" | "2012-10-17")`

For additional notes, see [Policy grammar notes](#policies-grammar-notes) following the grammar listing\.

## Grammar<a name="policies-grammar-bnf"></a>

The following listing describes the policy language grammar\. For conventions used in the listing, see the preceding section\. For additional information, see the notes that follow\.

**Note**  
This grammar describes policies marked with a version of `2008-10-17` and `2012-10-17`\. A `Version` policy element is different from a policy version\. The `Version` policy element is used within a policy and defines the version of the policy language\. A policy version, on the other hand, is created when you make changes to a customer managed policy in IAM\. The changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new version of the managed policy\. To learn more about the `Version` policy element see [IAM JSON policy elements: Version](reference_policies_elements_version.md)\. To learn more about policy versions, see [Versioning IAM policies](access_policies_managed-versioning.md)\.

```
policy  = {
     <version_block?>
     <id_block?>
     <statement_block>
}

<version_block> = "Version" : ("2008-10-17" | "2012-10-17")

<id_block> = "Id" : <policy_id_string>

<statement_block> = "Statement" : [ <statement>, <statement>, ... ]

<statement> = { 
    <sid_block?>,
    <principal_block?>,
    <effect_block>,
    <action_block>,
    <resource_block>,
    <condition_block?>
}

<sid_block> = "Sid" : <sid_string>

<effect_block> = "Effect" : ("Allow" | "Deny")  

<principal_block> = ("Principal" | "NotPrincipal") : ("*" | <principal_map>)

<principal_map> = { <principal_map_entry>, <principal_map_entry>, ... }

<principal_map_entry> = ("AWS" | "Federated" | "Service" | "CanonicalUser") :   
    [<principal_id_string>, <principal_id_string>, ...]

<action_block> = ("Action" | "NotAction") : 
    ("*" | [<action_string>, <action_string>, ...])

<resource_block> = ("Resource" | "NotResource") : 
    ("*" | [<resource_string>, <resource_string>, ...])

<condition_block> = "Condition" : { <condition_map> }
<condition_map> = { 
  <condition_type_string> : { <condition_key_string> : <condition_value_list> },
  <condition_type_string> : { <condition_key_string> : <condition_value_list> }, ...
}  
<condition_value_list> = [<condition_value>, <condition_value>, ...]
<condition_value> = ("string" | "number" | "Boolean")
```

## Policy grammar notes<a name="policies-grammar-notes"></a>
+ A single policy can contain an array of statements\.
+ Policies have a maximum size between 2048 characters and 10,240 characters, depending on what entity the policy is attached to\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\. Policy size calculations do not include white space characters\.
+ Individual elements must not contain multiple instances of the same key\. For example, you cannot include the `Effect` block twice in the same statement\. 
+ Blocks can appear in any order\. For example, `version_block` can follow `id_block` in a policy\. Similarly, `effect_block`, `principal_block`, `action_block` can appear in any order within a statement\.
+ The `id_block` is optional in resource\-based policies\. It must *not* be included in identity\-based policies\.
+ The `principal_block` element is required in resource\-based policies \(for example, in Amazon S3 bucket policies\) and in trust policies for IAM roles\. It must *not* be included in identity\-based policies\.
+ The `principal_map` element in Amazon S3 bucket policies can include the `CanonicalUser` ID\. Most resource\-based policies do not support this mapping\. To learn more about using the canonical user ID in a bucket policy, see [Specifying a Principal in a Policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/s3-bucket-user-policy-specifying-principal-intro.html) in the *Amazon Simple Storage Service Developer Guide*\.
+ Each string value \(`policy_id_string`, `sid_string`, `principal_id_string`, `action_string`, `resource_string`, `condition_type_string`, `condition_key_string`, and the string version of `condition_value`\) can have its own minimum and maximum length restrictions, specific allowed values, or required internal format\.

### Notes about string values<a name="policies-grammar-notes-strings"></a>

This section provides additional information about string values that are used in different elements in a policy\.

**`action_string`**  
Consists of a service namespace, a colon, and the name of an action\. Action names can include wildcards\. Examples:  

```
"Action":"ec2:StartInstances"

"Action":[
  "ec2:StartInstances",
  "ec2:StopInstances"
]

"Action":"cloudformation:*"

"Action":"*"

"Action":[
  "s3:Get*",
  "s3:List*"
]
```

**`policy_id_string`**  
Provides a way to include information about the policy as a whole\. Some services, such as Amazon SQS and Amazon SNS, use the `Id` element in reserved ways\. Unless otherwise restricted by an individual service, policy\_id\_string can include spaces\. Some services require this value to be unique within an AWS account\.   
The `id_block` is allowed in resource\-based policies, but not in identity\-based policies\.
There is no limit to the length, although this string contributes to the overall length of the policy, which is limited\.   

```
"Id":"Admin_Policy"

"Id":"cd3ad3d9-2776-4ef1-a904-4c229d1642ee"
```

**`sid_string`**  
Provides a way to include information about an individual statement\. For IAM policies, basic alphanumeric characters \(A\-Z,a\-z,0\-9\) are the only allowed characters in the `Sid` value\. Other AWS services that support resource policies may have other requirements for the `Sid` value\. For example, some services require this value to be unique within an AWS account, and some services allow additional characters such as spaces in the `Sid` value\.  

```
"Sid":"1" 

"Sid": "ThisStatementProvidesPermissionsForConsoleAccess"
```

**`principal_id_string`**  
Provides a way to specify a principal using the [*Amazon Resource Name* \(ARN\)](reference_identifiers.md#identifiers-arns) of the AWS account, IAM user, IAM role, federated user, or assumed\-role user\. For an AWS account, you can also use the short form `AWS:accountnumber` instead of the full ARN\. For all of the options including AWS services, assumed roles, and so on, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\.  
Note that you can use \* only to specify "everyone/anonymous\." You cannot use it to specify part of a name or ARN\.

**`resource_string`**  
In most cases, consists of an [Amazon Resource Name](reference_identifiers.md#identifiers-arns) \(ARN\)\.  

```
"Resource":"arn:aws:iam::123456789012:user/Bob"

"Resource":"arn:aws:s3:::examplebucket/*"
```

**`condition_type_string`**  
Identifies the type of condition being tested, such as `StringEquals`, `StringLike`, `NumericLessThan`, `DateGreaterThanEquals`, `Bool`, `BinaryEquals`, `IpAddress`, `ArnEquals`, etc\. For a complete list of condition types, see [IAM JSON policy elements: Condition operators](reference_policies_elements_condition_operators.md)\.   

```
"Condition": {
  "NumericLessThanEquals": {
    "s3:max-keys": "10"
  }
}

"Condition": {
  "Bool": {
    "aws:SecureTransport": "true"
  }
}

"Condition": {
  "StringEquals": {
      "s3:x-amz-server-side-encryption": "AES256"
   }
}
```

**`condition_key_string`**  
Identifies the condition key whose value will be tested to determine whether the condition is met\. AWS defines a set of condition keys that are available in all AWS services, including `aws:PrincipalType`, `aws:SecureTransport`, and `aws:userid`\.  
For a list of AWS condition keys, see [AWS global condition context keys](reference_policies_condition-keys.md)\. For condition keys that are specific to a service, see the documentation for that service such as the following:  
+ [Specifying Conditions in a Policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html) in the *Amazon Simple Storage Service Developer Guide*
+ [IAM Policies for Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policies-for-amazon-ec2.html) in the *Amazon EC2 User Guide for Linux Instances*\.

```
"Condition":{
  "Bool": {
      "aws:SecureTransport": "true"
   }
}

"Condition": {
  "StringNotEquals": {
      "s3:x-amz-server-side-encryption": "AES256"
   }
}

"Condition": {
  "StringEquals": {
    "ec2:ResourceTag/purpose": "test"
  }
}
```