# IAM JSON policy elements: Action<a name="reference_policies_elements_action"></a>

The `Action` element describes the specific action or actions that will be allowed or denied\. Statements must include either an `Action` or `NotAction` element\. Each AWS service has its own set of actions that describe tasks that you can perform with that service\. For example, the list of actions for Amazon S3 can be found at [Specifying Permissions in a Policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-with-s3-actions.html) in the *Amazon Simple Storage Service Developer Guide*, the list of actions for Amazon EC2 can be found in the [Amazon EC2 API Reference](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/query-apis.html), and the list of actions for AWS Identity and Access Management can be found in the [IAM API Reference](https://docs.aws.amazon.com/IAM/latest/APIReference/API_Operations.html)\. To find the list of actions for other services, consult the API reference [documentation](http://aws.amazon.com/documentation) for the service\.

You specify a value using a service namespace as an action prefix \(`iam`, `ec2`, `sqs`, `sns`, `s3`, etc\.\) followed by the name of the action to allow or deny\. The name must match an action that is supported by the service\. The prefix and the action name are case insensitive\. For example, `iam:ListAccessKeys` is the same as `IAM:listaccesskeys`\. The following examples show `Action` elements for different services\.

**Amazon SQS action**

```
"Action": "sqs:SendMessage"
```

**Amazon EC2 action**

```
"Action": "ec2:StartInstances"
```

**IAM action**

```
"Action": "iam:ChangePassword"
```

**Amazon S3 action**

```
"Action": "s3:GetObject"
```

You can specify multiple values for the `Action` element\.

```
"Action": [ "sqs:SendMessage", "sqs:ReceiveMessage", "ec2:StartInstances", "iam:ChangePassword", "s3:GetObject" ]
```

You can use a wildcard \(\*\) to give access to all the actions the specific AWS product offers\. For example, the following `Action` element applies to all S3 actions\.

```
"Action": "s3:*"
```

You can also use wildcards \(\*\) as part of the action name\. For example, the following `Action` element applies to all IAM actions that include the string `AccessKey`, including `CreateAccessKey`, `DeleteAccessKey`, `ListAccessKeys`, and `UpdateAccessKey`\.

```
"Action": "iam:*AccessKey*"
```

Some services let you limit the actions that are available\. For example, Amazon SQS lets you make available just a subset of all the possible Amazon SQS actions\. In that case, the `*` wildcard doesn't allow complete control of the queue; it allows only the subset of actions that you've shared\. For more information, see [Understanding Permissions](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/acp-overview.html#PermissionTypes) in the *Amazon Simple Queue Service Developer Guide*\.