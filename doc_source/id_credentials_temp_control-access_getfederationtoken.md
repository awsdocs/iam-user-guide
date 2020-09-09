# Permissions for GetFederationToken<a name="id_credentials_temp_control-access_getfederationtoken"></a>

The `GetFederationToken` operation is called by an IAM user and returns temporary credentials for that user\. This operation *federates* the user\. The permissions assigned a federated user are defined in one of two places: 
+ The session policies passed as a parameter of the `GetFederationToken` API call\. \(This is most common\.\)
+ A resource\-based policy that explicitly names the federated user in the `Principal` element of the policy\. \(This is less common\.\)

Session policies are advanced policies that you pass as parameters when you programmatically create a temporary session\. When you create a federated user session and pass session policies, the resulting session's permissions are the intersection of the IAM user's identity\-based policy and the session policies\. You cannot use the session policy to grant more permissions than those allowed by the identity\-based policy of the user that is being federated\.

In most cases if you do not pass a policy with the `GetFederationToken` API call, the resulting temporary security credentials have no permissions\. However, a resource\-based policy can provide additional permissions for the session\. You can access a resource with a resource\-based policy that specifies your session as the allowed principal\. 

The following figures show a visual representation of how the policies interact to determine permissions for the temporary security credentials returned by a call to `GetFederationToken`\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

## Example: Assigning permissions using GetFederationToken<a name="permissions-get-federation-token-example"></a>

You can use the `GetFederationToken` API action with different kinds of policies\. Here are a few examples\.

### Policy attached to the IAM user<a name="permissions-get-federation-token-example-iam-user"></a>

In this example, you have a browser\-based client application that relies on two backend web services\. One backend service is your own authentication server that uses your own identity system to authenticate the client application\. The other backend service is an AWS service that provides some of the client application's functionality\. The client application is authenticated by your server, and your server creates or retrieves the appropriate permissions policy\. Your server then calls the `GetFederationToken` API to obtain temporary security credentials, and returns those credentials to the client application\. The client application can then make requests directly to the AWS service with the temporary security credentials\. This architecture allows the client application to make AWS requests without embedding long\-term AWS credentials\.

Your authentication server calls the `GetFederationToken` API with the long\-term security credentials of an IAM user named `token-app`\. But the long\-term IAM user credentials remain on your server and are never distributed to the client\. The following example policy is attached to the `token-app` IAM user and defines the broadest set of permissions that your federated users \(clients\) will need\. Note that the `sts:GetFederationToken` permission is required for your authentication service to obtain temporary security credentials for the federated users\.

**Note**  
AWS provides a sample Java application to serve this purpose, which you can download here: [Token Vending Machine for Identity Registration \- Sample Java Web Application](https://aws.amazon.com/code/7351543942956566)\.

**Example policy attached to IAM user `token-app` that calls `GetFederationToken`**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "sts:GetFederationToken",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "dynamodb:ListTables",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "sqs:ReceiveMessage",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "sns:ListSubscriptions",
      "Resource": "*"
    }
  ]
}
```

The preceding policy grants several permissions to the IAM user\. However, this policy alone doesn't grant any permissions to the federated user\. If this IAM user calls `GetFederationToken` and does not pass a policy as a parameter of the API call, the resulting federated user has no effective permissions\. 

### Session policy passed as parameter<a name="permissions-get-federation-token-example-passed-policy"></a>

The most common way to ensure that the federated user is assigned appropriate permission is to pass session policies in the `GetFederationToken` API call\. Expanding on the previous example, imagine that `GetFederationToken` is called with the credentials of the IAM user `token-app`\. Then imagine that the following session policy is passed as a parameter of the API call\. The resulting federated user has permission to list the contents of the Amazon S3 bucket named `productionapp`\. The user can't perform the Amazon S3 `GetObject`, `PutObject`, and `DeleteObject` actions on items in the `productionapp` bucket\.

The federated user is assigned these permissions because the permissions are the intersection of the IAM user policies and the session policies that you pass\.

The federated user could not perform actions in Amazon SNS, Amazon SQS, Amazon DynamoDB, or in any S3 bucket except `productionapp`\. These actions are denied even though those permissions are granted to the IAM user that is associated with the `GetFederationToken` call\.

**Example session policy passed as parameter of `GetFederationToken` API call**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListBucket"],
      "Resource": ["arn:aws:s3:::productionapp"]
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:DeleteObject"
      ],
      "Resource": ["arn:aws:s3:::productionapp/*"]
    }
  ]
}
```

### Resource\-based policies<a name="permissions-get-federation-token-resource-based-policy"></a>

Some AWS resources support resource\-based policies, and these policies provide another mechanism to grant permissions directly to a federated user\. Only some AWS services support resource\-based policies\. For example, Amazon S3 has buckets, Amazon SNS has topics, and Amazon SQS has queues that you can attach policies to\. For a list of all services that support resource\-based policies, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and review the "Resource\-based policies" column of the tables\. You can use resource\-based policies to assign permissions directly to a federated user\. Do this by specifying the Amazon Resource Name \(ARN\) of the federated user in the `Principal` element of the resource\-based policy\. The following example illustrates this and expands on the previous examples, using an S3 bucket named `productionapp`\. 

The following resource\-based policy is attached to the bucket\. This bucket policy allows a federated user named Carol to access the bucket\. When the example policy described earlier is attached to the `token-app` IAM user, the federated user named Carol has permission to perform the `s3:GetObject`, `s3:PutObject`, and `s3:DeleteObject` actions on the bucket named `productionapp`\. This is true even when no session policy is passed as a parameter of the `GetFederationToken` API call\. That's because in this case the federated user named Carol has been explicitly granted permissions by the following resource\-based policy\. 

Remember, a federated user is granted permissions only when those permissions are explicitly granted to both the IAM user ***and*** the federated user\. Permissions can be granted to the federated user by the session policy passed as a parameter of the `GetFederationToken` API call\. They can also be granted by a resource\-based policy that explicitly names the federated user in the `Principal` element of the policy, as in the following example\.

**Example bucket policy that allows access to federated user**  

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Principal": {"AWS": "arn:aws:sts::ACCOUNT-ID-WITHOUT-HYPHENS:federated-user/Carol"},
    "Effect": "Allow",
    "Action": [
      "s3:GetObject",
      "s3:PutObject",
      "s3:DeleteObject"
    ],
    "Resource": ["arn:aws:s3:::productionapp/*"]
  }
}
```