# Identifying users with web identity federation<a name="id_roles_providers_oidc_user-id"></a>

When you create access policies in IAM, it's often useful to be able to specify permissions based on configured apps and on the ID of users who have authenticated using an external identity provider \(IdP\)\. For example, your mobile app that's using web identity federation might keep information in Amazon S3 using a structure like this:

```
myBucket/app1/user1
myBucket/app1/user2
myBucket/app1/user3
...
myBucket/app2/user1
myBucket/app2/user2
myBucket/app2/user3
...
```

You might also want to additionally distinguish these paths by provider\. In that case, the structure might look like the following \(only two providers are listed to save space\):

```
myBucket/Amazon/app1/user1
myBucket/Amazon/app1/user2
myBucket/Amazon/app1/user3
...
myBucket/Amazon/app2/user1
myBucket/Amazon/app2/user2
myBucket/Amazon/app2/user3

myBucket/Facebook/app1/user1
myBucket/Facebook/app1/user2
myBucket/Facebook/app1/user3
...
myBucket/Facebook/app2/user1
myBucket/Facebook/app2/user2
myBucket/Facebook/app2/user3
...
```

For these structures, `app1` and `app2` represent different apps, such as different games, and each user of the app has a distinct folder\. The values for `app1` and `app2` might be friendly names that you assign \(for example, `mynumbersgame`\) or they might be the app IDs that the providers assign when you configure your app\. If you decide to include provider names in the path, those can also be friendly names like `Cognito`, `Amazon`, `Facebook`, and `Google`\. 

You can typically create the folders for `app1` and `app2` through the AWS Management Console, since the application names are static values\. That's true also if you include the provider name in the path, since the provider name is also a static value\. In contrast, the user\-specific folders \(*user1*, *user2*, *user3*, etc\.\) have to be created at run time from the app, using the user ID that's available in the `SubjectFromWebIdentityToken` value that is returned by the request to `AssumeRoleWithWebIdentity`\.

To write policies that allow exclusive access to resources for individual users, you can match the complete folder name, including the app name and provider name, if you're using that\. You can then include the following provider\-specific context keys that reference the user ID that the provider returns:
+ `cognito-identity.amazonaws.com:sub`
+ `www.amazon.com:user_id`
+ `graph.facebook.com:id`
+ `accounts.google.com:sub`

For OIDC providers, use the fully qualified URL of the OIDC provider with the subcontext key, like the following example:
+ `server.example.com:sub`

The following example shows a permission policy that grants access to a bucket in Amazon S3 only if the prefix for the bucket matches the string:

`myBucket/Amazon/mynumbersgame/user1`

The example assumes that the user is signed in using Login with Amazon, and that the user is using an app called `mynumbersgame`\. The user's unique ID is presented as an attribute called `user_id`\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListBucket"],
      "Resource": ["arn:aws:s3:::myBucket"],
      "Condition": {"StringLike": {"s3:prefix": ["Amazon/mynumbersgame/${www.amazon.com:user_id}/*"]}}
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:DeleteObject"
      ],
      "Resource": [
        "arn:aws:s3:::myBucket/amazon/mynumbersgame/${www.amazon.com:user_id}",
        "arn:aws:s3:::myBucket/amazon/mynumbersgame/${www.amazon.com:user_id}/*"
      ]
    }
  ]
}
```

You would create similar policies for users who sign in using Amazon Cognito, Facebook, Google, or another OpenID Connect–compatible IdP\. Those policies would use a different provider name as part of the path as well as different app IDs\.

For more information about the web identity federation keys available for condition checks in policies, see [Available keys for AWS web identity federation](reference_policies_iam-condition-keys.md#condition-keys-wif)\.