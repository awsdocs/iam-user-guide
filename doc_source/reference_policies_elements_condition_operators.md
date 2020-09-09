# IAM JSON policy elements: Condition operators<a name="reference_policies_elements_condition_operators"></a>

Use condition operators in the `Condition` element to match the condition key and value in the policy against values in the request context\. For more information about the `Condition` element, see [IAM JSON policy elements: Condition](reference_policies_elements_condition.md)\.

The condition operator that you can use in a policy depends on the condition key you choose\. You can choose a global condition key or a service\-specific condition key\. To learn which condition operator you can use for a global condition key, see [AWS global condition context keys](reference_policies_condition-keys.md)\. To learn which condition operator you can use for a service\-specific condition key, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html) and choose the service that you want to view\.

**Important**  
If the key that you specify in a policy condition is not present in the request context, the values do not match\. This applies to all condition operators except [\.\.\.IfExists](#Conditions_IfExists) and [Null check](#Conditions_Null)\. These operators test whether the key is present \(exists\) in the request context\.

The condition operators can be grouped into the following categories:
+ [String](#Conditions_String)
+ [Numeric](#Conditions_Numeric)
+ [Date and time](#Conditions_Date)
+ [Boolean](#Conditions_Boolean)
+ [Binary](#Conditions_BinaryEquals)
+ [IP address](#Conditions_IPAddress)
+ [Amazon Resource Name \(ARN\)](#Conditions_ARN) \(available for only some services\.\)
+ [\.\.\.IfExists](#Conditions_IfExists) \(checks if the key value exists as part of another check\)
+ [Null check](#Conditions_Null) \(checks if the key value exists as a standalone check\)

## String condition operators<a name="Conditions_String"></a>

String condition operators let you construct `Condition` elements that restrict access based on comparing a key to a string value\.


****  

| Condition operator | Description | 
| --- | --- | 
|   `StringEquals`   |  Exact matching, case sensitive  | 
|   `StringNotEquals`   |  Negated matching  | 
|   `StringEqualsIgnoreCase`   |  Exact matching, ignoring case  | 
|   `StringNotEqualsIgnoreCase`   |  Negated matching, ignoring case  | 
|   `StringLike`   |  Case\-sensitive matching\. The values can include a multi\-character match wildcard \(\*\) or a single\-character match wildcard \(?\) anywhere in the string\.  If a key contains multiple values, `StringLike` can be qualified with set operators—`ForAllValues:StringLike` and `ForAnyValue:StringLike`\. For more information, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)\.    | 
|   `StringNotLike`   |  Negated case\-sensitive matching\. The values can include a multi\-character match wildcard \(\*\) or a single\-character match wildcard \(?\) anywhere in the string\.  | 

For example, the following statement contains a `Condition` element that uses the `StringEquals` condition operator with the `aws:PrincipalTag` key to specify that the principal making the request must be tagged with the `iamuser-admin` job category\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "iam:*AccessKey*",
    "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:user/*",
    "Condition": {"StringEquals": {"aws:PrincipalTag/job-category": "iamuser-admin"}}
  }
}
```

If the key that you specify in a policy condition is not present in the request context, the values do not match\. In this example, the `aws:PrincipalTag/job-category` key is present in the request context if the principal is using an IAM user with attached tags\. It is also included for a principal using an IAM role with attached tags or session tags\. If a user without the tag attempts to view or edit an access key, the condition returns `false` and the request is implicitly denied by this statement\.

You can use a [policy variable](reference_policies_variables.md) with the `String` condition operator\.

The following example uses the `StringLike` condition operator to perform string matching with a [policy variable](reference_policies_variables.md) to create a policy that lets an IAM user use the Amazon S3 console to manage his or her own "home directory" in an Amazon S3 bucket\. The policy allows the specified actions on an S3 bucket as long as the `s3:prefix` matches any one of the specified patterns\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets",
        "s3:GetBucketLocation"
      ],
      "Resource": "arn:aws:s3:::*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::BUCKET-NAME",
      "Condition": {"StringLike": {"s3:prefix": [
        "",
        "home/",
        "home/${aws:username}/"
      ]}}
    },
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::BUCKET-NAME/home/${aws:username}",
        "arn:aws:s3:::BUCKET-NAME/home/${aws:username}/*"
      ]
    }
  ]
}
```

For an example of a policy that shows how to use the `Condition` element to restrict access to resources based on an application ID and a user ID for web identity federation, see [Amazon S3: Allows Amazon Cognito users to access objects in their bucket](reference_policies_examples_s3_cognito-bucket.md)\. 

## Numeric condition operators<a name="Conditions_Numeric"></a>

Numeric condition operators let you construct `Condition` elements that restrict access based on comparing a key to an integer or decimal value\.


****  

| Condition operator | Description | 
| --- | --- | 
|   `NumericEquals`   |  Matching  | 
|   `NumericNotEquals`   |  Negated matching  | 
|   `NumericLessThan`   |  "Less than" matching  | 
|   `NumericLessThanEquals`   |  "Less than or equals" matching  | 
|   `NumericGreaterThan`   |  "Greater than" matching  | 
|   `NumericGreaterThanEquals`   |  "Greater than or equals" matching  | 

For example, the following statement contains a `Condition` element that uses the `NumericLessThanEquals` condition operator with the `s3:max-keys` key to specify that the requester can list *up to* 10 objects in `example_bucket` at a time\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "s3:ListBucket",
    "Resource": "arn:aws:s3:::example_bucket",
    "Condition": {"NumericLessThanEquals": {"s3:max-keys": "10"}}
  }
}
```

If the key that you specify in a policy condition is not present in the request context, the values do not match\. In this example, the `s3:max-keys` key is always present in the request when you perform the `ListBucket` operation\. If this policy allowed all Amazon S3 operations, then only the operations that include the `max-keys` context key with a value of less than or equal to 10 would be allowed\. 

You can not use a [policy variable](reference_policies_variables.md) with the `Numeric` condition operator\.

## Date condition operators<a name="Conditions_Date"></a>

Date condition operators let you construct `Condition` elements that restrict access based on comparing a key to a date/time value\. You use these condition operators with the `aws:CurrentTime` key or `aws:EpochTime` keys\. You must specify date/time values with one of the [W3C implementations of the ISO 8601 date formats](http://www.w3.org/TR/NOTE-datetime) or in epoch \(UNIX\) time\.  

**Note**  
Wildcards are not permitted for date condition operators\.


****  

| Condition operator | Description | 
| --- | --- | 
|   `DateEquals`   |  Matching a specific date  | 
|   `DateNotEquals`   |  Negated matching  | 
|   `DateLessThan`   |  Matching before a specific date and time  | 
|   `DateLessThanEquals`   |  Matching at or before a specific date and time  | 
|   `DateGreaterThan`   |  Matching after a specific a date and time  | 
|   `DateGreaterThanEquals`   |  Matching at or after a specific date and time  | 

For example, the following statement contains a `Condition` element that uses the `DateGreaterThan` condition operator with the `aws:TokenIssueTime` key\. This condition specifies that the temporary security credentials used to make the request were issued in 2020\. This policy can be updated programmatically every day to ensure that account members use fresh credentials\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "iam:*AccessKey*",
    "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:user/*",
    "Condition": {"DateGreaterThan": {"aws:TokenIssueTime": "2020-01-01T00:00:01Z"}}
  }
}
```

If the key that you specify in a policy condition is not present in the request context, the values do not match\. The `aws:TokenIssueTime` key is present in the request context only when the principal uses temporary credentials to make the request\. They key is not present in AWS CLI, AWS API, or AWS SDK requests that are made using access keys\. In this example, if an IAM user attempts to view or edit an access key, the request is denied\.

You can not use a [policy variable](reference_policies_variables.md) with the `Date` condition operator\.

## Boolean condition operators<a name="Conditions_Boolean"></a>

Boolean conditions let you construct `Condition` elements that restrict access based on comparing a key to "true" or "false\." 


****  

| Condition operator | Description | 
| --- | --- | 
|   `Bool`   |  Boolean matching  | 

For example, the following statement uses the `Bool` condition operator with the `aws:SecureTransport` key to specify that the request must use SSL\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "iam:*AccessKey*",
    "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:user/*",
    "Condition": {"Bool": {"aws:SecureTransport": "true"}}
  }
}
```

If the key that you specify in a policy condition is not present in the request context, the values do not match\. The `aws:SecureTransport` key is always present in the request context\. 

You can not use a [policy variable](reference_policies_variables.md) with the `Boolean` condition operator\.

## Binary condition operators<a name="Conditions_BinaryEquals"></a>

The `BinaryEquals` condition operator let you construct `Condition` elements that test key values that are in binary format\. It compares the value of the specified key byte for byte against a [base\-64](https://en.wikipedia.org/wiki/Base64) encoded representation of the binary value in the policy\. 

```
"Condition" : {
  "BinaryEquals": {
    "key" : "QmluYXJ5VmFsdWVJbkJhc2U2NA=="
  }
}
```

If the key that you specify in a policy condition is not present in the request context, the values do not match\.

You can not use a [policy variable](reference_policies_variables.md) with the `Binary` condition operator\.

## IP address condition operators<a name="Conditions_IPAddress"></a>

IP address condition operators let you construct `Condition` elements that restrict access based on comparing a key to an IPv4 or IPv6 address or range of IP addresses\. You use these with the `aws:SourceIp` key\. The value must be in the standard CIDR format \(for example, 203\.0\.113\.0/24 or 2001:DB8:1234:5678::/64\)\. If you specify an IP address without the associated routing prefix, IAM uses the default prefix value of `/32`\.

Some AWS services support IPv6, using :: to represent a range of 0s\. To learn whether a service supports IPv6, see the documentation for that service\.


****  

| Condition operator | Description | 
| --- | --- | 
|   `IpAddress`   |  The specified IP address or range  | 
|   `NotIpAddress`   |  All IP addresses except the specified IP address or range  | 

For example, the following statement uses the `IpAddress` condition operator with the `aws:SourceIp` key to specify that the request must come from the IP range 203\.0\.113\.0 to 203\.0\.113\.255\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "iam:*AccessKey*",
    "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:user/*",
    "Condition": {"IpAddress": {"aws:SourceIp": "203.0.113.0/24"}}
  }
}
```

The `aws:SourceIp` condition key resolves to the IP address that the request originates from\. If the requests originates from an Amazon EC2 instance, `aws:SourceIp` evaluates to the instance's public IP address\. 

If the key that you specify in a policy condition is not present in the request context, the values do not match\. The `aws:SourceIp` key is always present in the request context, except when the requester uses a VPC endpoint to make the request\. In this case, the condition returns `false` and the request is implicitly denied by this statement\.

You can not use a [policy variable](reference_policies_variables.md) with the `IP Address` condition operator\.

The following example shows how to mix IPv4 and IPv6 addresses to cover all of your organization's valid IP addresses\. We recommend that you augment your organization's policies with your IPv6 address ranges in addition to IPv4 ranges you already have to ensure the policies continue to work as you make the transition to IPv6\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "someservice:*",
    "Resource": "*",
    "Condition": {
      "IpAddress": {
        "aws:SourceIp": [
          "203.0.113.0/24",
          "2001:DB8:1234:5678::/64"
        ]
      }
    }
  }
}
```

The `aws:SourceIp` condition key works only in a JSON policy if you are calling the tested API directly as a user\. If you instead use a service to call the target service on your behalf, the target service sees the IP address of the calling service rather than the IP address of the originating user\. This can happen, for example, if you use AWS CloudFormation to call Amazon EC2 to construct instances for you\. There is currently no way to pass the originating IP address through a calling service to the target service for evaluation in a JSON policy\. For these types of service API calls, do not use the `aws:SourceIp` condition key\.

## Amazon Resource Name \(ARN\) condition operators<a name="Conditions_ARN"></a>

Amazon Resource Name \(ARN\) condition operators let you construct `Condition` elements that restrict access based on comparing a key to an ARN\. The ARN is considered a string\. Not all services support comparing ARNs using this operator\. If the ARN condition operator doesn't work, then try using [string condition operators](#Conditions_String)\.


****  

| Condition operator | Description | 
| --- | --- | 
|   `ArnEquals`, `ArnLike`  |  Case\-sensitive matching of the ARN\. Each of the six colon\-delimited components of the ARN is checked separately and each can include a multi\-character match wildcard \(\*\) or a single\-character match wildcard \(?\)\. These behave identically\.  | 
|   `ArnNotEquals`, `ArnNotLike`  |  Negated matching for ARN\. These behave identically\.  | 

You can use a [policy variable](reference_policies_variables.md) with the `ARN` condition operator\.

The following resource\-based policy example shows a policy attached to an Amazon SQS queue to which you want to send SNS messages\. It gives Amazon SNS permission to send messages to the queue \(or queues\) of your choice, but only if the service is sending the messages on behalf of a particular Amazon SNS topic \(or topics\)\. You specify the queue in the `Resource` field, and the Amazon SNS topic as the value for the `SourceArn` key\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {"AWS": "123456789012"},
    "Action": "SQS:SendMessage",
    "Resource": "arn:aws:sqs:REGION:123456789012:QUEUE-ID",
    "Condition": {"ArnEquals": {"aws:SourceArn": "arn:aws:sns:REGION:123456789012:TOPIC-ID"}}
  }
}
```

If the key that you specify in a policy condition is not present in the request context, the values do not match\. The `aws:SourceArn` key is present in the request context only if a resource triggers a service to call another service on behalf of the resource owner\. If an IAM user attempts to perform this operation directly, the condition returns `false` and the request is implicitly denied by this statement\.

## \.\.\.IfExists condition operators<a name="Conditions_IfExists"></a>

You can add `IfExists` to the end of any condition operator name except the `Null` condition—for example, `StringLikeIfExists`\. You do this to say "If the policy key is present in the context of the request, process the key as specified in the policy\. If the key is not present, evaluate the condition element as true\." Other condition elements in the statement can still result in a nonmatch, but not a missing key when checked with `...IfExists`\.

**Example using `IfExists`**

Many condition keys describe information about a certain type of resource and only exist when accessing that type of resource\. These condition keys are not present on other types of resources\. This doesn't cause an issue when the policy statement applies to only one type of resource\. However, there are cases where a single statement can apply to multiple types of resources, such as when the policy statement references actions from multiple services or when a given action within a service accesses several different resource types within the same service\. In such cases, including a condition key that applies to only one of the resources in the policy statement can cause the `Condition` element in the policy statement to fail such that the statement's `"Effect"` does not apply\.

For example, consider the following policy example:

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Sid": "THISPOLICYDOESNOTWORK",
    "Effect": "Allow",
    "Action": "ec2:RunInstances",
    "Resource": "*",
    "Condition": {"StringLike": {"ec2:InstanceType": [
      "t1.*",
      "t2.*",
      "m3.*"
    ]}}
  }
}
```

The *intent* of the preceding policy is to enable the user to launch any instance that is type t1, t2 or m3\. However, launching an instance actually requires accessing many resources in addition to the instance itself; for example, images, key pairs, security groups, etc\. The entire statement is evaluated against every resource that is required to launch the instance\. These additional resources do not have the `ec2:InstanceType` condition key, so the `StringLike` check fails, and the user is not granted the ability to launch *any* instance type\. To address this, use the `StringLikeIfExists` condition operator instead\. This way, the test only happens if the condition key exists\. You could read the following as: "If the resource being checked has an "`ec2:InstanceType`" condition key, then allow the action only if the key value begins with "t1\.\*", "t2\.\*", or "m3\.\*"\. If the resource being checked does not have that condition key, then don't worry about it\." The `DescribeActions` statement includes the actions required to view the instance in the console\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "RunInstance",
            "Effect": "Allow",
            "Action": "ec2:RunInstances",
            "Resource": "*",
            "Condition": {
                "StringLikeIfExists": {
                    "ec2:InstanceType": [
                        "t1.*",
                        "t2.*",
                        "m3.*"
             ]}}
        },
        {
            "Sid": "DescribeActions",
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeImages",
                "ec2:DescribeInstances",
                "ec2:DescribeVpcs",
                "ec2:DescribeKeyPairs",
                "ec2:DescribeSubnets",
                "ec2:DescribeSecurityGroups"
            ],
            "Resource": "*"
        }]
}
```

## Condition operator to check existence of condition keys<a name="Conditions_Null"></a>

Use a `Null` condition operator to check if a condition key is present at the time of authorization\. In the policy statement, use either `true` \(the key doesn't exist — it is null\) or `false` \(the key exists and its value is not null\)\.

You can not use a [policy variable](reference_policies_variables.md) with the `Null` condition operator\.

For example, you can use this condition operator to determine whether a user is using their own credentials for the operation or temporary credentials\. If the user is using temporary credentials, then the key `aws:TokenIssueTime` exists and has a value\. The following example shows a condition that states that the user must not be using temporary credentials \(the key must not exist\) for the user to use the Amazon EC2 API\.

```
{
  "Version": "2012-10-17",
  "Statement":{
      "Action":"ec2:*",
      "Effect":"Allow",
      "Resource":"*",
      "Condition":{"Null":{"aws:TokenIssueTime":"true"}}
  }
}
```