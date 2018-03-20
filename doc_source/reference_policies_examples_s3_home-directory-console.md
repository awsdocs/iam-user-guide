# Amazon S3: Allows IAM Users Access to Their S3 Home Directory, Programmatically and In the Console<a name="reference_policies_examples_s3_home-directory-console"></a>

This example shows how you might create a policy that allows IAM users to access their own home directory in S3\. The home directory is a bucket that includes a `home` folder and folders for individual users\. This policy also provides the permissions necessary to complete this action on the console\. To use this policy, replace the red text in the example policy with your own information\.

Use `${aws:userid}` instead of `${aws:username}` to allows a federated user with IAM role to access their own home directory in S3. The value for the aws:userid variable should be "role id:caller-specified-name".

+ role-id is a unique identifier assigned to each role at creation. You can display the role ID with the AWS CLI command: `aws iam get-role --role-name rolename`   
+ caller-specified-name names that are passed by the calling process (such as an application or service) when it makes a call to get temporary credentials.

For example, if you specify the friendly name Bob, the correct format would be "AROAXXT2NJT7D3SIQN7Z6:Bob". This names your session and allows access to the S3 bucket with a matching prefix. 

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
      "Resource": "arn:aws:s3:::<BUCKET-NAME>",
      "Condition": {"StringLike": {"s3:prefix": [
        "",
        "home/",
        "home/${aws:username}/*"
      ]}}
    },
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::<BUCKET-NAME>/home/${aws:username}",
        "arn:aws:s3:::<BUCKET-NAME>/home/${aws:username}/*"
      ]
    }
  ]
}
```
