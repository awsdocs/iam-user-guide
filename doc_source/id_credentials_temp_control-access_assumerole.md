# Permissions for AssumeRole, AssumeRoleWithSAML, and AssumeRoleWithWebIdentity<a name="id_credentials_temp_control-access_assumerole"></a>

The permission policy of the role that is being assumed determines the permissions for the temporary security credentials returned by `AssumeRole`, `AssumeRoleWithSAML`, and `AssumeRoleWithWebIdentity`\. You define these permissions when you create or update the role\. 

Optionally, you can pass a separate policy as a parameter of the `AssumeRole`, `AssumeRoleWithSAML`, or `AssumeRoleWithWebIdentity` API call\. You use the passed policy to scope down the permissions assigned to the temporary security credentials—that is, to allow only a subset of the permissions that are allowed by the permission policy of the role\. You cannot use the passed policy to grant permissions that are in excess of those allowed by the permission policy of the role; it is a filter only\. If you do not pass a policy as a parameter of the `AssumeRole`, `AssumeRoleWithSAML`, or `AssumeRoleWithWebIdentity` API call, then the permissions attached to the temporary security credentials are the same as the permissions defined in the role permissions policy of the role that is being assumed\. 

When the temporary security credentials returned by `AssumeRole`, `AssumeRoleWithSAML`, and `AssumeRoleWithWebIdentity` are used to make AWS requests, AWS determines whether to allow or deny access by evaluating all of the following policies:
+ The combination of the role permission policy of the role that was assumed and the policy passed as a parameter to the API, as discussed previously\.
+ Any resource\-based policies \(such as an Amazon S3 bucket policy\) attached to the resource that is being accessed by the temporary security credentials\.

AWS uses all of these policies to arrive at an "allow" or "deny" authorization decision that follows the [IAM policy evaluation logic](reference_policies_evaluation-logic.md)\.

It is important to understand that the policies that are attached to the IAM user or the credentials that made the original call to `AssumeRole` are not evaluated by AWS when making the "allow" or "deny" authorization decision\. The user temporarily gives up its original permissions in favor of the permissions assigned by the assumed role\. In the case of the `AssumeRoleWithSAML` and `AssumeRoleWithWebIdentity` APIs, there are no policies to evaluate because the caller of the API is not an AWS identity\.

## Example: Assigning Permissions Using AssumeRole<a name="permissions-assume-role-example"></a>

You can use the `AssumeRole` API action with different kinds of policies\. Here are a few examples\.

### Role Permission Policy<a name="permissions-assume-role-example-role-access-policy"></a>

In this example, you call the `AssumeRole` API and do not include the optional `Policy` parameter\. The permissions assigned to the temporary security credentials that are returned by the call to `AssumeRole`—that is, the permissions assigned to the *assumed role user*—are determined by the permission policy of the role being assumed\. The following example is a role permission policy that grants the assumed role user permission to list all objects contained in an S3 bucket named `productionapp`, and to get, put, and delete objects within that bucket\.

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

Imagine that you want to allow a user to assume the same role as in the previous example, but you want the assumed role user to have permission only to get and put objects—but not delete objects—in the `productionapp` S3 bucket\. One way to accomplish this is to create a new role and specify the desired permissions in that role's permission policy\. Another way to accomplish this is to call the `AssumeRole` API and include the optional `Policy` parameter as part of the API call\. For example, imagine that the following policy is passed as a parameter of the API call\. The assumed role user would have permissions to perform only these actions: 
+ List all objects in the `productionapp` bucket\.
+ Get and put objects in the `productionapp` bucket\.

Note that because the `s3:DeleteObject` permission is not specified in the following policy, it is filtered out and the assumed role user is not granted the `s3:DeleteObject` permission\. When you pass a policy as a parameter of the `AssumeRole` API call, the effective permissions of the assumed role user consist of only those permissions that are granted both in the role permission policy ***and*** the passed policy\.

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

When you attach the following policy to the `productionapp` bucket, *all* users are denied permission to delete objects from the bucket \(note the `Principal` element in the policy\)\. This includes all assumed role users, even though the role permission policy grants the `DeleteObject` permission\. An explicit `Deny` statement always takes precedence over an explicit `Allow` statement\.

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

For more information about how multiple policies are combined and evaluated by AWS, see [IAM JSON Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.