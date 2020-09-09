# Examples of policies for delegating access<a name="id_roles_create_policy-examples"></a>

The following examples show how you can allow or grant an AWS account access to the resources in another AWS account\. To learn how to create an IAM policy using these example JSON policy documents, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

**Topics**
+ [Using roles to delegate access to another AWS account's resources](#example-delegate-xaccount-rolesapi)
+ [Using a policy to delegate access to services](#id_roles_create_policy-examples-access-to-services)
+ [Using a resource\-based policy to delegate access to an Amazon S3 bucket in another account](#example-delegate-xaccount-S3)
+ [Using a resource\-based policy to delegate access to an Amazon SQS queue in another account](#example-delegate-xaccount-SQS)
+ [Cannot delegate access when the account is denied access](#example-delegate-xaccount-SQS-denied)

## Using roles to delegate access to another AWS account's resources<a name="example-delegate-xaccount-rolesapi"></a>

 For a tutorial that shows how to use IAM roles to grant users in one account access to AWS resources that are in another account, see [IAM Tutorial: Delegate access across AWS accounts using IAM roles](tutorial_cross-account-with-roles.md)\. 

**Important**  
You can include the ARN for a specific role or user in the `Principal` element of a role trust policy\. When you save the policy, AWS transforms the ARN to a unique principal ID\. This helps mitigate the risk of someone escalating their privileges by removing and recreating the role or user\. You don't normally see this ID in the console, because there is also a reverse transformation back to the ARN when the trust policy is displayed\. However, if you delete the role or user, then the relationship is broken\. The policy no longer applies, even if you recreate the user or role because it does not match the principal ID stored in the trust policy\. When this happens, the principal ID shows up in the console because AWS can no longer map it back to an ARN\. The result is that if you delete and recreate a user or role referenced in a trust policy's `Principal` element, you must edit the role to replace the ARN\. It is transformed into the new principal ID when you save the policy\.

## Using a policy to delegate access to services<a name="id_roles_create_policy-examples-access-to-services"></a>

The following example shows a policy that can be attached to a role\. The policy enables two services, Amazon EMR and AWS Data Pipeline, to assume the role\. The services can then perform any tasks granted by the permissions policy assigned to the role \(not shown\)\. To specify multiple service principals, you do not specify two `Service` elements; you can have only one\. Instead, you use an array of multiple service principals as the value of a single `Service` element\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": [
          "elasticmapreduce.amazonaws.com",
          "datapipeline.amazonaws.com"
        ]
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

## Using a resource\-based policy to delegate access to an Amazon S3 bucket in another account<a name="example-delegate-xaccount-S3"></a>

In this example, account A uses a resource\-based policy \(an Amazon S3 [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucketPolicies.html)\) to grant account B full access to account A's S3 bucket\. Then account B creates an IAM user policy to delegate that access to account A's bucket to one of the users in account B\. 

The S3 bucket policy in account A might look like the following policy\. In this example, account A's S3 bucket is named *mybucket*, and account B's account number is 111122223333\. It does not specify any individual users or groups in account B, only the account itself\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Sid": "AccountBAccess1",
    "Effect": "Allow",
    "Principal": {"AWS": "111122223333"},
    "Action": "s3:*",
    "Resource": [
      "arn:aws:s3:::mybucket",
      "arn:aws:s3:::mybucket/*"
    ]
  }
}
```

Alternatively, account A can use Amazon S3 [Access Control Lists \(ACLs\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html) to grant account B access to an S3 bucket or a single object within a bucket\. In that case, the only thing that changes is how account A grants access to account B\. Account B still uses a policy to delegate access to an IAM group in account B, as described in the next part of this example\. For more information about controlling access on S3 buckets and objects, go to [Access Control](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingAuthAccess.html) in the *Amazon Simple Storage Service Developer Guide*\. 

The administrator of account B might create the following policy sample\. The policy allows read access to a group or user in account B\. The preceding policy grants access to account B\. However, individual groups and users in account B cannot access the resource until a group or user policy explicitly grants permissions to the resource\. The permissions in this policy can only be a subset of those in the preceding cross\-account policy\. Account B cannot grant more permissions to its groups and users than account A granted to account B in the first policy\. In this policy, the `Action` element is explicitly defined to allow only `List` actions, and the `Resource` element of this policy matches the `Resource` for the bucket policy implemented by account A\.

To implement this policy account B uses IAM to attach it to the appropriate user \(or group\) in account B\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "s3:List*",
    "Resource": [
      "arn:aws:s3:::mybucket",
      "arn:aws:s3:::mybucket/*"
    ]
  }
}
```

## Using a resource\-based policy to delegate access to an Amazon SQS queue in another account<a name="example-delegate-xaccount-SQS"></a>

In the following example, account A has an Amazon SQS queue that uses a resource\-based policy attached to the queue to grant queue access to account B\. Then account B uses an IAM group policy to delegate access to a group in account B\. 

The following example queue policy gives account B permission to perform the `SendMessage` and `ReceiveMessage` actions on account A's queue named *queue1*, but only between noon and 3:00 p\.m\. on November 30, 2014\. Account B's account number is 1111\-2222\-3333\. Account A uses Amazon SQS to implement this policy\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {"AWS": "111122223333"},
    "Action": [
      "sqs:SendMessage",
      "sqs:ReceiveMessage"
    ],
    "Resource": ["arn:aws:sqs:*:123456789012:queue1"],
    "Condition": {
      "DateGreaterThan": {"aws:CurrentTime": "2014-11-30T12:00Z"},
      "DateLessThan": {"aws:CurrentTime": "2014-11-30T15:00Z"}
    }
  }
}
```

Account B's policy for delegating access to a group in account B might look like the following example\. Account B uses IAM to attach this policy to a group \(or user\)\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "sqs:*",
    "Resource": "arn:aws:sqs:*:123456789012:queue1"
  }
}
```

In the preceding IAM user policy example, account B uses a wildcard to grant its user access to all Amazon SQS actions on account A's queue\. However account B can delegate access only to the extent that account B has been granted access\. The account B group that has the second policy can access the queue only between noon and 3:00 p\.m\. on November 30, 2014\. The user can only perform the `SendMessage` and `ReceiveMessage` actions, as defined in account A's Amazon SQS queue policy\. 

## Cannot delegate access when the account is denied access<a name="example-delegate-xaccount-SQS-denied"></a>

An AWS account cannot delegate access to another account's resources if the other account has explicitly denied access to the user's parent account\. The deny propagates to the users under that account whether or not the users have existing policies granting them access\.

For example, account A writes a bucket policy on account A's S3 bucket that explicitly denies account B access to account A's bucket\. But account B writes an IAM user policy that grants a user in account B access to account A's bucket\. The explicit deny applied to account A's S3 bucket propagates to the users in account B\. It overrides the IAM user policy granting access to the user in account B\. \(For detailed information how permissions are evaluated, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.\) 

Account A's bucket policy might look like the following policy\. In this example, account A's S3 bucket is named *mybucket*, and account B's account number is 1111\-2222\-3333\. Account A uses Amazon S3 to implement this policy\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Sid": "AccountBDeny",
    "Effect": "Deny",
    "Principal": {"AWS": "111122223333"},
    "Action": "s3:*",
    "Resource": "arn:aws:s3:::mybucket/*"
  }
}
```

This explicit deny overrides any policies in account B that provide permission to access the S3 bucket in account A\. 