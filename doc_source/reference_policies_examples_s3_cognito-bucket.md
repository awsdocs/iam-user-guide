# Amazon S3: Allows Amazon Cognito Users to Access Objects in Their Bucket<a name="reference_policies_examples_s3_cognito-bucket"></a>

This example shows how you might create a policy that allows Amazon Cognito users to access objects in a specific S3 bucket\. This policy allows access only to objects with a name that includes `cognito`, the name of the application, and the federated user's ID, represented by the $\{cognito\-identity\.amazonaws\.com:sub\} variable\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\. To use this policy, replace the red text in the example policy with your own information\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListBucket"],
      "Resource": ["arn:aws:s3:::<BUCKET-NAME>"],
      "Condition": {"StringLike": {"s3:prefix": ["cognito/<APPLICATION-NAME>/"]}}
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:DeleteObject"
      ],
      "Resource": [
        "arn:aws:s3:::<BUCKET-NAME>/cognito/<APPLICATION-NAME>/${cognito-identity.amazonaws.com:sub}",
        "arn:aws:s3:::<BUCKET-NAME>/cognito/<APPLICATION-NAME>/${cognito-identity.amazonaws.com:sub}/*"
      ]
    }
  ]
}
```

Amazon Cognito is an easy way to use web identity federation in your mobile app\. Using Amazon Cognito, you can provide access to AWS resources for users who have signed in to your app using a third\-party identity provider like Login with Amazon, Facebook, Google, or any Open\-ID Connect \(OIDC\) compatible identity provider instead of using an IAM user\. To use Amazon Cognito for web identity federation, you create a role that determines what permissions the federated user will have\. You can create one role for authenticated users\. If your app allows unauthenticated \(guest\) users, you can create a second role that defines the permissions for those users\. 

For more information about Amazon Cognito, see the following:
+ [Amazon Cognito Identity](http://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html) in the *AWS Mobile SDK for Android Developer Guide*
+ [Amazon Cognito Identity](http://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html) in the *AWS Mobile SDK for iOS Developer Guide*