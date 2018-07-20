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
            "Condition": {
                "StringLike": {
                    "s3:prefix": ["cognito/<APPLICATION-NAME>/"]
                }
            }
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

Amazon Cognito provides authentication, authorization, and user management for your web and mobile apps\. Your users can sign in directly with a user name and password, or through a third party such as Facebook, Amazon, or Google\. 

The two main components of Amazon Cognito are user pools and identity pools\. User pools are user directories that provide sign\-up and sign\-in options for your app users\. Identity pools enable you to grant your users access to other AWS services\. You can use identity pools and user pools separately or together\. 

For more information about Amazon Cognito, see the following:
+ [Amazon Cognito Identity](http://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html) in the *AWS Mobile SDK for Android Developer Guide*
+ [Amazon Cognito Identity](http://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html) in the *AWS Mobile SDK for iOS Developer Guide*