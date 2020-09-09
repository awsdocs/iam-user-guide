# Amazon S3: Allows Amazon Cognito users to access objects in their bucket<a name="reference_policies_examples_s3_cognito-bucket"></a>

This example shows how you might create a policy that allows Amazon Cognito users to access objects in a specific S3 bucket\. This policy allows access only to objects with a name that includes `cognito`, the name of the application, and the federated user's ID, represented by the $\{cognito\-identity\.amazonaws\.com:sub\} variable\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

**Note**  
The 'sub' value used in the object key is not the user's sub value in the User Pool, it is the identity id associated with the user in the Identity Pool\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ListYourObjects",
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": ["arn:aws:s3:::bucket-name"],
            "Condition": {
                "StringLike": {
                    "s3:prefix": ["cognito/application-name/${cognito-identity.amazonaws.com:sub}"]
                }
            }
        },
        {
            "Sid": "ReadWriteDeleteYourObjects",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::bucket-name/cognito/application-name/${cognito-identity.amazonaws.com:sub}",
                "arn:aws:s3:::bucket-name/cognito/application-name/${cognito-identity.amazonaws.com:sub}/*"
            ]
        }
    ]
}
```

Amazon Cognito provides authentication, authorization, and user management for your web and mobile apps\. Your users can sign in directly with a user name and password, or through a third party such as Facebook, Amazon, or Google\. 

The two main components of Amazon Cognito are user pools and identity pools\. User pools are user directories that provide sign\-up and sign\-in options for your app users\. Identity pools enable you to grant your users access to other AWS services\. You can use identity pools and user pools separately or together\. 

For more information about Amazon Cognito, see the following:
+ [Amazon Cognito Identity](https://docs.aws.amazon.com/mobile/sdkforandroid/developerguide/cognito-auth.html) in the *AWS Mobile SDK for Android Developer Guide*
+ [Amazon Cognito Identity](https://docs.aws.amazon.com/mobile/sdkforios/developerguide/cognito-auth.html) in the *AWS Mobile SDK for iOS Developer Guide*