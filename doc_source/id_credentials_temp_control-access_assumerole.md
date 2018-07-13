# Permissions for AssumeRole, AssumeRoleWithSAML, and AssumeRoleWithWebIdentity<a name="id_credentials_temp_control-access_assumerole"></a>

The permission policy of the role that is being assumed determines the permissions for the temporary security credentials that are returned by `AssumeRole`, `AssumeRoleWithSAML`, and `AssumeRoleWithWebIdentity`\. You define these permissions when you create or update the role\. 

Optionally, you can pass a JSON policy as a parameter of the `AssumeRole`, `AssumeRoleWithSAML`, or `AssumeRoleWithWebIdentity` API call\. This allows you to restrict permissions for that for the role's temporary credentials by setting a permissions boundary for the role\. You can use the role's temporary credentials in subsequent AWS API calls to access resources in the account that owns the role\. You cannot use the passed policy to grant permissions that are in excess of those allowed by the permissions policy of the role that is being assumed\. To learn more about how AWS determines the effective permissions of a role, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.

![\[PermissionsWhenPassingRoles_Diagram\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/role_passed_policy_permissions.png)

The policies that are attached to the credentials that made the original call to `AssumeRole` are not evaluated by AWS when making the "allow" or "deny" authorization decision\. The user temporarily gives up its original permissions in favor of the permissions assigned by the assumed role\. In the case of the `AssumeRoleWithSAML` and `AssumeRoleWithWebIdentity` API operations, there are no policies to evaluate because the caller of the API is not an AWS identity\.

## Example: Assigning Permissions Using AssumeRole<a name="permissions-assume-role-example"></a>

You can use the `AssumeRole` API operation with different kinds of policies\. Here are a few examples\.

### Role Permission Policy<a name="permissions-assume-role-example-role-access-policy"></a>

In this example, you call the `AssumeRole` API operation without the optional `Policy` parameter\. The permissions assigned to the temporary credentials are determined by the permissions policy of the role being assumed\. The following example permissions policy grants the role permission to list all objects that are contained in an S3 bucket named `productionapp`\. It also allows the role to get, put, and delete objects within that bucket\.

**Example Role Permission Policy**  

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

### Policy Passed as a Parameter<a name="permissions-assume-role-example-passed-policy"></a>

Imagine that you want to allow a user to assume the same role as in the previous example, but you want the assumed role user to have permission only to get and put objects in the `productionapp` S3 bucket\. You do not want to allow them to delete objects\. One way to accomplish this is to create a new role and specify the desired permissions in that role's permission policy\. Another way to accomplish this is to call the `AssumeRole` API and include a permissions boundary policy in the optional `Policy` parameter as part of the API call\. For example, imagine that the following policy is passed as a parameter of the API call\. The assumed role user would have permissions to perform only these actions: 
+ List all objects in the `productionapp` bucket\.
+ Get and put objects in the `productionapp` bucket\.

In the following policy, the `s3:DeleteObject` permission is filtered out and the assumed role user is not granted the `s3:DeleteObject` permission\. The policy sets the permissions boundary for the role so that it overrides any existing permissions policies on the role\.

**Example Policy Passed with `AssumeRole` API call**  

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

### Resource\-based Policy<a name="permissions-assume-role-example-resource-based-policy"></a>

Some AWS resources support resource\-based policies, and these policies provide another mechanism to define permissions that affect temporary security credentials\. Only a few resources, like Amazon S3 buckets, Amazon SNS topics, and Amazon SQS queues support resource\-based policies\. The following example expands on the previous examples, using an S3 bucket named `productionapp`\. The following policy is attached to the bucket\. 

When you attach the following policy to the `productionapp` bucket, *all* users are denied permission to delete objects from the bucket \(note the `Principal` element in the policy\)\. This includes all assumed role users, even though the role permission policy grants the `DeleteObject` permission\. An explicit `Deny` statement always takes precedence over an explicit `Allow` statement, and a policy set as the permissions boundary still overrides the bucket policy\.

**Example Bucket Policy**  

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

For more information about how multiple policies are combined and evaluated by AWS, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.