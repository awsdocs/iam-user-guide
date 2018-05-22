# Permissions for GetFederationToken<a name="id_credentials_temp_control-access_getfederationtoken"></a>

The permissions for the temporary security credentials returned by `GetFederationToken` are determined by a combination of the following: 
+ The policy or policies that are attached to the IAM user whose credentials are used to call `GetFederationToken`\.
+ The policy that is passed as a parameter in the call\. 

The passed policy is attached to the temporary security credentials that result from the `GetFederationToken` API call—that is, to the *federated user*\. When the federated user makes an AWS request, AWS evaluates the policy attached to the federated user in combination with the policy or policies attached to the IAM user whose credentials were used to call `GetFederationToken`\. 

**Important**  
AWS allows the federated user's request only when both the attached policy ***and*** the IAM user policy explicitly allow the federated user to perform the requested action\. 

The permissions assigned to the federated user are defined in one of two places: 
+ The policy passed as a parameter of the `GetFederationToken` API call\. \(This is most common\.\)
+ A resource\-based policy that explicitly names the federated user in the `Principal` element of the policy\. \(This is less common\.\)

This means that in most cases if you do not pass a policy with the `GetFederationToken` API call, the resulting temporary security credentials have no permissions\. The only exception is when the credentials are used to access a resource that has a resource\-based policy that specifically references the federated user in the `Principal` element of the policy\. 

The following figures show a visual representation of how the policies interact to determine permissions for the temporary security credentials returned by a call to `GetFederationToken`\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

## Example: Assigning Permissions Using GetFederationToken<a name="permissions-get-federation-token-example"></a>

You can use the `GetFederationToken` API action with different kinds of policies\. Here are a few examples\.

### Policy Attached to the IAM User<a name="permissions-get-federation-token-example-iam-user"></a>

In this example, you have a browser\-based client application that relies on two back\-end web services\. One back\-end service is your own authentication server that uses your own identity system to authenticate the client application\. The other back\-end service is an AWS service that provides some of the client application's functionality\. The client application is authenticated by your server, and your server creates or retrieves the appropriate permission policy\. Your server then calls the `GetFederationToken` API to obtain temporary security credentials, and returns those credentials to the client application\. The client application can then make requests directly to the AWS service with the temporary security credentials\. This architecture allows the client application to make AWS requests without embedding long\-term AWS credentials\.

Your authentication server calls the `GetFederationToken` API with the long\-term security credentials of an IAM user named `token-app`, but the long\-term IAM user credentials remain on your server and are never distributed to the client\. The following example policy is attached to the `token-app` IAM user and defines the broadest set of permissions that your federated users \(clients\) will need\. Note that the `sts:GetFederationToken` permission is required for your authentication service to obtain temporary security credentials for the federated users\.

**Note**  
AWS provides a sample Java application to serve this purpose, which you can download here: [Token Vending Machine for Identity Registration \- Sample Java Web Application](https://aws.amazon.com/code/7351543942956566)\.

**Example Policy Attached to IAM User `token-app` that Calls `GetFederationToken`**  

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
      "Action": "dynamodb:*",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "sqs:*",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "sns:*",
      "Resource": "*"
    }
  ]
}
```

Although the preceding policy grants several permissions, by itself it is not enough to grant any permissions to the federated user\. If the IAM user that has the permissions defined in the preceding policy calls `GetFederationToken` and does not pass a policy as a parameter of the API call, the resulting federated user has no effective permissions\. 

### Policy Passed as Parameter<a name="permissions-get-federation-token-example-passed-policy"></a>

The most common way to ensure that the federated user is assigned appropriate permission is to pass a policy as a parameter of the `GetFederationToken` API call\. Expanding on our previous example, imagine that `GetFederationToken` is called with the credentials of the IAM user `token-app` and imagine that the following policy is passed as a parameter of the API call\. The federated user would have permission to perform only these actions: 
+ List the contents of the Amazon S3 bucket named `productionapp`\. 
+ Perform the Amazon S3 `GetObject`, `PutObject`, and `DeleteObject` actions on items in the `productionapp` bucket\.

The federated user is assigned these permissions because the permissions have been granted to both the IAM user who called `GetFederationToken` \(via the policy attached to the IAM user\) ***and*** to the federated user \(via the passed policy\)\. The federated user could not perform actions in Amazon SNS, Amazon SQS, Amazon DynamoDB, or in any S3 bucket except `productionapp`, even though those permissions are granted to the IAM user associated with the `GetFederationToken` call\. This is true because the effective permissions for the federated user consist of only those permissions that are granted in both the IAM user policy ***and*** the passed policy\. 

**Example Policy Passed as Parameter of `GetFederationToken` API call**  

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

### Resource\-based Policies<a name="permissions-get-federation-token-resource-based-policy"></a>

Some AWS resources support resource\-based policies, and these policies provide another mechanism to grant permissions directly to a federated user\. Only some AWS services support resource\-based policies\. For example, Amazon S3 has buckets, Amazon SNS has topics, and Amazon SQS has queues that you can attach policies to\. For a list of all services that support resource\-based policies, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and review the "Resource Based" column of the tables\. If you use one of these services and resource\-based policies makes sense for your scenario, you assign permissions directly to a federated user by specifying the Amazon Resource Name of the federated user in the `Principal` element of the resource\-based policy\. The following example illustrates this\. The following example expands on the previous examples, using an S3 bucket named `productionapp`\. 

The following policy is attached to the bucket\. The policy allows a federated user named Carol to access the bucket\. When the following resource\-based policy is in place, and the example policy described earlier is attached to IAM user `token-app`, the federated user named Carol has permission to perform the `s3:GetObject`, `s3:PutObject`, and `s3:DeleteObject` actions on the bucket named `productionapp`\. This is true even when no policy is passed as a parameter of the `GetFederationToken` API call\. That's because in this case the federated user named Carol has been explicitly granted permissions by the following resource\-based policy\. 

Remember, a federated user is granted permissions only when those permissions are explicitly granted to both the IAM user ***and*** the federated user\. Permissions can be granted to the federated user by the policy passed as a parameter of the `GetFederationToken` API call, or by a resource\-based policy that explicitly names the federated user in the `Principal` element of the policy, as in the following example\.

**Example Bucket Policy that Allows Access to Federated User**  

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