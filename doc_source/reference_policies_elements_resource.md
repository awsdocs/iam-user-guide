# IAM JSON policy elements: Resource<a name="reference_policies_elements_resource"></a>

The `Resource` element specifies the object or objects that the statement covers\. Statements must include either a `Resource` or a `NotResource` element\. You specify a resource using an ARN\. For more information about the format of ARNs, see [IAM ARNs](reference_identifiers.md#identifiers-arns)\.

Each service has its own set of resources\. Although you always use an ARN to specify a resource, the details of the ARN for a resource depend on the service and the resource\. For information about how to specify a resource, refer to the documentation for the service whose resources you're writing a statement for\.

**Note**  
Some services do not let you specify actions for individual resources; instead, any actions that you list in the `Action` or `NotAction` element apply to all resources in that service\. In these cases, you use the wildcard `*` in the `Resource` element\. 

The following example refers to a specific Amazon SQS queue\.

```
"Resource": "arn:aws:sqs:us-east-2:account-ID-without-hyphens:queue1"
```

The following example refers to the IAM user named Bob in an AWS account\.

```
"Resource": "arn:aws:iam::account-ID-without-hyphens:user/Bob"
```

## Using wildcards in resource ARNs<a name="reference_policies_elements_resource_wildcards"></a>

You can use wildcards as part of the resource ARN\. You can use wildcard characters \(\* and ?\) within any ARN segment \(the parts separated by colons\)\. An asterisk \(\*\) represents any combination of characters and a question mark \(?\) represents any single character\. You can use multiple \* or ? characters in each segment\. The following example refers to all IAM users whose path is `/accounting`\. 

```
"Resource": "arn:aws:iam::account-ID-without-hyphens:user/accounting/*"
```

The following example refers to all items within a specific Amazon S3 bucket\.

```
"Resource": "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*"
```

The asterisk \(\*\) character can expand to replace everything within a segment, including characters like a forward slash \(/\) that may otherwise appear to be a delimiter within a given service’s namespace\. For example, consider the following Amazon S3 ARN \(the same wildcard expansion logic applies to all services\)\.

```
"Resource": "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*/test/*"
```

The wildcards in the ARN apply to all of the following objects in the bucket, not only the first object listed\.

```
DOC-EXAMPLE-BUCKET/1/test/object.jpg
DOC-EXAMPLE-BUCKET/1/2/test/object.jpg
DOC-EXAMPLE-BUCKET/1/2/test/3/object.jpg 
DOC-EXAMPLE-BUCKET/1/2/3/test/4/object.jpg
DOC-EXAMPLE-BUCKET/1///test///object.jpg
DOC-EXAMPLE-BUCKET/1/test/.jpg
DOC-EXAMPLE-BUCKET//test/object.jpg
DOC-EXAMPLE-BUCKET/1/test/
```

Consider the last two objects in the previous list\. An Amazon S3 object name can validly begin or end with the conventional delimiter forward slash \(/\) character\. While "/" works as a delimiter, there is no specific significance when this character is used within a resource ARN\. It is treated the same as any other valid character\. The ARN would not match the following objects:

```
DOC-EXAMPLE-BUCKET/1-test/object.jpg
DOC-EXAMPLE-BUCKET/test/object.jpg
DOC-EXAMPLE-BUCKET/1/2/test.jpg
```

## Specifying multiple resources<a name="reference_policies_elements_resource_multiple-resources"></a>

You can specify multiple resources\. The following example refers to two DynamoDB tables\.

```
"Resource": [
    "arn:aws:dynamodb:us-east-2:account-ID-without-hyphens:table/books_table",
    "arn:aws:dynamodb:us-east-2:account-ID-without-hyphens:table/magazines_table"
]
```

## Using policy variables in resource ARNs<a name="reference_policies_elements_resource_policy-variables"></a>

In the `Resource` element, you can use JSON [policy variables](reference_policies_variables.md) in the part of the ARN that identifies the specific resource \(that is, in the trailing part of the ARN\)\. For example, you can use the key `{aws:username}` as part of a resource ARN to indicate that the current user's name should be included as part of the resource's name\. The following example shows how you can use the `{aws:username}` key in a `Resource` element\. The policy allows access to a Amazon DynamoDB table that matches the current user's name\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "dynamodb:*",
    "Resource": "arn:aws:dynamodb:us-east-2:ACCOUNT-ID-WITHOUT-HYPHENS:table/${aws:username}"
  }
}
```

For more information about JSON policy variables, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.