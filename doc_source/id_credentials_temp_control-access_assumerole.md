# Permissions for AssumeRole, AssumeRoleWithSAML, and AssumeRoleWithWebIdentity<a name="id_credentials_temp_control-access_assumerole"></a>

The permissions policy of the role that is being assumed determines the permissions for the temporary security credentials that are returned by `AssumeRole`, `AssumeRoleWithSAML`, and `AssumeRoleWithWebIdentity`\. You define these permissions when you create or update the role\. 

Optionally, you can pass inline or managed [session policies](access_policies.md#policies_session) as parameters of the `AssumeRole`, `AssumeRoleWithSAML`, or `AssumeRoleWithWebIdentity` API operations\. Session policies limit the permissions for the role's temporary credential session\. The resulting session's permissions are the intersection of the role's identity\-based policy and the session policies\. You can use the role's temporary credentials in subsequent AWS API calls to access resources in the account that owns the role\. You cannot use session policies to grant more permissions than those allowed by the identity\-based policy of the role that is being assumed\. To learn more about how AWS determines the effective permissions of a role, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.

![\[PermissionsWhenPassingRoles_Diagram\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/role_passed_policy_permissions.png)

The policies that are attached to the credentials that made the original call to `AssumeRole` are not evaluated by AWS when making the "allow" or "deny" authorization decision\. The user temporarily gives up its original permissions in favor of the permissions assigned by the assumed role\. In the case of the `AssumeRoleWithSAML` and `AssumeRoleWithWebIdentity` API operations, there are no policies to evaluate because the caller of the API is not an AWS identity\.

## Example: Assigning permissions using AssumeRole<a name="permissions-assume-role-example"></a>

You can use the `AssumeRole` API operation with different kinds of policies\. Here are a few examples\.

### Role permissions policy<a name="permissions-assume-role-example-role-access-policy"></a>

In this example, you call the `AssumeRole` API operation without specifying the session policy in the optional `Policy` parameter\. The permissions assigned to the temporary credentials are determined by the permissions policy of the role being assumed\. The following example permissions policy grants the role permission to list all objects that are contained in an S3 bucket named `productionapp`\. It also allows the role to get, put, and delete objects within that bucket\.

**Example role permissions policy**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::productionapp"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:DeleteObject"
      ],
      "Resource": "arn:aws:s3:::productionapp/*"
    }
  ]
}
```

### Session policy passed as a parameter<a name="permissions-assume-role-example-passed-policy"></a>

Imagine that you want to allow a user to assume the same role as in the previous example\. But in this case you want the role session to have permission only to get and put objects in the `productionapp` S3 bucket\. You do not want to allow them to delete objects\. One way to accomplish this is to create a new role and specify the desired permissions in that role's permissions policy\. Another way to accomplish this is to call the `AssumeRole` API and include session policies in the optional `Policy` parameter as part of the API operation\. The resulting session's permissions are the intersection of the role's identity\-based policies and the session policies\. Session policies cannot be used to grant more permissions than those allowed by the identity\-based policy of the role that is being assumed\. For more information about role session permissions, see [Session policies](access_policies.md#policies_session)\. 

After you retrieve the new session's temporary credentials, you can pass them to the user that you want to have those permissions\.

For example, imagine that the following policy is passed as a parameter of the API call\. The person using the session has permissions to perform only these actions: 
+ List all objects in the `productionapp` bucket\.
+ Get and put objects in the `productionapp` bucket\.

In the following session policy, the `s3:DeleteObject` permission is filtered out and the assumed session is not granted the `s3:DeleteObject` permission\. The policy sets the maximum permissions for the role session so that it overrides any existing permissions policies on the role\.

**Example session policy passed with `AssumeRole` API call**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::productionapp"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::productionapp/*"
    }
  ]
}
```

### Resource\-based policy<a name="permissions-assume-role-example-resource-based-policy"></a>

Some AWS resources support resource\-based policies, and these policies provide another mechanism to define permissions that affect temporary security credentials\. Only a few resources, like Amazon S3 buckets, Amazon SNS topics, and Amazon SQS queues support resource\-based policies\. The following example expands on the previous examples, using an S3 bucket named `productionapp`\. The following policy is attached to the bucket\. 

When you attach the following resource\-based policy to the `productionapp` bucket, *all* users are denied permission to delete objects from the bucket\. \(See the `Principal` element in the policy\.\) This includes all assumed role users, even though the role permissions policy grants the `DeleteObject` permission\. An explicit `Deny` statement always takes precedence over an `Allow` statement\.

**Example bucket policy**  

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Principal": {"AWS": "*"},
    "Effect": "Deny",
    "Action": "s3:DeleteObject",
    "Resource": "arn:aws:s3:::productionapp/*"
  }
}
```

For more information about how multiple policy types are combined and evaluated by AWS, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.