# IAM Policy Elements: Variables<a name="reference_policies_variables"></a>

**Topics**
+ [Introduction](#policy-vars-intro)
+ [Where You Can Use Policy Variables](#policy-vars-wheretouse)
+ [Request Information That You Can Use for Policy Variables](#policy-vars-infotouse)
+ [For More Information](#policy-vars-formoreinfo)

## Introduction<a name="policy-vars-intro"></a>

In IAM policies, many actions allow you to provide a name for the specific resources that want to control access to\. For example, the following policy allows the user to list, read, and write objects with a prefix `David` in the Amazon S3 bucket `mybucket`\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": ["s3:ListBucket"],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::mybucket"],
      "Condition": {"StringLike": {"s3:prefix": ["David/*"]}}
    },
    {
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::mybucket/David/*"]
    }
  ]
}
```

In some cases, you might not know the exact name of the resource when you write the policy\. You might want to generalize the policy so it works for many users without having to make a unique copy of the policy for each user\. For example, consider writing a policy allow each user to have access to his or her own objects in an Amazon S3 bucket, as in the previous example\. However, instead of creating a separate policy for each user that explicitly specifies the user's name as part of the resource, you want to create a single group policy that works for any user in that group\. 

You can do this by using *policy variables*, a feature that lets you specify placeholders in a policy\. When the policy is evaluated, the policy variables are replaced with values that come from the context of the request itself\. 

The following example shows a policy for an Amazon S3 bucket that uses a policy variable\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": ["s3:ListBucket"],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::mybucket"],
      "Condition": {"StringLike": {"s3:prefix": ["${aws:username}/*"]}}
    },
    {
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::mybucket/${aws:username}/*"]
    }
  ]
}
```

When this policy is evaluated, IAM replaces the variable `${aws:username}`with the [friendly name](reference_identifiers.md#identifiers-friendly-names) of the actual current user\. This means that a single policy applied to a group of users can control access to a bucket by using the user name as part of the resource's name\. 

The variable is marked using a `$` prefix followed by a pair of curly braces \(`{ }`\)\. Inside the `${ }` characters, you can include the name of the value from the request that you want to use in the policy\. The values you can use are discussed later on this page\.

**Note**  
In order to use policy variables, you must include the `Version` element in a statement, and the version must be set to a version that supports policy variables\. Variables were introduced in version `2012-10-17`\. Earlier versions of the policy language don't support policy variables\. If you don't include the `Version` element and set it to an appropriate version date, variables like `${aws:username}` are treated as literal strings in the policy\.   
A `Version` policy element is different from a policy version\. The `Version` policy element is used within a policy and defines the version of the policy language\. A policy version, on the other hand, is created when you make changes to a customer managed policy in IAM\. The changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new version of the managed policy\. To learn more about the `Version` policy element see [IAM JSON Policy Elements: Version](reference_policies_elements_version.md)\. To learn more about policy versions, see [Versioning IAM Policies](access_policies_managed-versioning.md)\.

You can use policy variables in a similar way to allow each user to manage his or her own access keys\. A policy that allows a user to programmatically change the access key for user `David` looks like this: 

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Action": ["iam:*AccessKey*"],
    "Effect": "Allow",
    "Resource": ["arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:user/David"]
  }]
}
```

If this policy is attached to user `David`, that user can change his own access key\. As with the policies for accessing user\-specific Amazon S3 objects, you would have to create a separate policy for each user that includes the user's name\. You would then attach each policy to the individual users\. 

By using a policy variable, you can create a policy like this: 

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Action": ["iam:*AccessKey*"],
    "Effect": "Allow",
    "Resource": ["arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:user/${aws:username}"]
  }]
}
```

When you use a policy variable for the user name like this, you don't have to have a separate policy for each individual user\. Instead, you can attach this new policy to an IAM group that includes everyone who should be allowed to manage their own access keys\. When a user makes a request to modify his or her access key, IAM substitutes the user name from the current request for the `${aws:username}` variable and evaluates the policy\. 

## Where You Can Use Policy Variables<a name="policy-vars-wheretouse"></a>

You can use policy variables in the `Resource` element and in string comparisons in the `Condition` element\.

### Resource Element<a name="policy-vars-resourceelement"></a>

A policy variable can appear as the last part of the [ARN](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) that identifies a resource\. The following policy might be attached to a group\. It gives each of the users in the group full programmatic access to a user\-specific object \(their own "home directory"\) in Amazon S3\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": ["s3:ListBucket"],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::mybucket"],
      "Condition": {"StringLike": {"s3:prefix": ["${aws:username}/*"]}}
    },
    {
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::mybucket/${aws:username}/*"]
    }
  ]
}
```

**Note**  
This example uses the `aws:username` key, which returns the user's friendly name \(like "Adele" or "David"\)\. Under some circumstances, you might want to use the `aws:userid` key instead, which is a globally unique value\. For more information, see [Unique IDs](reference_identifiers.md#identifiers-unique-ids)\.

The following policy might be used for an IAM group\. It gives users in that group the ability to create, use, and delete queues that have their names and that are in the us\-east\-2 region\.

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "sqs:*",
    "Resource": "arn:aws:sqs:us-east-2:*:${aws:username}-queue"
  }]
}
```

### Condition Element<a name="policy-vars-conditionelement"></a>

A policy variable can also be used for `Condition` values in any condition that involves the string operators \(`StringEquals`, `StringLike`, `StringNotLike`, etc\.\) or the ARN operators \(`ArnEquals`, `ArnLike`, etc\.\)\. The following Amazon SNS topic policy gives users in AWS account `999999999999` the ability to manage \(perform all actions for\) the topic only if the URL matches their AWS user name\. 

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Principal": {"AWS": "999999999999"},
    "Effect": "Allow",
    "Action": "sns:*",
    "Condition": {"StringLike": {"sns:endpoint": "https://example.com/${aws:username}/*"}}
  }]
}
```

## Request Information That You Can Use for Policy Variables<a name="policy-vars-infotouse"></a>

 The values that can be substituted for policy variables must come from the current [request context](reference_policies_evaluation-logic.md#policy-eval-reqcontext)\. 

### Information Available in All Requests<a name="policy-vars-infoallreqs"></a>

Policies contain keys whose values you can use as policy variables\. \(Under some circumstances, the keys do not contain a value—see the information that follows this list\.\) 
+ **`aws:CurrentTime`** This can be used for conditions that check the date and time\.
+ **`aws:EpochTime`** This is the date in epoch or UNIX time, for use with date/time conditions\.
+ **`aws:TokenIssueTime`** This is the date and time that temporary security credentials were issued and can be used with date/time conditions\. **Note:** This key is only available in requests that are signed using temporary security credentials\. For more information about temporary security credentials, see [Temporary Security Credentials](id_credentials_temp.md)\.
+ **`aws:principaltype`** This value indicates whether the principal is an account, user, federated, or assumed role—see the explanation that follows later\.
+ **`aws:SecureTransport`** This is a Boolean value that represents whether the request was sent using SSL\.
+ **`aws:SourceIp`** This is the requester's IP address, for use with IP address conditions\. Refer to [IP Address Condition Operators](reference_policies_elements_condition_operators.md#Conditions_IPAddress) for information about when `SourceIp` is valid and when you should use a VPC\-specific key instead\. 
+ **`aws:UserAgent`** This value is a string that contains information about the requester's client application\.
+ **`aws:userid`** This value is the unique ID for the current user—see the chart that follows\.
+ **`aws:username`** This is a string containing the [friendly name](reference_identifiers.md#identifiers-friendly-names) of the current user—see the chart that follows\.
+ **`ec2:SourceInstanceARN`** This is the Amazon Resource Name \(ARN\) of the Amazon EC2 instance from which the request is made\. This key is present only when the request comes from an Amazon EC2 instance using an IAM role associated with an EC2 instance profile\.

**Important**  
Key names are case\-insensitive\. For example, `aws:CurrentTime` is equivalent to `AWS:currenttime`\. 

The values for `aws:username`, `aws:userid`, and `aws:principaltype` depend on what type of principal initiated the request—whether the request was made using the credentials of an AWS account, an IAM user, an IAM role, and so on\. The following shows values for these keys for different types of principal\. 

In this 
+ *not present* means that the value is not in the current request information, and any attempt to match it fails and causes the request to be denied\. 
+ *role\-id* is a unique identifier assigned to each role at creation\. You can display the role ID with the AWS CLI command: `aws iam get-role --role-name rolename`
+ *caller\-specified\-name* and *caller\-specified\-role\-name* are names that are passed by the calling process \(such as an application or service\) when it makes a call to get temporary credentials\.
+ *ec2\-instance\-id* is a value assigned to the instance when it is launched and appears on the **Instances** page of the Amazon EC2 console\. You can also display the instance ID by running the AWS CLI command: `aws ec2 describe-instances`

### Information Available in Requests for Federated Users<a name="policy-vars-infoWIF"></a>

Federated users are users who are authenticated using a system other than IAM\. For example, a company might have an application for use in\-house that makes calls to AWS\. It might be impractical to give an IAM identity to every corporate user who uses the application\. Instead, the company might use a proxy \(middle\-tier\) application that has a single IAM identity, or the company might use a SAML identity provider \(IdP\)\. The proxy application or SAML IdP authenticates individual users using the corporate network\. A proxy application can then use its IAM identity to get temporary security credentials for individual users\. A SAML IdP can in effect exchange identity information for AWS temporary security credentials\. The temporary credentials can then be used to access AWS resources\. 

Similarly, you might create an app for a mobile device in which the app needs to access AWS resources\. In that case, you might use *web identity federation*, where the app authenticates the user using a well\-known identity provider like Login with Amazon, Amazon Cognito, Facebook, or Google\. The app can then use the user's authentication information from these providers to get temporary security credentials for accessing AWS resources\. 

The recommended way to use web identity federation is by taking advantage of Amazon Cognito and the AWS mobile SDKs\. For more information, see the following:
+ [Amazon Cognito Overview ](http://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html#d0e840) in the *AWS Mobile SDK for Android Developer Guide* 
+ [Amazon Cognito Overview ](http://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html#d0e664) in the *AWS Mobile SDK for iOS Developer Guide* 
+ [Common Scenarios for Temporary Credentials](id_credentials_temp.md#sts-introduction)\.

### Service\-Specific Information<a name="policy-vars-infoperservice"></a>

Requests can also include service\-specific keys and values in its request context\. Examples include the following: 
+ `s3:prefix`
+ `s3:max-keys`
+ `s3:x-amz-acl`
+ `sns:Endpoint`
+ `sns:Protocol`

For information about service\-specific keys that you can use to get values for policy variables, refer to the documentation for the individual services\. For example, see the following topics: 
+  [Bucket Keys in Amazon S3 Policies](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingResOpsConditions.html#BucketKeysinAmazonS3Policies) in the *Amazon Simple Storage Service Developer Guide*\. 
+  [Amazon SNS Keys](http://docs.aws.amazon.com/sns/latest/dg/AccessPolicyLanguage_SpecialInfo.html#sns_aspen_keys) in the *Amazon Simple Notification Service Developer Guide*\. 

### Special Characters<a name="policy-vars-specialchars"></a>

There are a few special predefined policy variables that have fixed values that enable you to represent characters that otherwise have special meaning\. If these special characters are part of the string, you are trying to match and you inserted them literally they would be misinterpreted\. For example, inserting an \* asterisk in the string would be interpreted as a wildcard, matching any characters, instead of as a literal \*\. In these cases, you can use the following predefined policy variables:
+ **$\{\*\}** \- use where you need an \* asterisk character\.
+ **$\{?\}** \- use where you need a ? question mark character\.
+ **$\{$\}** \- use where you need a $ dollar sign character\.

These predefined policy variables can be used in any string where you can use regular policy variables\.

## For More Information<a name="policy-vars-formoreinfo"></a>

 For more information about policies, see the following: 
+  [IAM Policies](access_policies.md) 
+  [Example Policies](access_policies_examples.md) 
+  [IAM JSON Policy Elements Reference](reference_policies_elements.md) 
+  [IAM JSON Policy Evaluation Logic](reference_policies_evaluation-logic.md) 
+  [About Web Identity Federation](id_roles_providers_oidc.md)